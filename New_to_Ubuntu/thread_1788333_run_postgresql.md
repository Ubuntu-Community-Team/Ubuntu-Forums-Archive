---
title: "run postgresql"
date: 2011-06-22
forum: New to Ubuntu
---

### Post by pacalici on 2011-06-22
i've been trying to install postgresql9.0.4 on ubuntu 11.04. first i took the source code from [here]("http://www.postgresql.org/ftp/source/") and extracted it to /home/user/postgresql-9.0.4. closely following the labyrinthine user manual, as a compliant windows user that i am, i performed ./configure, ./make, install, set LD_LIBRARY_PATH to /usr/local/pgsql/lib and PATH to /usr/local/pgsql/bin:$PATH.

still not sure what / why i was doing this (apart from being written in online tutorials), but i just added a linux user mycat, i then swtiched to postgres unix user with "su - postgres" and then i tried to connect to the db server with "psql template1". i got this message: "psql: could not connect to server: No such file or directory
	Is the server running locally and accepting
	connections on Unix domain socket "/tmp/.s.PGSQL.5432"?
", which i can't answer on my own. 

anyway, here is the output of " ps auxw | grep post", which i think means that postgresql does run on my system.

postgres  1030  0.0  0.1 105448  6728 ?        S    16:07   0:00 /usr/lib/postgresql/8.4/bin/postgres -D /var/lib/postgresql/8.4/main -c config_file=/etc/postgresql/8.4/main/postgresql.conf
postgres  1177  0.0  0.0 105448  1664 ?        Ss   16:07   0:00 postgres: writer process                                                                                                    
postgres  1178  0.0  0.0 105448  1424 ?        Ss   16:07   0:00 postgres: wal writer process                                                                                                
postgres  1179  0.0  0.0 105580  1824 ?        Ss   16:07   0:00 postgres: autovacuum launcher process                                                                                       
postgres  1180  0.0  0.0  77000  1516 ?        Ss   16:07   0:00 postgres: stats collector process                                                                                           
postgres  2081  0.0  0.0 104716  3964 pts/0    S    16:24   0:00 su - postgres
postgres  2089  0.0  0.2  30696  8156 pts/0    S    16:24   0:00 -su
postgres  2218  0.0  0.0  21932  1388 pts/0    R+   16:31   0:00 ps auxw
postgres  2219  0.0  0.0  13128  1060 pts/0    S+   16:31   0:00 grep --color=auto post


all i wanna do (actually need to do) is to create a db and use it. how can i accomplish this?

thank u

---

### Post by ratcheer on 2011-07-22
Just use your package manager to install postgresql on ubuntu, e.g., sudo apt-get install postgresql

Tim

---

### Post by SeijiSensei on 2011-07-22
The output from ps says you already have PostgreSQL 8.4 running.  I can't tell from your description if you then tried to start the 9.x server you built.  You would have needed to run a command like 
```
su -l postgres -c "/path/to/postmaster -D /path/to/pgdata &" >> /path/to/pg_log GLOG" 2>&1 < /dev/null
```
If you tried that, it should have failed if you didn't specify a non-standard port (one other than 5432) since the 8.4 instance already uses that port.

That said, you should still have been able to connect to the running instance using psql.  You would have a version conflict, since putting /usr/local/pgsql/bin at the beginning of your PATH would make it run the 9.04 client in that directory to connect to the 8.4 server.  Usually you just get a warning about the mismatch in cases like this.

I think you have such a confused mess at the moment that starting over seems the best approach.  First, remove the reference to /usr/local/pgsql/bin from your PATH and get rid of the LD_LIBRARY_PATH.  Next run:

```
sudo apt-get purge postgresql
sudo apt-get install postgresql
```

to remove any traces of the old PG-8.4 installation then create a new fresh installation.  Then try

```

sudo su
su postgres
psql template1

```

and see how you fare.

To create users and databases you should use the createuser and createdb utilities.  From a terminal prompt, type "man createuser" and "man createdb" for details.

---

### Post by sadaruwan12 on 2011-07-22
> **ratcheer said:**
> Just use your package manager to install postgresql on ubuntu, e.g., sudo apt-get install postgresql

Tim

Ratcheer is correct it's easier and mostly ERROR free. Also postgre have mentioned to use the APT to install it.

Why did you wanted to compile it from the source.

---

