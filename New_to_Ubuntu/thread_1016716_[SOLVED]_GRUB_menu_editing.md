---
title: "[SOLVED] GRUB menu editing"
date: 2008-12-20
forum: New to Ubuntu
---

### Post by lernatix on 2008-12-20
I have dualboot working thanks to this site.
However,  one little niggling issue remains.

On startup I get the OS choice (XP,Ubuntu,Ubuntu-Recovery)
If I select either Ubuntu, loads up fine.

When I select XP, I get ANOTHER menu asking if 
I want XP or Ubuntu.  It's not a big deal really.

Just curious if anyone would have the time to look
at my menu.lst file and recommend some edits.

Thanks.

---

### Post by lovelyvik293 on 2008-12-20
You have two hardisks.And each having there grub.
You have the xp on harddisk 1 and the hard disk two have the ubuntu.

---

### Post by hexanol on 2008-12-20
Could you post the result of
```
sudo fdisk -l
```
I believe that if your XP partition is really the first partition of your first hard drive, if shouldn't go to another grub screen before booting.

---

### Post by lernatix on 2008-12-20
Yes, here's the Fdisk

> Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0b170b17

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9728    78140128+   7  HPFS/NTFS

Disk /dev/sdb: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x96c796c7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        2327    18691596   83  Linux
/dev/sdb2            2328        2434      859477+   f  W95 Ext'd (LBA)
/dev/sdb5            2328        2434      859446   82  Linux swap / Solaris


Thanks

---

### Post by hexanol on 2008-12-20
Hum, well, I don't see anything abnormal in this. (also, next time, please post the result of a command in a "code" tag instead of a "quote" tag :))

Couldn't help you more. I'm not the most knowledgeable of grub, but maybe you could try to enter the command via the grub command line to see if there's something wrong with the menu.lst file or if it has to do with somethine else. When you are in the grub menu screen, hit the 'c' button, this will bring you in the grub command line. Next, enter
```
grub> root (hd0,0)
grub> makeactive
grub> chainloader +1
```
where *grub>* is the prompt used by grub.
If you don't get another grub menu with this, then the problem is with your menu.lst file. If you do get another grub menu, well, I really don't know then. :)

---

### Post by unutbu on 2008-12-20
When you select Windows, are you seeing a second menu like the one on this page:
[http://www.computerhope.com/issues/ch000492.htm](http://www.computerhope.com/issues/ch000492.htm)

If so, you need to edit your boot.ini file on Windows.

---

### Post by lernatix on 2008-12-20
You might be onto something there unutbu...

I also get an error when windblows loads,

XNMT 2002 failed to load.

---

### Post by unutbu on 2008-12-20
Hm. I really don't know much about Windows. Does this help? (Search for XMNT):
[http://www.tek-tips.com/viewthread.cfm?qid=439106&page=2](http://www.tek-tips.com/viewthread.cfm?qid=439106&page=2)

The above link was found here:
[http://www.velocityreviews.com/forums/t219494-error-message-xmnt-2002.html](http://www.velocityreviews.com/forums/t219494-error-message-xmnt-2002.html)

> brogan (TechnicalUser)	12 Dec 04 12:30
NOTE - For anybody who has partitioned their hard drive and receive the following errors using Partition Magic:
"xmnt2002 not found skipping autocheck"
"autochk not found skipping autocheck"

and can access the Linux partition but not the Windows.

Find the [menu.lst] in [/boot/grub]. The Windows partition may look like this depending on what you named your partition and which hardrive you are using:
title XP
    rootnoverify (hd0,0)
    chainloader +1
 
Change it to:

title XP
    unhide (hd0,0)
    rootnoverify (hd0,0)
    chainloader +1

Save it and now you will be able to access Windows.
The things in brackets [...] are my edits.

---

### Post by lernatix on 2008-12-20
OK cheers.  I think I may have copied Partition Magic straight from
my old windows ME laptop. (missing file in system)

Thanks again, I'll spend some time with my boot.ini file later.


This is obviously a windows problem so I'll leave it there.

---

