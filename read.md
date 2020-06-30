이현룡
email :hylee@dshub.cloud
dshub.cloud
www.ocmkorea.com

docker.com  가입

cloud.google.com (GKE)  가입


Registry
	hub.docker.com
	private registry
	Google Containver registry(GCR)

Utility computing
	cluster, provisioning, partitioning
	grid, Autinomic, virtualization
	
Cloud computing

컨테이너는 프로세스
도커
리눅스의 커널관리
namespace 프로세스 디바이스관리
c-group 자원관리
chroot

CPU 	연산기 (지사? 커널)
Memory 	작업장 (
Storage(disk) 저장영역(SAN, DAS, NAS)

docker engine 설치 제한사항 64bit, kernel version 3.1 이상

docker Edition
	EE
	CE (stable, Edge)
	
sudo su -

Cannot connect to the Docker daemon at unix:///var/run/docker.sock. Is the docker daemon running?
jeff@jeff-VirtualBox:/$ sudo service docker start
jeff@jeff-VirtualBox:/$ docker version

os와 컨테이너 통신은 소켓통신

dockerd
docker-proxy
containerd


		 (docker registry)
docker.io/libaray/busy


docker pull gcr.io/google-samples/hello-app:1.0


OS변경해서 ubuntu 와 centos
docker pull ubuntu:latest
docker images
docker run -it ubuntu:latest echo 'test'
docker run -it ubuntu:latest bash   >> exit 하고 나오면 
exec -it sdsd  bash
컨트롤 p q 


root@07790e3d1a76:/# cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=20.04
DISTRIB_CODENAME=focal
DISTRIB_DESCRIPTION="Ubuntu 20.04 LTS"
if a
apt-get update
apt-get install net-tools
apt-get -y install iputils-ping

yum update


docker0 인터페이스 에 컨테이너 
brctl show

docker ps -a

docker run의 실체
있으면 실행하고

jeff@jeff-VirtualBox:/$ docker pull mysql:5.7
5.7: Pulling from library/mysql
8559a31e96f4: Pull complete
d51ce1c2e575: Pull complete
c2344adc4858: Pull complete
fcf3ceff18fc: Pull complete
16da0c38dc5b: Pull complete
b905d1797e97: Pull complete
4b50d1c6b05c: Pull complete
d85174a87144: Pull complete
a4ad33703fa8: Pull complete
f7a5433ce20d: Pull complete
3dcd2a278b4a: Pull complete
Digest: sha256:32f9d9a069f7a735e28fd44ea944d53c61f990ba71460c5c183e610854ca4854
Status: Downloaded newer image for mysql:5.7
jeff@jeff-VirtualBox:/$ docker images
REPOSITORY                        TAG                 IMAGE ID            CREATED             SIZE
busybox                           latest              c7c37e472d31        7 hours ago         1.22MB
ubuntu                            latest              74435f89ab78        13 days ago         73.9MB
centos                            latest              831691599b88        13 days ago         215MB
mysql                             5.7                 9cfcce23593a        2 weeks ago         448MB
nginx                             latest              881bd08c0b08        16 months ago       109MB
ubuntu                            <none>              47b19964fb50        16 months ago       88.1MB
gcr.io/google-samples/hello-app   1.0                 bc5c421ecd6c        2 years ago         9.86MB
jeff@jeff-VirtualBox:/$ docker run -it mysql:5.7 bash
root@e1bdf6d93c32:/# cat /etc/os-release
PRETTY_NAME="Debian GNU/Linux 10 (buster)"
NAME="Debian GNU/Linux"
VERSION_ID="10"
VERSION="10 (buster)"
VERSION_CODENAME=buster
ID=debian
HOME_URL="https://www.debian.org/"
SUPPORT_URL="https://www.debian.org/support"
BUG_REPORT_URL="https://bugs.debian.org/"
root@e1bdf6d93c32:/# /e
entrypoint.sh  etc/
root@e1bdf6d93c32:/# /e
entrypoint.sh  etc/
root@e1bdf6d93c32:/# /etc/init.d/mysql start
su: warning: cannot change directory to /home/mysql: No such file or directory
2020-06-30T03:04:29.477897Z 0 [Warning] TIMESTAMP with implicit DEFAULT value is deprecated. Please use --explicit_defaults_for_timestamp server option (see documentation for more details).
2020-06-30T03:04:29.686117Z 0 [Warning] InnoDB: New log files created, LSN=45790
2020-06-30T03:04:29.807465Z 0 [Warning] InnoDB: Creating foreign key constraint system tables.
2020-06-30T03:04:29.847872Z 0 [Warning] No existing UUID has been found, so we assume that this is the first time that this server has been started. Generating a new UUID: 6a313c42-ba7e-11ea-ba54-0242ac110004.
2020-06-30T03:04:29.849284Z 0 [Warning] Gtid table is not ready to be used. Table 'mysql.gtid_executed' cannot be opened.
2020-06-30T03:04:30.419098Z 0 [Warning] CA certificate ca.pem is self signed.
2020-06-30T03:04:30.450673Z 1 [Warning] root@localhost is created with an empty password ! Please consider switching off the --initialize-insecure option.
su: warning: cannot change directory to /home/mysql: No such file or directory
..
[info] MySQL Community Server 5.7.30 is started.
root@e1bdf6d93c32:/# mysql -uroot
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 2
Server version: 5.7.30 MySQL Community Server (GPL)

Copyright (c) 2000, 2020, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| mysql              |
| performance_schema |
| sys                |
+--------------------+
4 rows in set (0.00 sec)

mysql> create database dockerdb;
Query OK, 1 row affected (0.00 sec)

mysql> show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| dockerdb           |
| mysql              |
| performance_schema |
| sys                |
+--------------------+
5 rows in set (0.00 sec)

mysql> exit
Bye
root@e1bdf6d93c32:/# cd /var/lib/mysql
mysql/         mysql-files/   mysql-keyring/
root@e1bdf6d93c32:/# cd /var/lib/mysql
mysql/         mysql-files/   mysql-keyring/
root@e1bdf6d93c32:/# cd /var/lib/mysql
root@e1bdf6d93c32:/var/lib/mysql# ll
bash: ll: command not found
root@e1bdf6d93c32:/var/lib/mysql# ls
auto.cnf    ca.pem           client-key.pem  e1bdf6d93c32.err  ib_logfile0  ibdata1  mysql               private_key.pem  server-cert.pem  sys
ca-key.pem  client-cert.pem  dockerdb        ib_buffer_pool    ib_logfile1  ibtmp1   performance_schema  public_key.pem   server-key.pem
root@e1bdf6d93c32:/var/lib/mysql# cat dockerdb/
cat: dockerdb/: Is a directory
root@e1bdf6d93c32:/var/lib/mysql# cd dockerdb/
root@e1bdf6d93c32:/var/lib/mysql/dockerdb# ll
bash: ll: command not found
root@e1bdf6d93c32:/var/lib/mysql/dockerdb# ls
db.opt
root@e1bdf6d93c32:/var/lib/mysql/dockerdb# exit
exit
jeff@jeff-VirtualBox:/$ docker ps -a
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS                         PORTS               NAMES
e1bdf6d93c32        mysql:5.7           "docker-entrypoint.s…"   2 minutes ago       Exited (0) 5 seconds ago                           inspiring_saha
a4cb8d58101a        centos:latest       "bash"                   20 minutes ago      Up 20 minutes                                      confident_lewin
8826ddb7619e        centos:latest       "echo test"              20 minutes ago      Exited (0) 20 minutes ago                          gallant_hopper
07790e3d1a76        ubuntu:latest       "bash"                   24 minutes ago      Up 24 minutes                                      amazing_proskuriakova
a493ceafde41        ubuntu:latest       "echo test"              24 minutes ago      Exited (0) 24 minutes ago                          zen_diffie
a192a4c01730        busybox             "echo 'hellow docker'"   About an hour ago   Exited (0) About an hour ago                       clever_mestorf
30df53e07a2d        nginx               "nginx -g 'daemon of…"   15 months ago       Exited (0) 15 months ago                           webserver
9b772a6c6c47        47b19964fb50        "bash"                   15 months ago       Exited (0) 15 months ago                           brave_sutherland
jeff@jeff-VirtualBox:/$ docker run -it mysql:5.7 bash
root@e9389737aafe:/# exit
exit
jeff@jeff-VirtualBox:/$ docker ps -a
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS                         PORTS               NAMES
e9389737aafe        mysql:5.7           "docker-entrypoint.s…"   6 seconds ago       Exited (0) 2 seconds ago                           loving_burnell
e1bdf6d93c32        mysql:5.7           "docker-entrypoint.s…"   2 minutes ago       Exited (0) 22 seconds ago                          inspiring_saha
a4cb8d58101a        centos:latest       "bash"                   20 minutes ago      Up 20 minutes                                      confident_lewin
8826ddb7619e        centos:latest       "echo test"              21 minutes ago      Exited (0) 21 minutes ago                          gallant_hopper
07790e3d1a76        ubuntu:latest       "bash"                   24 minutes ago      Up 24 minutes                                      amazing_proskuriakova
a493ceafde41        ubuntu:latest       "echo test"              24 minutes ago      Exited (0) 24 minutes ago                          zen_diffie
a192a4c01730        busybox             "echo 'hellow docker'"   About an hour ago   Exited (0) About an hour ago                       clever_mestorf
30df53e07a2d        nginx               "nginx -g 'daemon of…"   15 months ago       Exited (0) 15 months ago                           webserver
9b772a6c6c47        47b19964fb50        "bash"                   15 months ago       Exited (0) 15 months ago                           brave_sutherland
jeff@jeff-VirtualBox:/$ docker start e1bdf6d93c32
e1bdf6d93c32
jeff@jeff-VirtualBox:/$ docker exec -it e1bdf6d93c32
"docker exec" requires at least 2 arguments.
See 'docker exec --help'.

Usage:  docker exec [OPTIONS] CONTAINER COMMAND [ARG...]

Run a command in a running container
jeff@jeff-VirtualBox:/$ docker exec -it e1bdf6d93c32
"docker exec" requires at least 2 arguments.
See 'docker exec --help'.

Usage:  docker exec [OPTIONS] CONTAINER COMMAND [ARG...]

Run a command in a running container
jeff@jeff-VirtualBox:/$ docker ps
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS              PORTS                 NAMES
e1bdf6d93c32        mysql:5.7           "docker-entrypoint.s…"   3 minutes ago       Up 37 seconds       3306/tcp, 33060/tcp   inspiring_saha
a4cb8d58101a        centos:latest       "bash"                   21 minutes ago      Up 21 minutes                             confident_lewin
07790e3d1a76        ubuntu:latest       "bash"                   25 minutes ago      Up 25 minutes                             amazing_proskuriakova
jeff@jeff-VirtualBox:/$ docker exec -it e1bdf6d93c32
"docker exec" requires at least 2 arguments.
See 'docker exec --help'.

Usage:  docker exec [OPTIONS] CONTAINER COMMAND [ARG...]

Run a command in a running container
jeff@jeff-VirtualBox:/$ docker exec e1bdf6d93c32
"docker exec" requires at least 2 arguments.
See 'docker exec --help'.

Usage:  docker exec [OPTIONS] CONTAINER COMMAND [ARG...]

Run a command in a running container
jeff@jeff-VirtualBox:/$ docker exec -it e1bdf6d93c32 bash
root@e1bdf6d93c32:/# ll
bash: ll: command not found
root@e1bdf6d93c32:/# ls
bin  boot  dev  docker-entrypoint-initdb.d  entrypoint.sh  etc  home  lib  lib64  media  mnt  opt  proc  root  run  sbin  srv  sys  tmp  usr  var
root@e1bdf6d93c32:/# read escape sequence
jeff@jeff-VirtualBox:/$
jeff@jeff-VirtualBox:/$
jeff@jeff-VirtualBox:/$ docker ps
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS              PORTS                 NAMES
e1bdf6d93c32        mysql:5.7           "docker-entrypoint.s…"   4 minutes ago       Up About a minute   3306/tcp, 33060/tcp   inspiring_saha
a4cb8d58101a        centos:latest       "bash"                   22 minutes ago      Up 22 minutes                             confident_lewin
07790e3d1a76        ubuntu:latest       "bash"                   26 minutes ago      Up 26 minutes                             amazing_proskuriakova
jeff@jeff-VirtualBox:/$

경로 추가 실제 컨테이너는 가상이지만 파일은 OS에 있다. 특정경로
docker run -it -v /경로:/var/lib/mysql mysql:5.7 bash

root@jeff-VirtualBox:~# docker run --name maria-test -e MYSQL_ROOT_PASSWORD=mjeff -d mariadb:10.2
Unable to find image 'mariadb:10.2' locally
10.2: Pulling from library/mariadb
d7c3167c320d: Pull complete
131f805ec7fd: Pull complete
322ed380e680: Pull complete
6ac240b13098: Pull complete
4a8fb0bb28ae: Pull complete
6a320c2d25f0: Pull complete
4e7f7fcb7c44: Pull complete
6776a3c378e4: Pull complete
060d140619ea: Pull complete
5449be9b542d: Pull complete
8ee515fcc999: Pull complete
bdff1ff2c341: Pull complete
b9f3f5fb87ab: Pull complete
0fa5a0e34ccb: Pull complete
Digest: sha256:61e217668389acff524cabdb8f6417c7294741da2bb9abc24094ccd50be5cd5c
Status: Downloaded newer image for mariadb:10.2
d04b712da4f7b73f024295915cda3aef8eea13e47376415b4b159f537ea6677e
root@jeff-VirtualBox:~# docker ps
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS              PORTS                 NAMES
d04b712da4f7        mariadb:10.2        "docker-entrypoint.s…"   4 seconds ago       Up 3 seconds        3306/tcp              maria-test
e1bdf6d93c32        mysql:5.7           "docker-entrypoint.s…"   14 minutes ago      Up 12 minutes       3306/tcp, 33060/tcp   inspiring_saha
a4cb8d58101a        centos:latest       "bash"                   33 minutes ago      Up 33 minutes                             confident_lewin
07790e3d1a76        ubuntu:latest       "bash"                   36 minutes ago      Up 36 minutes                             amazing_proskuriakova
root@jeff-VirtualBox:~#
root@jeff-VirtualBox:~# docker exec -it maria-test /bin/bash
root@d04b712da4f7:/# service mysql start
 * Starting MariaDB database server mysqld                                                                                                           [ OK ]
root@d04b712da4f7:/# mysql -uroot -p
Enter password:
Welcome to the MariaDB monitor.  Commands end with ; or \g.
Your MariaDB connection id is 9
Server version: 10.2.32-MariaDB-1:10.2.32+maria~bionic mariadb.org binary distribution

Copyright (c) 2000, 2018, Oracle, MariaDB Corporation Ab and others.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

MariaDB [(none)]> create database item;
Query OK, 1 row affected (0.00 sec)

MariaDB [(none)]> user item;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MariaDB server version for the right syntax to use near 'user item' at line 1
MariaDB [(none)]> use item;
Database changed
MariaDB [item]> CREATE TABLE Projects )id int(11) NOT NULL, name varchar(255) DEFAULT NULL, code varchar(255) DEFAULT NULL, PRIMARY KEY (id));
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MariaDB server version for the right syntax to use near ')id int(11) NOT NULL, name varchar(255) DEFAULT NULL, code varchar(255) DEFAU...' at line 1
MariaDB [item]> CREATE TABLE Projects (id int(11) NOT NULL, name varchar(255) DEFAULT NULL, code varchar(255) DEFAULT NULL, PRIMARY KEY (id));
Query OK, 0 rows affected (0.01 sec)

