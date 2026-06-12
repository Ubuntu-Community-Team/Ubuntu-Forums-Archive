---
title: "help with transfering files from one drive to another via terminal"
date: 2010-02-08
forum: New to Ubuntu
---

### Post by hortstu on 2010-02-08
I booted a desktop w/ a hardy heron live CD.  The desktops primary HD runs only win XP.  Within XP I have files that I need to transfer to an external drive that is connected via a USB.

I can access both drive via PLACES.  I tried dragging and dropping the files but I received an error message along the lines of I don't have permission to install those files on the drive.

The USB drive is also running a hardy system I just installed. This drive is going to be installed in a friends computer as the primary drive but I need to move some pictures that I saved from a windows mishap.

Can anyone tell me how to do this via the terminal?

---

### Post by patchwork on 2010-02-08
Two things I would try:

1. If you prefer to drag-and-drop try ```
gksu nautilus
```
This will give you root permissions to the files and drives

2.  If that doesn't work, or you prefer the command line

sudo cp -r /path/to/directory /path/to/destination

---

### Post by hortstu on 2010-02-08
Thanks...

Just because I'm really trying to get the hang of this, understand the hows and whys, and remember what I'm doing... can you explain to me exactly what is happening when I enter "gksu nautilus" into the terminal?

---

### Post by eriktheblu on 2010-02-08
gksu is the graphical equivalent of sudo; it allows you to run commands as root. Nautilus is your graphical file manager (when you open a folder, that's Nautilus). So gksu nautilus opens a folder with root permissions.

---

### Post by nhasian on 2010-02-08
something is wrong here, you shouldn't need to use sudo or gksu to copy files to an external hard disk.  

lets see what file system format that external hard disk is.  please give us the output of the following terminal command with your external hard disk plugged in:

```
sudo fdisk -l
```

some of the new external western digital hard disks come with smartware tools that may interfere with its operation in linux.  you can remove it by using the method outlined in the followin link:

[http://www.wdc.com/wdproducts/updates/?family=wdsmartwareutilities](http://www.wdc.com/wdproducts/updates/?family=wdsmartwareutilities)

---

### Post by falconindy on 2010-02-08
patchwork would have you believe that this is a simple issue of 'apply more force' and all is well. 'gksu nautilus' gives you a file manager with root permissions. This is potentially dangerous and moreover, unnecessary. A better solution is to properly mount the external drive so that you can write to it as a user.

I'm going to assume the external drive is formatted as NTFS, and thus, doesn't respect linux file permissions and ownership. Try mounting manually:
```
mount -t ntfs-3g /dev/sdxy /media/label -o rw,uid=1000,gid=1000,fmask=133,dmask=022
```
Replace /dev/sdxy and /media/label appropriately with the device to be mounted and the place to mount it and all should be well. Since you seem to be interested in learning, I'll explain the options:

-t ntfs-3g = use the ntfs-3g driver to mount the volume (the kernelspace ntfs driver blows)
rw = read/write
uid/gid = set owner and group by ID (1000 is the first user created on the system, i.e. you)
fmask/dmask = subtract these values from 777 to ascertain file and directory permissions. in this case, we end up with 644 and 755 for permissions, respectively

---

### Post by patchwork on 2010-02-08
Could be wrong, but the permissions issue is probably due to the use of the live cd to access the host XP drive.

Didn't claim to know all the answers, just the first things I would try...

---

### Post by hortstu on 2010-02-08
The 80gb is the desktop internal that runs exclusively xp
The 120GB is the drive connected via USB that has hardy installed and will eventually be the primary internal drive on my friends desktop.


```
Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9dc96e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2   *           7        9268    74397015    7  HPFS/NTFS
/dev/sda3            9269        9725     3670852+  db  CP/M / CTOS / ...

Disk /dev/sdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xffa8ffa8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       13995   112414806   83  Linux
/dev/sdc2           13996       14593     4803435    5  Extended
/dev/sdc5           13996       14593     4803403+  82  Linux swap / Solaris
```


> **nhasian said:**
> something is wrong here, you shouldn't need to use sudo or gksu to copy files to an external hard disk.  

lets see what file system format that external hard disk is.  please give us the output of the following terminal command with your external hard disk plugged in:

```
sudo fdisk -l
```

some of the new external western digital hard disks come with smartware tools that may interfere with its operation in linux.  you can remove it by using the method outlined in the followin link:

[http://www.wdc.com/wdproducts/updates/?family=wdsmartwareutilities](http://www.wdc.com/wdproducts/updates/?family=wdsmartwareutilities)

There is some background story to this USB connected drive.  It had hardy installed via another laptop running hardy. Then I had boot problems and grub problems that presence helped me solve.

For some reason the hardy external drive won't boot up on this xp computer.  My main concern is that it needs to boot as the primary (only) drive on my friends computer.  For now I need to get all the files I saved for him onto this drive... then I'll solve the boot problems... with the forums help I hope.

---

### Post by hortstu on 2010-02-08
[QUOTE=FI]patchwork would have you believe that this is a simple issue of 'apply more force' and all is well. 'gksu nautilus' gives you a file manager with root permissions. This is potentially dangerous and moreover, unnecessary. A better solution is to properly mount the external drive so that you can write to it as a user.[/QUOTE]

Thanks PW I appreciate your attempt to help but it didn't work out... don't let that stop you in the future.  I'm into learning by trial and error.  My problem is I don't know most of this terminology so most of the time I even get lost by the explanations.

[QUOTE=FI]I'm going to assume the external drive is formatted as NTFS, and thus, doesn't respect linux file permissions and ownership. Try mounting manually:[/QUOTE]

I'm not sure/ don't remember but this drive originally had a wrecked WIN XP on it.  I saved the files I could and then used a disk tool CD to wipe it clean.  Then I used the hardy live CD to install Hardy on the drive via USB through my laptop.  I used the guided install, probably caused a lot of these problems, so whatever type of partition the CD suggested I used.

[QUOTE=FI]Code:

mount -t ntfs-3g /dev/sdxy /media/label -o rw,uid=1000,gid=1000,fmask=133,dmask=022

Replace /dev/sdxy and /media/label appropriately with the device to be mounted and the place to mount it and all should be well.[/QUOTE]

OK  Thank you, let me apologize up front and let you know you might as well treat me like a 3 year old when you explain this stuff... So you're suggesting I properly mount the external drive.  In order to do that I use the results I got from fdisk -l 

/dev/sdxy = /dev/sdc1
/media/label = I have no idea

Is that right.

[QUOTE=FI]
 Since you seem to be interested in learning, I'll explain the options:[/QUOTE]

I really appreciate it... can't express that enough.

[QUOTE=FI]-t ntfs-3g = use the ntfs-3g driver to mount the volume (the kernelspace ntfs driver blows)
rw = read/write
uid/gid = set owner and group by ID (1000 is the first user created on the system, i.e. you)
fmask/dmask = subtract these values from 777 to ascertain file and directory permissions. in this case, we end up with 644 and 755 for permissions, respectively[/QUOTE]

Some of that went over my head but thanks

---

### Post by falconindy on 2010-02-08
Hmmmmmm, if it was running Hardy then it's certainly **not** NTFS. Ext3 is a more likely candidate. You can safely ignore everything I mentioned about mounting manually.

How about this... with the drive automounted, post the output of the 'mount' command.

---

### Post by hortstu on 2010-02-08
sure thing

```
ubuntu@ubuntu:~$ mount
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.24-23-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.24-23-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sdb1 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)
/dev/sda2 on /media/disk-1 type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
/dev/sdc1 on /media/disk-2 type ext3 (rw,nosuid,nodev,uhelper=hal)
ubuntu@ubuntu:~$ 

```

---

### Post by falconindy on 2010-02-08
Ok, so presumably there's a user on that Hardy system (I'll call the user 'foo'). Try writing your files to /media/disk-2/home/foo/. If that doesn't work, let's get the output of: 
```
ls -ln /media/disk-2/home/foo
```

---

### Post by hortstu on 2010-02-08
Is this what you're looking for?

```
total 28
drwxr-xr-x 2 1000 1000 4096 2010-02-03 18:27 Desktop
drwxr-xr-x 2 1000 1000 4096 2010-02-03 18:27 Documents
lrwxrwxrwx 1 1000 1000   26 2010-02-03 18:20 Examples -> /usr/share/example-content
drwxr-xr-x 2 1000 1000 4096 2010-02-03 18:27 Music
drwxr-xr-x 2 1000 1000 4096 2010-02-03 18:27 Pictures
drwxr-xr-x 2 1000 1000 4096 2010-02-03 18:27 Public
drwxr-xr-x 2 1000 1000 4096 2010-02-03 18:27 Templates
drwxr-xr-x 2 1000 1000 4096 2010-02-03 18:27 Videos
ubuntu@ubuntu:~$ 

```

---

### Post by falconindy on 2010-02-08
Ayup. You should have permission to do whatever you please to that directory and the contained subdirectories.

---

### Post by theozzlives on 2010-02-08
First of all, it's not good to install Ubuntu on a computer other than the one it's meant to run on. However, if I were to do it this way, I would disconnect the internal drive and install as an OEM. I think it's F4 that allows you to do that at the original setup screen.

---

### Post by falconindy on 2010-02-08
> **theozzlives said:**
> First of all, it's not good to install Ubuntu on a computer other than the one it's meant to run on. However, if I were to do it this way, I would disconnect the internal drive and install as an OEM. I think it's F4 that allows you to do that at the original setup screen.
Actually, thanks to the flexibility of the Linux kernel, I could do a base install of a Linux distro (no X) on a hard drive attached to my computer, plug it in to almost any other computer, and it'll happily boot with little to no changes. This is, however, unrelated to the OP, who states:
[quote="OP"]This drive is going to be installed in a friends computer as the primary drive but **I need to move some pictures that I saved from a windows mishap**.[/quote]

---

### Post by hortstu on 2010-02-08
I think the files are transferring now.  I still got the same error message but I didn't hit cancel this time.  Whatever is happening it's slowed everything down to the point that the computer is useless for anything else.  I tried to take a screen shot, don't know if that screwed it up... I assume it has something to do with the fact that everything's running through the live CD.

Ozzlives is correct.  I did install HH through the USB. This did raise some issues but another forum member helped me overcome most of those so far.

---

