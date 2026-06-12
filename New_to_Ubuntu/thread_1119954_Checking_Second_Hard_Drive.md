---
title: "Checking Second Hard Drive"
date: 2009-04-08
forum: New to Ubuntu
---

### Post by stuart264 on 2009-04-08
I have a second 500gb hard drive in my Ubuntu Machine mounted as /dev/sdb1 that mainly contains multimedia files streamed by Mediatomb.

My question is how do I get the file system checked by fsck on boot after 30 boots the same as the system checks my first drive.

Bit of a newbie question but I am keeping an eye on the drive as its a replacement re manufactured drive I got under warranty from Western Digital and I always have doubts about re manufactured stuff no matter how reliable the manufacturer is

---

### Post by hatten on 2009-04-08
google for fstab and view the manpage for it. (/etc/fstab)

---

### Post by northern lights on 2009-04-08
Whether any device is regularly checked is set in */etc/fstab*. The file is structured as follows:```
# <device>      <mountpoint>    <filesystemtype><options>  <dump> <fsckorder>

/dev/sda1	/            	ext3    relatime,errors=remount-ro     1       1
/dev/sdb1	/media/streams        	ext3     	defaults       	1 	0
/dev/sdc1	/media/cdrom   	iso9660  	noauto,ro,user 	0 	0

```

Yours should look similar to the above. The last column defines the order fsck routinely scans devices in. A 0 means it's not going to be checked at all. Change the 0 to a 2 for sdb1.

This has to be done as root, so use either```
sudo nano /etc/fstab
```or```
gksu gedit /etc/fstab
```

Save and reboot.

---

### Post by MrWES on 2009-04-08
I read the man pages and I understand root file system gets a 1 and others should get a 2; but what exactly is the difference?

Thanks,
Bill

---

