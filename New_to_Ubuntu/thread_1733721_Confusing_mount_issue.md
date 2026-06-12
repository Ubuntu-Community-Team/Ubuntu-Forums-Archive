---
title: "Confusing mount issue"
date: 2011-04-19
forum: New to Ubuntu
---

### Post by breem42 on 2011-04-19
I dual boot 10.4 & Win7, plus I have a few other partitions, some ntfs/vfat, some ext3.

When I boot the machine, all bootable partitions appear in the menu as expected.

When I choose to boot Ubuntu, and log in, only one disk icon appears appears on the desktop, being "System Reserved".  If I start Nautilus it shows me the missing disks in the left hand frame, and if I click on them, they show up on the desktop.

The trouble is, if I don't use Nautilus to 'mount' the partitions first, programs like gpodder will fail because they can't find the directories they need.  This is a real annoyance.

Thanks for any assistance.  My apologies if this has already been dealt with elsewhere.

---

### Post by coffeecat on 2011-04-19
It sounds as though "System Reserved" is being automounted by means of a line in /etc/fstab - which is not a good idea - but partitions you do need /etc/fstab lines for do not have them.

Post the output of these three commands:

```
cat /etc/fstab
sudo fdisk -lu
sudo blkid
```Please post each between [noparse]```
 and 
```[/noparse] tags otherwise we'll lose essential formatting. Someone will then be able to help you edit /etc/fstab to achieve what you need. Let us know also which partitions you want mounted automatically.

And/or this is a useful link for editing /etc/fstab:

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

By the way, if someone suggests you install and use the app ntfs-config to configure your NTFS partitions, my advice is, DON'T. It's a buggy piece of software that does the most extraordinary things.

---

### Post by GWBouge on 2011-04-19
You can add some lines to /etc/fstab to automatically mount the filesystems at boot.  For example, here are the two lines I added to mount two NTFS partitions, my Windows partition and an External drive:

```
/dev/sda1 /media/Windows ntfs auto,user 0 0
/dev/sdb1 /media/External ntfs auto,user 0 0
```

Here are a couple decent overviews of fstab, but you can search the forums or Google for more info:

[https://help.ubuntu.com/community/Fstab]("https://help.ubuntu.com/community/Fstab")
[http://www.tuxfiles.org/linuxhelp/fstab.html]("http://www.tuxfiles.org/linuxhelp/fstab.html")

---

### Post by breem42 on 2011-04-19
OK here is my anonymized output

```

username@MachineName:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	nodev,noexec,nosuid	0	0
#Entry for /dev/sdc5 :
UUID=4cf5896e-43dd-4aee-8bea-c0b0799b01c2	/	ext4	errors=remount-ro	0	1
#Entry for /dev/sdc2 :
UUID=2872ADEA72ADBD46	/Win7	ntfs-3g	defaults,nosuid,nodev,locale=en_CA.utf800
#Entry for /dev/sdb1 :
UUID=84A433A0A43393A0	/OldXP	ntfs-3g	defaults,nosuid,nodev,locale=en_CA.utf800
#Entry for /dev/sdc1 :
UUID=72DCA54CDCA50B83	/media/System\040Reserved	ntfs	defaults,nls=utf8,umask=0222,nosuid,nodev	0	0
#Entry for /dev/sdc6 :
UUID=f9ef7b1c-c1ed-4bce-95fc-2b6ecfe76f83	none	swap	sw	0	0


username@MachineName:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	nodev,noexec,nosuid	0	0
#Entry for /dev/sdc5 :
UUID=4cf5896e-43dd-4aee-8bea-c0b0799b01c2	/	ext4	errors=remount-ro	0	1
#Entry for /dev/sdc2 :
UUID=2872ADEA72ADBD46	/Win7	ntfs-3g	defaults,nosuid,nodev,locale=en_CA.utf8	0	0
#Entry for /dev/sdb1 :
UUID=84A433A0A43393A0	/OldXP	ntfs-3g	defaults,nosuid,nodev,locale=en_CA.utf8	0	0
#Entry for /dev/sdc1 :
UUID=72DCA54CDCA50B83	/media/System\040Reserved	ntfs	defaults,nls=utf8,umask=0222,nosuid,nodev	0	0
#Entry for /dev/sdc6 :
UUID=f9ef7b1c-c1ed-4bce-95fc-2b6ecfe76f83	none	swap	sw	0	0


username@MachineName:~$ sudo fdisk -lu
[sudo] password for username: 

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb6edcea3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2          206848   522446847   261120000    7  HPFS/NTFS
/dev/sda3       522446848  1535152923   506353038   83  Linux
/dev/sda4      1535154174  1953523711   209184769    5  Extended
/dev/sda5      1535154176  1936478207   200662016   83  Linux
/dev/sda6      1936480256  1953523711     8521728   82  Linux swap / Solaris

Disk /dev/sdb: 40.1 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders, total 78242976 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x301b9edf

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    76148099    38074018+  83  Linux
/dev/sdb2        76148100    78236549     1044225   82  Linux swap / Solaris

Disk /dev/sdc: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0b4b0b4a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63   307194929   153597433+   7  HPFS/NTFS
/dev/sdc2       307194930   614405924   153605497+  83  Linux
/dev/sdc3       614405925   625137344     5365710    5  Extended
/dev/sdc5       614405988   625137344     5365678+  82  Linux swap / Solaris

Disk /dev/sdd: 2019 MB, 2019557376 bytes
19 heads, 18 sectors/track, 11533 cylinders, total 3944448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1            8192     3944447     1968128    b  W95 FAT32
username@MachineName:~$ sudo blkid
/dev/sda1: LABEL="System Reserved" UUID="72DCA54CDCA50B83" TYPE="ntfs" 
/dev/sda2: LABEL="MachineName" UUID="2872ADEA72ADBD46" TYPE="ntfs" 
/dev/sda3: UUID="ee59af83-dc97-4dba-9fc0-d81067db58a7" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="4cf5896e-43dd-4aee-8bea-c0b0799b01c2" TYPE="ext4" 
/dev/sda6: UUID="f9ef7b1c-c1ed-4bce-95fc-2b6ecfe76f83" TYPE="swap" 
/dev/sdb1: UUID="0c9c64ed-a412-4122-b321-123b2481dc1a" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb2: UUID="41079ba3-0c47-42cc-9005-9e12b2c1b076" TYPE="swap" 
/dev/sdc1: LABEL="Local Disk" UUID="84A433A0A43393A0" TYPE="ntfs" 
/dev/sdc2: UUID="c559e081-a4e3-4b9e-a677-dadc77d44381" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc5: UUID="57a39155-9655-4506-ad39-fbf782f8851d" TYPE="swap" 
/dev/sdd1: UUID="1943-E896" TYPE="vfat" 
username@MachineName:~$ 

```

However, I don't think these are the problem.  If these disks were not mounted, I would have thought that Nautilus would not find them and thus I would not be able to get them accessible except through changing fstab.

Why does clicking on the entry in Nautilus make these partitions available.  Is there some flag I need to turn on which tells Ubuntu to mount all disks in fstab at boot time?

---

### Post by breem42 on 2011-04-19
BTW the above output was generated before starting Nautilus to make the partitions accessible.

---

### Post by coffeecat on 2011-04-20
It looks as though you have let ntfs-config loose on your system in the past. I should have realised - setting up a mount point for "System Reserved", the Win7 boot partition, is the sort of silly thing it does. Not to worry - we can repair that before it does any damage. There are also two entries in fstab for NTFS partitions that no longer exist - I would have thought you would get error messages on boot up.

You don't say which partitions you want automounted. You have ext3 partitions at sdb1 and sdc2 and a NTFS partition at sdc1. All of them? There's also a FAT32 partition, sdd1, bot that looks like a 2GB pendrive. Your live USB perhaps?

Once you've confirmed those questions, I can give you a suggested modified fstab.

---

### Post by breem42 on 2011-04-20
Thanks for your quick replies.  I only get at this computer in the evening, which makes my response is slow.

Actually, all of the entries in fstab represent actual partitions.  I bought a new PC back in Nov. and transferred drives from my old one, which had WinXP and a 32 bit version of 10.04 Ubuntu.  It is kind of messy, but that is OK.  Yes, there is also a pen drive in there too, and it _does_ get "auto mounted" (i.e. the icon shows up on the desktop after I log in).

Some of the partitions are already mounted.  I tried an experiment to prove this.

I restarted my machine.  Right after logging again in I started a Gnome terminal (Ver 2.30.2).  There I typed ```
cd /Win7
```which is the mount point for my Windows 7 ntfs partition.  Then I typed "ls".  All expected files & directories showed up.

So... I then typed ```
cd /OldXP
```Again, the files show up fine.  These partitions work just fine.  However, drives with mount points in "/media" (except for the pen drive) do not work as well.  If I type ```
cd /media/ee59af83-dc97-4dba-9fc0-d81067db58a7
```(which is the mount point for the 500GB partition) I get the error "bash: cd: /media/ee59af83-dc97-4dba-9fc0-d81067db58a7: No such file or directory".  It is this partition that gpodder is looking for.

I want all drives to be auto mounted except the pen drive, which may be absent some times -- that one already works the way I want it to.  My experiment tells me that some drives _are_ getting auto mounted.

Thanks for your assistance.

---

### Post by coffeecat on 2011-04-21
First, apologies for this mistake:

> **coffeecat said:**
> There are also two entries in fstab for NTFS  partitions that no longer exist - I would have thought you would get  error messages on boot up.

That was misleading. I was a bit under the weather when I posted and missed that the  partitions do indeed exist. You've found that you need to cd to the  mountpoint, /Win7 or /OldXP, to navigate to them in the terminal. The GUI  way would be to open a Nautilus window, click on "File System" in the  left pane and you'll see the Win7 and OldXP folders among all the system  folders.

The reason they don't show up on the desktop automatically, and the  System Reserved folder does, is because they are not mounted in /media  and System Reserved is. If you create a mountpoint in /media for a  partition or external drive, a desktop icon will appear when you mount  it. If you create a mountpoint anywhere else then a desktop icon will  not appear and you have to navigate to the mountpoint as already  described.

One thing to think about, therefore, when you come to edit /etc/fstab is  to have those two NTFS partitions mounting in /media, so that you get  desktop icons for them.

Next point:

> **breem42 said:**
> However, drives with mount points in "/media" (except for the pen drive) do not work as well.  If I type ```
cd /media/ee59af83-dc97-4dba-9fc0-d81067db58a7
```(which is the mount point for the 500GB partition) I get the error "bash: cd: /media/ee59af83-dc97-4dba-9fc0-d81067db58a7: No such file or directory".  It is this partition that gpodder is looking for.

If you click on a partition in the Places menu or left pane of Nautilus it will get automounted in /media. If there is no partition label the  mountpoint will be the UUID of the partition. "ee59af83-dc97-4dba-9fc0-d81067db58a7" is the UUID of sda3. If you got a "no such file or directory" message when you tried to cd there, then the partition was not mounted. Mounting partitions in /media works perfectly well.

I will post back later with some suggested edits to /etc/fstab. In the meantime, something to think about. If you label a partition (easily done), then when it is automounted, the desktop icon will show the partition label and the mountpoint will be /media/*label*. This is useful. We can do the same using /etc/fstab. Label the partitions and mount them in mountpoints in /media. I will expand on that when I post again to include lines for these three partions: sda3, sdb1, sdc2. There are also swap partitions at sdb2 and sdc5, presumably relics of old installation. There is no point mounting them.

The pendrive. I would suggest simply leaving it unplugged when you don't want it automounted.

Lastly, let's clarify a point about the term "automount". If you plug an external drive in it will be automounted by the system (dbus, I believe) onto a dynamically created mountpoint in /media and a desktop icon will appear. The mountpoint will be deleted when you unmount the drive/partition.  If you click on an internal partition in Places, the same happens. But automounting can also apply to having entries in /etc/fstab where you can designate mountpoints other than in /media if you wish.

I'll be back. :)

---

### Post by coffeecat on 2011-04-21
A quick comment first. The drive that is currently sda was originally sdc. That's not a great problem because we are going to use UUIDs in /etc/fstab, but is slightly confusing when looking at your terminal outputs. The important thing is that you will need to take care with the suggestions I make in Part 3 &#8211; see below.

 Here are some suggestions for /etc/fstab edits. I've divided this into three parts so that you can pick and choose what you want. I've assumed that you want to mount in /media and have partition labels, because that is an elegant way of doing it.

 You probably know this, but for each of the three parts the terminal command for opening a text editor with administrative rights so that you can edit /etc/fstab is:
 
 ```
gksudo gedit /etc/fstab
``` **Part 1 &#8211; System reserved partition.**

 I strongly urge you not to have the System Reserved partition permanently mounted. It simply shouldn't be necessary. In the unlikely event of your needing to access it, it is easily mounted from the Places menu. Having it permanently mounted means that you could accidentally click on the icon and open a file browser window. That's just one step to accidentally modifying or deleting a file and making Windows unbootable. If you want to stop System Reserved being permanently mounted, run the above command, and find these two lines:

 ```
#Entry for /dev/sdc1 :
UUID=72DCA54CDCA50B83   /media/System\040Reserved       ntfs    defaults,nls=utf8,umask=0222,nosuid,nodev       0       0
``` Simply add # to the beginning of the second line so that it looks like this:

 ```
#Entry for /dev/sdc1 :
#UUID=72DCA54CDCA50B83   /media/System\040Reserved       ntfs    defaults,nls=utf8,umask=0222,nosuid,nodev       0       0
``` Save and exit gedit.
 
 **Part 2 &#8211; The other two NTFS partitions.  **

 At the moment those two partitions are being permanently mounted by means of /etc/fstab, which means that they cannot be mounted from the Places menu. Since the Win7 partition is a  working Windows C: partition (the same applies if OldXP is still a usable Windows system), I would strongly urge you not to have them permanently mounted for the same reasons as for the System Reserved partition. If you don't have them permanently mounted, you could always mount them on an as-needed basis from the Places menu. If you want to do this, then open /etc/fstab and find these lines:

 ```
#Entry for /dev/sdc2 :
UUID=2872ADEA72ADBD46   /Win7   ntfs-3g defaults,nosuid,nodev,locale=en_CA.utf8 0       0
#Entry for /dev/sdb1 :
UUID=84A433A0A43393A0   /OldXP  ntfs-3g defaults,nosuid,nodev,locale=en_CA.utf8 0       0
``` Simply add # before the two &#8220;UUID&#8221; lines as before to get this:
 
 ```
#Entry for /dev/sdc2 :
#UUID=2872ADEA72ADBD46   /Win7   ntfs-3g defaults,nosuid,nodev,locale=en_CA.utf8 0       0
#Entry for /dev/sdb1 :
#UUID=84A433A0A43393A0   /OldXP  ntfs-3g defaults,nosuid,nodev,locale=en_CA.utf8 0       0
``` If, however, you would like them mounted in /media so that desktop icons appear, then from a terminal:

 ```
sudo mkdir /media/Win7
sudo mkdir /media/OldXP
``` And then open /etc/fstab and change those two lines to:

 ```
#Entry for /dev/sdc2 :
UUID=2872ADEA72ADBD46   /media/Win7   ntfs-3g defaults,nosuid,nodev,locale=en_CA.utf8 0       0
#Entry for /dev/sdb1 :
UUID=84A433A0A43393A0   /media/OldXP  ntfs-3g defaults,nosuid,nodev,locale=en_CA.utf8 0       0
``` One oddity you'll see is that because the partition label for Win7 is &#8220;MachineName&#8221; and for OldXP is &#8220;Local Disk&#8221; that is what you will see under the desktop icons. If you want to change that, simply relabel the partitions. If you need help with that, post back.

 **Part 3 &#8211; The three ext3 partitions.**
 
These are currently sda3, sdb1 and sdc2. If you change the drive order in the machine, sda could become something else, and so on. With some BIOSs it happens spontaneously, so double-check at this point. The importance of this is that I am going to suggest that you label the three partitions and, not knowing what labels you would prefer, I'm going to use  &#8220;sda3&#8221;, &#8220;sdb1&#8221; and &#8220;sdc2&#8221; for illustration, and also use the same for the mountpoints. Change these to what you prefer, but double-check that sda is still sda, and so on. Substitute your choice for sda3, sdb1 and sdc2 in both the commands below and in the fstab lines.

 First, label the partitions:
 
 ```
sudo e2label /dev/sda3 sda3
sudo e2label /dev/sdb1 sdb1
sudo e2label /dev/sdc2 sdc2
``` Now make mountpoints:
 
 ```
sudo mkdir /media/sda3
sudo mkdir /media/sdb1
sudo mkdir /media/sdc2
``` Now open /etc/fstab and add these new lines:
 
 ```
UUID=ee59af83-dc97-4dba-9fc0-d81067db58a7        /media/sda3        ext3        defaults     0  2
UUID=0c9c64ed-a412-4122-b321-123b2481dc1a        /media/sdb1        ext3        defaults     0  2 
UUID=c559e081-a4e3-4b9e-a677-dadc77d44381        /media/sdc2        ext3        defaults     0  2
``` That will mount them with root privileges so you may encounter permission problems when writing to them. This may be the problem you are already experiencing with gpodder and your ext3 partitions. It is easily solved either by adding more options to &#8220;defaults&#8221; or by chowning and chmodding the partitions. If you explain what is on these partitions and what you want to use them for, I can expand on this, but let's get them permanently mounted and we can address the permissions issue once that's working.

 Once you've made all your modifications, reboot and you should see a number of desktop icons for the various partitions. As said before, if you want to relabel the NTFS partitions post back and we can take it from there, and we can also sort out the permissions issues with the ext3 partitions.

---

### Post by breem42 on 2011-04-22
Hi. Thanks again for your informative responses.  They are very helpful.

I've implemented Part 1 (commenting out the entry for "System Reserved") and Part 2 (opting to mount the NTFS partitions as you described).  For Part 3, I wanted write access to the ext3 partitions.  The settings I chose seem OK, but I'm not sure if they is the best. Here's what I have:```
UUID=ee59af83-dc97-4dba-9fc0-d81067db58a7        /media/sda3        ext3        rw,suid,nodev,noexec     0  2
UUID=0c9c64ed-a412-4122-b321-123b2481dc1a        /media/sdb1        ext3        rw,suid,nodev,noexec     0  2 
UUID=c559e081-a4e3-4b9e-a677-dadc77d44381        /media/sdc2        ext3        ro,suid,nodev,noexec     0  2

```

sda3 is my music & video collection
sdb1 is an old mostly empty ext3 partition I'm not really using yet.
sdc2 us an old Ubuntu install, which I want to leave as is, but may need to copy things from (thus mounted read only).

Labels like sda3 are kind of sucky but acceptable.  I know that they can be re-labeled.  Since I use Firefox & Thunderbird from both OS's I had to adjust internal settings in my Ubuntu installs so that they could find my profiles on the Win7 partition (modifying 'profiles.ini' for each).  Gpodder works properly after I told it where it's archive was on sda3.

---

### Post by coffeecat on 2011-04-22
The alternative to adding mount options to /etc/fstab is to chmod the root of the filesystem. If you mount the filesystem and chmod the mountpoint, you don't in fact change permissions of the mountpoint, but of the root of the filesystem itself. This isn't widely understood. So for really permissive permissions, you could:

```
sudo chmod 777 /media/sda3
sudo chmod 777 /media/sdb1
sudo chmod 777 /media/sdc2
```

If you then unmount the partitions and do a 'ls -l /media' you'll see that the permissions of /media/sda3 and so on haven't changed; the chmod acted on the filesystem itself. Which means that the changed permissions will "stick" if you choose a different mountpoint. Since...

[quote="breem42"]Labels like sda3 are kind of sucky but acceptable. [/quote]

Agreed. :) Which is why I guessed you would want to choose your own.

You can also apply chown to the root of the filesystem in the same way with:

```
sudo chown yourusername: /media/sda3
```

... and so on. That is not a recursive chown - neither is the chmod above - so files and folders already in existence are not affected.

---

### Post by breem42 on 2011-04-22
But... aside from the labels I'm using, my changes ti fstab are OK?

---

### Post by coffeecat on 2011-04-22
Tbh, I'm not sure but if they are working for you then they are OK. I find the simple "defaults" option and then a bit of judicious chowning and chmodding of my ext3/4 data partition to suit my needs.

---

### Post by breem42 on 2011-04-23
Thanks much coffeecat.  I think I'll mess around with it a bit more, but essentially the problem is solved.

---

