---
title: "Problems with space, browser, and internet"
date: 2009-04-24
forum: New to Ubuntu
---

### Post by chris.willis on 2009-04-24
Hi! I installed Jaunty recently and now have a problem. I was messing around with the Wine emulator, and went to copy some info from an external drive to my desktop, but I get the error "Error while copying to desktop. there is not enough space on the destination. Try to remove files to make space". When I go to /media/disk, there is 69GB left.

The browser I use has 'icon' view. I keep changing it to 'list' view, but it keeps changing to icon view again. Any ideas?

Does anybody know about this post: [http://ubuntuforums.org/showthread.php?t=1136159](http://ubuntuforums.org/showthread.php?t=1136159)

Sorry with the questions!

---

### Post by JoshuaRL on 2009-04-24
> **chris.willis said:**
> Hi! I installed Jaunty recently and now have a problem. I was messing around with the Wine emulator, and went to copy some info from an external drive to my desktop, but I get the error "Error while copying to desktop. there is not enough space on the destination. Try to remove files to make space". When I go to /media/disk, there is 69GB left.

Okay, how are you connected to the external drive?  Have you checked to make sure you're connected correctly?  What kind of drive is it?  Also, why do you think Wine had something to do with it?

---

### Post by chris.willis on 2009-04-24
Basically I have a dual boot with XP and allocated about 80GB to the Jaunty install. The external drive is a USB drive which I have since removed. I also rebooted the computer to the 'safe mode' or whatever it's called and ran disk checks and 'free disk space', and I now have 25MB. I don't understand why the other 60GB isn't there.

I thought it was Wine because it's the only thing I've been messing around with, except for the internet which I also stuffed up!!

So, USB drive removed - problems still exist. I've dared myself to not touch it now until these problems are resolved! Sorry I'm such a dork.

---

### Post by Rocket2DMn on 2009-04-24
It sounds like your /home partition doesn't have enough space on it (or just your / root partition if you don't keep a separate /home one).
Can you please post the ouput of
```
sudo fdisk -l
df -h
mount
```

---

### Post by chris.willis on 2009-04-24
Having a bit of a problem copying and pasting from the terminal to a SD card so I can take it to another computer to put it on the board. Give me a few minutes to work it out!

---

### Post by chris.willis on 2009-04-24
Used Open Office. Don't know if this will work:

chris@chris-laptop:~$ sudo fdisk -l 
[sudo] password for chris: 

Disk /dev/sda: 120.0 GB, 120034123776 bytes 
255 heads, 63 sectors/track, 14593 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Disk identifier: 0x11a8ba38 

   Device Boot      Start         End      Blocks   Id  System 
/dev/sda1               1         502     4032283+  12  Compaq diagnostics 
/dev/sda2   *         503        3117    21004987+   7  HPFS/NTFS 
/dev/sda3            3118       14593    92180970    5  Extended 
/dev/sda5            3118       12919    78734533+  83  Linux 
/dev/sda6           14224       14593     2971993+  82  Linux swap / Solaris 
/dev/sda7           13898       14201     2441848+  83  Linux 
/dev/sda8           14202       14223      176683+  82  Linux swap / Solaris 
/dev/sda9           13572       13875     2441848+  83  Linux 
/dev/sda10          13876       13897      176683+  82  Linux swap / Solaris 
/dev/sda11          13246       13549     2441848+  83  Linux 
/dev/sda12          13550       13571      176683+  82  Linux swap / Solaris 
/dev/sda13          12920       13223     2441848+  83  Linux 
/dev/sda14          13224       13245      176683+  82  Linux swap / Solaris 

Partition table entries are not in disk order 
chris@chris-laptop:~$ df -h 
Filesystem            Size Used Avail Use% Mounted on 
/dev/sda13            2.3G  2.2G   48M  98% / 
tmpfs                 496M     0  496M   0% /lib/init/rw 
varrun                496M  192K  496M   1% /var/run 
varlock               496M     0  496M   0% /var/lock 
udev                  496M  192K  496M   1% /dev 
tmpfs                 496M   84K  496M   1% /dev/shm 
lrm                   496M  2.4M  494M   1% /lib/modules/2.6.28-11-generic/volatile 
chris@chris-laptop:~$ mount 
/dev/sda13 on / type ext3 (rw,relatime,errors=remount-ro) 
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755) 
proc on /proc type proc (rw,noexec,nosuid,nodev) 
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev) 
varrun on /var/run type tmpfs (rw,nosuid,mode=0755) 
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777) 
udev on /dev type tmpfs (rw,mode=0755) 
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev) 
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620) 
fusectl on /sys/fs/fuse/connections type fusectl (rw) 
lrm on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=755) 
securityfs on /sys/kernel/security type securityfs (rw) 
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev) 
gvfs-fuse-daemon on /home/chris/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=chris) 
chris@chris-laptop:~$

