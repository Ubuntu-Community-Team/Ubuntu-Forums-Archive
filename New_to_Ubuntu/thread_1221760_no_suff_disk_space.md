---
title: "no suff disk space"
date: 2009-07-24
forum: New to Ubuntu
---

### Post by aaryan on 2009-07-24
Hi,
I have a list of updates but the disk shows that its full. how do I over come this problem because there should be space as far as I know.

---

### Post by bacil on 2009-07-24
can you run 
```
df -h
```

and mark what disk is the one you talking about and we can take it from there

---

### Post by aaryan on 2009-07-24
Hi,
This is the output for the command
aaryan@aaryan-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6             2.3G  2.3G     0 100% /
tmpfs                1003M     0 1003M   0% /lib/init/rw
varrun               1003M  108K 1002M   1% /var/run
varlock              1003M     0 1003M   0% /var/lock
udev                 1003M  184K 1002M   1% /dev
tmpfs                1003M  116K 1002M   1% /dev/shm
lrm                  1003M  2.4M 1000M   1% /lib/modules/2.6.28-11-generic/volatile
overflow              1.0M   24K 1000K   3% /tmp
/dev/sda5             247G  152G   96G  62% /media/disk
/dev/sda1              49G   13G   37G  27% /media/disk-1

in the update manager when I say install updates i get the warning
Not enough free disk space

The upgrade needs a total of 319M free space on disk '/'. Please free at least an additional 319M of disk space on '/'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'.

---

### Post by Majorix on 2009-07-24
It seems your root partition (/) is full. 2.3gb for a whole / is in most cases not enough.

---

### Post by aaryan on 2009-07-24
Is there any means of changing this. what will be the affect of not installing the updates.

---

### Post by aaryan on 2009-07-24
Is there a means of increasing the disc space now?

---

### Post by Cheesemill on 2009-07-24
When you installed you only gave Ubuntu 2.3GB of disk space, this is not enough for a Ubuntu installation to work properly.

Can you post the results of
```
sudo fdisk -l
```
and we'll take it from there.

---

### Post by philinux on 2009-07-24
[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)

With such a small / partition this is going to come around again and again. You'll have to use the livecd and gparted to shrink a partition and expand / to at least 6 gig. Mine is 10 gig.

---

### Post by aaryan on 2009-07-24
Hi this is the output for the command:
aaryan@aaryan-laptop:~$ sudo fdisk -l
[sudo] password for aaryan: 

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfcfefcfe

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6374    51199123+   7  HPFS/NTFS
/dev/sda2            6375       38913   261369517+   f  W95 Ext'd (LBA)
/dev/sda5            6375       38587   258750891    7  HPFS/NTFS
/dev/sda6           38588       38891     2441848+  83  Linux
/dev/sda7           38892       38913      176683+  82  Linux swap / Solaris

---

### Post by aaryan on 2009-07-24
Could you please gimme the procedure I would need to follow for this.

---

### Post by Mka on 2009-07-24
Try cleaning the cache and check again how much space is freed
```
sudo apt-get clean && df -h
```

---

### Post by aaryan on 2009-07-24
the space is around 2 gb which was alloted. I need to increase the disc space. Could you please guide me as to how to do it.

---

### Post by frunns on 2009-07-24
Boot up the live-cd and use GParted, should let you resize. But note that things can go terribly wrong when partitioning, so backup anything that's essential.

---

### Post by mikechant on 2009-07-24
Here's my suggestion:
1/ If you have any valuable data in windows or ubuntu, back it up to an external drive or DVD or something if possible. You should be backing up valuable data routinely anyhow so this shouldn't be a problem!
2/ If possible, boot into windows and use its disk management facilities to shrink the large NTFS partition (sda5). Check you can reboot windows OK. Details depend on which version of windows you have. **
3/ Reboot using the Ubuntu Live CD
4/ Start gparted (system->admin->partition management)
5/ sda7 will probably show as in use (padlock). Right click on it and select 'swapoff'. Even though you are not doing anything with sda7 it still needs to be not in use.
6/ Step 2/ should have given you some unallocated space between sda6 and sda7. Right click on sda7, select resize, and then drag the left end of the size box all the way to the left to fill up the space. OK this.
7/ Select 'apply' if you're happy with the new layout (should be no gap between sda6 and sda7 now). When gparted has finished, sda6 should be expanded.

** If you can't shrink sda5 with windows, try defragging it several times first. If you still can't, try shrinking sda5 with gparted. This can sometimes cause the next windows boot to appear to lock up but actually windows is sorting out its filesystem and will boot eventually (in my case it took about 3 hours). In other cases windows may fail to boot and give an error but this can be fixed without a reinstall. These issues are why it's best to shrink windows partitions with windows utilities, not gparted. If windows gives you an option to skip a file system check, don't skip it. 

As you don't have a separate Linux /home, I'd suggest you transfer at least enough space from sda5 to sda6 to make sda6 up to 10Gb, but it all depends on what data you might want to store on the linux partition.

Also, if you do shrink sda5 with gparted, it's probably best to reboot and check/sort out windows before expanding sda6. No point in going on to the next stage if the previous stage has messed up.

---

### Post by mapes12 on 2009-07-24
Hi

I had a similar problem and this worked for me:

[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)

Best wishes.

Mark

---

