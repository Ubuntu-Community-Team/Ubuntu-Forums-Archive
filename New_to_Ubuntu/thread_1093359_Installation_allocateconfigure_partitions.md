---
title: "Installation: allocate/configure partitions"
date: 2009-03-11
forum: New to Ubuntu
---

### Post by Charles Ingalls on 2009-03-11
Hi there, everyone.

I've recently bought an Asus Eee PC 1000H (the one with 160Gb HDD) and I'm quite happy about it, except for the fact that it comes with Windows XP installed and I'd really like to be able to dual-boot in Ubuntu/WinXP (WinXP being used only once in a while for specific applications).
So I burnt the image file and booted my laptop from it (assuming the desktop i386 8.10 version was the right choice) and started the installation process. When I get to the "Prepare disk page", where I'm supposed to allocate disk space to the new OS: since I'm a complete beginner, I liked the resizing option (like [this]("http://www.psychocats.net/ubuntu/images/installinghardyplus10.png")) but I apparently don't have it (I can choose between "Guided (entire disk)" or "Manual" and in both cases I'm totally lost.

Anyone any idea? That'd be greatly appreciated. Thanks in advance.

---

### Post by martrn on 2009-03-11
Its possible, although I do not know that your hard drive has a 'hidden' partition on your hard drive where it stores its windows installations files.  This happens a lot on new laptops from some manufactures which install windowze on all their computers.  

You should bear that in mind if you install ubuntu be careful to over-right your windowze installation partition.  Windows hides its own drives and partitions from itself sometimes, but if you use a partition software like [http://gparted.sourceforge.net/]("http://gparted.sourceforge.net/"), or simular then you should be able to partition format and move drives and partitions in a similar manner without destroying your windowze installation partition.

I am guessing but use something like gparted [http://gparted.sourceforge.net/]("http://gparted.sourceforge.net/"), to graphically partition your drives before you install if you need something like that to organise your hard drive and that will do the simular thing as the Prepare disk software on your ubuntu CD.

---

### Post by ivanvajar on 2009-03-11
Boot from LiveCD and you will find partitioner. Use it to prepare partition.

Start the installer. When the Ubuntu installer gets to 'Prepare disk' go to manual and mark your new created ext3 as root / and that's it.

---

