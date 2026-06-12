---
title: "Cant get a raid 0 mounted"
date: 2011-05-28
forum: New to Ubuntu
---

### Post by MuZiK on 2011-05-28
I know this is been posted all over but i have googled googled and did a little more googling... i just cant get it
I trying to get my raid 0 with my windows install to dual boot ubuntu. Seems "fakeraid" is not so well supported i have used windows disk magr to shrink the drive to what i want for the linux install. 

Heres what i have tryed so far i boot in the liveusb run "sudo dmraid -ay" output is 
RAID set "isw_dhjgifibad_Raid 0" already active <-drive
RAID set "isw_dhjgifibad_Raid 0p1" already active <-windows 
RAID set "isw_dhjgifibad_Raid 0p2" already active <-windows OS 
RAID set "isw_dhjgifibad_Raid 0p5" already active <-unused space for SWAP/Ubuntu
the above makes it so i can at least see the 2 drives as a raid in gparted and not just 2 drives hanging out with each other, buttttt the partitons are NOT mounted this is where im lost i have tryed "sudo mount -t ntfs-3g /dev/mapper/isw_dhjgifibad_Raid 0p5" output is 
NTFS signature is missing.
Failed to mount '/dev/mapper/isw_dhjgifibad_Raid 0p3': Invalid argument
The device '/dev/mapper/isw_dhjgifibad_Raid 0p3' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

I think sometime after "dmraid -ay" it removes the partion table no longer making is a valid NTFS not sure if im right or wrong here please correct me if I am. Im a noob at this but linux seems REALLY fun even tho im banging my head on the wall at this I know the outcome will be rewarding!

I may have missed something I been at this for sometime now any ideas?

---

### Post by MuZiK on 2011-05-28
Bump

---

### Post by Quackers on 2011-05-28
Have you tried installing from the live cd? How far did you get? Did you try installing kpartx to the live cd first? Does gparted in the live cd desktop show the /dev/mapper raid array, or just /dev/sda, /dev/sdb?
What version of Ubuntu are you trying to install?

---

### Post by MuZiK on 2011-05-28
> **Quackers said:**
> Have you tried installing from the live cd? How far did you get? Did you try installing kpartx to the live cd first? Does gparted in the live cd desktop show the /dev/mapper raid array, or just /dev/sda, /dev/sdb?
What version of Ubuntu are you trying to install?

I'm Running U11.04. When I run the installer without running anything I can only see my two TB storage drives when I do run kpartx -ay (after installing it) and then run the installer it says I don't have the storage to run the install. I'm currently at work I will have to get home to see if it's in dev/mapper but I do think it's at /dev/sda. I'm on my iPhone right now btw.

---

### Post by Quackers on 2011-05-28
You don't have to run kpartx, just install it. Then gparted should see your raid array as /dev/mapper/isw_makjfwwfei or whatever, rather than just /dev/sda or /dev/sdb

---

### Post by MuZiK on 2011-05-28
> **Quackers said:**
> You don't have to run kpartx, just install it. Then gparted should see your raid array as /dev/mapper/isw_makjfwwfei or whatever, rather than just /dev/sda or /dev/sdb

I ran the liveusb again got kpartx installed (sudo apt-get install xpartx), opened gparted and it only sees the 2 drives not the raid array. 

Only after i do "sudo dmraid -ay" it will see the raid set up.

---

### Post by MuZiK on 2011-05-28
Me being a noob thought i would add all the outputs.

> To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo apt-get install kpartx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  kpartx
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 22.4 kB of archives.
After this operation, 135 kB of additional disk space will be used.
Get:1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) natty/main kpartx amd64 0.4.8-14ubuntu10 [22.4 kB]
Fetched 22.4 kB in 0s (40.4 kB/s) 
Selecting previously deselected package kpartx.
(Reading database ... 134326 files and directories currently installed.)
Unpacking kpartx (from .../kpartx_0.4.8-14ubuntu10_amd64.deb) ...
Processing triggers for man-db ...
Setting up kpartx (0.4.8-14ubuntu10) ...
ubuntu@ubuntu:~$ sudo dmraid -ay
RAID set "isw_dhjgifibad_Raid 0" was activated
RAID set "isw_dhjgifibad_Raid 0p1" was not activated
RAID set "isw_dhjgifibad_Raid 0p2" was not activated
RAID set "isw_dhjgifibad_Raid 0p5" was not activated
ubuntu@ubuntu:~$ sudo mount -t /dev/mapper/isw_dhjgifibad_Raid 0p3
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .
ubuntu@ubuntu:~$ sudo mount -t ext4 /dev/mapper/isw_dhjgifibad_Raid 0p3
mount: mount point 0p3 does not exist
ubuntu@ubuntu:~$ sudo mount -t ext4 /dev/mapper/isw_dhjgifibad_Raid 0p5
mount: mount point 0p5 does not exist
ubuntu@ubuntu:~$ 
also a sceenshot:
[[IMG]http://i55.tinypic.com/6e11s0.png[/IMG]]("http://www.freeimagehosting.net/")

---

### Post by MuZiK on 2011-05-29
bump

---

### Post by MuZiK on 2011-05-29
bump

---

