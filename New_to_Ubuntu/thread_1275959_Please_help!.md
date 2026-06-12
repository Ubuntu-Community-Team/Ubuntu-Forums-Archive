---
title: "Please help!"
date: 2009-09-26
forum: New to Ubuntu
---

### Post by Kimbo84 on 2009-09-26
Hi there, I am totally new to Linux/Ubuntu. I have found it very easy to use until I got a technical problem!!

When I start up I get this (exact) message:

[B]starting up
loading, please wait...
19+0 records in
19+0 records out
kinit: name_to_dev_t (/dev/disk/by-uuid/962986a4-2e9d-47e1-942a-39cc6c0d8271)=dev (8,5)
kinit: trying to resume from dev/disk/by-uuid/92986a4-2e9d-47e1-942a-39cc6c0d8271
kinit: no resume image, doing normal boot...
mount: mounting /dev on /root/dev
failed: no such file or directory
mount: mounting /sys on /root/sys
failed: no such file or directory
mount: mounting /proc on /root/proc
failed: no such file or directory
target file system doesnt have /sbin/init
no init found. try passing init=bootarg

BusyBox v1.10.2 (ubuntu 1:1.10.2-2ubuntu.7) built in shell (ash) 
enter 'help' for a list of built- in commands

(initramfs)[/B]

Now, I have no idea how much of that is needed but I thought it would be better to type it all!

I have been running my laptop (Acer aspire one) off a boot disk which is fine for the short term bt obviously I need to either fix the issue or buy a new laptop!

If anyone can help I would be eternally grateful!!

THANKS!!!

---

### Post by mapes12 on 2009-09-26
So that I am clear, you are running Ubu from a Live CD and have another OS on the laptop HDD??

---

### Post by Kimbo84 on 2009-09-26
Erm... I have a USB startup disk :confused:

---

### Post by scrooge_74 on 2009-09-26
Hard drive not working anymore?

---

### Post by kansasnoob on 2009-09-26
We may be able to mount and chroot into Ubuntu and fix what's wrong.

Let's begin by gathering some information. Start by posting the output from terminal of:

```
sudo fdisk -l
```

BTW, that's a lower case L.

---

### Post by Kimbo84 on 2009-09-26
Disk /dev/sda: 8069 MB, 8069677056 bytes
255 heads, 63 sectors/track, 981 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf5d28b9b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         933     7494291   83  Linux
/dev/sda2             934         981      385560    5  Extended
/dev/sda5             934         981      385528+  82  Linux swap / Solaris

Disk /dev/sdb: 1028 MB, 1028653056 bytes
255 heads, 63 sectors/track, 125 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000830c0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         125     1004031    b  W95 FAT32
ubuntu@ubuntu:~$

---

### Post by kansasnoob on 2009-09-26
OK, working from terminal run the following commands (copy & paste if possible):

```
sudo mount /dev/sda1 /mnt
```

```
sudo mount --bind /dev /mnt/dev
```

```
sudo mount --bind /proc /mnt/proc
```

And finally:

```
sudo chroot /mnt
```

You'll see the command prompt change from a $ to # indicating that sda1 is mounted as root. Post the full output of:

```
cat /etc/issue
```

and:

```
uname -a
```

just so we can see what we're working on.

---

### Post by kansasnoob on 2009-09-26
Forgot one. Lets see what disc usage is like:

```
df -H
```

---

### Post by Kimbo84 on 2009-09-26
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt
sudo mount --bind /dev /mnt/dev
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

