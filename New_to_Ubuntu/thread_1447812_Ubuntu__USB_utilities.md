---
title: "Ubuntu  USB utilities"
date: 2010-04-05
forum: New to Ubuntu
---

### Post by 3948ctyj on 2010-04-05
whats a good comprehensive USB utilitiy for UBU..???  for formatting usb, erasing USB, 
reinstalling U3,   all kinds of stuff.....??

---

### Post by zeroseven0183 on 2010-04-05
My 2GB USB flash drive once have this U3 software and it consumes a little bit of space (which I might need in the future). So I decided to uninstall it using this [http://u3uninstall.s3.amazonaws.com/U3Uninstall.exe](http://u3uninstall.s3.amazonaws.com/U3Uninstall.exe) when I was using Windows back then.

Anyway, you can use GParted to format your USB drive. It's in the Ubuntu Software Center (repositories) but of course it doesn't have the ability to reinstall U3.

---

### Post by egalvan on 2010-04-05
> **3948ctyj said:**
> whats a good comprehensive USB utilitiy for UBU..???  for formatting usb, erasing USB, 
**reinstalling U3**,   all kinds of stuff.....??

Last I used it (back in 2009) U3 was strictly a Microsoft Shop.

As for USB utilities...

Disk Partitioner (gparted) will erase, partition, format, etc...

There ARE command-line versions of these functions... is this what you are looking for?

---

### Post by mikewhatever on 2010-04-05
I don't think there is a need for something USB specific. In Karmic, there are Gparted and Disk Utility, and U3 will probably require Windows.

---

### Post by 3948ctyj on 2010-04-05
whats the command to erase USB???

---

### Post by mikewhatever on 2010-04-05
> **3948ctyj said:**
> whats the command to erase USB???

You can't. It's sort of like saying, "How do I delete the CPU". It's hardware, you can melt or crush it, but not erase.;)
In case you wanted to delete a partitions on a USB hdd, or in fact, any partition, and you must use command line, try fdisk.

---

### Post by oldefoxx on 2010-04-06
If you just need to delete information about what has been placed on any drive, you can use gparted or any partitioning software and ask for a new partition table.  Instantly, the drive appears empty, no partitions or anything.

If you want to ensure that the contents are really gone, you have to overwrite everything on the drive with something without meaning, such as some random pattern.  It is argued that initial magnetic impressions leave some tracings of what they were, so it is argued that you may have to do this repeatedly seven times or more.  That could take quite awhile.

People have different ideas about how much their information has to be protected and why, but the real thing here is to not let the hard drive go without some cleaning, otherwise someone else will now have access to some of that information, and that is probably not a good thing.

---

