---
title: "Need to rescue brand new HDD after gparted mistake"
date: 2009-01-29
forum: New to Ubuntu
---

### Post by ranch hand on 2009-01-29
I got 2 new WD 320GB HDDs.  I put one in my spare tray and fired it up.

Not knowing which SATA SLOT it was in, I turned them all on.  On boot up I got an error saying that SATA 2 and 4 were not detected.  Went back to BIOS and turned off SATA 2 AND 4.

Booted fine.  Pulled up gparted and created 1 partition, extended no file system.
Created an 8 GB partition at the end of that with file system linux swap.

This did not work.  Just got message that it failed to create that partition.

Gparted ground away for several minutes and then came back up with just sda detected.

Tried;
```

slade@slade-desktop:~$ sudo fdisk -lu 

Disk /dev/sda: 320.0 GB, 320072933376 bytes 
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors 
Units = sectors of 1 * 512 = 512 bytes 
Disk identifier: 0x0004630f 

   Device Boot      Start         End      Blocks   Id  System 
/dev/sda1   *          63   292527584   146263761   83  Linux 
/dev/sda2       394925895   625137344   115105725    5  Extended 
/dev/sda3       292527585   394925894    51199155   83  Linux 
/dev/sda5       606887568   625137344     9124888+  82  Linux swap / Solaris 
/dev/sda6       394926021   606887504   105980742   83  Linux 

Partition table entries are not in disk order 

```
and;
```

slade@slade-desktop:~$ sudo sfdisk -d 
[sudo] password for slade: 
# partition table of /dev/sda 
unit: sectors 

/dev/sda1 : start=       63, size=292527522, Id=83, bootable 
/dev/sda2 : start=394925895, size=230211450, Id= 5 
/dev/sda3 : start=292527585, size=102398310, Id=83 
/dev/sda4 : start=        0, size=        0, Id= 0 
/dev/sda5 : start=606887568, size= 18249777, Id=82 
/dev/sda6 : start=394926021, size=211961484, Id=83 
read: Input/output error 

sfdisk: read error on /dev/sdb - cannot read sector 0 
 /dev/sdb: unrecognized partition table type 
No partitions found 

```

Then I thought of trying to see what I could do with a live disk.  Could not read the stuff that scrolled across the screen (too fast for me) but it had to do with sdb.  Would not boot.

Tried to reboot and the normal grub menu came up and I tried to boot to this install (sda6 - 8.10).  Did not work, same deal.

Tried to reboot in rescue mode.  This was interesting if you like a lot of fast scrolling text for several minutes.

I did get some of it;
> 
DRDU ERR
Buffer I/O error on device sdb, logical block 0

and
> 
625142448  512-byte hardware sectors (320073MB)
write protection is off
Write cache: enabled, read cache: enabled, don't support DPO or FUA

When the scrolling ran down I typed exit at which time I was offered the standard choices and tried "return to normal boot".  Here I am.

Gparted sees just sda still, I checked.  The fdisk and sfdisk results are the same also.

What do I do now?  And what did I do wrong?

---

### Post by ranch hand on 2009-02-01
I find it hard to believe that I have done something that noone knows how to fix.  If this keeps up I'll feel mighty proud, if bummed.

---

