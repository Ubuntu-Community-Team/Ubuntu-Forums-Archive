---
title: "mounting /dev on /root/dev failed: No such file or directory"
date: 2009-08-19
forum: New to Ubuntu
---

### Post by amarumayo on 2009-08-19
Hi all,

I put my computer (which was working fine) into suspend and the battery died overnight.  Now it will not boot.  I get:

mount: mounting /dev/disk/by-uuid/c3c4608e-fb99-4989-bfe2-ede4aec72b38 on /root
failed: Invalid argument
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting / sys/ on root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or dirctory
Target filesystem doesn't have /sbin/init.
No init found. Try passing init= boot arg

BusyBox v1.10.2 (Ubuntu 1:1.10.2.2ubuntu7) built-in shell (ash)

(initramfs)

I have no idea what may have happened and would not want to lose what was on my hard drive.  Any suggestions? Thanks for any help.

P.s. My computer is an Acer Aspire 4810tz-4696 running ubuntu 9.04

Thanks
Chris

---

### Post by Bodsda on 2009-08-19
> **amarumayo said:**
> Hi all,

I put my computer (which was working fine) into suspend and the battery died overnight.  Now it will not boot.  I get:

mount: mounting /dev/disk/by-uuid/c3c4608e-fb99-4989-bfe2-ede4aec72b38 on /root
failed: Invalid argument
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting / sys/ on root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or dirctory
Target filesystem doesn't have /sbin/init.
No init found. Try passing init= boot arg

BusyBox v1.10.2 (Ubuntu 1:1.10.2.2ubuntu7) built-in shell (ash)

(initramfs)

I have no idea what may have happened and would not want to lose what was on my hard drive.  Any suggestions? Thanks for any help.

P.s. My computer is an Acer Aspire 4810tz-4696 running ubuntu 9.04

Thanks
Chris

Not sure what has happened here, but could you please boot a live cd and mount your system with the following

This will provide you with a list of your drives and partitions, you need to pick the one that your root file system is installed to, it will be something like /dev/sda1
```
sudo fdisk -l
```

Then run this command, which will mount your system. Remember to replace /dev/sda1 in the following command with your device from the first step
```
sudo mkdir /mnt/ubuntu && sudo mount /dev/sda1 /mnt/ubuntu
```

Now could you please paste the contents of your fstab which can be found by running the following command.
```
gksudo gedit /mnt/ubuntu/etc/fstab
```

That should give us some more info to work with.

Kind regards,
Bodsda

---

### Post by amarumayo on 2009-08-19
Hi Bodsda. Thanks for the reply

When I run  sudo mkdir /mnt/ubuntu && sudo mount /dev/sda1 /mnt/ubuntu 
I get:

mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Thanks
Chris

---

### Post by ibuclaw on 2009-08-19
Grab your Ubuntu LiveCD, boot into it, and mount the filesystem with Ubuntu on.

Then run:
```
sudo fdisk -l
```
and
```
cat /*/*/etc/fstab
```

And post the output.

Regards
Iain

---

### Post by amarumayo on 2009-08-19
Sorry, but I am a newb.  Once I have booted into live CD how do I mount the filesystem with boot?
Thanks 
Chris

---

### Post by amarumayo on 2009-08-19
When I try to mount the filesystem from the Live CD I get:

mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Thanks for any help
Chris

---

### Post by ibuclaw on 2009-08-19
> **amarumayo said:**
> When I try to mount the filesystem from the Live CD I get:

mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Thanks for any help
Chris

Go into:  Applications -> Accessories -> Terminal
in the Gnome Menu, then type in

```
sudo fdisk -l
```

---

### Post by amarumayo on 2009-08-19
OK, I get:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7c18dd06

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       37810   303708793+  83  Linux
/dev/sda2           37811       38913     8859847+   5  Extended
/dev/sda5           37811       38913     8859816   82  Linux swap / Solaris
ubuntu@ubuntu:~$ cat /*/*/etc/fstab
cat: /*/*/etc/fstab: No such file or directory
ubuntu@ubuntu:~$

---

### Post by LewRockwell on 2009-08-19
we suspect that due to your battery failure your system was not properly dismounted

[http://manpages.ubuntu.com/manpages/hardy/man8/fsck.8.html](http://manpages.ubuntu.com/manpages/hardy/man8/fsck.8.html)

.

---

### Post by ibuclaw on 2009-08-19
In the terminal, type in (or copy and paste in).
```
sudo e2fsck -fyv /dev/sda1
```

Then Go into: **Places -> Computer**
And select the "300GB Media" or so size disk to mount it, post any errors you may get.

Regards
Iain

---

### Post by amarumayo on 2009-08-19
ubuntu@ubuntu:~$ sudo e2fsck -fyv /dev/sda1
e2fsck 1.41.4 (27-Jan-2009)
/dev/sda1: Attempt to read block from filesystem resulted in short read while reading block 37913090

/dev/sda1: Attempt to read block from filesystem resulted in short read reading journal superblock

e2fsck: Attempt to read block from filesystem resulted in short read while checking ext3 journal for /dev/sda1

and when I try to open the 311GB media is says:

mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Thanks for any help,
Chris

---

### Post by amarumayo on 2009-08-19
So is there anything I can do to fix the problem or recover the data?
Thanks
Chris

---

### Post by michy99 on 2009-08-19
Sounds like it's time to try testdisk to recover the partition.

---

### Post by amarumayo on 2009-08-19
I am a newb.  If anyone could please tell me how to recover the partition I would be extremely grateful.  Thanks a lot.
Chris

---

### Post by scoobeee on 2009-09-15
Just wondering if there was a solution found for this as I am having the same problem with the same initial errors. Did you lose your data?

---

### Post by amarumayo on 2009-09-15
I had to buy a new hard drive however, I was able to recover the data using testdisk.

---

### Post by scoobeee on 2009-09-15
Hmm.. good to know. Thanks.

---

### Post by ssv1986 on 2010-06-21
Helo My Dear Friend..
    Thank you very much for you valuable help.This is one of the great post i have ever seen

---

### Post by ibuclaw on 2010-06-21
*cough*

Closed. :)

---

