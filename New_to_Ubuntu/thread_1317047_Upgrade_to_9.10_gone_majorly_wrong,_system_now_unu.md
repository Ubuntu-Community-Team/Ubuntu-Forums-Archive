---
title: "Upgrade to 9.10 gone majorly wrong, system now unusable"
date: 2009-11-06
forum: New to Ubuntu
---

### Post by nightshade209 on 2009-11-06
I recently upgraded from 9.04 to 9.10 using alternate cd which i downloaded, burnt and then used the automatic upgrade feature.
While upgrading it, i received errors stating that libpang1.0-common, gsfonts and ttf-freefont packages had some problem updating. I chose the "Proceed Anyway" or something equivalent to that.
The installation displayed a message saying that the upgrade had completed successfully.
Now, after rebooting, the system won't boot up. I reach a screen saying:
```
One or more of the mounts listed in /etc/fstab cannot yet be mounted: 
(ESC for recovery shell)
/: waiting for /dev/disk/by-uuid/e59eb16e-0384-4f12-9514-99a8c9eadb44
/tmp: waiting for (null)
swap: waiting for UUID=0eb81804-260f-4315-a34e-a091897cbe88
```
The bootup process stops right there.
Pls help, i need to get my PC up and running as soon as possible.

---

### Post by tacantara on 2009-11-06
First thing I'd do is try to regain control of your computer.  Do you have a 9.04 LiveCD that you can boot from the CD drive with?  If that's an option, go ahead and reinstall 9.04.  After that, attempt to reinstall 9.10.  If you get the same error more than once, it may be a problem with the 9.10 CD (i.e. corrupted file).  Of course, I wouldn't rule out a hardware issue.

---

### Post by nightshade209 on 2009-11-06
I hv a 9.04 cd, bt installing that would mean losing all my data. So, if there's any other way, i'd appreciate it. And i had also tested the 9.10 cd using its menu option - it returned no errors. And as for hardware problems, i am not sure what colud have gone wrong, since 9.04 was working perfectly well a couple of hours back.

---

### Post by dv3500ea on 2009-11-06
You need to know which partition on your hard drive should be mounted to /.
Boot up with your 9.04 live cd and go into system->administration->partition manager
Have a look at the partitions. On a normal Karmic install you should see an Ext4 formatted partition. Take a note of the path to the volume (/dev/sda*). Reeboot and remove the CD. When you get to the sticking point press ESC. Make a backup of fstab:
```
sudo cp /etc/fstab /etc/fstab~
```find out the uuid of the volume:
```
sudo vol_id -u /dev/sda*
```, replacing /dev/sda* with what you took a note of.
Edit fstab:
```
sudo nano /etc/fstab
```and append ```
UUID=uuid / ext4 defaults 0 0
```replace uuid with the uuid you found out.
reboot and see what happens.
If it doesn't work:
```
sudo cp /etc/fstab~ /etc/fstab
```I hope that works.

EDIT: Also, if that doesn't work, give us the output of [code]cat /etc/fstab[code]

---

### Post by nightshade209 on 2009-11-06
Afraid that didn't help.
Here's the output u asked for:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=e59eb16e-0384-4f12-9514-99a8c9eadb44 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=0eb81804-260f-4315-a34e-a091897cbe88 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

---

### Post by dv3500ea on 2009-11-07
Did vol_id not work?
 It appears that that program is no longer installed on Karmic (or has a different name).
Try going into gparted on the live cd and right-clicking on the karmic partition and clicking info. You should take a note of the UUID and use that for uuid instead.
I hope this will solve it.

---

### Post by nightshade209 on 2009-11-07
The UUID shown in vol_id and gparted is the same one as that in the fstab file shown above.

---

