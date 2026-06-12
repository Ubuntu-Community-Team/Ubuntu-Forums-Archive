---
title: "Error 21"
date: 2009-01-12
forum: New to Ubuntu
---

### Post by tsuchang on 2009-01-12
Hi again
I got Ubuntu working great on my new computer and wanted to put it on the old one.
I was running windoze xp pro and partitioned in Ubuntu.
Now the computer won't start.  I get an error 21.
I rebooted and brought up the ubuntu disc and ran the demo and that worked but jo joy with starting and running without the disc.

Thanks again

---

### Post by HunterThomson on 2009-01-12
> **tsuchang said:**
> Hi again
I got Ubuntu working great on my new computer and wanted to put it on the old one.
I was running windoze xp pro and partitioned in Ubuntu.
Now the computer won't start.  I get an error 21.
I rebooted and brought up the ubuntu disc and ran the demo and that worked but jo joy with starting and running without the disc.

Thanks again

Is that not the Grub error of it not finding the kernel/root partiton to boot?
You may need to eddit the grub menu. You can do that from the Grub comandline.

just thinking out loud....

---

### Post by Terl on 2009-01-12
This thread should help:  [Grub Error 21]("http://ubuntuforums.org/showthread.php?t=62717")

---

### Post by Elfy on 2009-01-12
Should just be a simple edit to get that going again.

Assuming that you have a standardish install you should have only one linux partition. Boot your livecd and run

```
sudo fdisk -l
```the linux drive will be called /dev/sdxy with xy being a number and letter, possibly sda1. Use your drive name in the following

```
sudo mkdir /mnt/tmp
sudo mount -t ext3 /dev/sdxy /mnt/tmp
```

Now run this in a terminal and post it and the reuslt of fdisk -l

```
cat /mnt/tmp/boot/grub/menu.lst
```

If you feel capable of doing so, error 21 is > For example if there are two hard disks in the computer and the boot entry in menu.lst has a mistake in it making it point to (hd2,y)

If you can do so edit the file 

```
gksu gedit /mnt/tmp/boot/grub/menu.lst
```

[http://users.bigpond.net.au/hermanzone/p15.htm#21](http://users.bigpond.net.au/hermanzone/p15.htm#21)

---

