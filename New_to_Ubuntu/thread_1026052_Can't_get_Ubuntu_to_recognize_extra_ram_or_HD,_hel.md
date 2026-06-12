---
title: "Can't get Ubuntu to recognize extra ram or HD, help, please."
date: 2008-12-30
forum: New to Ubuntu
---

### Post by silverblue23 on 2008-12-30
I have a Gateway GT5028 that I had the "Anti-virus 2009" virus get onto. (I have a girlfriend, and 3 kids....hope that explains the virus! with Kaspersky no less)

Anyway, I reformatted my 2 x 250gb HD, did a Ubuntu 64 install disc and installed it on my comp.

Worked beautifully. However, I cannot get it to recognize my 3gb of ram (and I am upgrading to 4 next week, as soon as the extra ram gets here), nor will it recognize the other 250gb HD. 

I really could use some help, and I would really, really appreciate it.

Thanks so much for any help that anyone can offer!

Matt

---

### Post by taurus on 2008-12-30
What are the outputs of these commands from a terminal?

Applications -> Accessories -> Terminal
```
free -m
sudo fdisk -l
sudo blkid
cat /etc/fstab
df -h
```

---

### Post by silverblue23 on 2008-12-30
thanks so much for your help, I really appreciate it!

           total            used        free     shared    buffers      cached
mem   1000         985            14        0               27              318

-/+ buffers/cache:            639          360
swap:        2925         5         2920


now once i try the sudo fdisk -1, my numbers will not work? weird, let me try to connect a wired keyboard, hang on

---

### Post by Scarlath on 2008-12-30
> **silverblue23 said:**
> now once i try the sudo fdisk -1, my numbers will not work? weird, let me try to connect a wired keyboard, hang on

Please note that it's an l (L), not 1 (one) :p

---

### Post by silverblue23 on 2008-12-30
ok, new batteries, duh

invalid option '1'

usage: fdisk [-b SSZ] [-u] DISK change partition table
            fdisk  -l  [-b SSZ]    [-u] DISK    List partition table(s)
            fdisk  -s PARTITION      give partition size(s) in blocks
             fdisk    -v            give fdisk version

sudo blkid-

/dev/sdal: uuid-"c005cea6-9b0e-4717-9c93-3190e8

---

### Post by silverblue23 on 2008-12-30
OH, sorry, k, got that, waiting for system to restart, it just finished updates, brb, thanks again

---

### Post by silverblue23 on 2008-12-30
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1d231d22

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30028   241199878+  83  Linux
/dev/sda2           30029       30401     2996122+   5  Extended
/dev/sda5           30029       30401     2996091   82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x14cb14cb

   Device Boot      Start         End      Blocks   Id  System
silverblue23@Silverblue:~$

---

### Post by silverblue23 on 2008-12-30
sudo blkid

/dev/sda1: UUID="c005cea6-9b0e-4717-9c93-3190e890a106" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="5793f028-b722-415e-b12e-2a97fb011ed6" 

cat /etc/fstab

silverblue23@Silverblue:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=c005cea6-9b0e-4717-9c93-3190e890a106 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=5793f028-b722-415e-b12e-2a97fb011ed6 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


df -h

silverblue23@Silverblue:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             227G  2.8G  213G   2% /
tmpfs                 501M     0  501M   0% /lib/init/rw
varrun                501M  100K  500M   1% /var/run
varlock               501M     0  501M   0% /var/lock
udev                  501M  2.8M  498M   1% /dev
tmpfs                 501M  624K  500M   1% /dev/shm
lrm                   501M  2.4M  498M   1% /lib/modules/2.6.27-9-generic/volatile
silverblue23@Silverblue:~$

---

### Post by taurus on 2008-12-30
> **silverblue23 said:**
> Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1d231d22

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30028   241199878+  83  Linux
/dev/sda2           30029       30401     2996122+   5  Extended
/dev/sda5           30029       30401     2996091   82  Linux swap / Solaris

