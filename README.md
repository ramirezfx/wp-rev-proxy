# wordpress with reverse-proxy
Get The file with

git clone https://github.com/ramirezfx/wp-rev-proxy.git

Navigate To The Working-Directory:

cd wp-rev-proxy

Change The File .env to your needs (DB-NAME, DW-PWD,...)

Change The File docker-compose.yml to your needs

Change The File nginx.conf to your needs

The config can be changed to serve multiple websites

Compile/Start The Container:

docker-compose up -d

Point Your Browser To http://yourhost:port (8080 by default) and start the installation

If you want to reload the nginx-config do this:

docker exec -it {yournginxcontainer} nginx -s reload

If you use all-in-one-wp-migration, you can use this procedure to restore:
Download and install the plugin:

https://freestuff.digital/wp-content/uploads/2020/07/all-in-one-wp-migration.6.77.zip

Copy the backup into the container:

docker cp {BACKUPFILE} {WP-CONTAINER}:/var/www/html/wp-content/ai1wm-backups

Change the correct permissions:

docker exec -it {WP-CONTAINER} chown www-data /var/www/html/wp-content/ai1wm-backups/{BACKUPFILE}

docker exec -it {WP-CONTAINER} chgrp www-data /var/www/html/wp-content/ai1wm-backups/{BACKUPFILE}
