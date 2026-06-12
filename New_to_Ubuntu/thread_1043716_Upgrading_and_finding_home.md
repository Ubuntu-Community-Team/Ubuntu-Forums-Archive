---
title: "Upgrading and finding /home"
date: 2009-01-18
forum: New to Ubuntu
---

### Post by quari on 2009-01-18
I've run ubuntu for a little while but still a beginner so I hope this question is OK for this forum.  

I recently upgraded from Hardy Heron to Intrepid Ibex and the upgrade seems to have gone fine, things work etc.  But I used to have my /home dir on a separate partition - it is still there, but the upgrade created a new /home on the primary partition.  

I want to use the old one as /home because it is where all my stuff and settings (bookmarks, mail etc) are.  

How do I point ubuntu back to the old /home? Do I need to copy anything from the new /home to the old one because of the upgrade? Do I need to rename or delete the new /home?

Any help greatly appreciated, especially if you can tell me exactly what commands to use or where to change settings.  Thanks!

quari

---

### Post by linuxisevolution on 2009-01-18
> **quari said:**
> I've run ubuntu for a little while but still a beginner so I hope this question is OK for this forum.  

I recently upgraded from Hardy Heron to Intrepid Ibex and the upgrade seems to have gone fine, things work etc.  But I used to have my /home dir on a separate partition - it is still there, but the upgrade created a new /home on the primary partition.  

I want to use the old one as /home because it is where all my stuff and settings (bookmarks, mail etc) are.  

How do I point ubuntu back to the old /home? Do I need to copy anything from the new /home to the old one because of the upgrade? Do I need to rename or delete the new /home?

Any help greatly appreciated, especially if you can tell me exactly what commands to use or where to change settings.  Thanks!

quari

Simply link the directories, like so:

ls -s /media/home /home/home

---

### Post by quari on 2009-01-19
Thanks linuxisevolution

Unfortunately I have realised I have another problem to solve first - the old home dir is not just a separate partition, its a separate physical drive and it is not being mounted automatically at startup.  Is there an easy way to do this?

quari

---

### Post by vanadium on 2009-01-19
Then you will need to do the more "fundamental" solution anyway, which is mounting the separate partition under /home in your /etc/fstab. This was the way it was before.

It involves adding one line to /etc/fstab. To do it the "modern" way, you would use an UUID instead of a device name. Post the output here of "sudo blkid" and we will be able to tell you how the line will need to look.

---

### Post by quari on 2009-01-19
Ahh! I think thats how it was done before, thanks Vanadium.

Here is what I get:

root@criollo:~# sudo blkid
/dev/sda1: UUID="7de3ac02-046f-46a6-a447-5723577ede88" TYPE="ext3" SEC_TYPE="ext2" 
/dev/sda5: TYPE="swap" UUID="aceea30c-8afd-4a1a-9d3f-0d8765e4a447" 
/dev/sda6: UUID="36f6d2d3-d430-4dbe-99b6-414cfe69e7a1" TYPE="ext3" 
/dev/sda7: TYPE="swap" UUID="8a559f5d-8bdf-482a-82b5-e25437a76b71" 
/dev/sdb1: UUID="3cc33c14-56dd-4cd4-832b-8891e80eed05" SEC_TYPE="ext2" TYPE="ext3" 

I'm pretty sure /dev/sdb1 is the drive I have my old home dir on, and as there is no actual /home on it (just the stuff you find under /home) I guess it was set so that the root dir was /home.  

What do I need to add to fstab? Also, do I need to rename my new /home before I recreate the old one?  Is there anything in the new one that I should migrate back to the old one?  

Thanks so much for the help!

quari

---

### Post by quari on 2009-01-19
I should also point out I don't know why that drive is coming up as /sdb1 instead of /hdb1 - all my drives are ide and I just peeked into fstab and there is a line that says /hdb1 is /home....so maybe fstab is set up ok and its just that 8.10 has decided that all my drives must be scsi?  Not sure...help! 

Its times like these I feel like such a girl.  I'm quite confident using ubuntu but not so good configuring.

quari

---