MariaDB [item]> show tables;
+----------------+
| Tables_in_item |
+----------------+
| Projects       |
+----------------+
1 row in set (0.00 sec)


MariaDB [item]> insert into Projects (id, name, code) values (1,'DevOps','D0180');
Query OK, 1 row affected (0.00 sec)

MariaDB [item]> select * from Projects;
+----+--------+-------+
| id | name   | code  |
+----+--------+-------+
|  1 | DevOps | D0180 |
+----+--------+-------+
1 row in set (0.00 sec)

MariaDB [item]> exit
Bye
root@d04b712da4f7:/# exit
exit
root@jeff-VirtualBox:~# docker ps
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS              PORTS                 NAMES
d04b712da4f7        mariadb:10.2        "docker-entrypoint.s…"   About an hour ago   Up About an hour    3306/tcp              maria-test
e1bdf6d93c32        mysql:5.7           "docker-entrypoint.s…"   About an hour ago   Up About an hour    3306/tcp, 33060/tcp   inspiring_saha
a4cb8d58101a        centos:latest       "bash"                   2 hours ago         Up 2 hours                                confident_lewin
07790e3d1a76        ubuntu:latest       "bash"                   2 hours ago         Up 2 hours                                amazing_proskuriakova
root@jeff-VirtualBox:~#

