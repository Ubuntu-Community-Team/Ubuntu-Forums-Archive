---
title: "modprobe ndiswrapper problems"
date: 2005-07-06
forum: Networking &amp; Wireless
---

### Post by jcom on 2005-07-06
hello,

I've been using Ubuntu for sometimes in VMware under windows and now I want to make it my main OS. I've thrown winxp away and installed Ubuntu. Now I have trouble to use my wifi usb key (D-Link DWL-G122, ralink chipset) with ndiswrapper.

What I do :

lsusb
>> D-Link Corp. [hex] (the wifi key is detected)

ndiswrapper-utils installation from synaptic.
Windows driver decompression.

ndiswrapper -i NetRTUSB.inf
ndiswrapper -l 
>> "netrtusb present, hardware present" (so everything seems to be ok)

modprobe ndiswrapper

...and that is where the trouble begins since nothing is happening, the command doesn't stop, it keep processing i-don't-know-what without displaying anything.

when I do : modprobe -v ndiswrapper :
it shows :  insmod /lib/modules/2.6.10-5-386/misc/ndiswrapper.ko
and keeps doing nothing.

If ANYONE has an idea, i'd love to hear it.

---

### Post by scoon on 2005-07-07
Hey there, 

I think you should modprobe ndiswrapper first.  And then install the INF file.

regards, 


scoon

---

