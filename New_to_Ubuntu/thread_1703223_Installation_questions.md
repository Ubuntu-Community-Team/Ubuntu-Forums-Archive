---
title: "Installation questions"
date: 2011-03-09
forum: New to Ubuntu
---

### Post by user_123 on 2011-03-09
Hi everyone,
 
I'm new to Ubuntu, I just have a few questions about installing Ubuntu 10.10.
First, when I booted the Ubuntu CD to install the OS, it asked where should I install the MBR. I have Windows 7 already, so can I boot to Ubuntu from the Windows 7 boot menu, instead of having it replace the Windows 7 boot menu?
Also, I just want to ask if I can install Ubuntu to an NTFS partition, or do I have to use ext2/3/4?
Lastly, how big t=should the swap file be?
 
Thanks

---

### Post by mcduck on 2011-03-09
First, it's not asking you where to install MBR (MBR is the first 512 bytes of your hard drive, so it's noting that could be installed. :D). It's probably asking if it should install the Grub menu into MBR.

If you want to make things easy for yourself, then you should let in install Grub there and use Ubuntu's menu for selecting between Ubuntu and Windows. While it's possible to use the Windows boot menu instead, that's  something you'd have to set up manually as Windows doesn't handle any other operating systems than different Windows versions automatically.

You can't install Linux on a Windows filesystem, like NTFS, they don't support all the features that Linux requires to run. You can still access NTFS partitions, though, so you can use them for storage purposes and to share files between Windows and Linux. Ext4 would be a good choice for your Linux partition(s).

The swap partition should be at least the same size your RAM is. Going much over that isn't usually necessary, unless you have very little RAM on your system it's unlikely that the swap partition would actually be used much at all, apart from if you want to hibernate your computer.

---

