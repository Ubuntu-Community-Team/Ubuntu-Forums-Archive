---
title: "partition change in windows... grub unknown filesystem"
date: 2009-11-15
forum: New to Ubuntu
---

### Post by luvgirl12345 on 2009-11-15
i changed the partitions in windows (right click computer, manage) and then restarted thinking it wouldn't cause any problems...

grub error 
unknown filesystem 
grub rescue<

I read somewhere that you had to change grub.config partition tabel...

---

### Post by RJ12 on 2009-11-15
Well your problem is that by resizing a partition you have messed up the UUID (A long string of characters (I believe numbers only)) that is given to a partition depending on its size, location, other stuff. And since you changed the partition the UUID changed causing GRUB not know where it is. Infact I think you have also changed all the other UUIDs to. To correct this you need to boot into a live CD/USB and edit one of the files for GRUB (If your using GRUB2 I have no idea which file) And edit menu.lst (Infact if you have the regular GRUB (The ones that came in the versions of Ubuntu from 9.04 and below) Please post the menu.lst and run blkid in the terminal) if you do have GRUB2 I believe someone else can help you. But for sure you have changed UUIDs and I believe the command to find it is ```
blkid
``` but have that ready and open to copy/paste

---

### Post by sameer.walgude on 2010-03-12
Try this at grub rescue> prompt....

grub rescue> set prefix=(hd0,x)/boot/grub
grub rescue> insmod (hd0,x)/boot/grub/normal.mod
rescue:grub> normal


If still fails...boot up live cd...

at terminal...
sudo grub-setup -d /media/{kubuntu9.10partition}/boot/grub /dev/sda

substitute /media/{kubuntu9.10partition} with actual partition :)

If you get error message,(mapping fails), do this..

sudo grub-setup -d /media/{kubuntu9.10partition}/boot/grub -m 
/media/{kubuntu9.10partition}/boot/grub/device.map /dev/sda

All the best!

Thanks & Regards
Sameer J Walgude
[email]sameer.walgude@aol.in[/email]
+91 98191 15533

---

### Post by srs5694 on 2010-03-12
Chances are the partitions' UUIDs have *not* changed, and even if they have, most GRUB configurations don't use UUIDs, so that's most probably not the issue. Rather, the partition *numbers* have changed. What was /dev/sda3 may now be /dev/sda2, or whatever. Unfortunately, GRUB uses a different addressing scheme, and it varies between GRUB Legacy and GRUB2, so it can get confusing pretty quickly.

I recommend you start by booting a Linux emergency system and obtain a list of partitions on your boot disk. Typing "fdisk -l" at a root shell prompt will do this. You'll need to figure out which is your boot partition, which can be either your root partition (/) or a separate partition that holds only the contents of the /boot directory. If you've got just one Linux partition, that's easy, but if you've got two or more, you may need to mount them and check their contents. Also, most /boot partitions are small (100-200MB), which can help you identify them. Once you've identified it, mount your boot partition. You can then edit /boot/grub/menu.lst (GRUB Legacy) or /boot/grub/grub.cfg (GRUB2) (but note in both cases that the path will be different, depending on where you've mounted it) and edit the partition identifiers, which take the form (hdx,y), with x and y being numbers, to match. In GRUB Legacy, numbering starts with (hd0,0); with GRUB2, it starts at (hd0,1). Thus, /dev/sda1 will most likely be (hd0,0) in GRUB Legacy and (hd0,1) in GRUB2.

Ubuntu's GRUB2 configuration includes some auto-configuration scripts. Specifically, typing "grub-mkconfig" may reconfigure GRUB2; however, you'll need to be booted into Ubuntu for this to work, so you'll either need to find an alternate way of booting Ubuntu (maybe with an Ubuntu install disc) or do some manual reconfiguration, as I've just outlined.

---

### Post by egalvan on 2010-03-12
> **srs5694 said:**
> Chances are the partitions' UUIDs have *not* changed,

If the partition was changed in *any* fashion,
such as shrink, grow, delete/recreate...
then the UUID changed.
The UUID is *unique* to that partition *only*.

>  and even if they have, most GRUB configurations don't use UUIDs, so that's most probably not the issue.

GRUB uses UUID as default to identify / and /boot partitions, since the UUID is unique to the partition.

fstab is another matter... older versions of Linux used sdx.
I change mine to use LABEL identifiers instead of UUID identifiers or sdx identifiers.

>  Rather, the partition *numbers* have changed. What was /dev/sda3 may now be /dev/sda2, or whatever.
**Unfortunately, GRUB uses a different addressing scheme, and it varies between GRUB Legacy and GRUB2, **so it can get confusing pretty quickly.


GRUB Legacy (since Hardy at least) and GRUB 2 both use UUID as default for the boot and grub partition info.

---

