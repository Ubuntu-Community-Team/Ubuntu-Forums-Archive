---
title: "How to transfer file using Shell acces to remote server"
date: 2008-11-17
forum: Networking &amp; Wireless
---

### Post by vinusweety on 2008-11-17
My task is to transfer application as well as MySQL database from remote server A to remote server B (via) my local machine. 

Im given Shell access to my remote Server A. So downloading application files using SCP. Is there a better way for this?

How to take backup from remote MySQL database Server A, provided only Shell Access.

Can anyone help me out?

---

### Post by dimitar_g_g on 2008-11-17
Are you looking for mysqldump ?
          shell> mysqldump [options] db_name [tables]
          shell> mysqldump [options] --databases db_name1 [db_name2 db_name3...]
          shell> mysqldump [options] --all-databases

mysqldump -u USER -pPASSWORD --all-databases > backupfile.sql

On the other server you do   
mysql -u USER -pPASSWORD < backupfile.sql

---

### Post by Meson on 2008-11-17
To do the actual transfer of backupfile.sql:

```

local$ ssh user@serverA
serverA$ scp backupfile.sql user@serverB:

```

That will move copy backupfile.sql from the current directory on serverA and put it into "user's" home directory on serverB.

If the backup is fairly large, I like to do:
```

local$ ssh user@serverA
serverA$ rsync --partial --progress -e "ssh" backupfile.sql user@serverB:

```

That does the same thing as the first, however if the transfer is interupted, you don't need to start from scratch when you restart it.

---

