---
title: "2 Logical Partitions in Extended Partition - Setting up!!"
date: 2009-06-26
forum: New to Ubuntu
---

### Post by peterkim582 on 2009-06-26
First off, I'm one week into Linux and it's been non-stop googling issues left and right.  I have very little Linux background and it's been frustrating / rewarding on numerous fronts.

I created 3 Primary Partitions, 1 Extended Partition and 3 Logical Partitions within the Extended:
sda1 - recovery
sda2 - root
sda4 - home
sda3 - extended
sda5 - swap (logical)
sda6 - data (logical)
sda7 - backup (logical)

I tried to test the whole mounting process by making a test folder in my mnt directory, which I did successfully.  I then took the UUID of sda6 and pointed it to the test folder I created (I forget how I did that, but I'm pretty sure it worked).  Anyway, just before mounting, I decided to delete the folder.  Long story short, using Computer Janitor, I deleted my test folder, and now my data partition (sda6) is no longer in my Places bar.  1)  How do I get the partition to show in my Places bar?
2)  How do I mount?  Please explain this to me like I'm a 5 year old....
3)  And do I need to setup these partitions to automatically mount, if I want to treat them as additional internal hard drives?  ie. If I mount once, is it good permanently, or will I need to mount after every reboot?

---

### Post by bodhi.zazen on 2009-06-26
[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")

---

### Post by fugaki on 2009-06-26
Also, check out GParted, its easy mode for partitioning :D

sudo apt-get installl gparted

---

### Post by peterkim582 on 2009-06-26
Thanks Bodhi.

How about my question of the missing data partition in my Places bar?

---

### Post by peterkim582 on 2009-06-26
Fugaki, I actually did partition my laptop using Gparted.. it worked great.

Now I'm just having trouble with the actual partitions - mounting, not being able to see from Places bar..

---

### Post by raymondh on 2009-06-26
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by bodhi.zazen on 2009-06-26
> **peterkim582 said:**
> Thanks Bodhi.

How about my question of the missing data partition in my Places bar?

I believe when you mount a partition it will appear in places, not 100 % on that one.

---

### Post by peterkim582 on 2009-06-26
Raymond, thanks for the reply.  Mounting and giving proper rights doesn't sound so hard.. any idea why one of my partitions isn't showing up in my Places bar?  Is it b/c I haven't added it to the fstab?

---

### Post by topher-t-mill on 2009-06-26
I am not sure if I can help, but installing and reinstalling linux does help you to get to grips with how the partitions work, Gparted is already within Ubuntu, you can set up various partitions using the advanced option during installation, the first time I installed I did it automatically, which was great, I set every thing  ( or so I thought 0 as I wanted it and downloaded plenty of apps Linux and Windows (Real player, Picasa etc)  which was great, untill a distro upgrade appeared to separate the kernel from Grub, Thankfully I had just downloaded Slax another live Cd, which at least enabled me to look at the problem and get stuff moved, I have since reinstalled Ubuntu, but initially I used Slax with Gparted as an included module to partition the drive and then used the advanced installation to mount the drives, you need to set the mount point or you will have trouble with permissions etc.

---

### Post by bodhi.zazen on 2009-06-26
> **peterkim582 said:**
> Raymond, thanks for the reply.  Mounting and giving proper rights doesn't sound so hard.. any idea why one of my partitions isn't showing up in my Places bar?  Is it b/c I haven't added it to the fstab?

See: 

[http://scratching.psybermonkey.net/2009/05/23/ubuntu-how-to-add-or-create-hard-disk-partition-and-make-it-automatically-mount/](http://scratching.psybermonkey.net/2009/05/23/ubuntu-how-to-add-or-create-hard-disk-partition-and-make-it-automatically-mount/)

---

### Post by raymondh on 2009-06-26
> **peterkim582 said:**
> Raymond, thanks for the reply.  Mounting and giving proper rights doesn't sound so hard.. any idea why one of my partitions isn't showing up in my Places bar?  Is it b/c I haven't added it to the fstab?

I think you have to add it to your fstab but, like bodhi says ... try mounting it first and see if it shows in places.

---

### Post by kansasnoob on 2009-06-26
> **peterkim582 said:**
> Raymond, thanks for the reply.  Mounting and giving proper rights doesn't sound so hard.. any idea why one of my partitions isn't showing up in my Places bar?  Is it b/c I haven't added it to the fstab?

Well, which partition?

One of the things I install on every Ubuntu install is "ntfsprogs" which allows full mounting of anything ntfs.

I also always install "pmount" which allows for mounting almost anything that's not "set" to mount in fstab.

I seldom have trouble, but from what I've read, I'm going to have to learn some new tricks beginning with Karmic.

As far as Primary, Extended, Logical look at mine:

[ATTACH]119052[/ATTACH]

One primary and everything else is contained in another extended partition.

---

### Post by peterkim582 on 2009-06-26
Ok, I'm pretty sure I mounted sda6.. I did a cat /etc/mtab in my terminal, and this is what I got:

/dev/sda2 / ext3 rw,relatime,errors=remount-ro 0 0
tmpfs /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,nosuid,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
tmpfs /dev/shm tmpfs rw,nosuid,nodev 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=620 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
lrm /lib/modules/2.6.28-13-generic/volatile tmpfs rw,mode=755 0 0
/dev/sda4 /home ext3 rw,relatime 0 0
securityfs /sys/kernel/security securityfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc bionfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/livelife/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=livelife 0 0
/dev/sda6 /data ext3 rw 0 0

so it looks like sda6 is mounted.. where would I access that folder?  and do I just drag and drop files into that folder if I want to store "data" files in there?

Also, the partition is STILL NOT located in the Places Bar.. which is bothering me for some reason.. any help on this would be MUCH appreciated!

---

