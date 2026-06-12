---
title: "Wirelesse Networking Help (PPC, Edubuntu, Linksys WUSB54GC)"
date: 2006-10-27
forum: Networking &amp; Wireless
---

### Post by thornomad on 2006-10-27
Hi,

Just installed Edubuntu (Edgy) on an old iMac G3.  Works great, except no internet (wired is busted hardware-wise, can't plug in).  I have a Linksys WUSB54G and a Linksys WUSB54GC that I use with WinXP machines that I can put on the Edubuntu system temporarily to download software and whatnot.

However, these don't seem to work "out of the box."  With the WUSB54G nothing happens when I plug it in; with the WUSB54GC I get wmaster0 and wlan0 options in my System/Networking area but configuring the network provides me with no internet.  

If I run lspci, I get:

```
Class ffff: Illegal Vendor ID Unknown device ffff (rev ff)
```

I get the same result for both the WUSB54G and WUSB54GC.

I am sort of stuck -- not sure where to start.  I would think that since the WUSB54GC at least is recongized as a wireless device, that might be easiest; however, when searching google, I am finding that the WUSB54G has more info about installing a nsdiwrapper driver.

Any help?

---

### Post by wieman01 on 2006-10-27
I have got a WUSB54G **V4** as well & it runs with "ndiswrapper" ("wlan0") just fine. "lspci" list PCI devices, but you happen to have USB ones. So try this instead:
> lsusb
Do they show now?

There is a good guide for the WUSB54G **V4**... Please follow all the steps (including the blacklisting of the Linux driver): [http://www.ubuntuforums.org/showthread.php?t=192588&highlight=wusb54g]("http://www.ubuntuforums.org/showthread.php?t=192588&highlight=wusb54g")

_**EDIT:**_
The guide should also work for a WUSB54G **V2**... Check this out: [http://www.ubuntuforums.org/showthread.php?t=276494&page=6&highlight=wusb54g]("http://www.ubuntuforums.org/showthread.php?t=276494&page=6&highlight=wusb54g")

---

### Post by thornomad on 2006-10-28
Oh!  Silly me, you are right -- if I run lsusb I get:

```
ID 13b1:000d Linksys
```

Great.  Now I need to figure out how to install ndiswrapper from a disk.  Thanks!

---

### Post by wieman01 on 2006-10-28
Installing the device should not be much of a problem. "ndiswrapper" is fairly reliable as far as these devices are concerned.

---

### Post by stevenwagner on 2006-11-04
I am having the exact same problem with my WUSB54GC. I am running the final Edgy (ubuntu 6.10) release. I get the wmaster0 and wlan0 network devices, and can associate with my access point, but am unable to receive dhcp or manually assign an IP address and ping the router. I really wish this worked, but oh well. I had it working with Dapper after a few patches. Please message me if we get a fix.

Regards~
Steven


> **thornomad said:**
> Hi,

Just installed Edubuntu (Edgy) on an old iMac G3.  Works great, except no internet (wired is busted hardware-wise, can't plug in).  I have a Linksys WUSB54G and a Linksys WUSB54GC that I use with WinXP machines that I can put on the Edubuntu system temporarily to download software and whatnot.

However, these don't seem to work "out of the box."  With the WUSB54G nothing happens when I plug it in; with the WUSB54GC I get wmaster0 and wlan0 options in my System/Networking area but configuring the network provides me with no internet.  

If I run lspci, I get:

```
Class ffff: Illegal Vendor ID Unknown device ffff (rev ff)
```

I get the same result for both the WUSB54G and WUSB54GC.

I am sort of stuck -- not sure where to start.  I would think that since the WUSB54GC at least is recongized as a wireless device, that might be easiest; however, when searching google, I am finding that the WUSB54G has more info about installing a nsdiwrapper driver.

Any help?

---

### Post by BartlebyScrivener on 2006-11-12
I have Edgy installed and also can't get Linksys WUSB54GC installed using ndiswrapper or trying install the RT73 Ralink Linux drivers.

It works fine under windows, but nothing under Ubuntu.

May take it back and try D-Link.

My ndiswrapper attempt was using the version 1.8 of the ndiswrapper utils in Synaptic and the driver from the Linksys MFR cd. Had to install on Windows to extract the rt73.inf file, which didn't work.

Next attempt will be to make the newest ndiswrapper files from SourceForge with the newest Windows drivers from Linksys. But not optimistic about this working. This thing just does not want to work under Ubuntu.

rd

---

