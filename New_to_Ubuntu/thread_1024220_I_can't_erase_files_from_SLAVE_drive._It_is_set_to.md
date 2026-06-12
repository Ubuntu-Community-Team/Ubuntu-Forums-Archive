---
title: "I can't erase files from SLAVE drive. It is set to READ ONLY Please help"
date: 2008-12-28
forum: New to Ubuntu
---

### Post by Drodriguez64 on 2008-12-28
Hi,

My SLAVE hard drive is READ-ONLY and I need to delete files from it. How do I change the drive from a being a READ-ONLY drive to get full access?

Error: "media/disk <file_name> cannot be deleted because it is on a read-only disk."

Thanks for your help.

Dan

---

### Post by taurus on 2008-12-28
Is it ntfs or fat32/vfat filesystem?  Open a terminal and post the outputs of these commands here.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

### Post by Drodriguez64 on 2008-12-28
sarah@sarah-desktop:~$ sudo fdisk -l
Password:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9544    76662148+  83  Linux
/dev/sda2            9545        9729     1486012+   5  Extended
/dev/sda5            9545        9729     1485981   82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *         483        9728    74268495    7  HPFS/NTFS
/dev/sdb2               1         482     3871633+   b  W95 FAT32

Partition table entries are not in disk order
sarah@sarah-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=e4143682-9343-4dbb-a6f7-59d5bd2a004b /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=30906fd2-1a9b-4252-b17a-2d388d848820 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
sarah@sarah-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              72G   26G   43G  38% /
varrun                375M  232K  375M   1% /var/run
varlock               375M     0  375M   0% /var/lock
procbususb            375M  100K  375M   1% /proc/bus/usb
udev                  375M  100K  375M   1% /dev
devshm                375M     0  375M   0% /dev/shm
/dev/sdb1              71G   25G   47G  35% /media/disk
sarah@sarah-desktop:~$

---

### Post by newbee70 on 2008-12-29
deleted,

---

### Post by Michael.Godawski on 2008-12-29
morning,

I guess you are talking about the ntfs partitions sdb1.
The easiest way to configure it is to install these packages, some of it might be already installed some may not:

```
sudo apt-get install ntfs-config ntfsprogs ntfs-3g
```Now use the tool ntfs-config which will be installed in
Applications > System Tools > ntfs configuration tools.

I do not have a ntfs partition on my laptop, so I cannot guide you further but it should work, and if not we are happy to help.

---

### Post by Drodriguez64 on 2008-12-29
Top of the morning to ya'

I tried the script but it some services seem to be unavailable at this moment. Also I tried to remove some installation files (as suggested by the terminal) and it says I am not root.

Secondary question: How do I log in as root? and shouldn't I be the SuperUser on my own PC anyway?

Here is the output:
sarah@sarah-desktop:~$ sudo apt-get install ntfs-config ntfsprogs ntfs-3g
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  clamav clamav-freshclam ttf-dustin clamav-base libclamav3 kalzium-data
  atomix-data klettres-data kstars-data libkdeedu3 libgcompris-1-0
  gcompris-data indi libnumber-compare-perl
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  fuse-utils libfuse2 libntfs-3g0 libntfs9
The following NEW packages will be installed:
  fuse-utils libfuse2 libntfs-3g0 libntfs9 ntfs-3g ntfs-config ntfsprogs
0 upgraded, 7 newly installed, 0 to remove and 164 not upgraded.
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory
sarah@sarah-desktop:~$ apt-get autoremove
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
sarah@sarah-desktop:~$ su
Password: 
su: Authentication failure
Sorry.


Your help is sincerely appreciated.
Dan

---

### Post by taurus on 2008-12-29
1.  There was another program running in the background when you ran your apt-get command from a terminal.  That's why you got that error message.

```

E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

```

2.  And if you want to remove the unwanted programs/files, you have to include the sudo in front of the command.

```
sudo apt-get autoremove
```

---

### Post by handydan918 on 2008-12-29
> **Drodriguez64 said:**
> 
Secondary question: How do I log in as root? and shouldn't I be the SuperUser on my own PC anyway?

This is one of the reasons that Linux is so much more secure than that OTHER system. You can obtain "superuser" (root) privileges by prepending "sudo" to any command, so, in effect, you ARE the super user on your own system. The password prompt is there to make sure you stay that way.
:D

