---
title: "How to backup data of a crashed windows from Ubuntu 7.10 Live CD"
date: 2010-02-24
forum: New to Ubuntu
---

### Post by sohailhusain on 2010-02-24
Ok first of all I am using this OS for the 1st time....and my windows is DEAD so i want to backup my data as i have to reinstall windows....i have UBUNTU 7.10 live cd...so i booted it up and then tried to open the drive which i want to backup...the windows drive is actually c: but in Ubuntu its /dev/sda1 .....when i want to open that drive of mine i get this error

> ntfs_attr_pread: ntfs_pread failed: Input/Output error Failed to read NTFS $Bitmap: Input/output error Unmounting /dev/sda1 ()well i have searched google a bit and no one's getting this type of error...so i thought the best thing was to ask in the main Ubuntu forum....so plz plz plz help me!!

---

### Post by Lord Stig on 2010-02-24
I think that error could occur if Windows has marked the drive as in use when it crashed. If so it has locked it temporarily.

You could try [this]("http://ubuntuforums.org/showthread.php?t=1107440&highlight=mount+partition+in+use+by+windows")

---

### Post by sohailhusain on 2010-02-24
> **Ptero-4 said:**
> type into the terminal:
```
sudo mount -t ntfs -o force /dev/*windows partition* /media/windows
```You'll need to put the partition number instead of *windows partition*, and you'll need to create the "windows" folder inside /media before trying to mount the partition.
You can use gparted to see where is your windows partition.

i tried this....i get the same error as i usually get..

EDIT
I can't download or upgrade cuz i think they have dropped support for Ubuntu 7.10 as all the servers jst give the error "404 not found"...so i cant use what McTricks used.

---

### Post by amsterdamharu on 2010-02-24
You tried to mount with -force as the example? And did you just get the same error or a different one?

You might try using 7.10 to download tinycore linux, mount the iso and copy to usb (smaller the better formatted as fat16). 
Then use syslinux to make the usb bootable. 
Copy isolinux.conf in the root of the usb and rename it syslinux.conf.

You can now boot off the usb and try to mount the ntfs using the following commands:

```
sudo su
mkdir /mnt/windows
mount -t ntfs -o force /dev/sda1 partition /media/windows
```If that doesn't work try to install testdisk from tinycore, you can install a web browser named seamonkey and a file browser named xfs (I think). The software installer lets you install stuff from the Internet but it'll be gone on next reboot. Try alt tab to get a menu.

---

### Post by sohailhusain on 2010-02-24
> **amsterdamharu said:**
> You tried to mount with -force as the example? And did you just get the same error or a different one?

no i just used force....and yes i get the same error that i posted in the first post of this thread

> **amsterdamharu said:**
> You might try using 7.10 to download tinycore linux, mount the iso and copy to usb (smaller the better formatted as fat16). 
Then use syslinux to make the usb bootable. 
Copy isolinux.conf in the root of the usb and rename it syslinux.conf.

You can now boot off the usb and try to mount the ntfs using the following commands:

```
sudo su
mkdir /mnt/windows
mount -t ntfs -o force /dev/sda1 partition /media/windows
```If that doesn't work try to install testdisk from tinycore, you can install a web browser named seamonkey and a file browser named xfs (I think). The software installer lets you install stuff from the Internet but it'll be gone on next reboot. Try alt tab to get a menu.

I'll try and then tell if it worked or not....

---

### Post by sohailhusain on 2010-02-24
by the way i don't have a USB just now so i'll try what u told me tomorrow......

And yes i thought the files /etc/fstab and /etc/mtab may be a bit useful...so this is what my /etc/Fstab contains
> 
unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0

and my /etc/mtab contains

> proc /proc proc rw 0 0
sysfs /sys sysfs rw 0 0
tmpfs /lib/modules/2.6.22-14-generic/volatile tmpfs rw,mode=0755 0 0
tmpfs /lib/modules/2.6.22-14-generic/volatile tmpfs rw,mode=0755 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
tmpfs /tmp tmpfs rw,nosuid,nodev 0 0and yes i'll try the Tiny Core linux thing told to me by **amsterdamharu tomorrow as i don't have a USB/CD right now**

---

### Post by amsterdamharu on 2010-02-24
Assuming your usb is on /deb/sdb

use fdisk to create a fat16 partition and format it (if it's formatted as fat32 and you don't want to loose data you can just skip fdisk and format. You need about 12MB free space)

```
mkfs -t vfat /dev/sdb1
```Copy the files from the iso to the usb

```
sudo su
mkdir /media/tiny
mount -t iso9660 filename.iso /media/tiny -o loop
mkdir /media/usb
mount -t vfat /dev/sdb1 /media/usb
cp -R /media/tiny/* /media/usb
cp /media/usb/boot/isolinux/isolinux.cfg /media/usb/syslinux.cfg
cp /media/usb/boot/isolinux/boot.msg /media/usb/boot.msg
umount /dev/sdb1

```
```
syslinux /dev/sdb1
```If you don't have syslinux you can download it:
[http://www.kernel.org/pub/linux/utils/boot/syslinux/syslinux-3.81.tar.gz](http://www.kernel.org/pub/linux/utils/boot/syslinux/syslinux-3.81.tar.gz)

```
tar -zxvf syslinux-3.81.tar.gz
cd syslinux-3.81/linux
syslinux /dev/sda1
```Good luck

---

### Post by sohailhusain on 2010-02-24
hey i've the same problem as in this thread [http://ubuntuforums.org/showthread.php?t=661051](http://ubuntuforums.org/showthread.php?t=661051)

i've the exact problem with the windows restarting and again restarting.....but i actually i din't get the solution given there

> It seems to me that you need to find a way to get windows to run  checkdisk all the way through.  Try to get your hands on a XP install cd  and run it from the recovery console:

chkdisk /r

But even that may not prevent it from boot looping
 
the above suggestion is posted by [logos34]("http://ubuntuforums.org/member.php?u=127804").....plz can sum1 tell me step by wat it actually meant cuz I'm a noob at this

---

### Post by Mark Phelps on 2010-02-25
> **sohailhusain said:**
> hey i've the same problem as in this thread [http://ubuntuforums.org/showthread.php?t=661051](http://ubuntuforums.org/showthread.php?t=661051)

This thread is focused on helping someone recover data from a crashed MS Windows system utilizing an Ubuntu LiveCD.  That does not appear to be related to your problem.

I can tell you're new to the forums -- but please don't hijack this thread with a very different problem.

You would do better starting your own thread.

---

### Post by gallifrey on 2010-02-25
Do you still have access to the internet?? If you could download the GParted live CD, you could use the terminal to run testdisk and photorec. I used these to save my data a while back, which is what kick started me moving from Winblows to Ubuntu.


EDIT: Sorry, I just reread your post. If you can't access testdisk and photorec through the 7.10 disk, try booting into the live environment, setting up a connection, and download Gparted Live to get the tools.

---

### Post by d3v1150m471c on 2010-02-25
You could boot from the live cd and then "try ubuntu without installing". Plug in an external hard drive or some other storage device and try:
```

rsync -a /stuff/you/need/saved /media/volumename/folderwithin

```Or...
```

cp -r ~/* /media/external

```

---

