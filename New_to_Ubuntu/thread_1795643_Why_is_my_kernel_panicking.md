---
title: "Why is my kernel panicking?"
date: 2011-07-03
forum: New to Ubuntu
---

### Post by shimmshaw on 2011-07-03
Laptop has been running ubuntu 10.10 for six months or so just fine. But today when I opened it to wake up from hibernation, it told me: 'kernel panic - not syncing vfs unable to mount root fs is on unknown block (0,0)'.Restarting it doesn't change anything.

this is my computer: [http://www.gateway.com/systems/product/529668522.php](http://www.gateway.com/systems/product/529668522.php)
the only trouble I've had was a problem with the graphics driver when i first installed it, and it was working fine just fifteen minutes before. What did I do to cause this? How do I get the computer back?

---

### Post by sam_delta on 2011-07-03
does it panics at every boot now? or just everytime you wake up from hibernation?

sam

---

### Post by shimmshaw on 2011-07-03
Every time I try to start it up, it gives me this message. I can't get past the grub menu thing.

---

### Post by sam_delta on 2011-07-03
you did an update lately?
in the grub menu, do you have other kernel options to boot from? if yes, try booting an older kernel.

sam

---

### Post by ian dobson on 2011-07-03
Hi,

Boot from a livecd and check your filesytem. Sounds like the kernel can find your rootfs.

Regards
Ian Dobson

---

### Post by shimmshaw on 2011-07-03
I don't think it's because of an update, last update I did was last week or so. I've tried booting the oldest version, it did a disk check and told me there was an error in drive /. Should I try all the other ones too?
 I could boot from my live cd but I honestly have no idea what to check for once I do :oops: Where do I look and what am I looking for exactly? Sorry for being so clueless...

---

### Post by nandesh on 2011-07-03
> **sam_delta said:**
> you did an update lately?
in the grub menu, do you have other kernel options to boot from? if yes, try booting an older kernel.

sam
thanks i am facing same problem & u have given me a sulution

---

### Post by sam_delta on 2011-07-03
@nandesh, no problem, glad it worked :)

@shimmshaw, boot the live cd and try mounting the root partition or do a fsck on the root partition to see if there is any problem with it.

To mount it, it should mount automatically or appear under "places".
To do a fsck (fsck will check that the file system has no errors, and fix them if posible). type in a terminal ```
 sudo fsck device 
``` where device is the partition you want to check (e.g. /dev/sda1), if your unsure of what is the device name of your root partition, post the output of ```
sudo fdisk -l
``` here.

sam

---

### Post by shimmshaw on 2011-07-03
I see a 500 GB filesystem under places. when i try clicking on it, it  give me an error: '/dev/sda/1 already mounted or  /media/b4e31656-0386-4f3d-9064-e39748e5dc40 busy'. 

I'm having trouble connecting it to the internet, but when I typed sudo fdisk -l it gives me 3 devices and some numbers on them:
/dev/sda1 (linux)
/dev/sda/2 (extended) 
/dev/sda/5 (linux swap/solaris)

dev/sda/1 would be the root partition, yes? So i started the fsck on that one. 

in pass 2: checking directory structure, it says: 
'error reading block 112730197 (attempt to read block from filesystem  resulted in a short read) while reading directory block' and asks if I  want to ignore it (I said yes to continue), then if i want to force  rewrite.  do i tell it yes?

---

