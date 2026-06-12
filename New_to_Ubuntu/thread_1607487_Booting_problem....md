---
title: "Booting problem..."
date: 2010-10-27
forum: New to Ubuntu
---

### Post by Tonylicious on 2010-10-27
Hi,

By the way, I am completely new to Ubuntu and I am not very good in english.

Here is my problem: I can't boot into Ubuntu.

I installed Ubuntu (the latest) using Wubi. Everything was going fine, I explored Ubuntu, installed some programs, and then, I made my updates. Right after, I restarted my laptop. Now, I have a strange black page with text that I don't understand the meaning. I can't boot on Ubuntu...

This is what appeared:

> GNU GRUB version 1.98-28*******-5ubuntu2
Minimal BASH-like line editing is supported. For the first word, TAB list possible command completion. Anywhere else TAB lists possible device or file completion.

grub> _

Thank you very much for your help,

Tonylicious

---

### Post by bcbc on 2010-10-28
Try this: [http://ubuntuforums.org/showpost.php?p=9932369&postcount=5](http://ubuntuforums.org/showpost.php?p=9932369&postcount=5)

It's a slightly different scenario - not an upgrade - but essentially there is a process in wubi Ubuntu that regenerates the wubildr file under certain circumstances - and this will break it as there is a bug in 10.10. 

Anyway - try the fix/workaround. And if it works great. If not, we can try something else.

---

### Post by Tonylicious on 2010-10-28
Thank you for your response:

I tried to replace the wubilr file from C:/ubuntu/winboot/ to C:/ but nothing changed. My problem is still there. So I tried your other solution using the Live CD. When I try to enter this command:

```
sudo mount -o loop /win/ubuntu/disks/root.disk /vdisk
```I get: No such file or directory

I searched manualy in the /win/ folder and there's no root.disk file...

Is it normal... ?

Thank you very much

EDIT:

I skipped the part about the loop command and tried to edit the grub file directly. The file is empty.

---

### Post by bcbc on 2010-10-28
> **Tonylicious said:**
> Thank you for your response:

I tried to replace the wubilr file from C:/ubuntu/winboot/ to C:/ but nothing changed. My problem is still there. So I tried your other solution using the Live CD. When I try to enter this command:

```
sudo mount -o loop /win/ubuntu/disks/root.disk /vdisk
```I get: No such file or directory

I searched manualy in the /win/ folder and there's no root.disk file...

Is it normal... ?

Thank you very much

EDIT:

I skipped the part about the loop command and tried to edit the grub file directly. The file is empty.

You need to find and mount the root.disk. Your hard drive is partitioned and your windows may be on any one of these. Ubuntu sees each partition as /dev/sda1, /dev/sda2 etc. In some cases, if you boot from a usb, the usb becomes /dev/sda and the hard drive is /dev/sdb with partitions /dev/sdb1 etc.

So when you mount e.g.
```
sudo mount /dev/sda1 /win
```
Then you can follow that up with 
```
ls /win/ubuntu/disks/
```
If that doesn't show the root.disk, it's not on /dev/sda1
So, unmount /win and try the next partition
```
sudo umount /win
sudo mount /dev/sda2 /win
```
and try again...etc.

(List your available partitions with "sudo fdisk -l" (lower case L))

When you find it, then this will work (make /vdisk if not already there, loop mount root.disk to /vdisk)
```
sudo mkdir -p /vdisk
sudo mount -o loop /win/ubuntu/disks/root.disk /vdisk
```

If you want explicit instructions, run and post the results of the [bootinfoscript]("http://bootinfoscript.sourceforge.net") - that will tell me where everything is.

---

### Post by Tonylicious on 2010-10-28
I decided to simply re-install Ubuntu but this time on a real partition. Everything works fine.

Thank you for your help !

---

