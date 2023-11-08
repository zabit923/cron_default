# cron_default





Шпаргалка скрипта для автобэкапа 




1) установка

   sudo apt update
   sudo apt install cron



2) Создание файла скрипта

   sudo nano /path/to/backup_script.sh

   __________________________________________

   export PGPASSWORD="PASSWORD_PG"

   timestamp=$(date +"%Y%m%d%H%M%S")
   backup_dir="/path/to/backups_dir"
   backup_file="$backup_dir/db_backup_$timestamp.sql"
  
   pg_dump -h 127.0.0.1 -U user -d db -f $backup_file
  
   unset PGPASSWORD

   __________________________________________


4) Разрешение для скрипта

   sudo chmod +x /usr/local/bin/backup_postgresql.sh



5) Создание задачи

   sudo crontab -e
   0 0 * * * /path/to/backup_script.sh
   ( от root)


(чтоб проверить работу скрипта /path/to/backup_script.sh)
(чтоб проверить наличие задачи sudo crontab -l)





