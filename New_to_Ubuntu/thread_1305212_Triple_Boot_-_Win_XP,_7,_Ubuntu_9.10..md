---
title: "Triple Boot - Win XP, 7, Ubuntu 9.10."
date: 2009-10-29
forum: New to Ubuntu
---

### Post by PhoenixTank on 2009-10-29
Hi all,
I am attempting to get GRUB2 triple booting XP, Win 7 and Karmic, and so far so good, but it isn't quite there. I have googled, attempted to familiarise myself with the docs and searched in this forum, but nothing has come up that gets me any further.

So, I have 3 harddrives and installed XP, then 7, then Ubuntu each to the first partition on each of the drives. GRUB loads and I have the option to boot Ubuntu and the Windows 7 loader (which then gives me the choice of XP or 7). While this works, I'd really like to cut out the intermediary step and have GRUB entries for each.
[Why? XP loves deleting my Win7 restore points and apparently GRUB has the functionality for me to hide the Win 7 partition from XP on boot. One thing at a time, though.]

Result of fdisk -lu
```
Disk /dev/sda: 300.1 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders, total 586114704 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x170a1709

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    73400984    36700461    7  HPFS/NTFS
/dev/sda2        73400985   586099394   256349205    f  W95 Ext'd (LBA)
/dev/sda5        73401048   125837144    26218048+   7  HPFS/NTFS
/dev/sda6       125837208   544137614   209150203+   7  HPFS/NTFS
dev/sda7       544137678   586099394    20980858+   7  HPFS/NTFS

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x25588350

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1        54540738   488392064   216925663+   7  HPFS/NTFS
/dev/sdb2              63    42540119    21270028+  83  Linux
/dev/sdb3        42540120    54540674     6000277+  82  Linux swap / Solaris

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x187d8464

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1       157420935   313026524    77802795    7  HPFS/NTFS
/dev/sdc2       313026525  1953520064   820246770    7  HPFS/NTFS
/dev/sdc3              63   157420934    78710436    7  HPFS/NTFS

```I do have other partitions as above, but they are only for sharing and storing (and shouldn't matter, right?).
The naming order is somewhat messed up but:
/dev/sda1 = XP, /dev/sdb2 = Ubuntu, /dev/sdc3 = Win7

All help and pointers appreciated, but please note that removing XP is not an option for me.
Thanks!

---

### Post by phillw on 2009-10-29
A couple of pointers ....

[http://raviratlami1.blogspot.com/2009/01/how-to-dual-triple-boot-windows-7-with.html](http://raviratlami1.blogspot.com/2009/01/how-to-dual-triple-boot-windows-7-with.html)

another triple boot, although not win7.

[http://lifehacker.com/193474/hack-attack-how-to-triple+boot-windows-xp-vista-and-ubuntu](http://lifehacker.com/193474/hack-attack-how-to-triple+boot-windows-xp-vista-and-ubuntu)

Are by people who have done it.

The secret seems to be XP 1st, then Win7 (which will see XP) and then ubuntu (which will see them both)

Hope they are of help.

Phill.

---

### Post by hotmail@yahoo.com on 2009-10-29
I am also in the same boat. 

First Install: Win vista
Second install : win xp (new partition)
Third install: Removed vista and installed Win7 where win vista was.
forth install: planning to install ubuntu 9.10 

I hope I can run all the them. Lets see.

I posted my question an hour ago but my thread is lost now lol! Still searching for it. may be they moved it and in this forum there is nothing that says where you have posted :/

---

### Post by PhoenixTank on 2009-10-29
> **phillw said:**
> 
The secret seems to be XP 1st, then Win7 (which will see XP) and then ubuntu (which will see them both)
Agreed, and luckily, that is what I did but, as I posted, I am wanting to take it one step further have menu entries for XP and 7 in GRUB, instead of letting the Win7 loader deal with it. Unfortunately I don't really understand legacy grub completely, and converting some of the examples (that I don't understand) to GRUB2 is a bit of a stretch.
Thanks for the links, but I have seen a few of those before and am don't think they are much use to me.

[EMAIL="hotmail@yahoo.com"]hotmail@yahoo.com[/EMAIL]
I figure you should be fine with that - the install order is close to what I just did.

---

### Post by grafted_scion on 2009-10-30
I also ran into problems
I installed karmic fresh over older ubuntu already had a xp partition.
Then decided to install windows 7 on the same drive.
Wasn't thinking about that it was grub2 and i knew nothing about restoring it.
Searching in the forum only made me aware that i was not the only one with grub2 problems.
Then i found this link [http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html](http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html)
So im back now i only have to figure out how to get grub2 to add the win7 partition :p

---

