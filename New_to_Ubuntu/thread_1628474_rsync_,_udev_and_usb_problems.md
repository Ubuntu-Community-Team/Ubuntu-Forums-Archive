---
title: "rsync , udev and usb problems"
date: 2010-11-22
forum: New to Ubuntu
---

### Post by A_M_S on 2010-11-22
Hello
 I'm using udev and rsync to backup my pendrive (/media/123)to a folder (/home/ams/Documents/Trabalho/pen_rsync/)in my hard drive.

When i connect the pen the rsync shows the following error:

```
2010/11/22 21:10:31 [3330] building file list
2010/11/22 21:10:31 [3330] rsync: change_dir "/media/123" failed: No such file or directory (2)
2010/11/22 21:10:31 [3330] sent 12 bytes  received 12 bytes  48.00 bytes/sec
2010/11/22 21:10:31 [3330] total size is 0  speedup is 0.00
2010/11/22 21:10:31 [3330] rsync error: some files/attrs were not transferred (see previous errors) (code 23) at main.c(1060) [sender=3.0.7]
2010/11/22 21:10:31 [3362] building file list
2010/11/22 21:10:31 [3362] rsync: change_dir "/media/123" failed: No such file or directory (2)
2010/11/22 21:10:31 [3362] sent 12 bytes  received 12 bytes  48.00 bytes/sec
2010/11/22 21:10:31 [3362] total size is 0  speedup is 0.00

```

The udev rule to that is executed when i connect the pen is:
```

ACTION=="add",SUBSYSTEMS=="usb",ATTRS{manufacturer}=="Silicom Power",ATTRS{serial}=="000000000068EA",RUN+="/bin/su ams -c /bin/rs.sh"

```

And the script called by the udev rules is : 
rs.sh 
```

#!/bin/bash
rsync -av --log-file=/home/ams/tmp/rs.log /media/123/ /home/ams/Documents/Trabalho/pen_rsync/

```

**Everything works well if the source folder is not my pen drive (/media/123/) but another directory in my harddrive.**

The pen filesystem is fat32 (I use this pen in windows machines so i can't format it to ext3).

Any ideas how to fix this problem?

Tnx.

---

### Post by yankysunny on 2010-11-22
I think it is relates to mounting. Are you mounting the pendrive manually? If yes what command are you using. it must be something like
mount /dev/sd5 /media/123
because if u r using automatic mounting done by ubuntu you are not sure where it is mounting your pendrive

---

### Post by A_M_S on 2010-11-22
Thank you for the reply 

> **yankysunny said:**
> 
mount /dev/sd5 /media/123
because if u r using automatic mounting done by ubuntu you are not sure where it is mounting your pendrive

I've tried to mount manually my pen int the rs.sh but with no success.The error continues.

---

### Post by yankysunny on 2010-11-22
> **A_M_S said:**
> Thank you for the reply 



I've tried to mount manually my pen int the rs.sh but with no success.
The mounting should be done at the start of the computer or you can set it in startup applications

---

### Post by A_M_S on 2010-11-22
> **yankysunny said:**
> The mounting should be done at the start of the computer or you can set it in startup applications

But shouldn't i mount only a removable device after i connect it?

---

### Post by yankysunny on 2010-11-22
I missed
RUN+="/bin/su ams -c /bin/rs.sh (put here the device in which it is picked up?)"OR

go here if you find anything useful

[http://ninetynine.be/blog/2009/03/ubuntu-backup-to-usb-drive-on-mount/](http://ninetynine.be/blog/2009/03/ubuntu-backup-to-usb-drive-on-mount/)

---

### Post by A_M_S on 2010-11-22
Thank you for the replies and the link. Now its time read and learn :)

---

### Post by A_M_S on 2010-11-23
> **yankysunny said:**
> I missed
go here if you find anything useful

[http://ninetynine.be/blog/2009/03/ubuntu-backup-to-usb-drive-on-mount/](http://ninetynine.be/blog/2009/03/ubuntu-backup-to-usb-drive-on-mount/)
Success! Now everything is perfect!
Tnx a lot for the link! :D

---

