---
title: "How do I access my files that are in folders in windows"
date: 2009-05-02
forum: New to Ubuntu
---

### Post by skaught78 on 2009-05-02
Forgive my ignorance. I'm very new to Ubuntu. I'm running v 8.10 I want to know how to access my files that are stored in windows folders. Any help would be greatly appreciated.

---

### Post by cariboo on 2009-05-02
Go to Places-->Home Folder and look in the left pane. IF your Windows hard drive doesn't have a proper label, that will stand out, look for a drive with a label of the aprroximate size of you Windows partition See the screenshot. I don't have any Windows partitions on this computer, but if you look in the left pane you will see 6.0GB Media, that is the / partition of my Jaunty installation.

---

### Post by dabomb1022 on 2009-05-02
> **cariboo907 said:**
> Go to Places-->Home Folder and look in the left pane. IF your Windows hard drive doesn't have a proper label, that will stand out, look for a drive with a label of the aprroximate size of you Windows partition See the screenshot. I don't have any Windows partitions on this computer, but if you look in the left pane you will see 6.0GB Media, that is the / partition of my Jaunty installation.
But don't you need ntfs read/write?

---

### Post by skaught78 on 2009-05-02
There is nothing there. All it has is my cd-rom drive...

---

### Post by powel212 on 2009-05-02
The quick answer is yes, you need to enable NTFS support. 

aplications/add-remove - search NTFS - will return NTFS configuration tool. Select it hit apply changes. Launch NTFS and enable all. Done.

The longer more detailed answer;

```
This is the easiest and best way I know of. Easy GUI method. No scripts or messing around with text files.

Go to "Applications-Add/Remove...

Change the box at top that says "show" from "Conical-maintained-applications" to "All available applications"

Than type into the search box "NTFS"

in a second or 2 you will see a program called NTFS configuration tool.

Put a check in the box beside it and then apply changes.

Close Add/remove

Then go to "Applications-System_Tools-NTFS Configuration tool"

if it is not there try

"System-Administration-NTFS Configuration tool"

After launching the tool just check the boxes next to; enable read and write to internal and external drives.

the next time you boot all your drives will appear on the desktop.

```


I hope that helps.

Powel

---

### Post by skaught78 on 2009-05-02
No luck there. The option to "enable read and write to internal and external drives isnt even there. The following is my desktop with the ntfs config tool open, and my home folder in the background.

[IMG]http://i232.photobucket.com/albums/ee41/skaught78/desktop2.gif[/IMG]

---

### Post by egalvan on 2009-05-02
Try this:

go to 

Places -> Computer -> File System

check the following folders

/media

/mnt


your NTFS drive(s) may be there.

also, post the output of

```
sudo fdisk -l
```

---

### Post by RyanVanDiemen on 2009-05-02
i'm not sure but i don't think ubuntu mounts ntfs partitions unless you tell the installer to.the easiest way is to use gparted (it should be called partition editor in administration menu).all you need to do is edit windows partition,mark it as ntfs and tell linux the path where it should be mounted.this will also be the path where you will find your win folders.you might need to reboot after the changes.ntfs write support is in ubuntu turned on by default.

---

### Post by SunnyRabbiera on 2009-05-02
> **RyanVanDiemen said:**
> i'm not sure but i don't think ubuntu mounts ntfs partitions unless you tell the installer to.the easiest way is to use gparted (it should be called partition editor in administration menu).all you need to do is edit windows partition,mark it as ntfs and tell linux the path where it should be mounted.this will also be the path where you will find your win folders.you might need to reboot after the changes.ntfs write support is in ubuntu turned on by default.

No it should pick up, this is odd as usually windows drives are picked up in no time.]
to the op, do you still have a windows boot option when you load ubuntu?

---

### Post by skaught78 on 2009-05-02
> **egalvan said:**
> Try this:

go to 

Places -> Computer -> File System

check the following folders

/media

/mnt


your NTFS drive(s) may be there.

also, post the output of

```
sudo fdisk -l
```

Nothing in either of those folders  

sudo fdisk -l:
owner@ubuntu:~$ sudo fdisk -l
[sudo] password for owner: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xedaaedaa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *         894       19456   149107297+   7  HPFS/NTFS
/dev/sda2               1         893     7172991    b  W95 FAT32

Partition table entries are not in disk order
owner@ubuntu:~$ 





> **SunnyRabbiera said:**
> No it should pick up, this is odd as usually windows drives are picked up in no time.]
to the op, do you still have a windows boot option when you load ubuntu?