---

### Post by mapes12 on 2008-12-29
If you're using Terminal try changing permissions for sdb1 (that's if the data you want to delete is on sdb1) like this ```
sudo chmod -R 777 /dev/sdb1
``` but you may need a wildcard for the files to inherit the permissions like this ```
sudo chmod -R 777 /dev/sdb1/*
```
Note that 777 gives permissions for anyone to do anything.

Or a GUI option would be to go in with root access like this ```
gksudo nautilus
```find the files you want to delete then **Shift+Del**. The shift key is needed to permanently delete the file otherwise your Root trash bin will fill up with stuff your thought you had got rid off.

---

### Post by joukez on 2008-12-29
[QUOTE=mapes12;6457189]If you're using Terminal try changing permissions for sdb1 (that's if the data you want to delete is on sdb1) like this ```
sudo chmod -R 777 /dev/sdb1
``` but you may need a wildcard for the files to inherit the permissions like this ```
sudo chmod -R 777 /dev/sdb1/*
```
Note that 777 gives permissions for anyone to do anything.

Or a GUI option would be to go in with root access like this ```
gksudo nautilus
```find the files you want to delete then **Shift+Del**. The shift key is needed to permanently delete the file otherwise your Root trash bin will fill up with stuff your thought you had got rid off.[/QUOTE

To use de GUI option you first have to press alt+f2, then a small window wil open then gksu (not gksudo) nautilus  so> gksu nautilus then it will ask your userpassword and your in, go to the disk and give userpermission to read/write

---

### Post by Drodriguez64 on 2008-12-29
Thanks to all that have tried to help.
So far I have had no luck.

1st. I tried stopping the programs running in the background."sudo apt-get autoremove" it ran fine I guess.

2nd. I tried loading the NTSF program. It ran half way and encountered problems:
sarah@sarah-desktop:~$ sudo apt-get install ntfs-config ntfsprogs ntfs-3g
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  fuse-utils libfuse2 libntfs-3g0 libntfs9
The following NEW packages will be installed:
  fuse-utils libfuse2 libntfs-3g0 libntfs9 ntfs-3g ntfs-config ntfsprogs
0 upgraded, 7 newly installed, 0 to remove and 164 not upgraded.
Need to get 265kB/715kB of archives.
After unpacking 2195kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  fuse-utils libfuse2 libntfs-3g0 ntfs-3g libntfs9 ntfs-config ntfsprogs
Install these packages without verification [y/N]? y
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main fuse-utils 2.6.3-1ubuntu2
  404 Not Found [IP: 91.189.88.40 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main libfuse2 2.6.3-1ubuntu2
  404 Not Found [IP: 91.189.88.40 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe libntfs-3g0 1:1.328-1
  404 Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe libntfs-3g0 1:1.328-1
  404 Not Found [IP: 91.189.88.31 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe ntfs-3g 1:1.328-1
  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/f/fuse/fuse-utils_2.6.3-1ubuntu2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/f/fuse/fuse-utils_2.6.3-1ubuntu2_i386.deb)  404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/f/fuse/libfuse2_2.6.3-1ubuntu2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/f/fuse/libfuse2_2.6.3-1ubuntu2_i386.deb)  404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/n/ntfs-3g/libntfs-3g0_1.328-1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/n/ntfs-3g/libntfs-3g0_1.328-1_i386.deb)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/n/ntfs-3g/ntfs-3g_1.328-1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/n/ntfs-3g/ntfs-3g_1.328-1_i386.deb)  404 Not Found [IP: 91.189.88.31 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
No NTFS program in the applications folder yet.

3rd. I tried changing the permissions to the slave drive. As far as I understand (not alot) it is not a lack of permission... the drive is MOUNTED as a READ-ONLY drive. Not files set to read-only. "sudo chmod -R 777 /dev/sdb1" will not work for that reason.

Any other ideas?
I really appreciate everyones help.

Dan

---

### Post by handydan918 on 2008-12-29
> **Drodriguez64 said:**
> 
3rd. I tried changing the permissions to the slave drive. As far as I understand (not alot) it is not a lack of permission... the drive is MOUNTED as a READ-ONLY drive. Not files set to read-only. "sudo chmod -R 777 /dev/sdb1" will not work for that reason.

Any other ideas?
I really appreciate everyones help.

Dan
As regards #3...
Don't try to reason it out. Just do it. 
chmod'ing the FILE /dev/sdb1 will change the -ahem- **_write_** permissions of the entire volume. If that for  some reason fails, post back with your the output of ```
cat /etc/fstab
```

---

### Post by Drodriguez64 on 2008-12-30
Good morning,

I had already tried the chmod command with no luck. However here is the terminal output for chmod, attempting to delete (rm) the file, and the cat results:
sarah@sarah-desktop:~$ sudo chmod -R 777 /dev/sdb1
sarah@sarah-desktop:~$ rm /media/disk/temp/remove/results.txt
rm: cannot remove `/media/disk/temp/remove/results.txt': Read-only file system
sarah@sarah-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=e4143682-9343-4dbb-a6f7-59d5bd2a004b /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=30906fd2-1a9b-4252-b17a-2d388d848820 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


I don't see the sdb1 drive mounted. it is a NTSF drive and I get errors trying to install the NTSF program (see previous threads of this plea for help.)
I can't even install the upgrade of UBUNTU as it spits out errors...

Any clues?

Thanks for taking your time to look at this.
Dan

---

### Post by handydan918 on 2008-12-30
I guess I'd want to know what you get from ```
sudo mount /dev/sdb1
``` If it wants a mount point, just do ```
sudo mkdir /mnt/sdb1
``` and try the mount again.

If the ntfs partition was not clanly unmounted, you may have to run ckdisk (?) on it. I always hose any device that comes with a M/S filesystem, so I don't have much hands on experience with the interoperability thing...

---

### Post by Drodriguez64 on 2008-12-30
Hello once again,

I ran the suggested command and it says it is already mounted.
I will pull the HD and run a checkdisk on it on it's original PC.
Then re-install on my Ubuntu PC and see if that changes anything.
Just in case you ask, the HDD jack is set to SLAVE.
Here is the result of the mount command suggested:

sarah@sarah-desktop:~$ sudo mount /dev/sdb1
Password:
mount: /dev/sdb1 already mounted or /media/disk busy
mount: according to mtab, /dev/sdb1 is already mounted on /media/disk

Hang there with me... I would really like to get this fixed!!!
Thanks for your help.

Dan

---

### Post by mc4man on 2008-12-30
> /dev/sdb1 is already mounted on /media/disk

Go look in Places - computer or removable drives and see if it's there. Or navigate in filesystem to /media/disk and click to open

---

### Post by handydan918 on 2008-12-30
Okay, how about posting the output of ```
cd /media/disk && ls -la
```
I'd really like a look at the permissions on that turkey.

---

### Post by Drodriguez64 on 2009-01-04
Thanks for all your help.
Unfortunately the Hard drive had to return to it's original XP computer, so I can't attempt to delete the files anymore.

I appreciate all the support the community offered me.

Best Regards,

---

### Post by fairy._.queen on 2009-01-07
_

---

### Post by physeetcosmo on 2009-01-07
> **joukez said:**
> ```
gksudo nautilus
```

joukez,

Thanks for the commmand: *gksudo nautilus*. For newbies like me, it opens a file-browser with root permisions which one can navigate to the disk in question and use the GUI to change the disk permissions. 
1.Right-click
2.Select Properties
3.Go to Permissions tab

Similar to Windows, if you've finally dumped it for Linux like i have ;)

-Dustin

---

### Post by drhiii on 2009-02-17
Folks, I am having the same problem.  Here is the scenario...

Everything has run fine for USB external devices since 7.* of Ubuntu.  Have gone through several upgrades on several machines.  When going to 8.10, all of my USB external devices are now Read-Only.  I cannot chmod them to anything (as root of course).  Running   gksudo nautilis   does not allow any tweaking of permissions.  It continues to come back as a 'read-only' file system.  Again, all this was working with no problems until going from 8.04 to 8.10.  I see this problem described quite a bit, but no one seems to have found a solution for why the USB devices are being mounted as RO only.  This never happened until 8.10.  

Ideas anyone?  Am a bit stumped on this one....

---

