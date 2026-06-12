---
title: "Packages location?"
date: 2011-05-17
forum: New to Ubuntu
---

### Post by G4MJW on 2011-05-17
The main drive on my Asus Eee PC 900 is only 4gB and shortly after a fresh installation and then doing the updates, I'm seriously low on space. I would like to install all additional apps using Synaptic or Ubuntu Software Center on a different drive.

1: What is the default location that Ubuntu installs apps to?

2: Which file can I edit to change the folder location for future applications installed?

Many thanks

Steve

---

### Post by TeoBigusGeekus on 2011-05-17
```
df -h
```
from a terminal will give you a view of your disk usage.
Consider installing bleachbit (the equivalent of CCleaner for linux) and running both as a normal user and as root to clean up some space.

Creating a separate partition for /usr would probably solve your problem.

---

### Post by G4MJW on 2011-05-17
Many thanks for the info.

I'll try downloading bleachbit and running it.

My 4GB SSD Drive is SDA1 and I'd want to create a new /USR folder on the 8GB SSD Drive which is SDB1. What do I edit to tell Ubuntu to look at the moved folder?

Many thanks

Steve

---

### Post by TeoBigusGeekus on 2011-05-17
You can do it editing your fstab file and copying your entire /usr folder to the new location, but...
...the procedure could be dangerous and it could render your whole system unusable.
I suggest you do a reinstallation; when the partitioner comes up, select manual partitioning. Choose your 4gb disk as your root partition (mount point: /) and your 8gb disk as your /usr partition (mount point: /usr).

---

### Post by wildmanne39 on 2011-05-17
> **TeoBigusGeekus said:**
> You can do it editing your fstab file and copying your entire /usr folder to the new location, but...
...the procedure could be dangerous and it could render your whole system unusable.
I suggest you do a reinstallation; when the partitioner comes up, select manual partitioning. Choose your 4gb disk as your root partition (mount point: /) and your 8gb disk as your /usr partition (mount point: /usr).

Hi, I had to move and resize all my partitions 3 weeks ago and then I had to reinstall grub from live cd, it was a task because the cd was not working quite right.

---

### Post by G4MJW on 2011-05-18
I did a new installation a few weeks ago and have not added anything extra yet. 

I use OpenOffice and a host of other bundled apps. I think I will un-install them, create the new folder in the second drive and then re-install them. My little Asus Eee PC 's main use is as the "Workstation" in my sailing boat. I install GPSD which is the driver for my GPS and also OpenCPN which is my Chart Plotter/Navigator (the most important app on my Asus. I have a global chart package which on it's own is over 1GB. They need to be in the same folder as the main app for a smooth transition when I go onto the next chart or zoom in and out. Normally there would not be sufficient space on the 4GB drive!

My FSTAB has this in it:

[COLOR="Red"]# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1[/COLOR]

What would I need to add to for it to look at the /USR folder on my SDB1 drive (when I create it!)?

Many thanks

Steve

---

### Post by G4MJW on 2011-05-19
Problem solved and it was so easy!

I did a new installation and when it came to selection the drive/partitioning etc I selected Advanced/custom or whatever it says. Created a /  root drive EXT4 in the 4GM SSD Drive. I then selected the second drive, the 8GB SSD and created a /USR EXT4. 

I did wonder if it would still make a /USR with all it's sub directories in the root but no, it worked. There are 125,000 file spread around 8 sub-folders in /USR in SDB1 and everything works OK. 

My 4GB drive usage is only 20% leaving something like 2.8GB free.

I can now put my Marine Navigation Program on + 1GB of charts in the same folder.
___________________________________________________________________________________
Actually, this is my FSTAB file after the new installation.  It should be possible just to move or copy & paste the /USR file to the alternative drive (in my case: sdb1) and modify the FSTAB file:

[COLOR="Blue"]# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc nodev,noexec,nosuid 0 0
# / was on /dev/sda1 during installation
UUID=98e4235a-a345-4751-8986-df556c33e4ee /                ext4    errors=remount-ro 0      1
/dev/sda1              /usr           ext4          defaults        0      2[/COLOR]

Many thanks everyone for your help and inspiration.

Steve
My Boat: [http://www.microyacht.com]("http://www.microyacht.com")

---