---

### Post by Rocket2DMn on 2009-04-24
Ok, we can see here that you are out of space on your root partition:
```
/dev/sda13 2.3G 2.2G 48M 98% / 
```
There is barely enough space there for an Ubuntu install, so there isn't any space available to copy other stuff.

Why do you have so many parititons?  Are you running a sextuple (6 way) boot?  I see 5 instances of Linux and matching Swap space, plus a NTFS partition (Windows install?).  Did you try a bunch of times to install Ubuntu with the intent of only having a dual boot?

---

### Post by chris.willis on 2009-04-24
Yeah, I used about 18 different CD and DVD's. Before installing, I checked them for errors and if no errors there, went to install. As you say, it failed a bunch of times until this morning. I have a hidden PQ-something partition to install Windows, a working Windows install, then I expect a swap drive, the main Ubuntu install, then a SDCard. That's the 6 partitions I expect. When I installed, I made sure there was around 80GB available using the slider at the bottom - a large brown bar (sounds ominous).

---

### Post by nandemonai on 2009-04-24
> **chris.willis said:**
> Used Open Office. Don't know if this will work:

chris@chris-laptop:~$ sudo fdisk -l 
[sudo] password for chris: 

Disk /dev/sda: 120.0 GB, 120034123776 bytes 
255 heads, 63 sectors/track, 14593 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Disk identifier: 0x11a8ba38 

   Device Boot      Start         End      Blocks   Id  System 
/dev/sda1               1         502     4032283+  12  Compaq diagnostics 
/dev/sda2   *         503        3117    21004987+   7  HPFS/NTFS 
/dev/sda3            3118       14593    92180970    5  Extended 
/dev/sda5            3118       12919    78734533+  83  Linux 
/dev/sda6           14224       14593     2971993+  82  Linux swap / Solaris 
/dev/sda7           13898       14201     2441848+  83  Linux 
/dev/sda8           14202       14223      176683+  82  Linux swap / Solaris 
/dev/sda9           13572       13875     2441848+  83  Linux 
/dev/sda10          13876       13897      176683+  82  Linux swap / Solaris 
/dev/sda11          13246       13549     2441848+  83  Linux 
/dev/sda12          13550       13571      176683+  82  Linux swap / Solaris 
/dev/sda13          12920       13223     2441848+  83  Linux 
/dev/sda14          13224       13245      176683+  82  Linux swap / Solaris 

That's hardcore.. 5 / and 5 swaps. phew~

---

### Post by chris.willis on 2009-04-24
Real sorry. I appreciate your time on this (insert smily face here)

---

### Post by nandemonai on 2009-04-24
> **chris.willis said:**
> Yeah, I used about 18 different CD and DVD's. Before installing, I checked them for errors and if no errors there, went to install. As you say, it failed a bunch of times until this morning. I have a hidden PQ-something partition to install Windows, a working Windows install, then I expect a swap drive, the main Ubuntu install, then a SDCard. That's the 6 partitions I expect. When I installed, I made sure there was around 80GB available using the slider at the bottom - a large brown bar (sounds ominous).

While you could use gparted to remove the unused partitions and resize your install I would probably suggest reinstalling and using manual partitioning (Need to use the live CD for this either way).