jeff@jeff-VirtualBox:/root$ docker run --name maria-test1 -e MYSQL_ROOT_PASSWORD=mjeff -d -v /home/jeff/maria-test1:/var/lib/mysql mariadb:10.2
cbb15f67f7a92cb8583bfb62620f9bc62426e2451f4c055a2ac94032f82ebae0
jeff@jeff-VirtualBox:/root$ ls /home/jeff/maria-test1/

jeff@jeff-VirtualBox:~/maria-test1$ docker run \
> --volume=/:rootfs:re\
> --volume=/var/run:/var/run:rw\
> --volume=/sys:/sys:ro\
> --volume=/var/lib/docker/:/var/lib/docker:ro\
> --publish=8282:8080\
> --detach=true\
> --name=cadvisor\
> google/cadvisor:latest
"docker run" requires at least 1 argument.
See 'docker run --help'.

Usage:  docker run [OPTIONS] IMAGE [COMMAND] [ARG...]

Run a command in a new container
jeff@jeff-VirtualBox:~/maria-test1$ docker run --volume=/:rootfs:re --volume=/var/run:/var/run:rw --volume=/sys:/sys:ro --volume=/var/lib/docker/:/var/lib/docker:ro --publish=8282:8080 --detach=true --name=cadvisor google/cadvisor:latest
Unable to find image 'google/cadvisor:latest' locally
latest: Pulling from google/cadvisor
ff3a5c916c92: Pull complete
44a45bb65cdf: Pull complete
0bbe1a2fe2a6: Pull complete
Digest: sha256:815386ebbe9a3490f38785ab11bda34ec8dacf4634af77b8912832d4f85dca04
Status: Downloaded newer image for google/cadvisor:latest
docker: Error response from daemon: invalid mode: re.
See 'docker run --help'.
jeff@jeff-VirtualBox:~/maria-test1$ docker run --volume=/:rootfs:re --volume=/var/run:/var/run:rw --volume=/sys:/sys:ro --volume=/var/lib/docker/:/var/lib/docker:ro --publish=8282:8080 --detach=true --name=cadvisor google/cadvisor:latest
docker: Error response from daemon: invalid mode: re.
See 'docker run --help'.
jeff@jeff-VirtualBox:~/maria-test1$ docker run --volume=/:rootfs:re --volume=/var/run:/var/run:rw --volume=/sys:/sys:ro --volume=/var/lib/docker/:/var/lib/docker:ro --publish=8282:8080 --detach=true --name=cadvisor google/cadvisor:latest
docker: Error response from daemon: invalid mode: re.
See 'docker run --help'.
jeff@jeff-VirtualBox:~/maria-test1$ docker run --volume=/:rootfs:ro --volume=/var/run:/var/run:rw --volume=/sys:/sys:ro --volume=/var/lib/docker/:/var/lib/docker:ro --publish=8282:8080 --detach=true --name=cadvisor google/cadvisor:latest
docker: Error response from daemon: invalid volume specification: '/:rootfs:ro': invalid mount config for type "bind": invalid mount path: 'rootfs' mount path must be absolute.
See 'docker run --help'.
jeff@jeff-VirtualBox:~/maria-test1$ docker run --volume=/:rootfs:ro --volume=/var/run:/var/run:rw --volume=/sys:/sys:ro --volume=/var/lib/docker/:/var/lib/docker:ro --publish=8282:8080 --detach=true --name=cadvisor google/cadvisor:latest
docker: Error response from daemon: invalid volume specification: '/:rootfs:ro': invalid mount config for type "bind": invalid mount path: 'rootfs' mount path must be absolute.
See 'docker run --help'.
jeff@jeff-VirtualBox:~/maria-test1$ sudo docker run \
>   --volume=/:/rootfs:ro \
>   --volume=/var/run:/var/run:ro \
>   --volume=/sys:/sys:ro \
>   --volume=/var/lib/docker/:/var/lib/docker:ro \
>   --volume=/dev/disk/:/dev/disk:ro \
>   --publish=8080:8080 \
>   --detach=true \
>   --name=cadvisor \
>   --privileged \
>   --device=/dev/kmsg \
>   gcr.io/google-containers/cadvisor:$VERSION
[sudo] password for jeff:
Sorry, try again.
[sudo] password for jeff:
docker: invalid reference format.
See 'docker run --help'.
jeff@jeff-VirtualBox:~/maria-test1$ sudo docker run   --volume=/:/rootfs:ro   --volume=/var/run:/var/run:ro   --volume=/sys:/sys:ro   --volume=/var/lib/docker/:/var/lib/docker:ro   --volume=/dev/disk/:/dev/disk:ro   --publish=8080:8080   --detach=true   --name=cadvisor   --privileged   --device=/dev/kmsg   gcr.io/google-containers/cadvisor:$VERSION
docker: invalid reference format.
See 'docker run --help'.
jeff@jeff-VirtualBox:~/maria-test1$ sudo docker run   --volume=/:/rootfs:ro   --volume=/var/run:/var/run:ro   --volume=/sys:/sys:ro   --volume=/var/lib/docker/:/var/lib/docker:ro   --volume=/dev/disk/:/dev/disk:ro   --publish=8080:8080   --detach=true   --name=cadvisor   --privileged   --device=/dev/kmsg   google/cadvisor:latest
a4edc2a404e7a5f4fa139f2000cc178fc6dbf1a0357178ad38301a99cc98a87c
jeff@jeff-VirtualBox:~/maria-test1$ docker ps
CONTAINER ID        IMAGE                    COMMAND                  CREATED             STATUS              PORTS                    NAMES
a4edc2a404e7        google/cadvisor:latest   "/usr/bin/cadvisor -…"   5 seconds ago       Up 5 seconds        0.0.0.0:8080->8080/tcp   cadvisor
cbb15f67f7a9        mariadb:10.2             "docker-entrypoint.s…"   19 minutes ago      Up 19 minutes       3306/tcp                 maria-test1
d04b712da4f7        mariadb:10.2             "docker-entrypoint.s…"   About an hour ago   Up About an hour    3306/tcp                 maria-test
e1bdf6d93c32        mysql:5.7                "docker-entrypoint.s…"   2 hours ago         Up 2 hours          3306/tcp, 33060/tcp      inspiring_saha
a4cb8d58101a        centos:latest            "bash"                   2 hours ago         Up 2 hours                                   confident_lewin
07790e3d1a76        ubuntu:latest            "bash"                   2 hours ago         Up 2 hours                                   amazing_proskuriakova