Yes. I can choose to either boot into windows or boot into ubuntu

---

### Post by gandaran on 2009-05-02
post your /etc/fstab

---

### Post by skaught78 on 2009-05-02
owner@ubuntu:~$ /etc/fstab
bash: /etc/fstab: Permission denied
owner@ubuntu:~$

---

### Post by gandaran on 2009-05-02
> **skaught78 said:**
> owner@ubuntu:~$ /etc/fstab
bash: /etc/fstab: Permission denied
owner@ubuntu:~$
no, go to this file open it and post the output

---

### Post by llemm on 2009-05-02
> **skaught78 said:**
> owner@ubuntu:~$ /etc/fstab
bash: /etc/fstab: Permission denied
owner@ubuntu:~$

do this skaught78

more /etc/fstab

---

### Post by skaught78 on 2009-05-02
> **gandaran said:**
> no, go to this file open it and post the output

Umm.... Where do I find it?

---

### Post by gandaran on 2009-05-02
> **skaught78 said:**
> Umm.... Where do I find it?
in the file system » /etc/fstab!
okay type this command in terminal instead
```
gedit /etc/fstab
```
 and also the output of
```
sudo blkid
```

---

### Post by skaught78 on 2009-05-02
> **gandaran said:**
> in the file system » /etc/fstab!
okay type this command in terminal instead
```
gedit /etc/fstab
``` and also the output of

proc /proc proc defaults 0 0
/dev/sda1 /host ntfs-3g defaults,nosuid,nodev,locale=en_US.UTF-8 0 0
/dev/sda2 /media/RECOVERY vfat defaults,utf8,umask=0 0 2
/dev/loop0 /media/loop0 ext3 defaults 0 2
/host/ubuntu/disks/root.disk / ext3 loop,errors=remount-ro 0 1
/host/ubuntu/disks/boot /boot none bind 0 0
/host/ubuntu/disks/swap.disk none swap loop,sw 0 0



> ```
sudo blkid
```
[/QUOTE]
owner@ubuntu:~$ sudo blkid
[sudo] password for owner: 
/dev/sda1: UUID="2454B94254B9178E" TYPE="ntfs" 
/dev/sda2: LABEL="RECOVERY" UUID="6A5F-1690" TYPE="vfat" 
/dev/loop0: UUID="12b382a0-4b2b-4fb8-993d-ea9f6706aa83" TYPE="ext3" 
owner@ubuntu:~$ 




I have to take off for now and go to work. I'll be back on probably tomorrow. I really appreciate everyones help!:guitar:

---

### Post by egalvan on 2009-05-02
> **skaught78 said:**
> 
/dev/sda1 /host **ntfs-3g** defaults,nosuid,nodev,locale=en_US.UTF-8 0 0
/dev/sda2 /**media/RECOVERY vfat** defaults,utf8,umask=0 0 2
/dev/loop0 /media/loop0 ext3 defaults 0 2
/host/ubuntu/disks/root.disk / ext3 loop,errors=remount-ro 0 1
/host/ubuntu/disks/boot /boot none bind 0 0
/host/ubuntu/disks/swap.disk none swap loop,sw 0 0


  sudo blkid
 
/dev/sda1: UUID="2454B94254B9178E" **TYPE="ntfs" **
/dev/sda2: LABEL="RECOVERY" UUID="6A5F-1690" **TYPE="vfat"** 
/dev/loop0: UUID="12b382a0-4b2b-4fb8-993d-ea9f6706aa83" TYPE="ext3" 


could this be a wubi install?
I don't see a Linux partition anywhere except the loopback...

---

### Post by gandaran on 2009-05-02
skaught78 
can you provide some details on how you installed ubuntu? wubi installer (inside windows) or installed on some flash drive?

---

### Post by skaught78 on 2009-05-03
Got some time to check in while at work.
 
I tried to install ubuntu by just putting the install disk in the cd drive and restarting, but for some reason it wouldn't work. Computer just froze up! So I went into windows and accessed the cd roms drive from explorer and installed it that way.

---

### Post by gandaran on 2009-05-03
> **skaught78 said:**
> Got some time to check in while at work.
 
I tried to install ubuntu by just putting the install disk in the cd drive and restarting, but for some reason it wouldn't work. Computer just froze up! So I went into windows and accessed the cd roms drive from explorer and installed it that way.
sorry I cont help you here, I have no experience of doing ubuntu wubi install, maybe you are not supposed to see windows partitions if ubuntu is installed inside windows, I don't know, ask that to someone that is running ubuntu the same way.

---

