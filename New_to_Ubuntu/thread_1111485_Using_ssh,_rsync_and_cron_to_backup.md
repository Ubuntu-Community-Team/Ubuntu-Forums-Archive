---
title: "Using ssh, rsync and cron to backup"
date: 2009-03-30
forum: New to Ubuntu
---

### Post by TideMan on 2009-03-30
I use the following to backup my home directory to directory AthlonBackup on BlueFront (an old computer running Xubuntu) using rsync and ssh:
```
 sudo rsync --delete -azvv -e ssh /home derek@BlueFront:AthlonBackup
```

When I run this from a terminal, I need to enter two passwords: one for sudo and another to log into BlueFront.  The ssh part also asks me a damn-fool question that I always answer yes to. All this works fine from the terminal with me in front of it.

But now, I'd like to run the command using cron at 1am every day, but how do I get around the silly ssh question and entering the passwords?

---

### Post by blueridgedog on 2009-03-30
I used "expect" when dealing with such problems in the past.  Note that the downside will be that you have to record passwords in a text file.  

The task would be not to call the rsync command with cron, but to call a shell script that uses expect.  You can also use a key on the remote system to eliminate one password, but you will still need expect to do the rest.

Google should give you many examples of the syntax.

Here is a link to the man page:

[http://www.manpagez.com/man/1/expect/](http://www.manpagez.com/man/1/expect/)

It is not installed by default.

---

### Post by kanikilu on 2009-03-30
You could also use public keys instead of passwords:

[https://help.ubuntu.com/community/SSHHowto#Public%20key%20authentication](https://help.ubuntu.com/community/SSHHowto#Public%20key%20authentication)

[http://www.debuntu.org/ssh-key-based-authentication](http://www.debuntu.org/ssh-key-based-authentication)

---

### Post by TideMan on 2009-03-30
> **kanikilu said:**
> You could also use public keys instead of passwords:

[https://help.ubuntu.com/community/SSHHowto#Public%20key%20authentication](https://help.ubuntu.com/community/SSHHowto#Public%20key%20authentication)

[http://www.debuntu.org/ssh-key-based-authentication](http://www.debuntu.org/ssh-key-based-authentication)

This has almost got me working.
I can now rsync to the other machine without using a password, having set up a private key on this machine and a public key on the server, as per the excellent instructions in the second link above.

I've put the rsync command in a bash script which works fine from my terminal, but when I try it using cron, it doesn't connect.

I suspect that it is because my private key is in .ssh/id_rsa in my home directory, but when cron runs it does not do so from my home directory, so it does not see .ssh/id_rsa holding my private key.  Should I copy my id_rsa somewhere higher up the tree?  If so, where?

---

### Post by kanikilu on 2009-03-30
Per those instructions, did you try specifying the key with *ssh -i*?

> user@host:~$ ssh -i /path/to/private/key remoteuser@remotehost

---

### Post by asmoore82 on 2009-03-30
+1 for public key password-less ssh

I would also suggest dropping the sudo altogether - you are not root on the remote box right "derek@" - so why do you need to be on the local box?

setting up password-less ssh on Debian based distros is as easy as 1,2,3...

```
ssh-keygen
ssh-copy-id *<user@remotehost>*
```
well, just 1,2 ;)

---

### Post by TideMan on 2009-03-31
I'm afraid I've gotten myself in a real muddle now.......

Here is my rsync command:
```
rsync --delete -azvv -e ssh -i /home/derek/.ssh /home derek@BlueFront:AthlonBackup > /home/derek/backup.log
```

As I understand this, -e ssh tells rsync to run ssh.
When it runs ssh, I want it to use -i /home/derek/.ssh to refer to where my private key is.  But I want -i to refer to an option for ssh, not to rsync, where -i means something else.  How do I do this?  Seems like I should put ssh -i /home/derek/.ssh in parentheses........

---

### Post by kanikilu on 2009-03-31
I think you just put it in quotes. Also, I'm not positive, but I think you may need to specify the ssh user. You might want to try it with the -l if it doesn't work without...

For example:```
rsync --delete -azvv -e "ssh -l derek -i /home/derek/.ssh" /home derek@BlueFront:AthlonBackup > /home/derek/backup.log
```

---

### Post by TideMan on 2009-03-31
Using:
```
rsync --delete -azvv -e "ssh -i /home/derek/.ssh" /home derek@BlueFront:AthlonBackup > /home/derek/test.log

```
produces this when I run from the terminal:
> opening connection using ssh -i /home/derek/.ssh -l derek BlueFront rsync --server -vvlogDtprz --delete . AthlonBackup 
building file list ... 
done
deleting in home
etc
etc

but just this line when I run in cron:
> opening connection using ssh -i /home/derek/.ssh -l derek BlueFront rsync --server -vvlogDtprz --delete . AthlonBackup 

So, it has figured out the user OK without me using -l,  and by using double quotes, it's associated the -i with ssh, but it still doesn't run from cron.

There has to be something simple that I'm missing.......

---

### Post by hyper_ch on 2009-03-31
put it in a shell script, add the shebang line and then run the shell script from cron. You have different shells whether you run something as user or cron so you need to define the shell.

---

### Post by TideMan on 2009-03-31
> **hyper_ch said:**
> put it in a shell script, add the shebang line and then run the shell script from cron. You have different shells whether you run something as user or cron so you need to define the shell.

But that's what I'm doing.
Here is my script:
```
#! /bin/bash
rsync --delete -azvv -e "ssh -i /home/derek/.ssh" /home derek@BlueFront:AthlonBackup > /home/derek/test.log

```

---

### Post by hyper_ch on 2009-03-31
ok, there should be no space between #! and /bin/bash

furthermore don't you call a profile when running dere@BlueFront:AthlonBackup? Shouldn't you rather be using dere@BlueFront:/path/to/AthlonBackup ?

Furthermore you should specify a key in -e "ssh -i KEYFILE".

Here's what I use (well, I have modified it meanwhile a lot but you'll get the basic message):

```

#!/bin/bash
unset PATH


# USER VARIABLES
BACKUPDIR=/backup							# Folder on the backup server where the backups shall be located
KEY=/root/.ssh/id_rsa						# SSH key
MYSQL_BACKUPSCRIPT=/root/my_backup.sh		# Path to the remote mysql backup script
PRODUCTION_USER=root@production.server.com	# The user and the address of the production server
EXCLUDES=/backup/backup_exclude				# File containing the excluded directories
DAYS=60										# The number of days after which old backups will be deleted


# PATH VARIABLES
SH=/bin/sh									# Location of the bash bin in the production server!!!!

CP=/bin/cp;									# Location of the cp bin
FIND=/usr/bin/find;							# Location of the find bin
ECHO=/bin/echo;								# Location of the echo bin
MK=/bin/mkdir;								# Location of the mk bin
SSH=/usr/bin/ssh;							# Location of the ssh bin
DATE=/bin/date;								# Location of the date bin
RM=/bin/rm;									# Location of the rm bin
GREP=/bin/grep;								# Location of the grep bin
MYSQL=/usr/bin/mysql;						# Location of the mysql bin
MYSQLDUMP=/usr/bin/mysqldump;				# Location of the mysql_dump bin
RSYNC=/usr/bin/rsync;						# Location of the rsync bin
TOUCH=/bin/touch;							# Location of the touch bin



##                                                      ##
##      --       DO NOT EDIT BELOW THIS HERE     --     ##
##                                                      ##



# CREATING NECESSARY FOLDERS
$MK $BACKUPDIR
CURRENT=$BACKUPDIR/current
OLD=$BACKUPDIR/old
$MK $CURRENT
$MK $OLD
# CREATING CURRENT DATE / TIME
NOW=`$DATE '+%Y-%m'-%d_%H:%M`
NOW=$OLD/$NOW
$MK $NOW


# CREATE REMOTE MYSQL BACKUP BY RUNNING THE REMOTE BACKUP SCRIPT
$SSH -i $KEY $PRODUCTION_USER "$SH $MYSQL_BACKUPSCRIPT"


# RUN RSYNC INTO CURRENT
$RSYNC															\
        -apvz --delete --delete-excluded						\
        --exclude-from="$EXCLUDES"								\
        -e "$SSH -i $KEY"										\
        $PRODUCTION_USER:/										\
		$CURRENT ;


# UPDATE THE MTIME TO REFELCT THE SNAPSHOT TIME
$TOUCH $BACKUPDIR/current


# MAKE HARDLINK COPY
$CP -al $CURRENT/* $NOW


# REMOVE OLD BACKUPS
for FILE in "$( $FIND $OLD -maxdepth 1 -type d -mtime +$DAYS )"
do
#	$RM -Rf $FILE
#   $ECHO $FILE
done
exit 0

```

---

