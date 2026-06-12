---
title: "Is there a way to save a copy of your bottable usb drive?"
date: 2009-08-02
forum: New to Ubuntu
---

### Post by virtualsamana on 2009-08-02
I saw this product for windows and wondering if there was something for Ubuntu that allowed you to save a copy of your own configured persistent live bootable UST onto another USB drive. I would be nice to have another copy of my system. 


[http://www.paragon-software.com/home/db-express/index.html](http://www.paragon-software.com/home/db-express/index.html)

---

### Post by lisati on 2009-08-02
I came to this thread out of curiosity about "bottable" usb drives......

Perhaps others might come up with a better method, but my thought would be that one way is to make a "custom" live CD using [Remastersys]("http://www.geekconnection.org/remastersys/remastersystool.html"), and then use the "usb startup disk creator" to put it on to USB drive.

---

### Post by niteshifter on 2009-08-02
Ok, I'm confused: You ask about copying USB to USB, but give a link to yet another backup utility for a Win box hard drive system.

So I'll give it a shot at untangling these two very different things ;)

As to copying an install of Ubuntu to a USB thumb drive, with persistence, it's as simple as running the dd command:
```
dd if=/dev/sdX of=/dev/sdY
```
where /dev/sdX is the device name of the "source" USB drive and /dev/sdY is the device name of the USB drive you wish to copy to. I said thumb drive above, that command will work on USB external hard drives - if you're patient. For 1, 2 4GB flash drives it completes reasonably quick (minutes). For a 1TB external - you'll be waiting hours.

Note that you'll do this NOT from the flash drive, use a box with Ubuntu on it (or booted from a Live CD) and unmount both drives after you plug them in.

Note also the drive should be the same size as it's a byte for byte copy. Not that there's anything wrong with having a copy drive that's larger - obviously it can't be smaller - but for example a 2GB source copied to a 4GB will appear as a 2GB. You could reclaim the extra 2GB with gparted - but then it wouldn't be an exact copy.



As to backup solutions sporting USB boot recovery: I do exactly that via System Rescue CD (on a USB thumb drive) and use partimage to do a full backup to an external USB connected hard drive. An Ubuntu Live CD could also be used, I prefer the System Rescue CD because it's a Swiss Army Knife of system recovery tools, the Ubuntu Live CD is somewhat limited (can't run totally in RAM, for example).

---

