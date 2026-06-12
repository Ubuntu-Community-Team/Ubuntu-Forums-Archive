---
title: "Only have a / partition with 2.3 GB"
date: 2009-05-31
forum: New to Ubuntu
---

### Post by dubbya on 2009-05-31
I just installed Ubuntu on my computer and when I connected to the internet the update manager wanted to install updates. However, I didn't have enough free disk space, which led me to searching these forums and to check my System Monitor.

My only directory is /, which is the system partition I think. It has used 100% of its 2.3 GB available. When I installed Ubuntu I had it partition my hard drive automatically. How do I go about creating the necessary partitions with the appropriate sizes?

(I'm assuming this is the reason for a host of other small problems, such as firefox being unable to go backwards in pages or create bookmarks)

Thank you for the help,

---

### Post by oldos2er on 2009-05-31
Could you please open a terminal, and post the output from this command:
```
sudo fdisk -l
```
?

---

### Post by dubbya on 2009-05-31
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x04ac1e08

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       32695   262622556    7  HPFS/NTFS
/dev/sda2           32696       36988    34477126+   f  W95 Ext'd (LBA)
/dev/sda3           36988       38914    15471448   12  Compaq diagnostics
/dev/sda5           33022       36988    31858562    7  HPFS/NTFS
/dev/sda6           32696       32999     2441817   83  Linux
/dev/sda7           33000       33021      176683+  82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by Random-penguin on 2009-05-31
I believe the recommended install space is 8Gb for an ubuntu install

---

### Post by dubbya on 2009-05-31
Yeah, that was what I ended up figuring out....but at the time of installation it never even gave me the choice, or at least I didn't see the option to choose partition sizes.

---

### Post by kkkkdddd on 2009-05-31
Could you give the output of the following command:
```
df -h
```

From what I see you have NTFS partition. Maybe it was almost full, so Ubuntu installer could not claim enough space for its partition.

---

### Post by dubbya on 2009-05-31
df -h gives:
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6             2.3G  2.3G     0 100% /
tmpfs                 1.5G     0  1.5G   0% /lib/init/rw
varrun                1.5G  104K  1.5G   1% /var/run
varlock               1.5G     0  1.5G   0% /var/lock
udev                  1.5G  164K  1.5G   1% /dev
tmpfs                 1.5G   84K  1.5G   1% /dev/shm
lrm                   1.5G  2.4M  1.5G   1% /lib/modules/2.6.28-11-generic/volatile
overflow              1.0M   16K 1008K   2% /tmp

---

### Post by Random-penguin on 2009-05-31
I must admit I can't off the top of my head remember the exact option but when you get to the partitioning window during install hit the advanced button (or similar... you can always go back) and it will give you the opportunity to change your partition sizes etc..... Obviously make sure you have backed up before repartitioning. 

By the way I find the tiny distro "System Rescue" so handy in setting up my hard-drives (and for rescuing data off corrupted drives for that matter). Google Distrowatch and you will find a download link. Be warned though it is quite basic from the gui point of view.

---

### Post by kkkkdddd on 2009-05-31
Firstly, make sure that you have enough free space on other partitions.

Then reinstall Ubuntu. You are going to have 3 options:
-automatic - it should work OK, but you need to have enough free space
-use whole disc - it will delete all other partitions, so if you want to keep them, do not choose this one
-manual - I always use this one because it gives me a lot of flexibility. I recommend using it. I can see that you have 320 GB hard drive. If you are seriously thinking about using Ubuntu, give it at least 20 GB. My Ubuntu partition uses about 30 GB from which 10 GB is for the system/programmes and the rest is used by my personal files.

---

### Post by dubbya on 2009-05-31
I think I understand how to partition everything correctly now. Perhaps I should uninstall and then reinstall jaunty? How do I do this properly?

---

### Post by dubbya on 2009-05-31
Ah, you beat me to it.

* I can see that you have 320 GB hard drive. If you are seriously thinking about using Ubuntu, give it at least 20 GB. My Ubuntu partition uses about 30 GB from which 10 GB is for the system/programmes and the rest is used by my personal files.*

How much do I allocate to each partition?
If I understand correctly I should create three:
root partition
home partition
swap partition

How many GB do I give to each of these?

---

### Post by ajgreeny on 2009-05-31
The minimum is just two partitions, / and swap.  A separate /home helps if you need to reinstall, but personally, I've never bothered as it's so easy to backup with a live CD to an external drive, that I don't think it's worth doing.

It would be worth mounting your windows partitions from nautilus places and then running ```
df -h
``` again as that will let us see how much space is available there if you need it.  You should always defrag before editing any windows partitions with either the ubuntu installer or gparted on the live CD.

---

### Post by Random-penguin on 2009-05-31
In general it is recommended that the swap partition is twice your RAM (but realistically 2Gb is usually ample) I tend to give root between 15Gb and 25Gb (this should be plenty) Then the home directory can be what you can afford to take from windows..... Mine is 80Gb but 10Gb would be fine as you can mount and read/write to your windows partition.....meaning all those mp3's (install lame to be able to use them) and pix can stay where they are!! How cool. If you right click on the panel under gnome you can install "Disk Mounter" which makes this easy!

---

### Post by dubbya on 2009-05-31
Okay, after a completely innocuous shutdown I restarted my computer...

Windows doesn't work
Ubuntu only worked after fiddling in memory test
everything crashes

What just happened to my computer? I haven't done anything different except insert the CD I downloaded Ubuntu on, then everything went wrong.

Can someone please help?

---

### Post by dubbya on 2009-05-31
The computer I just installed Ubuntu has been in my possession for three days.

In that time, I've installed Ubuntu, but the option I picked (which was supposed to partition automatically for me) only created a root partition with 2.3 GB space. In trying to restart I now cannot use Windows Vista (BOOTMGR missing) and can't figure out how to give more space to Ubuntu so I can actually use it.

Can someone please help me fix Ubuntu, windows, or both?

---

### Post by sailthesea on 2009-05-31
You'll need to fix Grub and get back into Windows ED: And Fdisk !! then best let the Vista disk manager handle creating the partition Then try a reinstall into the new partition
 I doubt you've lost too much on a three day old machine so you should be OK! Good luck

---

### Post by presence1960 on 2009-05-31
First you will need your Vista DVD to restore Vista's BootMgr. Follow this guide : [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

After completing that reboot and defrag Vista a couple of times. This is very important since you will be partitioning your hard disk. Windows is very sloppy about the way it places files in the filesystem.

After defragging use Vista's disk management utility to shrink the Vista partition. This will create free space on your hard disk. While you are in there you may as well delete that 2.3 GB partition that was created as well. You should free up at least 20 GB for Ubuntu.

Now boot the Ubuntu Live CD and when you get to the partitioner screen Prepare Disk Space choose "manual" option. This will display your hard disk(s) and partitions. Find the free space you had just created and highlight that. Click Edit Partition. Choose Primary for partition type. Choose ext 3 for filesystem. Choose "/" for mountpoint. 

When you get to the screen Ready to Install click the advanced button. Choose hd0 or sda to install GRUB to. see attached screenshot. Now continue the install process.

---

### Post by dubbya on 2009-06-01
Gonna try it in a bit. Thanks again fellas, hopefully I'll have learned something from all this, lol.

---