### Post by b0b138 on 2009-01-19
Umm...if I didn't know any better (which I might not ;)), it looks like you might have 2 installations going on. Can you post the output of ```
cat /boot/grub/menu.lst
```and```
cat /etc/fstab
```

---

### Post by quari on 2009-01-19
Eeep! Thats not a good thought.  Thanks for the idea though, I will be home in an hour or two and will post the output of those two command lines then.  

I did the upgrade from 8.04 to 8.10 from a DVD, it appeared to go well so I just assumed it had overwritten the old install. It did pick up on some programs I had installed in the old version, although not their settings (probably in /home) so I assumed it had melded the two together into one install.

Stay tuned, I'll post that info shortly.

quari

---

### Post by b0b138 on 2009-01-20
Ahhh... since you say you did it from dvd (instead of apt-get dist-upgrade), I bet it either used some unpartitioned space or resized your partition to make room.

Also throw in ```
mount
```and```
sudo fdisk -l
```

---

### Post by b0b138 on 2009-01-20
> 
root@criollo:~# sudo blkid
/dev/sda1: UUID="7de3ac02-046f-46a6-a447-5723577ede88" TYPE="ext3" SEC_TYPE="ext2"
**/dev/sda5: TYPE="swap" UUID="aceea30c-8afd-4a1a-9d3f-0d8765e4a447"**
/dev/sda6: UUID="36f6d2d3-d430-4dbe-99b6-414cfe69e7a1" TYPE="ext3"
**/dev/sda7: TYPE="swap" UUID="8a559f5d-8bdf-482a-82b5-e25437a76b71"**
/dev/sdb1: UUID="3cc33c14-56dd-4cd4-832b-8891e80eed05" SEC_TYPE="ext2" TYPE="ext3"

The 2 swap partitions were highly suspicious ;)

---

### Post by quari on 2009-01-20
OK, here goes with the outputs of some of those commands.  First, a big one, the output of cat /boot/grub/menu.lst


## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-9-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=36f6d2d3-d430-4dbe-99b6-414cfe69e7a1 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=36f6d2d3-d430-4dbe-99b6-414cfe69e7a1 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.24-23-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=36f6d2d3-d430-4dbe-99b6-414cfe69e7a1 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.10, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=36f6d2d3-d430-4dbe-99b6-414cfe69e7a1 ro  single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.10, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda1.
title		Ubuntu, kernel 2.6.20-16-generic (on /dev/hda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=7de3ac02-046f-46a6-a447-5723577ede88 ro quiet splash 
initrd		/boot/initrd.img-2.6.20-16-generic
savedefault
boot

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda1.
title		Ubuntu, kernel 2.6.20-16-generic (recovery mode) (on /dev/hda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=7de3ac02-046f-46a6-a447-5723577ede88 ro single 
initrd		/boot/initrd.img-2.6.20-16-generic
savedefault
boot

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda1.
title		Ubuntu, kernel 2.6.20-15-generic (on /dev/hda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=7de3ac02-046f-46a6-a447-5723577ede88 ro quiet splash 
initrd		/boot/initrd.img-2.6.20-15-generic
savedefault
boot

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda1.
title		Ubuntu, kernel 2.6.20-15-generic (recovery mode) (on /dev/hda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=7de3ac02-046f-46a6-a447-5723577ede88 ro single 
initrd		/boot/initrd.img-2.6.20-15-generic
savedefault
boot

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda1.
title		Ubuntu, memtest86+ (on /dev/hda1)
root		(hd0,0)
kernel		/boot/memtest86+.bin  
savedefault
boot

---

### Post by quari on 2009-01-20
Now fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults                    0  0  
# /dev/hda6
UUID=36f6d2d3-d430-4dbe-99b6-414cfe69e7a1  /              ext3         relatime,errors=remount-ro  0  1  
# /dev/hda7
UUID=8a559f5d-8bdf-482a-82b5-e25437a76b71  none           swap         sw                          0  0  

/dev/hdb1                                  /home          ext3         defaults,relatime           1  0  
/dev/hdd                                   /media/cdrom0  udf,iso9660  user,noauto,exec,utf8       0  0  
/dev/hdc                                   /media/cdrom1  udf,iso9660  user,noauto,exec,utf8       0  0  
/dev/sdb1                                  /media/sdb1    ext3         defaults                    0  0

---

### Post by quari on 2009-01-20
Now what I get from mount:

/dev/sda6 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-9-generic/volatile type tmpfs (rw,mode=755)
/dev/sdb1 on /media/sdb1 type ext3 (rw)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/louise/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=louise)

---

### Post by quari on 2009-01-20
And last but not least, the output of sudo fdisk -l


Disk /dev/sda: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x81138113

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2456    19727788+  83  Linux
/dev/sda2            2457        4866    19358325    5  Extended
/dev/sda5            4666        4866     1614501   82  Linux swap / Solaris
/dev/sda6            2457        4567    16956544+  83  Linux
/dev/sda7            4568        4665      787153+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7ccd4959

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14593   117218272   83  Linux

---

### Post by quari on 2009-01-20
Any help with the above would be greatly appreciated.  There is still plenty of free space on the main file system drive so I don't mind leaving anything as it is if it is just easier but I really want to get my old /home on /dev/sdb1 working.

Thanks so much!

quari

---

### Post by b0b138 on 2009-01-20
You do indeed have both hardy and intrepid installed (congratulations, you're dual booting :D) Which means you can boot into your old hardy.  When you reboot, it should show you what is now a big list. In that list is something that looks like Ubuntu, kernel 2.6.20-16-generic (on /dev/hda1). Thats your old hardy install that has /home where you want it with all your stuff.

The easiest thing to do would probably get booted into hardy, redo the added partitions and add that space back to where it was before (unless you had unpartitioned space anyways). Then from there you can upgrade to intrepid if you want.

Or, you can leave it like it is for now and dual boot. This would give you chance to try intrepid to make sure it works fine for you.

---

### Post by b0b138 on 2009-01-20
Actually, looking again at your menu.lst, it looks like you're triple booting :confused: or kept old kernels???  But in all those entries, kernel 2.6.27-9-generic is intrepid, kernel 2.6.24-23-generic is hardy (but its also pointing to the same partition intrepid is on???) and kernel 2.6.20-15-generic is feisty (had to look that one up)

---

### Post by quari on 2009-01-20
Thanks.

Well Intrepid seems to work fine for me, so I really would like to upgrade.  How do I add the extra partitions back in to the normal ones in Hardy?  And how do I upgrade to avoid this happening again?

quari

---

### Post by quari on 2009-01-20
Another thought, could I keep my current Intrepid setup and just blast away everything in the other partitions?

---

### Post by b0b138 on 2009-01-20
> **quari said:**
> Another thought, could I keep my current Intrepid setup and just blast away everything in the other partitions?

You could, yes.  But, you still wouldn't have your /home on the other drive.  It could be setup to by telling it where /home is, but I'm not sure if there would be any problems from having configuration files from hardy being used in intrepid. Or new ones intrepid is looking for that arent there.  I just don't know :(

If it were me, I would reinstall and redo all the partitions. That way, you could tell it to use the second drive for /home and also tell it NOT to format it that way your stuff is there, and it can add what it needs to.

---

### Post by quari on 2009-01-20
Ok, I just tried to boot back into Hardy and it didnt really work.  So from Intrepid, or from booting the Intrepid DVD, could I reformat my primary drive, repartition it and tell it to leave the other drive alone but make it /home?  I am happy to kill off hardy and feisty and only stuff that needs backup is on second drive.

Will I need to know how much swap space to setup on the first drive?

Sorry about this, I know this is pretty basic stuff.  Thanks heaps for your help.  

quari

---

### Post by b0b138 on 2009-01-20
Yes, boot from the dvd. Select try ubuntu blah blah... After its booted up double click install and go through the steps. When it gets to the partitioning, select MANUAL. You will get something that resembles this [http://johnbokma.com/mexit/2008/08/05/ubuntu-install-prepare-partitions.png](http://johnbokma.com/mexit/2008/08/05/ubuntu-install-prepare-partitions.png)[IMG]http://johnbokma.com/mexit/2008/08/05/ubuntu-install-prepare-partitions.png[/IMG]
but you wont have that many entries. Everything under /dev/sda (sda is your primary drive) you can select and "delete partition". Then the only thing left after that should say unpartitioned.  Select that, select new partition, and make it 38 gigs. (it will probably show the total space available something like 39485. So just take off 2000 from whatever number it says. This will leave around 2 gig for swap) Set the mount point to /  and set it to format.

Now you have to set the swap. Select remaining unpartitioned space, new partition, and set it for swap.

Now select the one partition on /dev/sdb1 and click **EDIT** Set its mount point as /home and make sure **IT IS NOT SET TO FORMAT** 

When thats done and your (hopefully)  back at something that resembles the pic above, **DO NOT CLICK FORWARD OR NEXT** Take a screenshot and post it here so I can check it because at this point nothing is set yet and can be undone.

---

### Post by quari on 2009-01-20
I can't access that pic (access forbidden) but I get the idea.  How do I take a screenshot at that point of the process? 

quari

---

### Post by b0b138 on 2009-01-20
you should be able to hit prtscn on your keyboard. alt-prtscn will get just the active window.  Or you can goto applications>accessories>take screenshot

---

### Post by quari on 2009-01-20
Ahh, I see the pic now, but still don't know how to take a screenshot of my own.

---

### Post by b0b138 on 2009-01-20
Heres an example of what yours should end up looking like.

---

### Post by quari on 2009-01-20
Thanks!

---

