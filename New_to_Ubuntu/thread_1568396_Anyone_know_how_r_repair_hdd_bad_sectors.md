---
title: "Anyone know how r repair hdd bad sectors ??"
date: 2010-09-05
forum: New to Ubuntu
---

### Post by Tracy177 on 2010-09-05
ubuntu 10.04 i checked disk mgr and i foud info about hhd that it has a few bad sectors.
 
i tried to run a test but it fails.
 
is there any chance to repair those bad sectors without formating hdd ?

---

### Post by cogier on 2010-09-05
Even reformatting the hard drive will not repair bad sectors. Bad sectors are marked as bad as they are unusable. Modern disks do not normally have bad sectors these days.

If you have more that a couple of percent bad then you may be heading for disk failure - Back it up!

---

### Post by Tracy177 on 2010-09-05
> **cogier said:**
> Even reformatting the hard drive will not repair bad sectors. Bad sectors are marked as bad as they are unusable. Modern disks do not normally have bad sectors these days.
 
If you have more that a couple of percent bad then you may be heading for disk failure - Back it up!
 
 
modern disks :) the disk i hae is year old wdc blue 
 
i know i cant repair but the thing is that if ubuntu or part of it i isnatalled in a bad sectors it will boot slower work slower right ?
 
even solid sate disks will have bad sectors

---