ubuntu@ubuntu:~$ sudo mount --bind /dev /mnt/dev
mount: mount point /mnt/dev does not exist
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ sudo mount --bind /proc /mnt/proc
mount: mount point /mnt/proc does not exist
ubuntu@ubuntu:~$ sudo chroot /mnt
chroot: cannot run command `/bin/bash': No such file or directory
ubuntu@ubuntu:~$ cat /etc/issue
Ubuntu 9.04 \n \l

ubuntu@ubuntu:~$ uname -a
Linux ubuntu 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux
ubuntu@ubuntu:~$ df -H
Filesystem             Size   Used  Avail Use% Mounted on
tmpfs                  255M   2.5M   253M   1% /lib/modules/2.6.28-11-generic/volatile
tmpfs                  255M   2.5M   253M   1% /lib/modules/2.6.28-11-generic/volatile
tmpfs                  255M      0   255M   0% /lib/init/rw
varrun                 255M   107k   255M   1% /var/run
varlock                255M      0   255M   0% /var/lock
udev                   255M   160k   255M   1% /dev
tmpfs                  255M   136k   255M   1% /dev/shm
rootfs                 255M    55M   201M  22% /
/dev/sdb1              1.1G   733M   294M  72% /cdrom
/dev/loop0             708M   708M      0 100% /rofs
tmpfs                  255M    13k   255M   1% /tmp
ubuntu@ubuntu:~$

---

### Post by kansasnoob on 2009-09-26
Well, that begins to look somewhat like a hard drive failure but let's still see the output of:

```
df -H
```

And if the installed Ubuntu is same version as the live USB:

```
cat /etc/issue
```

```
uname -a
```

Had you installed from the same live USB you're now using?

Had you done a dist-upgrade?

---

### Post by kansasnoob on 2009-09-26
> **Kimbo84 said:**
> ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt
sudo mount --bind /dev /mnt/dev
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

ubuntu@ubuntu:~$ sudo mount --bind /dev /mnt/dev
mount: mount point /mnt/dev does not exist
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ sudo mount --bind /proc /mnt/proc
mount: mount point /mnt/proc does not exist
ubuntu@ubuntu:~$ sudo chroot /mnt
chroot: cannot run command `/bin/bash': No such file or directory
ubuntu@ubuntu:~$ cat /etc/issue
Ubuntu 9.04 \n \l

ubuntu@ubuntu:~$ uname -a
Linux ubuntu 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux
ubuntu@ubuntu:~$ df -H
Filesystem             Size   Used  Avail Use% Mounted on
tmpfs                  255M   2.5M   253M   1% /lib/modules/2.6.28-11-generic/volatile
tmpfs                  255M   2.5M   253M   1% /lib/modules/2.6.28-11-generic/volatile
tmpfs                  255M      0   255M   0% /lib/init/rw
varrun                 255M   107k   255M   1% /var/run
varlock                255M      0   255M   0% /var/lock
udev                   255M   160k   255M   1% /dev
tmpfs                  255M   136k   255M   1% /dev/shm
rootfs                 255M    55M   201M  22% /
/dev/sdb1              1.1G   733M   294M  72% /cdrom
/dev/loop0             708M   708M      0 100% /rofs
tmpfs                  255M    13k   255M   1% /tmp
ubuntu@ubuntu:~$

Sorry! I hadn't read as far as I should have:(

Give me a minute. I don't like this:

> /dev/loop0             708M   708M      0 100% /rofs

Give me a few minutes to parse things.

---

### Post by Kimbo84 on 2009-09-26
ubuntu@ubuntu:~$ df -H
Filesystem             Size   Used  Avail Use% Mounted on
tmpfs                  255M   2.5M   253M   1% /lib/modules/2.6.28-11-generic/volatile
tmpfs                  255M   2.5M   253M   1% /lib/modules/2.6.28-11-generic/volatile
tmpfs                  255M      0   255M   0% /lib/init/rw
varrun                 255M   107k   255M   1% /var/run
varlock                255M      0   255M   0% /var/lock
udev                   255M   160k   255M   1% /dev
tmpfs                  255M   136k   255M   1% /dev/shm
rootfs                 255M    78M   178M  31% /
/dev/sdb1              1.1G   733M   294M  72% /cdrom
/dev/loop0             708M   708M      0 100% /rofs
tmpfs                  255M    13k   255M   1% /tmp
ubuntu@ubuntu:~$ cat /etc/issue
Ubuntu 9.04 \n \l

ubuntu@ubuntu:~$ uname -a
Linux ubuntu 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux
ubuntu@ubuntu:~$ 

The start up USB is the one I used originally and worked fine.

