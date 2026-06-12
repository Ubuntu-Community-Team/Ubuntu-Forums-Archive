---
title: "[SOLVED] Drive could not mount..."
date: 2008-12-07
forum: New to Ubuntu
---

### Post by boboxjordan on 2008-12-07
Hi there guys,
absolute beginner here, so please do not be too harsh. I managed to install Ubuntu 8.04. Still, I can't mount my other partitions as well as another HD that connects with an USB. I have XP on C Drive. Here is what I get when using **sudo fdisk -l**:


Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x82358235

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9729    78148161    7  HPFS/NTFS
/dev/sda2            9730        9791      498015   82  Linux swap / Solaris
/dev/sda3            9792       15870    48829567+  83  Linux
/dev/sda4           15871       19457    28812577+  83  Linux

Disk /dev/sdb: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe93a112c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       48641   390708801    7  HPFS/NTFS

Please help.
Thanx

---

### Post by drs305 on 2008-12-07
If you post the results of the following we can make additions to your fstab so all the devices get mounted. (If you run ntfsconfig below, post the fstab results *after* you do this.)

If you have specific names you want the mountpoint to be (for instance, myfiles, mymusic, data, etc) please let us know that also.

```

sudo blkid
cat /etc/fstab
mount | grep "/dev/s"

```

Note: You should be able to get the NTFS partitions to mount with this:
```

sudo apt-get install ntfsprogs ntfs-config

```

Then run System Tools, NTFS Configuration Tools. It will give your NTFS partitions read/write capability and put the appropriate entry into fstab after you have specified a mountpoint.

---

### Post by kansasnoob on 2008-12-07
First of all, is the dual boot working? I mean are you able to boot either Ubuntu or Windows from the bootloader?

If so I suspect that you need only add either ntfs-config or ntfsprogs to be able to read and write your ntfs partitions.

I use ntfsprogs, but I must warn you to be cautious! You will be able to mount and alter even windows system files so you could break things if you goofed. I've never had a problem, but it's possible to edit files that shouldn't be changed.

Both ntfs-config and ntfsprogs are in synaptic.

RE: the external drive, I like to install pmount which is also in synaptic. NOTE: always be certain to unmount the drive before unplugging!

---

### Post by boboxjordan on 2008-12-07
> **drs305 said:**
> If you post the results of the following we can make additions to your fstab so all the devices get mounted. 

If you have specific names you want the mountpoint to be (for instance, myfiles, mymusic, data, etc) please let us know that also.

```

sudo blkid
cat /etc/fstab

```


Thanx a lot drs305. Hereunder is what I get:

/dev/sda1: UUID="CA406282406274DB" TYPE="ntfs" 
/dev/sda2: TYPE="swap" UUID="5851d2a4-760a-4498-85db-ac1ae1033460" 
/dev/sda3: UUID="abe74682-89d9-415f-844d-fdacb8a188e6" TYPE="ext3" 
/dev/sda4: UUID="e94fe5cb-71c8-4ba8-851c-bf46c4af0e79" TYPE="ext3"

and

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=e94fe5cb-71c8-4ba8-851c-bf46c4af0e79 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=abe74682-89d9-415f-844d-fdacb8a188e6 /boot           ext3    relatime        0       2
# /dev/sda1
UUID=CA406282406274DB /windows        ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda2
UUID=5851d2a4-760a-4498-85db-ac1ae1033460 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0


and 


/dev/sda4 on / type ext3 (rw,relatime,errors=remount-ro)
devshm on /dev/shm type tmpfs (rw)
/dev/sda3 on /boot type ext3 (rw,relatime)
/dev/sda1 on /windows type fuseblk (rw,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096)
/dev/sda1 on /media/C_drive type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)

---

### Post by boboxjordan on 2008-12-07
> **kansasnoob said:**
> First of all, is the dual boot working? I mean are you able to boot either Ubuntu or Windows from the bootloader?

If so I suspect that you need only add either ntfs-config or ntfsprogs to be able to read and write your ntfs partitions.

