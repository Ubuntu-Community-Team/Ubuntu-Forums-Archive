---
title: "Having trouble permanently mounting other hdd"
date: 2009-03-17
forum: New to Ubuntu
---

### Post by johns6md on 2009-03-17
I'm new to Ubuntu and I am loving it but the one problem I have and can't really find a fix is that I have two internal hard drives one that is formated for Ubuntu and the other is for my M$ windows.  Every time I reboot I have to remount the one that is formatted for M$(ntfs).  I know I can't write to that hdd from Ubuntu but I need to read from it because that is where all my music is.  Basically I just need to know how to permanently have it mount so if I reboot I don't have to remount. I mean it isn't that big of a problem to remount every time but it would be nice to not do that all time.

I have looked around and found this thread: [http://ubuntuforums.org/showthread.php?t=836061&highlight=hard+drive+permanent+mount](http://ubuntuforums.org/showthread.php?t=836061&highlight=hard+drive+permanent+mount)

I followed it and it didn't seem to help.

P.s. Thanx in advance

---

### Post by iaculallad on 2009-03-17
To complete the information needed, try posting whatever displays when you issue the command below:

> sudo fdisk -l

---

### Post by logos34 on 2009-03-17
try this:

[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

then add the uuid if you want, as in the link you posted

---

### Post by johns6md on 2009-03-17
@iaculallad:  Here is the info that comes after:  sudo fdisk -l 

Disk /dev/sda: 120.0 GB, 120000000000 bytes
255 heads, 63 sectors/track, 14589 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9dc96e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14588   117178078+   7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6fe56fe5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9539    76621986   83  Linux
/dev/sdb2            9540        9726     1502077+   5  Extended
/dev/sdb5            9540        9726     1502046   82  Linux swap / Solaris

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5d7aba32


The one I'm trying to have permanently mounted is: /dev/sda1
the other two are the internal hdd for ubuntu and the other is an external usb hdd. And the external hdd is mounted every time I reboot.

---

### Post by johns6md on 2009-03-17
@logos34: I followed your link and I loaded the ntfs-config using:

sudo apt-get install ntfs-config

But then I get lost and have no idea what to do, I am still new to Linux I have only been using for a few of weeks.  I am hoping to make a full time switch and only use Linux but it sure is a new learning experience.

---

### Post by konqueror7 on 2009-03-17
assuming you already installed ntfs-3g from synaptic, type in the terminal,

make a backup first,
```
sudo cp /etc/fstab /etc/fstab.bak
```

then,
```
sudo gedit /etc/fstab
```

add the line in the end,
```
/dev/sda1 **/media/MyMountFolder** ntfs-3g defaults,locale=en_US.UTF-8 0 0
```

(the text with the Bold face is your mount folder, you can create it via issuing this command in the terminal "sudo mkdir /media/MyFolder" or any a separate directory if you want)

now, save it and reboot... hope it helps...

---

### Post by konqueror7 on 2009-03-17
> **johns6md said:**
> @logos34: I followed your link and I loaded the ntfs-config using:

sudo apt-get install ntfs-config

But then I get lost and have no idea what to do, I am still new to Linux I have only been using for a few of weeks.  I am hoping to make a full time switch and only use Linux but it sure is a new learning experience.

ah, open the terminal (Applications > Accessories > Terminal), and type in,
```
sudo apt-get install ntfs-config
```

this is the 'visual' version of my post above, you can open the app in ***Applications > System Utilies > NTFS Configuration***...

---

### Post by iaculallad on 2009-03-17
Let's do the automount manually. First thing to do is create a mount point for the partition:

```
sudo mkdir /media/Storage
```

Next thing to do is edit /etc/fstab file:

```
gksudo gedit /etc/fstab
```

and try adding the lines of texts below on the last part of the file.

```
/dev/sda1 /media/Storage     ntfs    defaults,umask=007,gid=46 0    
```

*Copy and Paste it*

Save and Close the file. 

Commands below will let you own the mount point.

```
sudo chown -R your_name:your_name /media/Storage
sudo chmod -R 755 /media/Storage

```

Mount it:

```
sudo mount -a
```

---

### Post by johns6md on 2009-03-17
CASE CLOSED!!!

I would like to thank all you that help me to solve this problem.  And all of you really make using Linux(Ubuntu) great.  All I did is ask a question here in the forums and in less than an hour I had the problem fixed. Again thank you.

---

