# MariaDB Docker Container for AARCH64, ARMv7l, X86 and X64

## Docker Container usage
To start an MariaDB 10.1 container execute

```
$ ./dc-run.sh 10.1

```

This will also print the TCP port number that MariaDB can be accessed by.

To stop the container use

```
$ ./dc-stop.sh 10.1

```

You may replace the version number with any number that corresponds  
to an available Docker Image (db-mariadb-\<ARCH\>:\<VERSION\>).

## Required Docker Image
The Docker Image **db-mariadb-\<ARCH\>** will automaticly be downloaded from the Docker Hub.  
The source for the image can be found here [https://github.com/tsitle/dockerimage-db-mariadb](https://github.com/tsitle/dockerimage-db-mariadb).

## Docker Container configuration
- CF\_SYSUSR\_MYSQL\_USER\_ID [int]: User-ID for user that ownes the database files
- CF\_SYSUSR\_MYSQL\_GROUP\_ID [int]: Group-ID for group that ownes the database files
- CF\_MYSQL\_MAX\_ALLOWED\_PACKET [string]: Size string (e.g. "128M")
- CF\_MYSQL\_INNODB\_BUFFER\_POOL\_SIZE [string]: Size string (e.g. "8G")
- CF\_MYSQL\_INNODB\_LOG\_FILE\_SIZE [string]: Size string (e.g. "64M")
- CF\_MYSQL\_SQLMODE [string]: List of options for sql_mode (e.g. "STRICT_TRANS_TABLES,ERROR_FOR_DIVISION_BY_ZERO")
- CF\_LANG [string]: Language to use (en\_EN.UTF-8 or de\_DE.UTF-8)
- CF\_TIMEZONE [string]: Timezone (e.g. 'Europe/Berlin')

Only when the internal data directory doesn't already exist:

- CF\_ENABLE\_DB\_INIT\_DEBUG [bool]: Enable debugging output when DB is initialized?  
Warning: This will print DB user passwords to the log output
- CF\_DB\_ROOT\_PASSWORD [string]: Password for DB root user (>= 4 chars)
- to create a new DB scheme when a container is started:
	- CF\_DB\_USER\_NAME [string]: Create a DB user with this name
	- CF\_DB\_USER\_PASS [string]: Password for CF\_DB\_USER\_NAME (>= 4 chars)
	- CF\_DB\_SCHEME\_NAME [string]: Create a DB scheme that CF\_DB\_USER\_NAME can access