Not done a dist-upgrade I dont think 


	 	 	 		  		 		 		 			[[IMG]http://ubuntuforums.org/images/buttons/quote.gif[/IMG]]("http://ubuntuforums.org/newreply.php?do=newreply&p=8011332")

---

### Post by kansasnoob on 2009-09-26
Must need more coffee. the df-H results are normal for a live USB!

So lets close the terminal and go to System > Administration > Partition Editor. In the upper right hand corner you'll see an area where you can toggle to either sda or sdb, sdb is your live USB so leave it alone, toggle to sda and then right click on sda1.

Then click on "check" and apply. Wait for it to run and read the results.

Also a screenshot of sda might be helpful regarding disc usage.

---

### Post by Kimbo84 on 2009-09-26
Screenshots attached

---

### Post by kansasnoob on 2009-09-26
Were you able to read the details?

---

### Post by Kimbo84 on 2009-09-26
Sorry, which details?

---

### Post by kansasnoob on 2009-09-26
From Gparted (aka: partition editor). There's a detail window.

But I'm thinking of something else. Give me a minute.

---

### Post by kansasnoob on 2009-09-26
> **Kimbo84 said:**
> Disk /dev/sda: 8069 MB, 8069677056 bytes
255 heads, 63 sectors/track, 981 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf5d28b9b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         933     7494291   83  Linux
/dev/sda2             934         981      385560    5  Extended
/dev/sda5             934         981      385528+  82  Linux swap / Solaris

Disk /dev/sdb: 1028 MB, 1028653056 bytes
255 heads, 63 sectors/track, 125 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000830c0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         125     1004031    b  W95 FAT32
ubuntu@ubuntu:~$

I'm looking at this again. I made the assumption that Ubuntu is installed on sda. That certainly looks like a typical Ubuntu install with / on sda1 followed by an extended partition (sda2) that contains swap (sda5).

But I see in those two screenshots that sda is only 7.51GB, that seems incredibly small. More like the size of a flash drive (maybe your USB live drive), but then I wonder what sdb is:

> Disk /dev/sdb: 1028 MB, 1028653056 bytes
255 heads, 63 sectors/track, 125 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000830c0

Device Boot Start End Blocks Id System
/dev/sdb1 * 1 125 1004031 b W95 FAT32

One of those things where I wish I was there. Do you know what size your original installed hard drive is?

Do you have a Live CD and a working CD ROM?

Also, just a thought: is it possible that you have some other external device plugged in or inserted? Like a camera or another storage device like an external drive (other than the Live USB) or a data card inserted in a card reader?

---

### Post by Kimbo84 on 2009-09-26
The laptop I have is 8g of solid state memory. Its an Acer Aspire One laptop

---

### Post by kansasnoob on 2009-09-26
> **Kimbo84 said:**
> The laptop I have is 8g of solid state memory. Its an Acer Aspire One laptop

In that case I think I was looking in the right place.

If you'd try to run a "check" on sda1 again from Gparted, please post the details, that is "why did check disk fail".

Also, with that small of a disc you must not have anything saved, so have you tried to reinstall?

I'm really betting on a bad drive.

---

### Post by Kimbo84 on 2009-09-26
It would appear the options have changed?? This is how it looks now (See screenshot)

There are no other options in the drop down menu... :confused:

Sorry, Im not very good at this :(

---

### Post by kansasnoob on 2009-09-26
Just FYI, nine times out of ten the bad sectors on any disc will be at the beginning of the disc, so you might get a few more miles out of that if you were to reformat the drive and create a 1 to 2 GB partition at the beginning, then install Ubuntu on the remaining part of the drive.

---

### Post by Kimbo84 on 2009-09-26
No idea how you would do that...

---

### Post by kansasnoob on 2009-09-26
That last screenshot looks like it's your Live USB.

I just don't think I could fix this without having it right in front of me, but it does sound like a dead hard drive!

And if you restart with the Live USB it may become the boot drive if no other drive is operational.

That said, I've seldom dealt with such a small drive!

---

### Post by YaKillaCJ on 2009-09-28
Hmm, I had a similar error. Thing is, it only happens after I installed the nVidia Drivers. Nothin still when I went to recovery to fix video card options.

I did a fresh install twice cause of it, lol. Im on a fresh install now, did all the updates except the nVidia Drivers. I was wonderin if its cause the SLI im usin now but he havin same issue wit a labtop tho.
Im certain it has somethin 2 do wit the Video Card Drivers because thats only time I get the error.

Heres a picture of the error:
[IMG]http://i51.photobucket.com/albums/f392/YaBoiCJ/img_0669.jpg[/IMG]

---