jeff@jeff-VirtualBox:~/maria-test1$ docker pull nginx
Using default tag: latest
latest: Pulling from library/nginx
8559a31e96f4: Already exists
8d69e59170f7: Pull complete
3f9f1ec1d262: Pull complete
d1f5ff4f210d: Pull complete
1e22bfa8652e: Pull complete
Digest: sha256:21f32f6c08406306d822a0e6e8b7dc81f53f336570e852e25fbe1e3e3d0d0133
Status: Downloaded newer image for nginx:latest
jeff@jeff-VirtualBox:~/maria-test1$


jeff@jeff-VirtualBox:~/maria-test1$ docker pull nginx
Using default tag: latest
latest: Pulling from library/nginx
8559a31e96f4: Already exists
8d69e59170f7: Pull complete
3f9f1ec1d262: Pull complete
d1f5ff4f210d: Pull complete
1e22bfa8652e: Pull complete
Digest: sha256:21f32f6c08406306d822a0e6e8b7dc81f53f336570e852e25fbe1e3e3d0d0133
Status: Downloaded newer image for nginx:latest
jeff@jeff-VirtualBox:~/maria-test1$ docker images
REPOSITORY                        TAG                 IMAGE ID            CREATED             SIZE
busybox                           latest              c7c37e472d31        9 hours ago         1.22MB
mariadb                           10.2                596bfae14a84        5 days ago          341MB
ubuntu                            latest              74435f89ab78        13 days ago         73.9MB
centos                            latest              831691599b88        13 days ago         215MB
nginx                             latest              2622e6cca7eb        2 weeks ago         132MB
mysql                             5.7                 9cfcce23593a        2 weeks ago         448MB
nginx                             <none>              881bd08c0b08        16 months ago       109MB
ubuntu                            <none>              47b19964fb50        17 months ago       88.1MB
google/cadvisor                   latest              eb1210707573        19 months ago       69.6MB
gcr.io/google-samples/hello-app   1.0                 bc5c421ecd6c        2 years ago         9.86MB
jeff@jeff-VirtualBox:~/maria-test1$ docker run --name webserver1 -d -p 8001L80 nginx
docker: invalid publish opts format (should be name=value but got '8001L80').
See 'docker run --help'.
jeff@jeff-VirtualBox:~/maria-test1$ docker run --name webserver1 -d -p 8001:80 nginx
af7e049db26e4797a0d207d2f471f6cd68b5b9fefdc57090fb0b61a0431ec1ce
jeff@jeff-VirtualBox:~/maria-test1$ docker ps
CONTAINER ID        IMAGE                    COMMAND                  CREATED             STATUS              PORTS                    NAMES
af7e049db26e        nginx                    "/docker-entrypoint.…"   5 seconds ago       Up 4 seconds        0.0.0.0:8001->80/tcp     webserver1
a4edc2a404e7        google/cadvisor:latest   "/usr/bin/cadvisor -…"   4 minutes ago       Up 4 minutes        0.0.0.0:8080->8080/tcp   cadvisor
cbb15f67f7a9        mariadb:10.2             "docker-entrypoint.s…"   23 minutes ago      Up 23 minutes       3306/tcp                 maria-test1
d04b712da4f7        mariadb:10.2             "docker-entrypoint.s…"   2 hours ago         Up 2 hours          3306/tcp                 maria-test
e1bdf6d93c32        mysql:5.7                "docker-entrypoint.s…"   2 hours ago         Up 2 hours          3306/tcp, 33060/tcp      inspiring_saha
a4cb8d58101a        centos:latest            "bash"                   2 hours ago         Up 2 hours                                   confident_lewin
07790e3d1a76        ubuntu:latest            "bash"                   2 hours ago         Up 2 hours                                   amazing_proskuriakova
jeff@jeff-VirtualBox:~/maria-test1$ docker stats webserver
CONTAINER ID        NAME                CPU %               MEM USAGE / LIMIT   MEM %               NET I/O             BLOCK I/O           PIDS
30df53e07a2d        webserver           0.00%               0B / 0B             0.00%               0B / 0B             0B / 0B             0
CONTAINER ID        NAME                CPU %               MEM USAGE / LIMIT   MEM %               NET I/O             BLOCK I/O           PIDS
30df53e07a2d        webserver           0.00%               0B / 0B             0.00%               0B / 0B             0B / 0B             0
CONTAINER ID        NAME                CPU %               MEM USAGE / LIMIT   MEM %               NET I/O             BLOCK I/O           PIDS
30df53e07a2d        webserver           0.00%               0B / 0B             0.00%               0B / 0B             0B / 0B             0
CONTAINER ID        NAME                CPU %               MEM USAGE / LIMIT   MEM %               NET I/O             BLOCK I/O           PIDS
30df53e07a2d        webserver           0.00%               0B / 0B             0.00%               0B / 0B             0B / 0B             0
CONTAINER ID        NAME                CPU %               MEM USAGE / LIMIT   MEM %               NET I/O             BLOCK I/O           PIDS
30df53e07a2d        webserver           0.00%               0B / 0B             0.00%               0B / 0B             0B / 0B             0
CONTAINER ID        NAME                CPU %               MEM USAGE / LIMIT   MEM %               NET I/O             BLOCK I/O           PIDS
30df53e07a2d        webserver           0.00%               0B / 0B             0.00%               0B / 0B             0B / 0B             0
CONTAINER ID        NAME                CPU %               MEM USAGE / LIMIT   MEM %               NET I/O             BLOCK I/O           PIDS
30df53e07a2d        webserver           0.00%               0B / 0B             0.00%               0B / 0B             0B / 0B             0
CONTAINER ID        NAME                CPU %               MEM USAGE / LIMIT   MEM %               NET I/O             BLOCK I/O           PIDS
30df53e07a2d        webserver           0.00%               0B / 0B             0.00%               0B / 0B             0B / 0B             0
CONTAINER ID        NAME                CPU %               MEM USAGE / LIMIT   MEM %               NET I/O             BLOCK I/O           PIDS
30df53e07a2d        webserver           0.00%               0B / 0B             0.00%               0B / 0B             0B / 0B             0
CONTAINER ID        NAME                CPU %               MEM USAGE / LIMIT   MEM %               NET I/O             BLOCK I/O           PIDS
30df53e07a2d        webserver           0.00%               0B / 0B             0.00%               0B / 0B             0B / 0B             0
CONTAINER ID        NAME                CPU %               MEM USAGE / LIMIT   MEM %               NET I/O             BLOCK I/O           PIDS
30df53e07a2d        webserver           0.00%               0B / 0B             0.00%               0B / 0B             0B / 0B             0
CONTAINER ID        NAME                CPU %               MEM USAGE / LIMIT   MEM %               NET I/O             BLOCK I/O           PIDS
30df53e07a2d        webserver           0.00%               0B / 0B             0.00%               0B / 0B             0B / 0B             0
^C
jeff@jeff-VirtualBox:~/maria-test1$

