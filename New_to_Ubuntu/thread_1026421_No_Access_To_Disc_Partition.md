---
title: "No Access To Disc Partition"
date: 2008-12-31
forum: New to Ubuntu
---

### Post by Bargeman on 2008-12-31
I have formatted my disc with a main linux partition, a swap partition and a third Ext3 partition that I intend to use for backup etc.

I can mount it (why doesn't it auto mount?) but not add any folders or see it in any backup program I am using.

I am old to computers (having started in Fortram on a CDC6600 but relatively new to Linux which looks good but why does everything have to be so complex)

Next goal once this is solved is to take and image of a working system to avoid a full rebuild each time I get it all pear-shaped.
:confused:
Thanks in advance  David

---

### Post by xjcannonx on 2008-12-31
Welcome to the forums

Well let me assure you that it may seem difficult now but once you learn your way around the filesystem it becomes straightforward (well most of the time)

Well for starters can you get to a terminal and type ```
sudo fdisk -l
``` 
And post the output from that here

---

### Post by Bargeman on 2008-12-31
Wow, that was a quick reply, thanks

Output is 

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xace22e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3414    27422923+  83  Linux
/dev/sda2            4690        4864     1405687+   5  Extended
/dev/sda3            3415        4689    10241437+  83  Linux
/dev/sda5            4690        4864     1405656   82  Linux swap / Solaris

Thanks

---

### Post by xjcannonx on 2008-12-31
Alright, hey i should have just told you before but now can you post the output of ```
cat /etc/fstab
```

---

### Post by Bargeman on 2008-12-31
david@LinuxEasyNote:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=cdd6e129-4893-4f7e-b1cb-cc5eb05e7be9 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=cbdef6fc-16de-4b7e-8e1b-069ca747379a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


David

---

### Post by mikewhatever on 2008-12-31
Here is a good guide on how to automount an ext3 partition:
[http://psychocats.net/ubuntu/mountlinux](http://psychocats.net/ubuntu/mountlinux).

Just create a mount point with <sudo mkdir /media/backup>, then add the following to your fstab 
**/dev/sda3 /media/backup ext3 defaults 0 0**, then give yourself the ownership.

---

### Post by Bargeman on 2008-12-31
Many Thanks, the guide seemed to do the job, Now I will just go through it again to learn what I actually did.

The Guide seems to cover the other topic I need which is a system-wide backup.


David  :D

---

### Post by billgoldberg on 2008-12-31
> **Bargeman said:**
> Many Thanks, the guide seemed to do the job, Now I will just go through it again to learn what I actually did.

The Guide seems to cover the other topic I need which is a system-wide backup.


David  :D

Your drive was assigned to /dev/sda3.

Before you can mount it, you need something to mount it to, the mount point.

You can create that with mkdir /media/mountpoint (or just use the file manager).

After you created the mountpoint, you could mount it manually using "mount /dev/sda3 /media/mountpoint" or add it to fstab so it automounts when you start your pc.

---

### Post by Bargeman on 2008-12-31
Thanks Current problem solved from your replies

---

### Post by 1jackjack on 2009-01-06
i used this line to automount my ext3 music partition into my home folder:

UUID=1ff05f7f-9433-4b91-b84d-a7c2320a739d /home/jack/music ext3 defaults 0 0

and it works a treat, but i've got a slight niggle: the partition ALSO appears as an icon on my desktop, which is just annoying... anyone know a way to prevent this?

cheers,
jack

---

### Post by Michael.Godawski on 2009-01-06
hi,
have a look at this, perhaps it helps:


[LIST]
[*][http://godawski.oxyhost.com/unvisiblefiles.html](http://godawski.oxyhost.com/unvisiblefiles.html)
[/LIST]
(typo in the url invisible ohohoh)

---

### Post by lswest on 2009-01-06
If you don't mind disabling the icons for all mounted drives (of course, only if you're running GNOME).  Hit alt+F2 and type in gconf-editor there, once the window opens navigate to apps->Nautilus-->Desktop and uncheck "volumes visible".

*Edit* also described visually in the link above.

---

### Post by 1jackjack on 2009-01-06
Thanks guys, but unfortunately I do mind. It's really useful having icons for all my removable drives... I'm sure this didnt happen last time i tried to automount a partition... it's weird.

---

