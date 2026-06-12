---
title: "Dual-Boot"
date: 2010-11-25
forum: New to Ubuntu
---

### Post by CsG_kieran_2 on 2010-11-25
hey,

How can I dual-boot linux and windows? I have ubuntu installed already and I want to ad widows.

---

### Post by fly-by-night on 2010-11-25
Try this:
[http://ubuntuforums.org/showthread.php?t=1035999](http://ubuntuforums.org/showthread.php?t=1035999)

And more if needed:
[http://www.google.com/search?q=dual+boot+7&sitesearch=ubuntuforums.org](http://www.google.com/search?q=dual+boot+7&sitesearch=ubuntuforums.org)

---

### Post by sikander3786 on 2010-11-25
This one should help.

[https://help.ubuntu.com/community/WindowsDualBoot#Installing%20Windows%20After%20Ubuntu](https://help.ubuntu.com/community/WindowsDualBoot#Installing%20Windows%20After%20Ubuntu)

Please read it and then you'll definitely have some queries that need to be addressed. But only when you ask ;-)

Short answer, install Windows and then re-install Grub2. Windows needs a primary partition BTW.

And please post the output of

```
sudo fdisk -l
```

In order to let us know more about your partitions.

---

### Post by CsG_kieran_2 on 2010-12-02
Its been a random busy week for me so sorry about the wait. :KS

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0001f7bc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60476   485765120   83  Linux
/dev/sda2           60476       60802     2619393    5  Extended
/dev/sda5           60476       60802     2619392   82  Linux swap / Solaris

anything else needed before i try this? :)

---

### Post by wilee-nilee on 2010-12-02
Yes a preformatted partition for Windows, a ntfs partition, you might at the least share which disto your planning to install.

---

### Post by CsG_kieran_2 on 2010-12-02
^i would recommend reading the first post. already have ubuntu.

---

### Post by wilee-nilee on 2010-12-02
> **CsG_kieran_2 said:**
> ^i would recommend reading the first post. already have ubuntu.

And I would recommend actually identifying the distro . Just because it say lucid in your side bar and mentioning Ubuntu means nothing to be quite honest. We have people on here every day who have no clue what they are doing, would you just like some slapshod advice that will possibly bork your system or informed help.

I was also asking for the Windows version, Good bye .

---

### Post by ahmed shabayek on 2010-12-02
hey, i think u should do a clean install of windows deleting ubuntu then u can reinstall it after windows cause as far as i know there was no way to do the other way around thts wat i concluded last year after a long search but who knows maybe they came up with smthin anyway its better to do it the normal way srry but u will have to remove ubuntu  then reinstall it if u need windows

---

### Post by wilee-nilee on 2010-12-02
> **ahmed shabayek said:**
> hey, i think u should do a clean install of windows deleting ubuntu then u can reinstall it after windows cause as far as i know there was no way to do the other way around thts wat i concluded last year after a long search but who knows maybe they came up with smthin anyway its better to do it the normal way srry but u will have to remove ubuntu  then reinstall it if u need windows

[B]Not true most of the time you can reload the MBR quite easily.
[/B]
Maybe the thread starter will realize that two people already posted in this thread who fix this stuff every day on the forum, if not their loss really.

---

### Post by CsG_kieran_2 on 2010-12-02
People get edgy on here I understand. If I have updated ubuntu I would have said but I haven't so its 10.04 LTS 32(bit). And the Version is W7 Ultimate 32(bit)

How this makes a difference I cant see...

---

### Post by oldfred on 2010-12-02
Partitions do not have to be in order. Just shrink sda1 with gparted and create sda3 as NTFS and with the boot flag.

Can also use for shrinking:
Resizing an Ubuntu System Partition
[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)
[http://www.howtoforge.com/linux_resizing_ext3_partitions](http://www.howtoforge.com/linux_resizing_ext3_partitions)

Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

To reinstall the grub2 boot loader:
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by CsG_kieran_2 on 2010-12-02
> **wilee-nilee said:**
> [B]Not true most of the time you can reload the MBR quite easily.
[/B]
Maybe the thread starter will realize that two people already posted in this thread who fix this stuff every day on the forum, if not their loss really.

This is also some what ignorant towards newcomers, thankful your the only one so far :) 

I have achieved Other advice from the forum (w/Version)
Thanks

---

### Post by nm_geo on 2010-12-02
CsG
Be sure to reread oldfred's first line of information that partition information boot flag will save you a world of grief

---

### Post by wilee-nilee on 2010-12-02
Lol.

---

### Post by CsG_kieran_2 on 2010-12-02
Nice :D W7 U is fired up and I have ubuntu working flawless. few years of fedora pay off lol 

Thanks a million guys!   :KS

---

### Post by nm_geo on 2010-12-02
> **CsG_kieran_2 said:**
> Nice :D W7 U is fired up and I have ubuntu working flawless. few years of fedora pay off lol 

Thanks a million guys!   :KS

Excellent now go and get Fedora14 and triple boot and screw it all up like I almost did LOL

---

