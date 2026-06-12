---
title: "ndiswrapper, Hoary: Operation not permitted"
date: 2005-03-25
forum: Networking &amp; Wireless
---

### Post by zardoz on 2005-03-25
As some others here, I too have problems getting an usb wlan adapter to work with ndiswrapper under hoary.

When I execute (as root!) "modprobe ndiswrapper" I get the following error message:
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.10-4-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation not permitted 

I tried this, with the ndiswrapper package from Hoary and also with the self-compiled actual version 1.1 from sourceforge. Same Error.

Some guys reported that everything went fine until they updated from Warty to Hoary. So it seems to be a Hoary specific problem. (Have not checked this myself).

Is there a solution for that problem right now?

---

### Post by rob martin on 2005-03-25
I had this problem too.  Here's how I got it work, 
I got the latest ndiswrapper source from here [http://sourceforge.net/projects/ndiswrapper/](http://sourceforge.net/projects/ndiswrapper/) and following the posting here [http://ubuntuforums.org/showthread.php?t=16868&highlight=ndiswrapper+deb](http://ubuntuforums.org/showthread.php?t=16868&highlight=ndiswrapper+deb) simply did sudo make deb and installed the packages using dpkg -i.  
It didn't work, as the new deb package placed the new ndiswrapper kernel module in /lib/modules/2.6.10-5-686/misc  rather than work out why, and as a quick and dirty hack, I just copied the new ndiswrapper.ko to /lib/modules/2.6.10-5-686/kernel/drivers/net/ndiswrapper/ndiswrapper.ko

then did a sudo modprobe ndiswrapper

make sure you back up the original ndiswrapper.ko to another place, so if it doesn't work, you can always drop it back in, without the need to reinstall the kernel image ;)

It'll work for now, but it's not pretty, every time you upgrade the kernel package you'll have to repeat the process.  

You could always wait a few days and get a fixed up ndiswrapper deb from Hoary.

hope this helps

---

### Post by zardoz on 2005-03-25
Ok, I got the ndiswrapper work under Warty, but my USB Wlan device still doesn't work.  The ndiswrapper loads the .inf driver, but it doesn't show up in iwconfig.
Seems to be, that my driver just don't work with ndiswrapper.
(Device: Siemens Wlan USB Adapter 11MBit)
I try now the atmelwlandrivers again.
Thanks.

---

### Post by Randabis on 2005-03-27
[QUOTE=zardoz]Ok, I got the ndiswrapper work under Warty, but my USB Wlan device still doesn't work.  The ndiswrapper loads the .inf driver, but it doesn't show up in iwconfig.
Seems to be, that my driver just don't work with ndiswrapper.
(Device: Siemens Wlan USB Adapter 11MBit)
I try now the atmelwlandrivers again.
Thanks.[/QUOTE]
 Atmel chipsets do not work with ndiswrapper. Use the native linux drivers.

---

### Post by calvinhopst on 2005-06-18
[QUOTE=zardoz]As some others here, I too have problems getting an usb wlan adapter to work with ndiswrapper under hoary.

When I execute (as root!) "modprobe ndiswrapper" I get the following error message:
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.10-4-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation not permitted 

I tried this, with the ndiswrapper package from Hoary and also with the self-compiled actual version 1.1 from sourceforge. Same Error.

Some guys reported that everything went fine until they updated from Warty to Hoary. So it seems to be a Hoary specific problem. (Have not checked this myself).

Is there a solution for that problem right now?[/QUOTE]


That was it:

[http://www.debianforum.de/forum/viewtopic.php?p=269823](http://www.debianforum.de/forum/viewtopic.php?p=269823)

I had the problem too. I must have forgotten to remove all of the old ndiswrapper installation, so there was already a driver loaded. After removing this driver (in my case bcmwl5) and reloading everything was fine.

---

