---
title: "Status of zd1201"
date: 2005-04-11
forum: Networking &amp; Wireless
---

### Post by tonysze on 2005-04-11
I wonder if support for zd1201 based USB wireless is going to be available for Hoary?

That's because I've been using Ubuntu for a while, everything works well except my wireless and I'd like to ditch my XP partition as soon as the wireless is ready.

Thanks!!

---

### Post by philcolbourn on 2005-04-11
I am using a zyair b-220 which I think is a zd1201 device (the windows driver is zd1201u) which works under ndiswrapper.

I downloaded the zd1201 driver files from sourceforge and compiled a kernel module and it works (i am using it now)

[http://linux-lc100020.sourceforge.net/](http://linux-lc100020.sourceforge.net/)

I think i read that it is in 2.6.12 now.

---

### Post by tonysze on 2005-04-14
I tried ndiswrapper, but as soon as I inserted the USB wireless key, the mod seems to hang, so ndiswrapper -l would hang until I remove the USB wireless key, I checked dmesg there is some errors with "hald" and an error code of -110, and if I check iwconfig I can see no wlan0.

I have to use ndiswrapper 0.12rc2 included in the Ubuntu installer because I cannot connect to ethernet easily in my house (the Airport Express doesn't have a LAN port). I wonder if you have used 1.1 with the new kernel you built yourself?

---

### Post by philcolbourn on 2005-04-18
[QUOTE=tonysze]I tried ndiswrapper, but as soon as I inserted the USB wireless key, the mod seems to hang, so ndiswrapper -l would hang until I remove the USB wireless key, I checked dmesg there is some errors with "hald" and an error code of -110, and if I check iwconfig I can see no wlan0.

I have to use ndiswrapper 0.12rc2 included in the Ubuntu installer because I cannot connect to ethernet easily in my house (the Airport Express doesn't have a LAN port). I wonder if you have used 1.1 with the new kernel you built yourself?[/QUOTE]
 I assume you installed the windows drivers.

I didn't build a kernel. I just built the module and moved it into the /lib/modules/xxx/extra from memory. I could post it if you like.

apart from some video files, I am using standard hoary.

---

### Post by tonysze on 2005-04-23
Thanks for all your replies, I had finally made it working by downloading the kernel source,  and compiling the zd1201 native driver. According to the information in some places, the first times the driver is loaded it would always complain about not able to find the firmware file. Removing the driver and loading it again solves the problem.

I'm using version 0.14 of that zd1201 driver from this site:
[http://linux-lc100020.sourceforge.net/](http://linux-lc100020.sourceforge.net/)

I'm now waiting for either an update which can fix the problem, but so far, I can use it.

---

### Post by ghaspias on 2005-04-28
I installed the kernel headers, got the drivers from the sourceforge project (v. 0.14), but make complains that it can't find ieee802_11.h.
Do I need to get th full linux kernel source?

I managed to compile by putting the missing file from the sourceforge cvs, but when I do modprobe zd1201 the module is not found (make install placed zd1201.ko in /lib/modules/2.6.10/extra/).
Can anyone help me with this?

---

### Post by tonysze on 2005-04-29
1. You need the full kernel source to compile the zd1201.ko
2. You need to copy the .ko file to /lib/modules/2.6.10.5-386/extra (there should be only 2.6.10.5-386 other than the 2.6.10 created by make install) and then do a depmod.

---

### Post by archibald.tuttle on 2005-04-30
hi, i'm a fresh owner of a zd1201 usb stick. 

i'd like to know why the whole kernel source package is needed, is it a (known?) bug in kernel-package, or a problem in the zd1201 distribution files? it doesn't build even on debian sid, and as previously pointed out also the "make install" doesn't put the module in the right place, making the installation process quite annoying, at least for newbies.

on the plus side zd1201 will be included in the next official linux kernel release, 2.6.12, it is already present in 2.6.12-rc3.

i didn't check very well but i couldn't find references to the license of the firmwares, can they be included in main or should they go in restricted-modules?

thanks.

---

### Post by philcolbourn on 2005-05-06
the source is needed since the header package is missing a header file. the header file is in the source package. the ieee802_11.h file is the problem.

---

### Post by philcolbourn on 2005-06-07
[QUOTE=tonysze]Thanks for all your replies, I had finally made it working by downloading the kernel source,  and compiling the zd1201 native driver. According to the information in some places, the first times the driver is loaded it would always complain about not able to find the firmware file. Removing the driver and loading it again solves the problem.

I'm using version 0.14 of that zd1201 driver from this site:
[http://linux-lc100020.sourceforge.net/](http://linux-lc100020.sourceforge.net/)

I'm now waiting for either an update which can fix the problem, but so far, I can use it.[/QUOTE]
 After a reboot (yes it has been a long time - noisy fan!) my zd1201 does not automatically come up. As others have mentioned, the zd1201 needs to be removed (rmmod zd1201) and reloaded (modprobe zd1201) for it to work.

I think I made this automatic by adding these lines to my wlan0 /etc/network/interface file
iface wlan0 inet dhcp
  pre-up rmmod zd1201
  pre-up modprobe zd1201
  post-down rmmod zd1201
  ...

 It worked once.

---

### Post by ameerirshad on 2005-12-08
[quote=philcolbourn]It worked once.[/quote]
 
as in:
 
1) Once it worked, now it doesn't
 
2) It worked AT once
 
Make your choice and let me know as I need this info to help out a Linux newbee.... :rolleyes:

---

### Post by philcolbourn on 2005-12-08
zd1201 support is in breezy. you just need the firmware installed. my hacks are not necessary now.

---