[B][COLOR="Blue"]Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x14cb14cb

   Device Boot      Start         End      Blocks   Id  System[/COLOR][/B]
silverblue23@Silverblue:~$

Are you sure you have partitioned your second harddrive because it looks like there is nothing on it as of right now.

Why don't you install gparted and use it to create some partitions on it.

```
sudo apt-get update
sudo apt-get install gparted
gksudo gparted
```

---

### Post by silverblue23 on 2008-12-30
Ok, there, I think that is everything, right? I hope that is the information that you needed, cause I am lost! Let me know if you need anything else. Thanks again!

Matt

---

### Post by silverblue23 on 2008-12-30
When I installed Ubuntu, I tried to do both of the hard drives, but I didn't see a way to add both of them, so ya, the other hard drive is completely empty, does it have to be partitioned even if it is empty?

---

### Post by taurus on 2008-12-30
> **silverblue23 said:**
> When I installed Ubuntu, I tried to do both of the hard drives, but I didn't see a way to add both of them, so ya, the other hard drive is completely empty, does it have to be partitioned even if it is empty?

It has to be partitioned and formatted (filesystem) first before you can use it.

---

### Post by silverblue23 on 2008-12-30
OK, put the code in terminal, thanks by the way, and it dl it, what do I do know?

---

### Post by taurus on 2008-12-30
How did you partition your second harddrive?  Can you post the outputs of these commands from a terminal?

```
sudo fdisk -l
sudo blkid
```

---

### Post by silverblue23 on 2008-12-30
ok, went to system, partion, gpart, changed devices to the other 250gb hd, partioned the whole thing, says creating primary partion #1 (ext2, 232.88 gib0 on /dev/sdb, is this correct?

---

### Post by silverblue23 on 2008-12-30
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1d231d22

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30028   241199878+  83  Linux
/dev/sda2           30029       30401     2996122+   5  Extended
/dev/sda5           30029       30401     2996091   82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x14cb14cb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001   83  Linux
silverblue23@Silverblue:~$ 


$ sudo blkid
/dev/sda1: UUID="c005cea6-9b0e-4717-9c93-3190e890a106" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="5793f028-b722-415e-b12e-2a97fb011ed6" 
/dev/sdb1: UUID="6e5b4583-e8b2-4493-92c1-5f3c4db6097e" TYPE="ext2" 
silverblue23@Silverblue:~$

---

### Post by taurus on 2008-12-30
I thought you want to created a swap partition out of that second harddrive since your initial swap partition is too small?

If that's the case, then you want to create two primary partitions: /dev/sdb1 & /dev/sdb2.  Format /dev/sdb1 as ext2 filesystem and the second partition (~2GB if you want) as swap.  

Then, you need to add two entries in /etc/fstab to have them mount automatically each time you boot.  Again, post the outputs of these two commands after you have finished partitioning your second harddrive with gparted.

---

### Post by silverblue23 on 2008-12-30
Now, I am an idiot when it comes to this stuff, but what it looks like is that Ubuntu is using my extra ram as "swap," which is kinda like OSX leopard, right? not sure.

anyway, shouldn't it recognize it as reg. ram? the system seems kinda slow, definitely slower than it was before I reformatted and installed Ubuntu instead of XP.

---

### Post by silverblue23 on 2008-12-30
ok, now you lost me.

I need to create two primary partitions on the 2nd hd? or 1 primary on the first hd, and the other on the 2nd hd?

---

### Post by silverblue23 on 2008-12-30
and I have, I think, 4gb of ram installed, but the comp. only came with 1gb, I upgraded, so I don't want to create swap unless I have to right? I need to have it recognize the extra ram as extra ram, right?

---

### Post by taurus on 2008-12-30
I guess you have enough swap space so you can leave /dev/sdb1 the way it is now.

Now, edit /etc/fstab
```
gksudo gedit /etc/fstab
```
and add this line to the end of it.

```

UUID=6e5b4583-e8b2-4493-92c1-5f3c4db6097e   /media/sdb1   ext2   defaults   0   2
```
Save it.  Then, create a new mount point and mount it.