I use ntfsprogs, but I must warn you to be cautious! You will be able to mount and alter even windows system files so you could break things if you goofed. I've never had a problem, but it's possible to edit files that shouldn't be changed.

Both ntfs-config and ntfsprogs are in synaptic.

RE: the external drive, I like to install pmount which is also in synaptic. NOTE: always be certain to unmount the drive before unplugging!

yes, I can boot both XP and Ubuntu. Still I have two choices more I think. What I get on the boot screen is:


Ubuntu - kernel 2.6.24-22 - generic
Ubuntu - kernel 2.6.24-22 - generic (recovery mode)
Ubuntu - kernel 2.6.24-19 - generic
Ubuntu - kernel 2.6.24-19 - generic (recovery mode)
Windows XP

I guess I should remove the Ubuntu xxxx . 19 or what?

Thanx for your help!

---

### Post by drs305 on 2008-12-07
[COLOR="Maroon"]Actually, after seeing what you added to your post regarding mount, I have not made any changes to your fstab as yet, based on the fact that you have a separate /boot partition. 

You are getting ubuntu to mount (sda2,3,4). Can you see your /windows partition?
If so, it appears you are only having problems getting sdb1 to mount, in which case you can use the NTFS Configuration Tool to mount it.[/COLOR]

For the kernel displays, you can tweak what you see in menu.lst with StartUp-Manager, a gui-based app that will allow you to change a lot of settings, including the number of kernels you see. 

For a complete explanation and howto, see:
[StartUp-Manager HowTo]("http://ubuntuforums.org/showthread.php?t=818177")
The short version: Install StartUpmanager, Start it (System, Admin, StartUp-Manager). Go to Advanced and select number of kernels to display if you don't want -19 to show.

---

### Post by boboxjordan on 2008-12-07
> **drs305 said:**
> Based on what we have so far, here is a revised fstab.


Make the mountpoints and make yourself the owner. Change the names of mountpoint1 and mountpoint2 to whatever you wish:
[CODE]
sudo mkdir /media/mountpoint1

it gives me the following error after **sudo mkdir /media/mountpoint1**

mkdir: cannot create directory `/media/mountpoint1': File exists

---

### Post by drs305 on 2008-12-07
> **boboxjordan said:**
> it gives me the following error after **sudo mkdir /media/mountpoint1**

mkdir: cannot create directory `/media/mountpoint1': File exists

Either you ran the same command twice without changing it to mountpoint**2** or out of the entire universe I happened to pick a name that already existed on your computer!

No problem, just pick another name. Actually, I would expect your to use a more descriptive name that *mountpoint1*, just change the reference to whatever you want and make the change in each command that references it.

[COLOR="Red"]See edited remarks in previous post.[/COLOR]

---

### Post by boboxjordan on 2008-12-07
[COLOR="Red"]See edited remarks in previous post.[/COLOR][/QUOTE]
actually the only thing I can see under Ubuntu is the Filesystem (around 50 GB) where I suppose is installed the Linux. The 80 GB partition where the Windows is is not visible. The 400 GB removable HD can be seen when pluged in but could not be mounted.

