---
title: "Need more disk space"
date: 2009-10-08
forum: New to Ubuntu
---

### Post by milan@djurasevich.com.au on 2009-10-08
Hi,
I'm a real novice at this so you may have to reply in monosylables for me to understand.
I have a message in OpenOffice that tells me I need more disk space.
How do I get more disk space ie what do I need to download or use from the Linux boot CD etc?
M

---

### Post by cariboo on 2009-10-08
You really don't need to download anything, or even use the Live Cd.

Open an Applications-->Accessories-->Terminal and type:

```
sudo apt-get autoclean
```

The above command will remove any unneeded dependencies. Next in the same terminal type:

```
sudo apt-get clean
```

This command will removed the archived packages in /var/cache/apt/archives.

This should give more free space on your hard drive.

To check your drive usage, go to Applications-->Accessories-->Disk Usage.

---

### Post by milan@djurasevich.com.au on 2009-10-08
Thanks for your response however I have now tried that and I get the same message.

Is there something else I can try?

M

---

### Post by fuzzyk.k on 2009-10-08
Please paste the output of ```
df -h
```

---

### Post by milan@djurasevich.com.au on 2009-10-08
Filesystem            Size Used Avail Use% Mounted on
/dev/sda5             2.3G  2.3G     0 100% /
tmpfs                1007M     0 1007M   0% /lib/init/rw
varrun               1007M  104K 1007M   1% /var/run
varlock              1007M     0 1007M   0% /var/lock
udev                 1007M  168K 1007M   1% /dev
tmpfs                1007M   96K 1007M   1% /dev/shm
lrm                  1007M  2.4M 1004M   1% /lib/modules/2.6.28-11-generic/volatile
overflow              1.0M  148K  876K  15% /tmp
/dev/sr0               22M   22M     0 100% /media/cdrom0
/dev/sda1             371G   49G  322G  14% /media/disk

I'm sure that makes more sense to you than me

M

---

### Post by random turnip on 2009-10-08
How much of a partition did you give to Ubuntu?
Have you been using Ubuntu before this?

---

### Post by mikechant on 2009-10-08
> /dev/sda5 2.3G 2.3G 0 100% /

This is the important bit.
You have allocated only 2.3Gb of disc space for Ubuntu and that's not enough.

You need to expand the sda5 partition. If you post the output of the command
```
fdisk -l
```
we can see how your partitions are arranged and advise.

Note that the character after the '-' sign above is a lower case letter L, not a number one!

---

### Post by milan@djurasevich.com.au on 2009-10-08
When I type in fdisk -l it returns to the c: prompt

---

### Post by ephmanjmm on 2009-10-08
use:

sudo fdisk -l

---

### Post by milan@djurasevich.com.au on 2009-10-08
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       48315   388090206    7  HPFS/NTFS
/dev/sda2           48316       48641     2618595    5  Extended
/dev/sda5           48316       48619     2441848+  83  Linux
/dev/sda6           48620       48641      176683+  82  Linux swap / Solaris

M

---

### Post by drs305 on 2009-10-08
> **milan@djurasevich.com.au said:**
> Filesystem            Size Used Avail Use% Mounted on
[COLOR="Red"]/dev/sda5             2.3G  2.3G     0 100% /[/COLOR]
/dev/sr0               22M   22M     0 100% /media/cdrom0
/dev/sda1             371G   49G  322G  14% /media/disk

I'm sure that makes more sense to you than me

M

[email]milan@djurasevich.com.au[/email],

Welcome to Ubuntu and the U. forums. :-)

My guess is you are a victim of Step 4 of a "side by side" with Windows installation. There is a bug about this (fixed in Karmic but not earlier versions).

You will have to reinstall or resize the partition. Here is the link to the response I made to another user yesterday about this issue:
[http://ubuntuforums.org/showthread.php?t=1285604#2]("http://ubuntuforums.org/showthread.php?t=1285604#2")

I've written a guides on how to resize the / partition or how to correct Step 4 if you choose to reinstall. The links are on the above linked page.

---

### Post by 3rdalbum on 2009-10-08
I don't believe you'll be able to resize the partition; it's sitting inside an "Extended" partition, and these can't be resized.

Your best option is to use Gparted from a live CD to erase the Extended partition, resize the Windows partition down further, and leave the rest of the space "unallocated". Then the Ubuntu installer will be able to install itself into the unallocated space.

---

### Post by drs305 on 2009-10-08
The resizing can be accomplished, it just has to be done in steps.
Shrink Windows.
Expand extended to include former Windows space.
Expand logical Linux partition.

In the end though it would probably be faster to reinstall.


If you have a 2.5 GB partition and want to reinstall:
[HOWTO: 2.5 GB System Partition - What Went Wrong?]("http://ubuntuforums.org/showthread.php?p=7658271")

If you have a 2.5 GB partition and want to resize the partition:
[Expanding an Ubuntu System Partition]("http://ubuntuforums.org/showthread.php?t=1219270")

---

### Post by mikechant on 2009-10-08
> I don't believe you'll be able to resize the partition; it's sitting inside an "Extended" partition, and these can't be resized.


This is wrong. I've resized my extended partition several times.
The important point is that you can't resize the extended partition if any of the partitions contained in it are mounted, so you need to use the Live CD and turn swap off. 

Anyhow drs305 has given the necessary links.

---

