---
title: "[SOLVED] fsck would not work"
date: 2008-12-27
forum: New to Ubuntu
---

### Post by Bigbob22 on 2008-12-27
I wanted to see if my hard drive was alright and typed fsck in my terminal and got this:
```
fsck 1.40.8 (13-Mar-2008)
fsck.ext3: Unable to resolve 'UUID=430f5b5a-3423-42fa-8978-e27d3f798ae9'
```

How do I get it to work?

---

### Post by Bigbob22 on 2008-12-27
Is there any thing wrong with my computer?

---

### Post by unutbu on 2008-12-27
Please post the output of 
```

cat /etc/fstab
blkid

```
Also, (out of curiosity) what fsck command did you use?

---

### Post by Miljet on 2008-12-27
I believe that the file system has to be unmounted to run fsck. In other words, you need to run it from a live CD.

---

### Post by Bigbob22 on 2008-12-27
The output I received from cat /etc/fstab : 
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=430f5b5a-3423-42fa-8978-e27d3f798ae9 /               ext3    noatime,nodiratime,errors=remount-ro,data=writeback 0       1
# /dev/sda5
UUID=8a5c8a9c-d985-4b54-b4a1-da49f530c34a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
usbfs         /proc/bus/usb usbfs   devgid=14,devmode=0660 0 0
```
There was no output from blkid. I just typed in fsck in my terminal.

---

### Post by unutbu on 2008-12-27
I think Miljet is right. Do not run fsck on a mounted filesystem -- it can lead to data loss.

If you wish to run fsck on /dev/sda1, then boot from a LiveCD, and run
```

sudo fsck /dev/sda1
```

(You have to run it from a LiveCD, because there /dev/sda1 will not be mounted. You can't unmount /dev/sda1 while the machine is running a regular session because it contains your root filesystem.)

---

### Post by Bigbob22 on 2008-12-27
alright thanks.

---

