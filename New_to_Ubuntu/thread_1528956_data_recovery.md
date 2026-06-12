---
title: "data recovery"
date: 2010-07-11
forum: New to Ubuntu
---

### Post by navdeep89 on 2010-07-11
need urgent help !!

earlier i had ubuntu on ma desktop, but when i was installing Windows7 on ma PC , d mistake i did was dat i deleted d ubuntu partitions completely n now only those partitions appear on ma PC which i had deleted . the other partitions do not appear in Windows7.
suggest me some solution pleaassseee !!!

---

### Post by IzByFl on 2010-07-11
maybe try gparted live to manage partitions.
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

and here is a video showing how to reinstall grub in case youe ubuntu partition is ok but y just can't load it.
[http://www.youtube.com/watch?v=WtBBl6HvdpM&playnext_from=TL&videos=Dh7CW0cpwvg](http://www.youtube.com/watch?v=WtBBl6HvdpM&playnext_from=TL&videos=Dh7CW0cpwvg)

good luck!

---

### Post by Steve603z on 2010-07-11
> **IzByFl said:**
> maybe try gparted live to manage partitions.
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

and here is a video showing how to reinstall grub in case youe ubuntu partition is ok but y just can't load it.
[http://www.youtube.com/watch?v=WtBBl6HvdpM&playnext_from=TL&videos=Dh7CW0cpwvg](http://www.youtube.com/watch?v=WtBBl6HvdpM&playnext_from=TL&videos=Dh7CW0cpwvg)

good luck!

Linux Partitions normally won't show up under Windows, assuming you didn't format your entire hard drive, your Linux Partitions are probably still there, however, Windows will always screw up the GRUB boot loader, to check that your files are still there, try using a ubuntu live CD, or verify that the partitions are still there using either Ubuntu Live CD or a gparted live CD

if the partition was formatted, it will probably be extremely difficult to recover any data, there is some software out there that can attempt to recover the data, however, if the data was important enough, it might be a good idea to send it to data recovery professionals.

---

### Post by bumanie on 2010-07-11
It would help if you typed correct English so that one could be certain what has happened. However, your title is clear - best to get [testdisk]("http://www.cgsecurity.org/wiki/TestDisk") and carefully read the documentation before going any further. [This]("http://members.iinet.net.au/~herman546/p21.html") may help too.

---

### Post by scottuss on 2010-07-11
I know this probably doesn't help much now, but I'd always advise installing Windows first before Ubuntu in a dual boot situation. That way, Ubuntu will adjust the partitions and set up the bootloader in a nice way as opposed to Windows which will try to nuke both.

---

### Post by Gone fishing on 2010-07-11
I can't quite follow your problem (I don't want to be a grammar nazi but try and be a little clearer) If you have deleted your Ubuntu partition this **can** be recovered Have a look at this

[http://ubuntuforums.org/showthread.php?t=1517401](http://ubuntuforums.org/showthread.php?t=1517401)

My advice:

* First don't do more damage write to the disk make new file systems etc.
* I would suggest downloading Parted magic [http://partedmagic.com](http://partedmagic.com) and using the TestDisk tool.

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

* Now go and have a coffee think about what you need to do before you start.

Good luck

TestDisk is an awesome piece of software I managed to recover not only deleted partitions (quite easy) but corrupted partitions after the PCBSD mangled my partition table with overlapping partitions etc.

---