### Post by srs5694 on 2010-03-12
The original post specifies a change to partitions in *Windows.* This is unlikely to affect UUIDs of *Linux* filesystems, which is why I think it's a matter of partition numbers rather than UUIDs. (GRUB can use either UUIDs or numbers, and confusingly, my default Ubuntu configurations specify both in different locations.) OTOH, I suppose GRUB could be getting finicky about the UUID of an NTFS partition. In my experience GRUB is more resilient than that, although I can't say I've tried changing the UUID of an NTFS partition in this way, so I've not tested GRUB for this type of problem.

---

### Post by srs5694 on 2010-03-12
> **egalvan said:**
> If the partition was changed in *any* fashion,
such as shrink, grow, delete/recreate...
then the UUID changed.
The UUID is *unique* to that partition *only*.

Actually, this is incorrect, at least when using GParted. I just tested, first with ext2fs and then with NTFS. I resized both partition types using GParted, and the filesystems' UUIDs did *not* change. I tried testing it in Vista, but it didn't want to resize the partition. Perhaps that's a feature that was added to Windows 7, or maybe it wouldn't resize my test filesystem on a USB flash drive. In any event, resizing a filesystem doesn't necessarily change its UUID. I certainly wouldn't rule out the possibility of it happening under certain circumstances or with certain tools, but it's definitely not something that will always happen.

---

### Post by coffeecat on 2010-03-12
> **srs5694 said:**
> Actually, this is incorrect, at least when using GParted.

Agreed. In my experience, using Gparted, UUIDs do not change if you move/resize a partition so long as it keeps the same sda3,4,5 whatever partition number. I moved an NTFS partition and moved + shrank 1 each of an ext3 and ext4 partition recently and none of the UUIDs changed.

---

### Post by egalvan on 2010-03-13
> **srs5694 said:**
> The original post specifies a change to partitions in *Windows.*
 This is unlikely to affect UUIDs of *Linux* filesystems, which is why I think it's a matter of partition numbers rather than UUIDs. 

Yeah, but the OP did not specify if the partitions were Windows or Linux... 
just that the change was done *in Windows*...
 so it got confusing :)

> (GRUB can use either UUIDs or numbers, and confusingly, my default Ubuntu configurations specify both in different locations.)

Again, yes... but you should find that / and /boot are default spec'd by UUID...
 at least that has been my experience with GRUB Legacy.

>  OTOH, I suppose GRUB could be getting finicky about the UUID of an NTFS partition.
 In my experience **GRUB is more resilient than that,** although I can't say I've tried changing the UUID of an NTFS partition in this way,
 so I've not tested GRUB for this type of problem.

As the other poster stated, he tested this and found no UUID change with a resize or move...
 changes which have happened to  me in the past.
it may be he's using a newer version of GRUB than I am...
although I try real hard to always use the latest GRUB...
I use the PartedMagic LiveCD distro for all my disk management...

So looks like some more testing for me... he seems to be on to something that needs verifying ;)

---

### Post by fchartier on 2011-09-17
Hello, 

I have the same pb. I have windows and xubuntu 9.10 on two partition. i wasnt really using ubuntu for a while so i change the partition size to minimum. then i taught about reusing it as it is faster than windows, but the partition was too small to update to the latest version of ubuntu. so in order to change the size, i had to add another small partition first, restart computer, and then i taught that i could change the partition size. I taught i had to go through that process as my partition editing software would not let me do two changes at the same time before having it rebooted. Now when i start my computer it goes straight to 
grub loading
grub rescue>...
i have tried your recommendations, fdisk -l
without success.
any ideas before i reinstall windows in order to try to wipe everything?
thanks
f

---

### Post by drs305 on 2011-09-17
> **fchartier said:**
> Hello, 

I have the same pb. I have windows and xubuntu 9.10 on two partition. i wasnt really using ubuntu for a while so i change the partition size to minimum. then i taught about reusing it as it is faster than windows, but the partition was too small to update to the latest version of ubuntu. so in order to change the size, i had to add another small partition first, restart computer, and then i taught that i could change the partition size. I taught i had to go through that process as my partition editing software would not let me do two changes at the same time before having it rebooted. Now when i start my computer it goes straight to 
grub loading
grub rescue>...
i have tried your recommendations, fdisk -l
without success.
any ideas before i reinstall windows in order to try to wipe everything?
thanks
f

fchartier,

Since this thread is quite old (by computing standards) we would prefer you start a new thread. State your problem and post the contents of RESULTS.txt  It will give us a pretty good idea of what is happening. Also, if you are not running "Grub 2", you may want to include "Grub Legacy" in the title. You can see which grub you are using with "grub-install -v" (Grub legacy is 0.97).

RESULTS.txt is a file created by running the Boot Info Script, which you can get from the "BIS" link in my signature line.

This thread is closed.

---

