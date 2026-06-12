---
title: "NAS-solution with a network-Box"
date: 2007-07-09
forum: Networking &amp; Wireless
---

### Post by Thorun on 2007-07-09
Hi. 
I have read several things about configureing a laptop/pc to be a dedicated LAN-NAS-server e.g. the Tiny-Linux-NAS where a PC can boot on a floppy and run as a NAS-server. 

But. What I'm looking for is something similar to this box:
[http://www.netgear.com/Products/Storage/NetworkStorage/SC101.aspx](http://www.netgear.com/Products/Storage/NetworkStorage/SC101.aspx)

but that would be accessed from both Linux and Windows (any). 
I have found this link:
[http://www.paragon-software.com/fsdt.htm](http://www.paragon-software.com/fsdt.htm)
 and saw the picture (scroll down to mid-page) - and I immideatly fell in love with the box they call "Linux Tiny Server + NTFS 4 Linux Support".
What I'm hoping is, that here exist a box like that. A box that could be plugged into the Switch with a RJ45 cable and where i could/can plug one or more NTFS-formatted harddrives onto. (and then on boot-up on the "tiny linux server-box" it will find the attached USB-harddrives. 


My problem is, that i don't want any PC or laptop running 24/7 as a NAS-server. I want something that uses less electricity e.g. some small box. (and I don't have any old PC's in my home anyway).


What I'm asking is: Do there exist a box as the one in the second link (a box where to i can attach one or more NTFS-formatted USB-harddrives that would be accessible for both Linux and Windows computers on a LAN) - that is byable anywhere?
Or is my only hope to setup a Tiny Linux NAS-server (the floppy-OS) and let the PC/laptop run all day long?



Regards
Rune

Denmark.

---

### Post by t4thfavor on 2007-07-09
A soekris net4801 uses like 15 watts, and has a usb port on it. You can install ubuntu on it and set it up any way you want.  I had one for a short time attached to a 300Gb sata drive (via usb). The only problem is that its pricey (250USD or more).  Other than that you could get the linksys nslu2 which is a tiny linux box that has 2 usb 20. ports for that purpose.  Both would be platform independant since they can either run samba, nfs, ftp or ssh file sharing protocols.  I would probably suggest the linksys though since its cheaper, and has a web interface to configure it through.

---

### Post by Thorun on 2007-07-09
@ 4thfavor

It seems in deed, that the Linksys is the way to go for me. 
But I can't read from anywhere, that it supports Linux. 
In the manual it says:
> 
Appendix B: Using the Storage Link’s Storage
Overview
Supported versions of Windows are:
• Windows 95/98/ME or later
• Windows NT 4.0, Windows 2000
• Windows XP

I know the words says "supported versions of Windows". But there's several installations (in the manual) for windows and stuff, but nothing mentioned about Linux. 
I'm a little bit confused if I can use it with Linux - and how it's setup in Linux. Because they don't mention anything about that in the manual.....

---

### Post by Thorun on 2007-07-12
> Both would be platform independant since they can either run samba, nfs, ftp or ssh file sharing protocols. I would probably suggest the linksys though since its cheaper, and has a web interface to configure it through.

Does this mean, that i can have access to the box with both Windows XP and my new Linux Ubuntu FF ??

I'm wery much in doubt and I will not buy the box before I'm 100% certain that it can be accesed with both Linux and Windows.

---

### Post by magicfab on 2008-06-13
Regarding the sc101 Netgear box, it works fine for me in Hardy with the nbd module. See:
[http://ubuntuforums.org/showpost.php?p=4151832&postcount=15](http://ubuntuforums.org/showpost.php?p=4151832&postcount=15)

If you'd like to know if/when this makes it into Ubuntu, please subscribe to this bug:
[https://bugs.edge.launchpad.net/ubuntu/+bug/213744](https://bugs.edge.launchpad.net/ubuntu/+bug/213744)

Cheers,

---

### Post by t4thfavor on 2008-06-27
Sorry for leaving this so long, I have been away. The Linksys works fine under linux as its a standalone device. There are no drivers, it will work just like its a full blown PC file server.

---

