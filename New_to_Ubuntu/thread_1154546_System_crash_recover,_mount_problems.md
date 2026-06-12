---
title: "System crash recover, mount problems"
date: 2009-05-09
forum: New to Ubuntu
---

### Post by ladasky on 2009-05-09
Hi folks,

This post is pretty long, thanks for your patience.
 
My Ubuntu 8.04 LTS desktop system has crashed.  I think it's a motherboard problem.  OS starts up, but then gives an endless loop of messages indicating DMA controller errors.
 
My data is more important than the computer, which is old.  I bought an IDE to USB adapter, plugged it into the hard drive on my desktop machine.  I have a Windows laptop, which of course cannot read ext3 partitions.  So I booted the laptop with the Ubuntu Live CD.
 
Two of the three partitions on my desktop drive mounted.  The swap partition was tagged as /dev/sdb1, and the system partition became /dev/sdb2.  Of course, the one partition I want, my user partition, is inaccessible.  GParted knows that there is a partition present that it should mount, but it says that its file system type is unknown.  I know I formatted it as ext3, the same as my system partition.

I've read the [device mount troubleshooting]("https://help.ubuntu.com/community/MountDevicesTroubleshooting") web page, which says I will invariably be asked to post the output from fdisk, lshw, and /etc/fstab.  Here they are, though I'll have to say I'm frustrated by the fact that my fstab looks nothing like the document that I am told to expect:



ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40007761920 bytes
240 heads, 63 sectors/track, 5168 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0xcccdcccd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4596    34745728+   7  HPFS/NTFS
/dev/sda2            4597        5168     4324320   12  Compaq diagnostics

Disk /dev/sdb: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x78e578e5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         122      979933+  82  Linux swap / Solaris
/dev/sdb2             123         730     4883760   83  Linux
/dev/sdb3             731        4998    34282710   83  Linux