Where can I find the NTFS Configuration Tool? I tried the Synaptic Package Manager but nothing is there
I downloaded one from here [http://flomertens.free.fr/ntfs-config/](http://flomertens.free.fr/ntfs-config/) download.html

it seems ok. I enable write support for external/internal devices. I "forced" the USB connected HDrive and it is OK now!, but still the C where the XP is is not good...

OK now - I found them - thanx a million dude!!!

---

### Post by drs305 on 2008-12-07
The ntfs configuration tools is listed in synaptic under 'ntfs-config' and is in the *universe* repository, so make sure you have that enabled (Settings, Repositories, Ubuntu Software).

The windows partition is being mounted under "/windows" which may be why you aren't seeing it. Normally partitions are mounted in /media or /mnt and you will be able to see them on your desktop (if you have viewing volumes enabled). So you can make a new mountpoint (/media/windows) and edit your fstab to get it mounted there.

```

sudo mkdir /media/windows
sudo chown -R *yourusername:* /media/windows
chmod -R 750 /media/windows

```

Edit fstab, changing the windows mount point and ownership:
```

# /dev/sda1
UUID=CA406282406274DB /[COLOR="Red"]media/[/COLOR]windows ntfs defaults,[COLOR="Red"]uid=1000[/COLOR],umask=0[COLOR="Red"]2[/COLOR]7,gid=46 0 1

```

---

### Post by boboxjordan on 2008-12-07
> **drs305 said:**
> [COLOR="Red"]See edited remarks in previous post.[/COLOR]

Thanx again drs305. As posted above I could find the C drive under Ubuntu and also the removable HD. First, here is what I see under Ubuntu:

[IMG]http://img184.imageshack.us/img184/1718/screenshotfj3.jpg[/IMG]

The first drive BOBO is the removable one. Works fine.
The Second and the Third (bobox1 and bobox2) I created according to the instructions given - sudo mkdir /media/mountpoint1 
C_drive and D_drive don't have anything in them. neither has mounting point 1. How can I erase all those not needed.

When I go under Windows in the Partitioning program I can see only C - drive NTFS. The other 3 are the swap + 2 Linux type. I cannot access them under Windows. How can I access all from both programs?

---

### Post by drs305 on 2008-12-07
> **boboxjordan said:**
> How can I erase all those not needed.
Check to make sure there is nothing in them, then just delete them. If they aren't owned by you, open nautilus with "gksudo nautilus" and then delete them. You might want to check once more to ensure they aren't mentioned in your fstab file.

> 
When I go under Windows in the Partitioning program I can see only C - drive NTFS. The other 3 are the swap + 2 Linux type. I cannot access them under Windows. How can I access all from both programs?
There is an app called ext2fs.sys for windows that will allow you to view linux files. Install it through the Windows add/remove program. Here is a link:
[http://www.fs-driver.org/]("http://www.fs-driver.org/")

---

### Post by boboxjordan on 2008-12-07
> **drs305 said:**
> Check to make sure there is nothing in them, then just delete them. If they aren't owned by you, open nautilus with "gksudo nautilus" and then delete them. You might want to check once more to ensure they aren't mentioned in your fstab file.


There is an app called ext2fs.sys for windows that will allow you to view linux files. Install it through the Windows add/remove program. Here is a link:
[http://www.fs-driver.org/]("http://www.fs-driver.org/")

Thank you so so much drs305. being my first day with Linux I still try to find my way round. I just want to understand some basic rules. hereunder are two shots - one of them made under XP and the other under Ubuntu. Please throw some light on the following and corect me if I am wrong please:

In the XP shot I have C drive - that is /windows under Ubuntu;
In the XP shot I have D Swap drive 512 MB- I'm afraid I formated it when I was under Windows - how can I make it again swap drive?
In the XP shot I have G Bobo drive - that is the removable that could be found in /media under Ubuntu;
In the XP shot I have H 29 GB drive - that is actually where Ubuntu is installed, right? and all the folders can be seen under / in Ubuntu?
In the XP shot I have I 50 GB drive - what are these and where can I find them under Ubuntu?

I really owe you one!


[IMG]http://img141.imageshack.us/img141/9292/111wq1.jpg[/IMG]
[IMG]http://img141.imageshack.us/img141/3015/screenshotxs1.jpg[/IMG]

---

### Post by drs305 on 2008-12-07
I've sent you a PM, but to answer a few questions:

You can format the D partition with an app called gparted. If it's not installed, install it with:
```
sudo apt-get install gparted
```

Then start it with the command 'sudo gparted' or via menu (System, Admin, Partition Editor). Highlight the D partition, then in the top menu select Partition, Unmount. Then you can format it as linux-swap. 

If you reformat it, the UUID will change and you will have to put the new UUID in fstab. To get the UUID, run the command "sudo blkid".

The H drive does appear to be your ubuntu install.

Removable drives are normally found in /media, so click on /media and look at the subfolders. If the 50GB drive is already mounted, you can find where it is by running the "mount" command. Also note there is an exclamation sign on your /media folder, which means you should open it to see what is going on inside that folder.

---

