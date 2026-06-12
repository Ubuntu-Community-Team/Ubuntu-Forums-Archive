---
title: "When sizing a partition in gparted how many MB=GB?"
date: 2010-02-15
forum: New to Ubuntu
---

### Post by hortstu on 2010-02-15
I wanted 15GB and I set it to 15360MB and I ended up with 14.3GB

For future reference what's the conversion?

---

### Post by pirateghost on 2010-02-15
here you go.  this should help you out

[http://webdeveloper.earthweb.com/repository/javascripts/2001/04/41291/byteconverter.htm](http://webdeveloper.earthweb.com/repository/javascripts/2001/04/41291/byteconverter.htm)

---

### Post by hortstu on 2010-02-15
Yeah I used a converter.  I used the same numbers that ones spitting out... apparently gparted uses a different one.

---

### Post by pirateghost on 2010-02-15
did you create a filesystem with it?

by default ext filesystem allocates 8% to reserve

if this is not going to be an OS partition you can drop to command line and hack this out:
```
sudo tune2fs -m 0 /dev/sdX
```
where X is the drive letter (sda, sdb, sdc, etc)

---

### Post by hortstu on 2010-02-15
> **pirateghost said:**
> did you create a filesystem with it?

by default ext filesystem allocates 8% to reserve

if this is not going to be an OS partition you can drop to command line and hack this out:
```
sudo tune2fs -m 0 /dev/sdX
```
where X is the drive letter (sda, sdb, sdc, etc)


Bear with me... I think what you're telling me is that the partitions are really the size I intended them to be but for some reason gparted tells me they're 8% smaller than they really are.  I can enter that piece of code in the terminal for everything but the root OS partitions to get it to show what's really there?

---

### Post by pirateghost on 2010-02-15
> **Modify Reserved Space  (Optional)**

 When  formatting the drive as ext2/ext3, 5% of the drive's total space is  reserved for the super-user (root) so that the operating system can  still write to the disk even if it is full. However, for disks that only  contain data, this is not necessary. 
NOTE: You  may run this command on a fat32 file system, but it will do nothing;  therefore, I highly recommend not running it. 
You can adjust the percentage of reserved space with the  "tune2fs" command, like this: 
 sudo tune2fs -m 1 /dev/sdb1This example reserves 1% of space - change this number  if you wish. 
[IMG]https://help.ubuntu.com/htdocs/ubuntunew/img/icon-info.png[/IMG] Using this command does not change  any existing data on the drive. You can use it on a drive which already  contains data. 
sorry its 5%
pulled from:
[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

---

### Post by hortstu on 2010-02-15
Thanks

---

