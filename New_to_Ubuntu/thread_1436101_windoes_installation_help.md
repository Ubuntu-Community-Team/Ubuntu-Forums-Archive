---
title: "windoes installation help"
date: 2010-03-22
forum: New to Ubuntu
---

### Post by en_mohamed on 2010-03-22
[SIZE=3]hello dears 
 firstly i have three partitions one on it ubuntu and other is extended  and have two [/SIZE][SIZE=3]partitions [/SIZE][SIZE=3] with ntfs files and this extended i take from it part for swap,the questions are:
1-if i want now to install xp beside the linux ,and i want to delete extended partition to install xp&#1548;what must i do to operate two operating sys in parallel (really i have read about booting process but i didnot understand so i want detailed way please)

2- if i deleted extended partition ,is this harmful for linux because it has aswap part ?

3- last ques sorry,i want also expand the linux (ext3) partition to take a part from deleted extended partition &#1548;is this available?
best regards
 [/SIZE]

---

### Post by howefield on 2010-03-22
The first thing you'll need to do is create a primary partition, if I remember correctly windows won't install into an extended partition.

Installing windows with Ubuntu already on the drive means that grub will be wiped out by the Windows bootloader meaning you will need to reinstall grub to be able to access Ubuntu. How you do this will depend on the version of grub that you are running.

---

### Post by en_mohamed on 2010-03-22
[QUOTE=howefield;9008875]The first thing you'll need to do is create a primary partition, if I remember correctly windows won't install into an extended partition.

[SIZE=3]thank you mr h[/SIZE][SIZE=3][COLOR=Black]owefield, i know[/COLOR][/SIZE]  [SIZE=3]about the windows must installed in primary ,i want to install two in different two partitions do this will impact on booting process.

ido not know about the type of my GRub boot,so please explain that,thank you about trying  help
    [/SIZE]

---

### Post by undecim on 2010-03-22
I can give you instructions on what you want to do, but first, I need some more specific info.

Can you open up a terminal (Applications -> Accessories -> Terminal), copy each of these commands below and paste them in the terminal, then post the output here?

( you will need to type a password for this one )
```
sudo fdisk -l
``` 
```
mount
``` 
```
cat /etc/lsb-release
```

---

### Post by en_mohamed on 2010-03-22
[SIZE=3][COLOR=Red]
```
sudo fdisk -l[/COLOR][/SIZE]
output:Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbeb0beb0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1216     9767488+  83  Linux
/dev/sda2            1217        7297    48845632+   f  W95 Ext'd (LBA)
/dev/sda5            1217        4055    22804236    7  HPFS/NTFS
/dev/sda6            4257        7297    24426328+   7  HPFS/NTFS
/dev/sda7            4056        4256     1614501   82  Linux swap / Solaris

[COLOR=Red]
[SIZE=3]
``````
moun[/SIZE][/COLOR][SIZE=3]t[/SIZE]
output:/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/mohamed/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=mohamed)
[COLOR=Red]
[SIZE=3]
```[code]cat /etc/lsb-release[/SIZE][/COLOR]
output:DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.10
DISTRIB_CODENAME=karmic
DISTRIB_DESCRIPTION="Ubuntu 9.10"

---

### Post by undecim on 2010-03-22
Alright, you are using three primary partitions, which means that we still have a slot to put Windows on, so you don't have to delete any partition you don't want to.

I would recommend leaving the swap partition on your hard drive, because that's what the computer uses when you run out of ram or use the hibernation feature.

You will need to use a live CD to resize the partitions using GParted (System -> Administration -> GParted from the Live CD menu). Resize the partions as you wish to create space for the new partition, then create a new NTFS partion between /dev/sda2 and your extended partition.

Then, install windows to that partition. Just be careful not to install it to the wrong partition. The Windows installer should identify this partitions as "Disk 0 Partition 3", a Primary partition, and whatever size you chose when you used GParted.

After windows is installed and working properly, you will need to restore your boot loader so that you can access Ubuntu again. Start your Live CD again, and open a terminal and copy/paste these commands:
```
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

If that command works out fine, you should have access to Ubuntu again (but not Windows just yet) once you are in Ubuntu, go to a terminal (this is the last time, I promise) and type
```
sudo update-grub
```

If all goes well, you should now be given the option when starting your computer to use either Windows or Ubuntu.

If you have any problems with any of this, post back here, and I will respond asap.

---

### Post by en_mohamed on 2010-03-22
```
sudo grub-install /dev/sda
```If that command works out fine, you should have access to Ubuntu again (but not Windows just yet) once you are in Ubuntu, go to a terminal (this is the last time, I promise) and type
```
sudo update-grub
```If all goes well, you should now be given the option when starting your computer to use either Windows or Ubuntu.

If you have any problems with any of this, post back here, and I will respond asap.[/QUOTE]

[SIZE=3]mr undecim,i do not know how can i thank you ,thank you very much,but i have some ques again ,sory
1-i have extended partition ,i understanded from your speech that i can install windows on it ,is this available?
2-  you mentioned after installing windows,write this code in terminal([/SIZE]sudo grub-install /dev/sda[SIZE=3]) does sda mean the bootable partition or you forget to mention (sda1) as it shown in the result of my terminal up,again thank you 
[/SIZE]

---

### Post by undecim on 2010-03-22
"sudo grub-install /dev/sda" is correct. /dev/sda means the master boot record of the hard drive, which is where Grub needs to be installed. (with grub installed, it doesn't really matter which partition is marked bootable)

Also, I should point out that I editted that part of my post shortly after posting it, adding the part with /dev/sda1 and /mnt (I couldn't remember if those were neccessary for restoring grub or just installing it, but it can't hurt to add it).

EDIT: Sorry, I didn't address your question about the extended partition.

As far as I know, Windows cannot run from an extended partition. However, since you are only using 3 out of a possible 4 primary partitions, you can easily install Windows to a brand new primary partition. It will just take a little more fidgeting in GParted. You will first need to resize the logical partitions inside the extended partition and more them to the end of the drive. Then, you will need to resize the extended partition to make room for a new primary partition.

---