Ensure you only create 1 / partition and one swap (swap should = your RAM size if you want to use hibernate, otherwise 2G is ample if hibernate isn't needed)

[https://help.ubuntu.com/community/WindowsDualBoot#Manual%20partitioning](https://help.ubuntu.com/community/WindowsDualBoot#Manual%20partitioning)

---

### Post by chris.willis on 2009-04-24
OK. Will do. I think I'll do the whole disk and delete Windows while I'm at it. At least I know the CD works. That's been the hardest part of the whole process.

Many thanks for being honest and open. Fully appreciate your time for a dysfunctional XP user like me.
8o)

---

### Post by Rocket2DMn on 2009-04-24
> **chris.willis said:**
> Yeah, I used about 18 different CD and DVD's. Before installing, I checked them for errors and if no errors there, went to install. As you say, it failed a bunch of times until this morning. I have a hidden PQ-something partition to install Windows, a working Windows install, then I expect a swap drive, the main Ubuntu install, then a SDCard. That's the 6 partitions I expect. When I installed, I made sure there was around 80GB available using the slider at the bottom - a large brown bar (sounds ominous).

Ok, so let me be sure I'm clear.  You want a dual boot setup - a Windows install, and then an Ubuntu install (plus the swap partition) of about 80 GB, leaving 40 GB for Windows?

I advise disconnecting your SD card for the time so it doesn't get in the way.  I don't currently see it listed, so I assume it is disconnected.

I can help you delete all the extra partitions.  It would be easier to just reinstall Ubuntu if that is feasible.  We would delete everything except the Windows install, but if that's no good, we can delete the extra unused installs and resize the active partition.  The latter option could take awhile.

Edit: per the previous comments, I see no reason to have to reinstall Windows.

---

### Post by chris.willis on 2009-04-24
I'll reinstall. I have 2 identical laptops so it's not a problem. I was only dual booting because I have to use MS Word (which is why I was stuffing around with Wine, to get MSWord2003 working), but I'll use the other laptop for such work.

Right. Installing. Will do it just once this time.

Thanks again for all the help. May I say I really like this Ubuntu system. Just have to get the basics right, especially turning the wifi on and off. If I leave it on, it drains the battery quicker. When I turn it off, I can't get it back on lol.

This is a great place to learn. Thanks everyone!

---

### Post by Rocket2DMn on 2009-04-24
Ok, if you want to start completely fresh, that is easy, too.  Here is how I suggest proceeding (this isn't the only way).  Boot into your Ubuntu LiveCD, and go to System->Administration->Partition Editor.  You should be looking at /dev/sda (see the upper right corner).  Make sure the Swap type filesystems are unmounted (right click).

Now just go ahead and delete everything so that you are left only with unpartitioned space.  Now we will create 3 partitions.  First right click that empty space and create a new partition.  Give it 40GB (or however much you want for Windows) - create it at the beginning of the free space and format it as NTFS.  

Now right click the rest of the unpartitioned space and give it the rest of the hard drive minus the amount you need for swap (typically 1.5x-2x your RAM is more than enough).  Format all that as ext3.  Now format the rest of the space (the few remaining GB) as Swap.

If you want, you can create the Ext3 and Swap inside of an Extended Partition much like you currently have, but this shouldn't be needed.

Now you have your partitions laid out which means we don't create them during install.  Reboot the computer with the Windows CD and install it to the NTFS partition we created (don't use the whole disk).  When you are finished with Windows, boot the Ubuntu LiveCD again and install.  You will select Manual partitioning, **not** Guided using the whole disk.  On the ext3 area, make the mount point / (the root of the filesystem) and assign the swap area to swap.  If prompted to format those partitions, its ok to do so, there isn't anything on them yet anyway.

That should get you setup with 3 partitions
sda1 - Windows (NTFS)
sda2 - Linux (ext3), i.e. your Ubuntu install
sda3 - Swap (swap)

If you ever have to go back and reinstall Ubuntu, you would follow the same steps with the LiveCD install, you won't need to setup the partitions again.  You just need to tell the installer where to install to and overwrite your existing install.  The reason you got into this mess is because your just pressed Next through the multiple Ubuntu installs that you did which used the Guided partitioning, and created new partitions each time you installed, which you didn't really want to do.

Whew, now my hands are tired.  I may not see your followup posts tonight, but I'll check up on you in the morning.  Good luck, and if you ever are not comfortable proceeding, stop and ask for help first.

---

### Post by chris.willis on 2009-04-24
Thanks for that! Just installing now and thanks for the information. I used the partitioner as you described, but it wouldn't let me delete partitions, saying that I had to unmount devices higher than SDAx. I'll reinstall across the whole drive and delete anything Windows.

Can't wait til it's finished installing. Thanks for answering all my questions. I've marked the post 'solved', and appreciate everything.

Chris

---

### Post by Rocket2DMn on 2009-04-24
Some partitions like Swap get automounted by the LiveCD so you need to unmount them manually, which you should be able to do by right clicking their entries in Gparted.  Rather than using the Ubuntu LiveCD, you can also use the [GParted LiveCD]("http://gparted.sourceforge.net/index.php") which is used almost exclusively for partition editing and won't automount swap.
Cheers.

---

### Post by chris.willis on 2009-04-24
I'm finding I can delete all the partitions and keep the Windows like you say, by installing the system, using the whole disk, then manually creating the partitions. It's all coming together like a cake. Hope I don't leave the oven on for too long. Will post when everything is working, and will check the partitions using the commands previously given.

---

### Post by chris.willis on 2009-04-25
Okay, rocketman - used the LiveCD and deleted partitions while installing, even kept the Windows stuff. Everything working apart from the MSOffice under Wine issue, but at least I can dual boot til I get my head around it. Checked the home directory, and there's 69.6GB so I'm happy about that. Have a large swap for hibernation. Can enable and disable wireless to save battery (Acer Aspire One has limited battery power). Very happy. Thanks very much!

---

