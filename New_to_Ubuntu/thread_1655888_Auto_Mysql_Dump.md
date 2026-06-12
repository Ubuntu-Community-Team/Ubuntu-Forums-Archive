---
title: "Auto Mysql Dump"
date: 2010-12-30
forum: New to Ubuntu
---

### Post by Nerflander on 2010-12-30
Hey there!

I got this linux server ( ubuntu ) and it contains a mysql DB. I need to backup this daily. Now i know you can do a mysql dump trough command line but my linux skills are not as pro as some of the users here , better said most of the users here. 

Can some one help me with doing this by clearly explaining this to a beginner? ( me )

Hope some one can help! 

cheers!

---

### Post by TSJason on 2010-12-30
You can use a cron and a small shell script to do this.

Create a script. I like to put custom root scripts in /usr/local/bin/, so something like this:

sudo gedit /usr/local/bin/dumpdbs.sh
```

!/bin/bash
# Dump and compress all mysql databases

if [[ $1 = "" ]] ; then
        out=/var/backups/databases/`date +%A`
else
        out=$1
fi

if [[ ! -d $out ]] ; then
        mkdir -p $out
fi

for db in `mysqlshow | cut -d " " -f 2 | grep -v "\-\-\+"` ; do
        mysqldump --add-drop-table --single-transaction $db |gzip -c > $out/$db.sql.gz
done

exit 0

```

Now you'll need to set the script executable and add a cronjob to run it on a nightly basis. Create a file with your cron entry describing the job:

gedit ~/newcron.txt

```
00 19 * * * /usr/local/bin/dumpdbs.sh

```

Open a terminal to proceed.
These commands will dump your current crons, merge in the new line and re-import the whole thing:
```
sudo bash -c "crontab -l > current"
sudo bash -c "cat newcron.txt >> current"
sudo crontab current
```

And finally, run this command to make your script executable:
```
sudo chmod 755 /usr/local/bin/dumpdbs.sh

```


Lots of options can be changed in the script like specifying the root username and password for your mysql server in the mysqldump line or the destination or compression of the dumps.

---

### Post by Nerflander on 2010-12-30
Wow thats some braincracking. Ok i can follow most of the steps but Where do i put in the database nam password username etc. 

This is very new to me but i hope your willing to continue the explaining :)

Kind Regards,
Maarten

---

### Post by TSJason on 2010-12-30
Just add them to the mysqldump line. Something like this:


```
mysqldump -u root -pyourpasswordhere --add-drop-table --single-transaction $db |gzip -c > $out/$db.sql.gz
```

*The lack of a space between the -p and the password is correct.

```
man mysqldump
``` to learn about all the command line options

---

