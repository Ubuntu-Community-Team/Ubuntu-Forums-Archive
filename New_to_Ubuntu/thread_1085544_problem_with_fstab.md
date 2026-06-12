---
title: "problem with fstab"
date: 2009-03-03
forum: New to Ubuntu
---

### Post by Free4Eternity on 2009-03-03
Hi all. I am currently trying to set up /home on a separate partition. All was well, except for some reason, no matter how I try, fstab seems to always ignore the my home partition, and when I try to login, ubuntu keeps saying /home/cheng is cannot be found.

I rebooted in recovery mode, and found that /home was not actually mounted in the boot up.

Here is my fstab set up.

```

/dev/sdb8 is my home partition

<~> cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
#
# System drives
#
proc            /proc           proc    defaults        0       0
/dev/sda1	/		ext3	relatime,errors=remount-ro 0 1
/dev/sdb8	/home		ext2	nodev,nousid	0	2
/dev/sda5	none		swap	sw		0	0
#
# Media Drives
#
none		/proc/bus/usb	usbfs	devgid=125,devmode=664 0	0

```

any ideas?

---

### Post by mikechant on 2009-03-03
One of your options looks wrong - 'nousid' should probably be 'nosuid'. So the /home line of fstab is probably being ignored as invalid.

Also, is there a good reason why you are using ext2 for your /home instead of ext3? ext3 is better for data integrety.


(Incidentally, the fstab looks very wrong on this board - missing spaces between /dev/sda and /home etc. but that seems seems to be a display error on this page - if I copy and paste the fstab data to another screen the tabs/spaces appear).

---

### Post by taurus on 2009-03-03
I would replace the current entry for /home in /etc/fstab from this

```
/dev/sdb8	/home		ext2	nodev,nousid	0	2
```
to this.

```
/dev/sdb8	/home		ext2	  defaults	0	2
```

---

### Post by egalvan on 2009-03-03
check this guide

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by taurus on 2009-03-03
> **egalvan said:**
> check this guide

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Here is my /etc/fstab and it is working just fine.

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=56123b3d-6ce8-4624-bd15-04ea93c157f2 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=d24f3cc0-0538-4ff3-bdf1-f46ed3cb21f3 /home           ext3    defaults        0       2
# /dev/sda2
UUID=0bdaba89-73fd-4bff-adf0-05585e4d6b6b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

---

### Post by Free4Eternity on 2009-03-04
Thanks guys for the quick reply. I think it is really because of nousid that caused it to ignore the line. However, although it is now mounting, when I try to logon, it keeps returning the error saying they can't find /home/cheng, although it IS there when I ls it in failsave terminal session AND when I boot into recovery mode. Also, when I am in a terminal session and try to ls /home/cheng, it returns with an operation denied error, and it worked if I sudo. I double and triple checked that the directory belongs to my usual username, and that it is set to 644 permission...Any ideas?

---

### Post by dmizer on 2009-03-04
Although fstab will work with regular /dev/xxx IDs, you're much better off mounting by UUID. This will probably solve your problem.

Find your /dev/sdb8 UUID with the following command (post the output if you're unsure):
```
blkid
```

Then replace /dev/sdb8 with the UUID as taurus has done.

---

### Post by egalvan on 2009-03-04
> **dmizer said:**
> Although fstab will work with regular /dev/xxx IDs, you're much better off mounting by UUID. This will probably solve your problem.


I've switched to using LABEL. easier for humans to remember :)

---

### Post by Free4Eternity on 2009-03-11
Thanks guys. I'll try it.

---

### Post by Free4Eternity on 2009-03-13
Solved! I changed it to uuid, but it didn't work either. I later found out that it was because my permissions/modes were really messed up. Neither /home nor /home/cheng were set as excultable. I changed it, and now it is working. YAY! Thanks guys.

---