### Post by Kyluke on 2010-09-05
Check out
[http://www.hiren.info/pages/bootcd](http://www.hiren.info/pages/bootcd)
(Download URL) [http://www.hirensbootcd.net/download.html](http://www.hirensbootcd.net/download.html)
I'm a pc technician and I use that at work.

HDAT2 4.53 & Hard Disk Regenerator are the two tools I use to fix bad sectors on a disk.

The process might take a long time but in my experience it has fixed the hard drives.
Plus there are bunch of other very handy tools on that disk.

Simply download the software, burn the ISO to a CD and boot from the CD.

---

### Post by Jazzy_Jeff on 2010-09-05
You can download a program from Western Digital to test your drive to see if it is on it's way out. While it is true all hard drives have bad sectors, if it is getting too many the hard drive may fail soon. Better to be safe than sorry.

---

### Post by da burger on 2010-09-05
Hey I don't know if this is still relevant but I think a while ago I heard something about disk manager giving false positives about bad sectors. You might want to read up on that before trying to any repairs. (Of course you should already have a backup of any data you can' afford to lose, if you don't look into something simple with rsync now).

---

### Post by Tracy177 on 2010-09-05
> **da burger said:**
> Hey I don't know if this is still relevant but I think a while ago I heard something about disk manager giving false positives about bad sectors. You might want to read up on that before trying to any repairs. (Of course you should already have a backup of any data you can' afford to lose, if you don't look into something simple with rsync now).


i have western digital hdd 500gb (widows files and ubuntu) other internal has 320gb (windows) the same western digital.  the external is connected trought sata.

internal doesnt show any bad sectors just the external one. i tried to use tool from western digital and it fail to test smart the same if i scan using windows tool.

in the tool from WDC is thing to scan and repair bad sectors so i started it completed it, took about 2 hours than there shwoed info if i want to reapir bad sectors i pressed yes it showed some error and didnt repair dont know why.
maybe it is cuz of i have on that hdd ubuntu and other windows files. 

i dont want to remove ubuntu and than repair it and install ubuntu again it will take me a week to do that:)

i also tried tool from win 7 dvd there is an option to scan and repair that one took to scan about half a day at the end didnt show any errors. 

just under ubuntu and tool from western digital show a few bad sectors


the 500gb hdd is just year old 
and the internal hdd is 4 months old


i have one more question !!!

can i copy all ubuntu and wondows  files from 500gb hdd to 320gb hdd than format that drive  use the tool from west digit scan it repair it and than copy and paste all this ubuntu and windows files back to 500gb hdd. will it work ? will ubuntu boot after i restart ?   and the other thing i have made a pertition on 500gb hdd the partition has 50gb but i cant see it under windows.

---

### Post by L Campbell on 2010-09-05
> **Kyluke said:**
> Check out
[http://www.hiren.info/pages/bootcd](http://www.hiren.info/pages/bootcd)
(Download URL) [http://www.hirensbootcd.net/download.html](http://www.hirensbootcd.net/download.html)
I'm a pc technician and I use that at work.

HDAT2 4.53 & Hard Disk Regenerator are the two tools I use to fix bad sectors on a disk.

The process might take a long time but in my experience it has fixed the hard drives.
Plus there are bunch of other very handy tools on that disk.

Simply download the software, burn the ISO to a CD and boot from the CD.

Hi, when I go to the download page I cannot seem to find how to download the file.

Help please.

TIA

---

### Post by bkratz on 2010-09-05
Go to where it says

+ Direct HTTP Mirror + Torrent + Torrent Magnet

at the bottom and select one.  I had trouble finding it too!!

---

### Post by realzippy on 2010-09-05
[I]can i copy all ubuntu and wondows files from 500gb hdd to 320gb hdd
[/I]

Have to run a LiveCD,then you can do it with dd:

dd if=/dev/sda of=/dev/sdb  

dumps sda to sdb. Details about DD (DiscDump):

[http://www.linuxquestions.org/linux/answers/Applications_GUI_Multimedia/How_To_Do_Eveything_With_DD](http://www.linuxquestions.org/linux/answers/Applications_GUI_Multimedia/How_To_Do_Eveything_With_DD)

       ----------------------------------------------------------------

[I]...has 50gb but i cant see it under windows.
[/I]

Windows cannot read the linux filesystem,but Linux can read NTFS.

---

### Post by philinux on 2010-09-05
> **Tracy177 said:**
> ubuntu 10.04 i checked disk mgr and i foud info about hhd that it has a few bad sectors.
 
i tried to run a test but it fails.
 
is there any chance to repair those bad sectors without formating hdd ?

How many bad sectors?

---

### Post by 3rdalbum on 2010-09-05
The disk contains some spare sectors. If you start getting bad sectors, the disk will automatically copy the data from that sector to a spare sector.

If you start getting bad sectors then the disk is on its way out. If it runs out of spare sectors, then your disk won't just be "slower" - it will start losing your data, which is not what you want.

Bad sectors cannot be repaired.

Back up all your data and put the disk into the bin.

---

### Post by da burger on 2010-09-05
> **realzippy said:**
> [I]can i copy all ubuntu and wondows files from 500gb hdd to 320gb hdd
[/I]

Have to run a LiveCD,then you can do it with dd:

```
dd if=/dev/sda of=/dev/sdb
```

Surely that command won't work since the receiving drive is smaller than the source drive.

---

### Post by L Campbell on 2010-09-05
> **bkratz said:**
> Go to where it says

+ Direct HTTP Mirror + Torrent + Torrent Magnet

at the bottom and select one.  I had trouble finding it too!!



Thanks, that worked perfectly.

---

### Post by philinux on 2010-09-05
[http://en.wikipedia.org/wiki/Bad_sector](http://en.wikipedia.org/wiki/Bad_sector)

---

### Post by realzippy on 2010-09-05
> **da burger said:**
> Surely that command won't work since the receiving drive is smaller than the source drive.

..thats why the next line (you did not quote) contains the link to


[http://www.linuxquestions.org/linux/...ything_With_DD](http://www.linuxquestions.org/linux/...ything_With_DD)

Anyway edited the post,preventing anybody to run this command (meant as "concept") without
having read the link to discdump.
Thanks.

---

### Post by philinux on 2010-09-05
Lets just take a reality check here. A few bad sectors don't mean a disc is dying. If they are increasing on say a daily basis then I would back up and replace the drive.

---

