---
title: "how to implement a backup automation"
date: 2009-04-03
forum: New to Ubuntu
---

### Post by codie72 on 2009-04-03
I was asked at work today that they wanted me to setup a backup solution using cpio and tar utilities, 
in conjunction with the scheduling service cron or crond how would I implement a full backup with /data/* folder as the source and 
/dev/sda? as the target(drive) at 1am daily except Saturday and Sunday.

this has me totally confused any help would be greatly appreciated
can i even do this in Ubuntu server
I am only just getting used too ubuntu client so im not that flash at linux yet

---

### Post by kpkeerthi on 2009-04-03
[http://forums.linuxmint.com/viewtopic.php?f=42&t=3969](http://forums.linuxmint.com/viewtopic.php?f=42&t=3969)
[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

---

### Post by codie72 on 2009-04-03
I will check it out -- i am having trouble setting this up  cheers

---

### Post by Anthon on 2009-04-03
I would use either cpio or tar, they essentially do the same: combine multiple files into one (called an archive). Tarring (or cpio) to a device I have normally only done when using tapedrives (attached to /dev/sda<NUM>).
If your /dev/sda? is a drive you should mount it, make sure it has enough discpace and write a tar file on the filesystem.
You can use a cron job ( look it up with man cron ) to schedule things at a certain time at night
You probably also want to include the date in the tar filename:
   tar cvjf /media/sdaX/backup$(date +'%Y%m%d').tar.bz2

---

### Post by hyper_ch on 2009-04-03
I use cron, rysync, ssh and hardlinks.

---

### Post by codie72 on 2009-04-03
It is a tape drive - i think it is \sda4 or something i will find out when i get back to work

so i should just write some sort of script to perform the tar process 
and mount the drive 
and then in the script to transfer the file to the tape
or does the scheduling software allow for copy and mounting
is there a easy way to compare the old copies of the backup etc

thanks for the help
im a little lost

---

### Post by codie72 on 2009-04-03
ive been reading for hours the links provided and searching many sites however i cannot seam to work this out.

I believe i need to write some sort of script
that cron will perform. 

i am pretty new to linux so i am finding this quite difficult.

now from what i understand 
i need to write a script that enables my script to have root access
then I need to mount the tape drive -- all i have here is it says its /dev/sda

then i need to log onto to tape drives directory say cd /sda/backup/
while in that directory run
tar cvjf /media/sda”tape no”/backup$(date +'%Y%m%d').tar.bz2

however i read there is many commands that are used to rewind tape etc.
but i just need to rewind the tape everytime

then i believe the tar will be installed onto the tape with all permissions to all files within the tar on the tape

---------------
from what i understand the script I have needs to be added to my cron tab file, in the right syntax so that it performs the backup automaticly week days..

if i am right please let me know

---

### Post by hyper_ch on 2009-04-03
no, cron is a scheduler and runs under that user it you the cronjob to. You can add a cronjob to the root crontab and then the script will run under root.

So no need to gain "root" access in the script.

---

### Post by codie72 on 2009-04-03
ok i will keep working on it
i will try a few more things on my ubuntu install at home 
thanks for the tips
i will get back to ya

---

### Post by codie72 on 2009-04-04
thanks guys - i worked it out finally completly
after a lot of reading lol

---

### Post by hyper_ch on 2009-04-04
> **codie72 said:**
> after a lot of reading lol

The information is all out there... the difficult part is about finding the right info (as there is so much out there).

Btw, if you need to do more stuff at servers and such have a look at [http://www.howtoforge.com](http://www.howtoforge.com) --> they've got plenty of good tutorials.

---

### Post by jbcola on 2009-06-30
Here is a quite simple script for autoloaders:
[http://ubuntuforums.org/showthread.php?p=7541317#post7541317](http://ubuntuforums.org/showthread.php?p=7541317#post7541317)

---

