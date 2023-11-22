# databases

## Set up MySQL server
1) Install docker on Ubuntu https://docs.docker.com/engine/install/ubuntu/
2) Install MySQL container https://dev.mysql.com/doc/mysql-installation-excerpt/8.0/en/linux-installation-docker.html
3) docker run --name=mysql2 -p 3306:3306 --mount type=bind,src=/root/all_docker_mounts/mysql1_mount_dirs/my.cnf,dst=/etc/my.cnf --mount type=bind,src=/root/all_docker_mounts/mysql1_mount_dirs/mysql,dst=/var/lib/mysql -d container-registry.oracle.com/mysql/community-server
4) The file my.cnf and mysql directory should be present on the host system
5) docker logs mysql2
7) ALTER USER 'root'@'localhost' IDENTIFIED BY 'root';
8) docker exec -it mysql2 bash
9) docker exec -it mysql2 mysql -u root -p
   1) To connect to db running in container you should change privileges
   2) 
      * `docker exec -it mysql2 mysql -u root -p`
      * `update mysql.user set host='%' where user='root' and host = 'localhost';`
      * `flush privileges;`
10) ..