docker run --name webserver1 -d -v /home/jeff/nginx:/var/log/nginx:rw -p 8001:80 nginx

jeff@jeff-VirtualBox:~/maria-test1$ sudo netstat -nlp |grep 80
tcp6       0      0 :::8080                 :::*                    LISTEN      11161/docker-proxy
tcp6       0      0 :::8001                 :::*                    LISTEN      11532/docker-proxy
unix  2      [ ACC ]     STREAM     LISTENING     22181    3080/systemd        /run/user/1000/systemd/private
unix  2      [ ACC ]     STREAM     LISTENING     39392    7347/containerd-shi @/containerd-shim/moby/a4cb8d58101a447e9171c09421f85eaf48c4426a92b465b80c72ff5536ea1d9c/shim.sock
jeff@jeff-VirtualBox:~/maria-test1$

 curl http://localhost:8001
jeff@jeff-VirtualBox:~/maria-test1$ sudo mkdir nginx
jeff@jeff-VirtualBox:~/maria-test1$ cd nginx/
jeff@jeff-VirtualBox:~/maria-test1/nginx$ ;;
bash: syntax error near unexpected token `;;'
jeff@jeff-VirtualBox:~/maria-test1/nginx$ ll
total 8
drwxr-xr-x 2 root root 4096  6월 30 14:05 ./
drwxr-xr-x 6  999 root 4096  6월 30 14:05 ../
jeff@jeff-VirtualBox:~/maria-test1/nginx$ vi Dockerfile
jeff@jeff-VirtualBox:~/maria-test1/nginx$ sudo vi Dockerfile
jeff@jeff-VirtualBox:~/maria-test1/nginx$ ls -l
total 4
-rw-r--r-- 1 root root 113  6월 30 14:12 Dockerfile
jeff@jeff-VirtualBox:~/maria-test1/nginx$ sudo vi index.html
jeff@jeff-VirtualBox:~/maria-test1/nginx$ docker build -t my-nginx-image:latest
"docker build" requires exactly 1 argument.
See 'docker build --help'.

Usage:  docker build [OPTIONS] PATH | URL | -

Build an image from a Dockerfile
jeff@jeff-VirtualBox:~/maria-test1/nginx$ ll
total 16
drwxr-xr-x 2 root root 4096  6월 30 14:13 ./
drwxr-xr-x 6  999 root 4096  6월 30 14:05 ../
-rw-r--r-- 1 root root  113  6월 30 14:12 Dockerfile
-rw-r--r-- 1 root root   31  6월 30 14:13 index.html
jeff@jeff-VirtualBox:~/maria-test1/nginx$ docker build -t my-nginx-image:latest .
Sending build context to Docker daemon  3.072kB
Step 1/4 : FROM nginx:latest
 ---> 2622e6cca7eb
Step 2/4 : COPY index.html /usr/share/nginx/html/index.html
 ---> 888dcf521451
Step 3/4 : EXPOSE 80
 ---> Running in f1377b8774be
Removing intermediate container f1377b8774be
 ---> 065e05071879
Step 4/4 : CMD ["nginx", "-g", "daemon off;"]
 ---> Running in fef558d3d96e
Removing intermediate container fef558d3d96e
 ---> e852292270e3
Successfully built e852292270e3
Successfully tagged my-nginx-image:latest
jeff@jeff-VirtualBox:~/maria-test1/nginx$ docker images
REPOSITORY                        TAG                 IMAGE ID            CREATED             SIZE
my-nginx-image                    latest              e852292270e3        8 seconds ago       132MB
busybox                           latest              c7c37e472d31        9 hours ago         1.22MB
mariadb                           10.2                596bfae14a84        5 days ago          341MB
ubuntu                            latest              74435f89ab78        13 days ago         73.9MB
centos                            latest              831691599b88        13 days ago         215MB
nginx                             latest              2622e6cca7eb        2 weeks ago         132MB
mysql                             5.7                 9cfcce23593a        2 weeks ago         448MB
nginx                             <none>              881bd08c0b08        16 months ago       109MB
ubuntu                            <none>              47b19964fb50        17 months ago       88.1MB
google/cadvisor                   latest              eb1210707573        19 months ago       69.6MB
gcr.io/google-samples/hello-app   1.0                 bc5c421ecd6c        2 years ago         9.86MB
jeff@jeff-VirtualBox:~/maria-test1/nginx$ docker run --name webserver2 -d -p 8002:80 my-nginx-image:latest
5570c066d4d19c8ed868a07e31b87c24f74b1a8401f2c1fbff463c25780c4865
jeff@jeff-VirtualBox:~/maria-test1/nginx$ curl http://localhost:80
curl: (7) Failed to connect to localhost port 80: Connection refused
jeff@jeff-VirtualBox:~/maria-test1/nginx$ curl http://localhost:80
curl: (7) Failed to connect to localhost port 80: Connection refused
jeff@jeff-VirtualBox:~/maria-test1/nginx$ curl http://localhost:8002





<h1>
HELLO, Docker!
</h1>
jeff@jeff-VirtualBox:~/maria-test1/nginx$ ^C
jeff@jeff-VirtualBox:~/maria-test1/nginx$ curl http://localhost:80
curl: (7) Failed to connect to localhost port 80: Connection refused
jeff@jeff-VirtualBox:~/maria-test1/nginx$
 
웹에서 확인 8002익스터널 아이피
 
 base 이미지를 가지고 new 이미지로 생성 : dockerfile로 저장
 
 Dockerfile 명령어
	FROM
	
-- dockergile, docker-compose
MSA, Devops >> code로 개발 운영  Iac (Infrastructure code)

jeff@jeff-VirtualBox:~/maria-test1/nginx$ docker search elasticsearch
NAME                                 DESCRIPTION                                     STARS               OFFICIAL            AUTOMATED
elasticsearch                        Elasticsearch is a powerful open source sear…   4449                [OK]
nshou/elasticsearch-kibana           Elasticsearch-7.7.0 Kibana-7.7.0                119                                     [OK]
itzg/elasticsearch                   Provides an easily configurable Elasticsearc…   70                                      [OK]
mobz/elasticsearch-head              elasticsearch-head front-end and standalone …   63
elastichq/elasticsearch-hq           Official Docker image for ElasticHQ: Elastic…   57                                      [OK]
elastic/elasticsearch                The Elasticsearch Docker image maintained by…   35
bitnami/elasticsearch                Bitnami Docker Image for Elasticsearch          32                                      [OK]
taskrabbit/elasticsearch-dump        Import and export tools for elasticsearch       22                                      [OK]
lmenezes/elasticsearch-kopf          elasticsearch kopf                              18                                      [OK]
barnybug/elasticsearch               Latest Elasticsearch 1.7.2 and previous rele…   17                                      [OK]
justwatch/elasticsearch_exporter     Elasticsearch stats exporter for Prometheus     15
esystemstech/elasticsearch           Debian based Elasticsearch packing for Lifer…   15
blacktop/elasticsearch               Alpine Linux based Elasticsearch Docker Image   13                                      [OK]
monsantoco/elasticsearch             ElasticSearch Docker image                      11                                      [OK]
mesoscloud/elasticsearch             [UNMAINTAINED] Elasticsearch                    9                                       [OK]
centerforopenscience/elasticsearch   Elasticsearch                                   4                                       [OK]
dtagdevsec/elasticsearch             elasticsearch                                   3                                       [OK]
barchart/elasticsearch-aws           Elasticsearch AWS node                          3
bitnami/elasticsearch-exporter       Bitnami Elasticsearch Exporter Docker Image     2                                       [OK]
jetstack/elasticsearch-pet           An elasticsearch image for kubernetes PetSets   1                                       [OK]
phenompeople/elasticsearch           Elasticsearch is a powerful open source sear…   1                                       [OK]
axway/elasticsearch-docker-beat      "Beat" extension to read logs of containers …   1                                       [OK]
wreulicke/elasticsearch              elasticsearch                                   0                                       [OK]
18fgsa/elasticsearch-ha              Built from https://github.com/18F/kubernetes…   0
18fgsa/elasticsearch                 Buil


jeff@jeff-VirtualBox:~/maria-test1/nginx$ docker run -d -p 8003:80 --name httpd-basic httpd:2.4
Unable to find image 'httpd:2.4' locally
2.4: Pulling from library/httpd
8559a31e96f4: Already exists
bd517d441028: Pull complete
f67007e59c3c: Pull complete
83c578481926: Pull complete
f3cbcb88690d: Pull complete
Digest: sha256:387f896f9b6867c7fa543f7d1a686b0ebe777ed13f6f11efc8b94bec743a1e51
Status: Downloaded newer image for httpd:2.4
73b6adb71d27e2dd7f4f21610f19b513560b89acce9de20858a53da8f04f2313
jeff@jeff-VirtualBox:~/maria-test1/nginx$ curl http://localhost:8001
<!DOCTYPE html>
<html>
<head>
<title>Welcome to nginx!</title>
<style>
    body {
        width: 35em;
        margin: 0 auto;
        font-family: Tahoma, Verdana, Arial, sans-serif;
    }
</style>
</head>
<body>
<h1>Welcome to nginx!</h1>
<p>If you see this page, the nginx web server is successfully installed and
working. Further configuration is required.</p>

<p>For online documentation and support please refer to
<a href="http://nginx.org/">nginx.org</a>.<br/>
Commercial support is available at
<a href="http://nginx.com/">nginx.com</a>.</p>

<p><em>Thank you for using nginx.</em></p>
</body>
</html>
jeff@jeff-VirtualBox:~/maria-test1/nginx$ curl http://localhost:8003
<html><body><h1>It works!</h1></body></html>
jeff@jeff-VirtualBox:~/maria-test1/nginx$ docker exec -it httpd-basic bash
root@73b6adb71d27:/usr/local/apache2# ls -la /usr/local/apache2/htdocs/
total 12
drwxr-xr-x 2 root     root     4096 Jun  9 07:02 .
drwxr-xr-x 1 www-data www-data 4096 Jun  9 07:02 ..
-rw-r--r-- 1 root     src        45 Jun 11  2007 index.html
root@73b6adb71d27:/usr/local/apache2# echo "hello docker cloud" > /usr/local/apache2/htdocs/index.html
root@73b6adb71d27:/usr/local/apache2# exit
exit
jeff@jeff-VirtualBox:~/maria-test1/nginx$ curl http://localhost:8003
hello docker cloud
jeff@jeff-VirtualBox:~/maria-test1/nginx$

박에 파일을 도커안에 넣기
jeff@jeff-VirtualBox:~/maria-test1/nginx$ docker cp index.html 73b6adb71d27:/usr/local/apache2/htdocs/index.html


jeff@jeff-VirtualBox:~/php$ git clone https://github.com/brayanlee/docker-phpserver.git
fatal: could not create work tree dir 'docker-phpserver': Permission denied
jeff@jeff-VirtualBox:~/php$ sudo git clone https://github.com/brayanlee/docker-phpserver.git
Cloning into 'docker-phpserver'...
remote: Enumerating objects: 12, done.
remote: Counting objects: 100% (12/12), done.
remote: Compressing objects: 100% (11/11), done.
remote: Total 12 (delta 2), reused 0 (delta 0), pack-reused 0
Unpacking objects: 100% (12/12), done.
Checking connectivity... done.
jeff@jeff-VirtualBox:~/php$ ll
total 12
drwxr-xr-x  3 root root 4096  6월 30 14:48 ./
drwxr-xr-x 20 jeff jeff 4096  6월 30 14:48 ../
drwxr-xr-x  3 root root 4096  6월 30 14:48 docker-phpserver/
jeff@jeff-VirtualBox:~/php$ cd odc
bash: cd: odc: No such file or directory
jeff@jeff-VirtualBox:~/php$ cd docker-phpserver/
jeff@jeff-VirtualBox:~/php/docker-phpserver$ ll
total 20
drwxr-xr-x 3 root root 4096  6월 30 14:48 ./
drwxr-xr-x 3 root root 4096  6월 30 14:48 ../
-rw-r--r-- 1 root root  166  6월 30 14:48 Dockerfile
drwxr-xr-x 8 root root 4096  6월 30 14:48 .git/
-rw-r--r-- 1 root root  165  6월 30 14:48 index.php
jeff@jeff-VirtualBox:~/php/docker-phpserver$ cat Dockerfile
FROM php:7.2-apache

MAINTAINER datastory Hub <hylee@dshub.cloud>

ADD index.php /var/www/html/index.php

EXPOSE 80

CMD ["/usr/sbin/apache2ctl", "-D", "FOREGROUND"]
jeff@jeff-VirtualBox:~/php/docker-phpserver$ cat index.php
<html>
<body>
<div style="font-size:25px">
<?php
$host=gethostname();
echo "Container Name : ";
echo $host;
?>
<p> Welcome to the Hell~! </p>
</div>
</body>
</html>
jeff@jeff-VirtualBox:~/php/docker-phpserver$ docker build -t phpserver:1.0 .
Sending build context to Docker daemon  65.02kB
Step 1/5 : FROM php:7.2-apache
7.2-apache: Pulling from library/php
8559a31e96f4: Already exists
e0276193a084: Pull complete
eb2d00c10344: Pull complete
f54006e0dc29: Pull complete
e0d3d1244592: Pull complete
3a60f364b0c5: Pull complete
3e309988c00b: Pull complete
4a6af7a03f84: Pull complete
b0b6cc63bda2: Pull complete
3b0ddef1d776: Pull complete
6d0d029909c5: Pull complete
bdc330bcb28e: Pull complete
5a1a48fbcf28: Pull complete
38900f7b5a66: Pull complete
Digest: sha256:051b1a3f996b8a3a8a22d06b2df77850956952c458e07f43fc11acc6969445f5
Status: Downloaded newer image for php:7.2-apache
 ---> 936e93fcdd74
Step 2/5 : MAINTAINER datastory Hub <hylee@dshub.cloud>
 ---> Running in a5e1ae80523d
Removing intermediate container a5e1ae80523d
 ---> 0a6d383d602f
Step 3/5 : ADD index.php /var/www/html/index.php
 ---> 737abfe19a73
Step 4/5 : EXPOSE 80
 ---> Running in 9f5260f898a5
Removing intermediate container 9f5260f898a5
 ---> 77b1cead7ca1
Step 5/5 : CMD ["/usr/sbin/apache2ctl", "-D", "FOREGROUND"]
 ---> Running in f7b6d618f6c8
Removing intermediate container f7b6d618f6c8
 ---> 74f4e43abffd
Successfully built 74f4e43abffd
Successfully tagged phpserver:1.0
jeff@jeff-VirtualBox:~/php/docker-phpserver$ docker images | grep php
phpserver                         1.0                 74f4e43abffd        13 seconds ago      410MB
php                               7.2-apache          936e93fcdd74        2 weeks ago         410MB
jeff@jeff-VirtualBox:~/php/docker-phpserver$ docker run -it -d -p 8004:80 -h phpserver --name=phpserver phpserver:1.0
93ef08b62799740fd684aed68a38b35f09231bd9c31689377c71ffb9e6e91938
jeff@jeff-VirtualBox:~/php/docker-phpserver$ curl localhost:8004
<html>
<body>
<div style="font-size:25px">
Container Name : phpserver<p> Welcome to the Hell~! </p>
</div>
</body>
</html>
jeff@jeff-VirtualBox:~/php/docker-phpserver$ docker exec -it phpserver bash
root@phpserver:/var/www/html# exit
exit
jeff@jeff-VirtualBox:~/php/docker-phpserver$ docker ps
CONTAINER ID        IMAGE                    COMMAND                  CREATED             STATUS              PORTS                    NAMES
93ef08b62799        phpserver:1.0            "docker-php-entrypoi…"   47 seconds ago      Up 46 seconds       0.0.0.0:8004->80/tcp     phpserver
73b6adb71d27        httpd:2.4                "httpd-foreground"       12 minutes ago      Up 12 minutes       0.0.0.0:8003->80/tcp     httpd-basic
5570c066d4d1        my-nginx-image:latest    "/docker-entrypoint.…"   35 minutes ago      Up 35 minutes       0.0.0.0:8002->80/tcp     webserver2
af7e049db26e        nginx                    "/docker-entrypoint.…"   About an hour ago   Up About an hour    0.0.0.0:8001->80/tcp     webserver1
a4edc2a404e7        google/cadvisor:latest   "/usr/bin/cadvisor -…"   About an hour ago   Up About an hour    0.0.0.0:8080->8080/tcp   cadvisor
cbb15f67f7a9        mariadb:10.2             "docker-entrypoint.s…"   About an hour ago   Up About an hour    3306/tcp                 maria-test1
d04b712da4f7        mariadb:10.2             "docker-entrypoint.s…"   3 hours ago         Up 3 hours          3306/tcp                 maria-test
e1bdf6d93c32        mysql:5.7                "docker-entrypoint.s…"   3 hours ago         Up 3 hours          3306/tcp, 33060/tcp      inspiring_saha
a4cb8d58101a        centos:latest            "bash"                   3 hours ago         Up 3 hours                                   confident_lewin
07790e3d1a76        ubuntu:latest            "bash"                   3 hours ago         Up 3 hours                                   amazing_proskuriakova
jeff@jeff-VirtualBox:~/php/docker-phpserver$





