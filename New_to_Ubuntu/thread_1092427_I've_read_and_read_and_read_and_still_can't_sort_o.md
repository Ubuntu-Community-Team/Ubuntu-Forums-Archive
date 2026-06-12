---
title: "I've read and read and read and still can't sort out my Hard drives HELP :("
date: 2009-03-10
forum: New to Ubuntu
---

### Post by Fenris_rising on 2009-03-10
Hi all

I am having a bit of a problem. When I first changed to ubuntu 10 months ago one of the problems I had was the auto mounting of 2 internal HDD's. The answer was a program called diskmounter. This added them to my fstab and I could mount/umount the drives at the click of a mouse.

Now last week I decided to do a complete re-install of my Ubuntu OS as I had played around heavil with it and wanted a clean install which once tweaked I could backup with remastersys. All well and good........except diskmounter is no longer accessible so I have been studying hard to see how to do it by hand.

At this point, 3hrs later, I am struggling. I have had partial success, where I can auto mount (it took me a while to get ownership so I could write to the disks) but unmounting had to be done via the terminal. (I'm not averse but am looking for the 'easy option' :D . Another problem is sharing folders on one of the drives (It's my data store) I can share selected folders but they wont stay shared. IE upon reboot they revert so I have to set the shares again.

At this juncture I have now installed disk-manager which I can mount and leave the drives mounted or I can use it to umount the drives. I can write to and from the drives. But Still folders that I mark for sharing revert upon reboot to not shared.

In a nutshell what I want to be able to do/happen is;

Drives to automount to the desktop (they always show under the places menu as they should)
Be able to unmount them with the right click mouse menu.
Share folders and not have to re-share them after a reboot or having unmounted and mounted the drives.

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	defaults	0	0
#Entry for /dev/sda1 :
UUID=c448e25a-e109-4401-97ec-277e831596c5	/	ext3	relatime,errors=remount-ro	0	1
#Entry for /dev/sda5 :
UUID=ad10dbf9-bbe9-4541-b1a2-6696d2df164a	none	swap	sw	0	0
/dev/scd0	/media/cdrom0	udf,iso9660	user,noauto,exec,utf8	0	0

[COLOR="Red"]#Entry for /dev/sdb1 :
UUID=49B4-204B	/media/sdb1	vfat	defaults,utf8,umask=0	0	2

#Entry for /dev/sdc1 :
UUID=7A3B6D386C9918C4	/media/sdc1	ntfs-3g	defaults,locale=en_GB.UTF-8	0	0[/COLOR]
```

Disk manager has added the Entry's for each drive. Do the strings need adjusting? Or are other tweaks required elsewhere? I get the gist of all I have read but I don't seem to be able to piece together the entry string 'I' need to set my drives up correctly. I am sure the solution and method are straight forward it is just me not quite understanding :)

regards

Fenris

---

### Post by Fenris_rising on 2009-03-10
Never mind it has become a bit academic as my sata drive appears to have died :( 

regards

Fenris

---

### Post by Locutus_of_Borg on 2009-03-10
easiest way

apt-get install thunar thunar-volman

add thunar --daemon into startup

use thunar in place of nautilus

mount and unmount through the side panel of thunar

---

