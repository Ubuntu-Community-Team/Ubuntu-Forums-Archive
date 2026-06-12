---
title: "Help compile driver for D-Link DFE-530TX+ adapter"
date: 2006-09-11
forum: Networking &amp; Wireless
---

### Post by BarkingSpider on 2006-09-11
Would someone be willing to teach how to actually compile the driver for my D-Link DFE-530TX+ Rev. F adapter? I have successfully added build-essentials and the linux-headers using apt-get. When I typed "make install" I got a number of errors and the files did not create the ".o" driver file.

The instructions on the linux.txt file seem to be wrong (e.g. the instructions say to create a directory named "/temp". I did this, but the "make file" command did hardly anything. When I tried the same command from the /tmp directory, the machine actually tried to compile the driver.

I have attached the tarball containing the driver source, Makefile, and linux.txt files. If you are successful in compiling the file, please share the process I need to follow.

Thanks in advance,

---

### Post by KaiLahteenmaki on 2007-08-09
I also didn't succes with compiling the source on D-Links CDROM

Can you help me getting right driver to my Ubuntu Linux?
Have you made a better driver ?
 

I have installed Ubuntu Linux - KERNEL VERSION IS 2.6.17-10-GENERIC
 
 to my 5yrs old PC. I bought 
D-Link  DFE-530Tx PCI Fast Ethernet card

 to my PC.

When trying to compile the driver (Linux code was on CDRom) , i get many errors, like

-    CONFIG_HZ

-     SHIFT_HZ

Could you send me relevant driver, or sources and Makefile so that I can get driver workng, Thanks in advance !

kind regards,


[email]Kai.Lahteenmaki@welho.com[/email]

---