ubuntu@ubuntu:~$ sudo lshw -C disk

  *-disk                  
       description: ATA Disk
       product: HTS541040G9SA00
       vendor: Hitachi
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: MB2I
       serial: MPBBL0X2H6AS1M
       size: 37GiB (40GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=cccdcccd
  *-cdrom
       description: DVD reader
       product: DVD/CDRW UJDA770
       vendor: MATSHITA
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       logical name: /cdrom
       version: 1.02
       capabilities: removable audio cd-r cd-rw dvd
       configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,noatime,relatime state=mounted status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom
          logical name: /cdrom
          configuration: mount.fstype=iso9660 mount.options=ro,noatime,relatime state=mounted
  *-disk
       description: SCSI Disk
       product: E040L0
       vendor: Maxtor 6
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/sdb
       version: 1590
       size: 38GiB (41GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=2 signature=78e578e5



ubuntu@ubuntu:~$ cat /etc/fstab

unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0



So, here are my questions.  Do I have more than a damaged desktop motherboard?  Is the third partition on my desktop also corrupt?  I find it very suspicious that I can mount two partitions and not the third.  Will this work differently for me if I'm working on a native Ubuntu system rather than the Live CD?
 
Finally -- if the hard drive is corrupt, how can I recover some data from it in spite of that?  Can I force the system to attempt to mount my missing partition as ext3 somehow?  Will I need to start investigating data recovery tools?

Thanks for your advice!

---

### Post by blueridgedog on 2009-05-10
It appears that you have two drives viewable in the system, the first appears to be your existing windows drive, sda.  The second is the drive out of your dead desktop.  This has three partitions.  A small swap and a small and large Linux (ext2/3) partitions.

/dev/sdb1 1 122 979933+ 82 Linux swap / Solaris
/dev/sdb2 123 730 4883760 83 Linux
/dev/sdb3 731 4998 34282710 83 Linux

To see where these are mounted, can you post the output of the command:

```
mount
```

Is your user/data partition one of the above?  What told you that it was unknown or not accessible.

---

### Post by ladasky on 2009-05-10
> **blueridgedog said:**
> It appears that you have two drives viewable in the system, the first appears to be your existing windows drive, sda.  The second is the drive out of your dead desktop.  This has three partitions.  A small swap and a small and large Linux (ext2/3) partitions.

 
Yes, I agree with all of that.


> **blueridgedog said:**
> 
/dev/sdb1 1 122 979933+ 82 Linux swap / Solaris
/dev/sdb2 123 730 4883760 83 Linux
/dev/sdb3 731 4998 34282710 83 Linux

To see where these are mounted, can you post the output of the command:

```
mount
```


Here it is:

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
/dev/sdb2 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)


> **blueridgedog said:**
>  Is your user/data partition one of the above?

Yes.  It's /dev/sdb3.  /dev/sdb1 does not appear to have mounted, but I don't care about that, as it's the swap partition from my old system.  /dev/sdb2 is my system and apps partition from the dead desktop system.  It mounts, and I can read files from it with no apparent difficulty.


> **blueridgedog said:**
> 
What told you that it was unknown or not accessible.

Well, first of all I can see that it doesn't mount.  /dev/sdb2/ appears on my desktop as removable media.  That's the only partition which does appear.  The partition editor application, GParted, gives more information.  GParted is accessible from the Ubuntu menu bar: System > Administration > Partition Editor.  I've posted a screen shot from the GParted main window:

[http://www.flickr.com/photos/43866729@N00/3520400098/](http://www.flickr.com/photos/43866729@N00/3520400098/)

And if I double-click on the warning icon next to /dev/sdb3, I get this dialog box:

[http://www.flickr.com/photos/43866729@N00/3519612917/](http://www.flickr.com/photos/43866729@N00/3519612917/)

Thanks again for reading all the way through!

---

### Post by blueridgedog on 2009-05-10
Well, you can try and mount it manually:

```
sudo mkdir /mnt/myfiles
sudo mount -t ext3 /dev/sdb3 /mnt/myfiles
```

Then use nautilus to view the contents.  Note you can name the mount point anything and place in your home director for that matter (it will go away when you rebood on the liveCD).

If it can't mount manually, then we can try and check it for errors.

---

### Post by ladasky on 2009-05-10
Thanks for getting back to me.  My attempt to mount the missing partition manually failed.  Here's the output:


ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/sdb3 /mnt/myfiles

mount: wrong fs type, bad option, bad superblock on /dev/sdb3,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
 
ubuntu@ubuntu:~$ dmesg | tail

[ 1055.019322] init_special_inode: bogus i_mode (134353)
[ 1055.019373] init_special_inode: bogus i_mode (53511)
[ 1055.019519] init_special_inode: bogus i_mode (153634)
[ 1055.019573] init_special_inode: bogus i_mode (163304)
[ 1077.624290] NET: Registered protocol family 17
[ 1077.867894] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[  497.362808] ieee80211_crypt: registered algorithm 'TKIP'
[ 1086.396785] eth1: no IPv6 routers present
[  760.572343] program gparted is using a deprecated SCSI ioctl, please convert it to SG_IO
[ 8855.656288] VFS: Can't find ext3 filesystem on dev sdb3.


That last message suggests that the partition may indeed have been damaged.


Just to make sure I didn't accidentally format my user partition as ext2, I tried mounting it that way as well.  The result was the same.

---

### Post by blueridgedog on 2009-05-11
I suggest you run fsck (file system check) on the partition:
```

e2fsck /dev/sdb3
```

You can also read up on the e2fsck program with 

```
man e2fsck
```

---

### Post by ladasky on 2009-05-11
> **blueridgedog said:**
> I suggest you run e2fsck

Thanks again, blueridgedog.  I haven't been down to the file system level of a computer since -- well, my Apple ][ days.  (Does that make me old?)  :lol:

I'm a RTFM guy.  I read the man pages for e2fsck first, tried it with the -p option.  Its output was:
 
```
ubuntu@ubuntu:~$ sudo e2fsck -p /dev/sdb3

/dev/sdb3 was not cleanly unmounted, check forced.
/dev/sdb3: Inode 3096673 has imagic flag set.  

/dev/sdb3: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
	(i.e., without -a or -p options)
```

Next I tried e2fsck manually, and there are indeed many errors.  It looks like my system may have crashed in the middle of a disk write operation.
 
e2fsck asked me if I wanted to fix any of these errors.  The first time through, I answered "no" to everything.  Before I say "yes" to everything -- are there any types of errors I should be cautious about fixing?

The e2fsck man pages state that the ext file system creates duplicate data which can be used in repairs, in case of a crash like the one I've apparently experienced.  I was JUST wishing for exactly that as I was contemplating my problems, and I am VERY impressed that it indeed exists.

---

### Post by blueridgedog on 2009-05-11
I would run it and answer yes (it may be a few hundred...so I use the -y option).  Don't get your hopes up as it looks like a hard drive crash.  I suggest you read this before proceeding:

[http://www.linuxjournal.com/article/10360](http://www.linuxjournal.com/article/10360)

(For those keeping score at home, this is a link to Kyle Rankin's March Linux Journal article regarding recovering crashed hard drives...excellent reading about hard drive recover and ddrescue or dd_rescue)

The other articles in the series are available online as well.

Good luck.

---

### Post by ladasky on 2009-05-11
Hey there... after the fsck, THE PARTITION MOUNTED!  It's accessible at /media/disk-1.  And I can see folders!  THANK YOU!  :)

Now, I'm not out of the woods yet.  As I wrote in my first message, I'm pretty sure I have a blown DMA controller on the desktop machine.  So I will likely need to operate the laptop's hard drive through the USB adapter for now.

I created a folder on the Windows laptop called "Ubuntu_backup" and then I tried running this...

```

sudo cp -r /media/disk-1/* /media/IBM_PRELOAD/Ubuntu_backup

```

...from the prompt because, if there's a way to operate as root from the GUI, I don't know it.  The terminal returned my command prompt to me unexpectedly soon.  Funny, only the first sub-folder was copied?  Folders WITHIN that folder appear to be copied recursively as I expected...

I'm ALMOST ready to mark this problem as solved!  :)

---

### Post by ladasky on 2009-05-11
Just a little problem with how I specified the folders and files for cp.  This is now running, and working recursively as I expect:

```
sudo cp -r /media/disk-1/my_user_name /media/IBM_PRELOAD/Ubuntu_backup
```

Will post results shortly.

---

### Post by ladasky on 2009-05-11
:KS I have recovered ALL of my files! :KS

Thanks to you, blueridgedog! :)
 
Now, did I tag this thread as "solved" in the correct way?

---

### Post by blueridgedog on 2009-05-11
Alternatively, you could try:
```

rsync -av /media/disk-1/my_user_name /media/IBM_PRELOAD/Ubuntu_backup
```

---

### Post by blueridgedog on 2009-05-11
> **ladasky said:**
> :KS I have recovered ALL of my files! :KS

Thanks to you, blueridgeheron! :)
 
Now, did I tag this thread as "solved" in the correct way?

Glad to help, and yes it is tagged.  Enjoy your files.

---

