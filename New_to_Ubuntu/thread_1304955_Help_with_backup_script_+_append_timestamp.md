---
title: "Help with backup script + append timestamp"
date: 2009-10-29
forum: New to Ubuntu
---

### Post by six30two on 2009-10-29
Looking for some help with a script to backup my Drupal installation as well as my MySQL database.

The following is what I need the script to do:

Back up my /var/www folder (where my drupal installation is at), as well as my MySQL database (I don't know where these are kept - not /etc/mysql, are they? I couldn't find them. I was told I need something involving a mysql_dump file).

I need the script to tar the backed up files in ONE tarball.
I need the tar to be named <user>_<timestamp>.tar.gz so that each time the script is run, it creates a new file with the user's name and the date it was backed up so I can have multiple backups. 

If possible, I would also like a second script that would restore one of the backed up files.

Thanks for the help.

I've been working on this for a day already, and I have made a little bit of progress, but I'm not really familiar with scripting or the exact commands to get the tar function to name the file properly... Maybe I haven't read the man page enough?

---

### Post by six30two on 2009-10-29
Still no success...

---

### Post by phillw on 2009-10-29
> **six30two said:**
> Looking for some help with a script to backup my Drupal installation as well as my MySQL database.

The following is what I need the script to do:

Back up my /var/www folder (where my drupal installation is at), as well as my MySQL database (I don't know where these are kept - not /etc/mysql, are they? I couldn't find them. I was told I need something involving a mysql_dump file).

I need the script to tar the backed up files in ONE tarball.
I need the tar to be named <user>_<timestamp>.tar.gz so that each time the script is run, it creates a new file with the user's name and the date it was backed up so I can have multiple backups. 

If possible, I would also like a second script that would restore one of the backed up files.

Thanks for the help.

I've been working on this for a day already, and I have made a little bit of progress, but I'm not really familiar with scripting or the exact commands to get the tar function to name the file properly... Maybe I haven't read the man page enough?

Hi, I've only just come back on-line (Upgraded to 9.10) - Give me 15-20 mins & I'll have you a set of instructions.

Phill.

---

### Post by KIAaze on 2009-10-29
Use $USER to get the current username (won't it always be the same?).
Use the "date" command to get a timestamp.

Here's my ~/bin/tar_datetime.sh script I regularly use:
```

#!/bin/bash

# Check if all parameters are present
# If no, exit
if [ $# -ne 1 ]
then
        echo
        echo 'archives a directory as <dir>_$(date +%Y%m%d_%H%M%S).tar.gz'
        echo "usage :"
        echo "$0 <dir>"
        echo
        exit 0
fi

BASENAME=$( readlink -f $1 )
DATE=$(date +%Y%m%d_%H%M%S)
ARCHIVE=$BASENAME\_$DATE.tar.gz

tar -czvf $ARCHIVE $1
echo "All archived in $ARCHIVE"

```

Note:
You'll probably want to use the "-P" switch with tar when archiving to make restoring easier. ;)
```
-P, --absolute-names
              don&#8217;t strip leading &#8216;/&#8217;s from file names
```

edit:
In two quick commands:
Backup:
```
tar -Pczvf $USER\_$(date +%Y%m%d_%H%M%S).tar.gz /var/www /directory_to_SQL_DB
```
(You may need to run it as root in case of permission problems on some files.)
Restore:
```
sudo tar -Pxzvf BACKUP.tar.gz
```

cf "man date" for infos on how to format the date/time stamp with date.

---

### Post by phillw on 2009-10-29
> **six30two said:**
> Looking for some help with a script to backup my Drupal installation as well as my MySQL database.

The following is what I need the script to do:

Back up my /var/www folder (where my drupal installation is at), as well as my MySQL database (I don't know where these are kept - not /etc/mysql, are they? I couldn't find them. I was told I need something involving a mysql_dump file).

I need the script to tar the backed up files in ONE tarball.
I need the tar to be named <user>_<timestamp>.tar.gz so that each time the script is run, it creates a new file with the user's name and the date it was backed up so I can have multiple backups. 

If possible, I would also like a second script that would restore one of the backed up files.

Thanks for the help.

I've been working on this for a day already, and I have made a little bit of progress, but I'm not really familiar with scripting or the exact commands to get the tar function to name the file properly... Maybe I haven't read the man page enough?


```
$echo {USER}
```

Will give the user name, time stamp can be got thus

```
DATE_STR=`date +%b%d`

```

So, you're looking to do .....

```

DATE_STR=`date +%b%d`
tar cvpfz $USER.DATE_STR.tgz /var/www/

```

This gives me  > phillw.Oct29.tgz

on my system

The flags for tar are here (It's based on that backup script - I use it for my system)  
[http://ubuntuforums.org/showthread.php?t=35087&highlight=backup](http://ubuntuforums.org/showthread.php?t=35087&highlight=backup)

Now for your MySQL dumps ....

---

### Post by KIAaze on 2009-10-29
Ah, good idea about the -p switch. Never used it, but I can imagine it being important for server backups.
```
    -p, --same-permissions, --preserve-permissions
              ignore umask when extracting files (the default for root)

```

---

### Post by phillw on 2009-10-29
MySQL ....

```
mysqldump -u NAME -pPASSWORD dbname filename.sql
```NAME = valid user name for the database
PASSWORD = password for the user name (Note there is no space between the -p and the password)
dbname = name of database to be backed up
filename.sql = path / filename that you want it to be saved as

To restore the backup tarball  do as the thread on the backup script. You'll have to put the filename of the tarball in manually

```
tar xvpfz username.date.tgz -C /var/www/ 
```PLEASE test the extract some where safe, I haven't run it !!!!

for restoring a mysql dbase you'd need to....

```
mysql -u NAME -pPASSWORD dbname < filename.sql
```Hope that helps you.

The info on mysqldump can be found here  [http://dev.mysql.com/doc/refman/5.1/en/mysqldump.html](http://dev.mysql.com/doc/refman/5.1/en/mysqldump.html)

Regards,

Phill.

---