```
sudo mkdir /media/sdb1
sudo mount -a
df -h
```
Your second harddrive, /dev/sdb1, is now mounted to /media/sdb1.  And if you want to write to it without using sudo/gksudo, then you need to change the ownership of /media/sdb1 from root to your login name, silverblue23.

```
sudo chown -R silverblue23:silverblue23 /media/sdb1
ls -la /media
```

---

### Post by silverblue23 on 2008-12-30
ok, I think that I have the 2nd hd formatted, now I just need to get it mounted, right?

I guess I need to do that in terminal, but I don't know how to do that.....

---

### Post by silverblue23 on 2008-12-30
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=c005cea6-9b0e-4717-9c93-3190e890a106 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=5793f028-b722-415e-b12e-2a97fb011ed6 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
UUID=6e5b4583-e8b2-4493-92c1-5f3c4db6097e   /media/sdb1   ext2   defaults   0   2

Like this?

---

### Post by taurus on 2008-12-30
Yes, and continue with my previous post about creating the new mount point, mounting it, and changing the ownership of /media/sdb1.

---

### Post by silverblue23 on 2008-12-30
silverblue23@Silverblue:~$ sudo mkdir /media/sdb1
mkdir: cannot create directory `/media/sdb1': File exists
silverblue23@Silverblue:~$ sudo mount -a
mount: special device /dev/disk/by-uuid/6e5b4583-e8b2-4493-92c1-5f3c4db6097e does not exist
silverblue23@Silverblue:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             227G  2.8G  213G   2% /
tmpfs                 501M     0  501M   0% /lib/init/rw
varrun                501M  100K  500M   1% /var/run
varlock               501M     0  501M   0% /var/lock
udev                  501M  2.8M  498M   1% /dev
tmpfs                 501M  624K  500M   1% /dev/shm
lrm                   501M  2.4M  498M   1% /lib/modules/2.6.27-9-generic/volatile
silverblue23@Silverblue:~$ 
silverblue23@Silverblue:~$ sudo mkdir /media/sdb1
mkdir: cannot create directory `/media/sdb1': File exists
silverblue23@Silverblue:~$ sudo mount -a
mount: special device /dev/disk/by-uuid/6e5b4583-e8b2-4493-92c1-5f3c4db6097e does not exist
silverblue23@Silverblue:~$ df -h

---

### Post by silverblue23 on 2008-12-30
How in the hell do you know all this stuff? Holy crap! anyway, don't think that i did it right?

---

### Post by taurus on 2008-12-30
Okay, edit /etc/fstab and replace this first part

```
UUID=6e5b4583-e8b2-4493-92c1-5f3c4db6097e
```
with this

```
/dev/sdb1
```
so it now looks like this.

```
/dev/sdb1   /media/sdb1   ext2   defaults   0   2
```
Save it and close down gedit editing window.  Then, mount it and change the ownership of /media/sdb1.

```
sudo mount -a
df -h
sudo chown -R silverblue23:silverblue23 /media/sdb1
ls -la /media
```

---

### Post by silverblue23 on 2008-12-30
Just another quick question....jk......

Is it possible to use the 2nd HD as like a mirror, so that if one HD goes bad, I can just buy another 250gb hd and replace it, have it re-mirror it, and go on...?

---

### Post by silverblue23 on 2008-12-30
silverblue23@Silverblue:~$ sudo mount -a
mount: special device /dev/disk/by-uuid/6e5b4583-e8b2-4493-92c1-5f3c4db6097e does not exist
silverblue23@Silverblue:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             227G  2.8G  213G   2% /
tmpfs                 501M     0  501M   0% /lib/init/rw
varrun                501M  100K  500M   1% /var/run
varlock               501M     0  501M   0% /var/lock
udev                  501M  2.8M  498M   1% /dev
tmpfs                 501M  624K  500M   1% /dev/shm
lrm                   501M  2.4M  498M   1% /lib/modules/2.6.27-9-generic/volatile
silverblue23@Silverblue:~$ gksudo gedit /etc/fstab
sudo mkdir /media/sdb1
sudo mount -a
df -h

silverblue23@Silverblue:~$ sudo mkdir /media/sdb1
mkdir: cannot create directory `/media/sdb1': File exists
silverblue23@Silverblue:~$ sudo mount -a
mount: special device /dev/disk/by-uuid/6e5b4583-e8b2-4493-92c1-5f3c4db6097e does not exist
silverblue23@Silverblue:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             227G  2.8G  213G   2% /
tmpfs                 501M     0  501M   0% /lib/init/rw
varrun                501M  100K  500M   1% /var/run
varlock               501M     0  501M   0% /var/lock
udev                  501M  2.8M  498M   1% /dev
tmpfs                 501M  624K  500M   1% /dev/shm
lrm                   501M  2.4M  498M   1% /lib/modules/2.6.27-9-generic/volatile
silverblue23@Silverblue:~$ 
silverblue23@Silverblue:~$ sudo mkdir /media/sdb1
mkdir: cannot create directory `/media/sdb1': File exists
silverblue23@Silverblue:~$ sudo mount -a
mount: special device /dev/disk/by-uuid/6e5b4583-e8b2-4493-92c1-5f3c4db6097e does not exist
silverblue23@Silverblue:~$ gksudo gedit /etc/fstab
silverblue23@Silverblue:~$ sudo mount -a
silverblue23@Silverblue:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             227G  2.8G  213G   2% /
tmpfs                 501M     0  501M   0% /lib/init/rw
varrun                501M  100K  500M   1% /var/run
varlock               501M     0  501M   0% /var/lock
udev                  501M  2.8M  498M   1% /dev
tmpfs                 501M  624K  500M   1% /dev/shm
lrm                   501M  2.4M  498M   1% /lib/modules/2.6.27-9-generic/volatile
/dev/sdb1             230G   60M  218G   1% /media/sdb1
silverblue23@Silverblue:~$ sudo chown -R silverblue23:silverblue23 /media/sdb1
silverblue23@Silverblue:~$ ls -la /media

---

### Post by silverblue23 on 2008-12-30
I think that worked!! Thanks so much for your help!!

Will the computer automatically use the 2nd HD when the first is full, or will the mirroring thing that I talked about work for me? Let me know what you think is best, really appreciate it!

Matt

---

### Post by taurus on 2008-12-30
No to both questions.  It will not mirror the first harddrive and the system will not use the second harddrive, /media/sdb1, when the first one is full.  However, if you plan to store a bunch of music and movies on your computer (those can take up a lot of space), save them to /media/sdb1.

---

### Post by silverblue23 on 2008-12-30
OH, ok, awesome, thanks so much. Do you know what to do about Ubuntu recognizing the extra installed RAM?

---

### Post by taurus on 2008-12-30
Are they the same module and speed?  Does the BIOS recognize all of them?  Switch them around on the mobo.  At the GRUB menu, run a memtest.

---

### Post by silverblue23 on 2008-12-30
they were working on this same system on windows xp, but not now on Ubuntu, where is the GRUB menu?

---

### Post by silverblue23 on 2008-12-30
ok, typed GRUB on terminal, got

grub>

now what do I type?

---

### Post by taurus on 2008-12-30
The GRUB menu is the menu when you first turn on (or reboot) your computer.

Type **quit** to get out of that.

---

### Post by silverblue23 on 2008-12-30
Ok, hang on, let me do that, I will boot up my laptop, brb

---

### Post by silverblue23 on 2008-12-30
Ok, I am running the memtest now, what I am looking for when the test is done?

---

### Post by silverblue23 on 2008-12-30
ok, guess I am losing my mind, just opened up the system, no extra ram installed, do you know how much ram I Ubuntu 64 will support?

---

### Post by silverblue23 on 2008-12-30
Thank you so much for your help, I cannot tell you how much I appreciate it!

---

