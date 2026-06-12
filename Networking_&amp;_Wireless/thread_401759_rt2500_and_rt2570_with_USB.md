---
title: "rt2500 and rt2570 with USB"
date: 2007-04-05
forum: Networking &amp; Wireless
---

### Post by mlapaglia on 2007-04-05
from [http://doc.gwos.org/index.php/RalinkDrivers#Notes_on_the_driver]("http://doc.gwos.org/index.php/RalinkDrivers#Notes_on_the_driver")
says
>  Notes on the driver

    * There are various drivers used for Ralink chipsets
          o rt2400 is an older driver
          o rt2500 is the replacement for the rt2400 (used for pci devices)
          o rt2570 is similar to the rt2500 chipset but used in usb devices
          o rt2x00 is a driver re-write which is meant to replace all above drivers
                + rt2x00 needs a 2.6.13 or newer kernel to work 


i have a wusb54g version 4 (ralink drivers), both feisty, edgy, and backtrack 2 match it up with the 2500 driver... shouldn't it use the 2570 drivers??

also, do the rt25xx drivers support packet injection out of the box with feisty, or do i need to patch them?

thanks a lot

---

### Post by mlapaglia on 2007-04-05
anybody?

[http://www.aircrack-ng.org/doku.php?id=install_drivers&DokuWiki=98d05934d3b5b1bac3997df85fe32b96]("http://www.aircrack-ng.org/doku.php?id=install_drivers&DokuWiki=98d05934d3b5b1bac3997df85fe32b96")

says > As of now, Aireplay-ng only supports injection on Prism2, PrismGT (FullMAC), Atheros, RTL8180, RTL8187 and Ralink. Injection on Centrino, Hermes, ACX1xx, Aironet, ZyDAS, Marvell and Broadcom is not supported because of firmware and/or driver limitations. 


Nearly all drivers (that can support injection) needs to be patched to support injection in Monitor mode.
You will need the following to compile drivers: 

Linux kernel headers that match your current running kernel.
The same gcc version that was used to compile your kernel. At least make sure that the first two version numbers or the compiler are thesame (e.g. it’s OK to use gcc 3.4.6 to compile the driver if the kernel was compiled by gcc 3.4.2). Ignoring this rule will cause Invalid module format errors during module load.
Always use latest patches that you can find here

Note: if you’re using drivers given with your distro they AREN’T patched. 

i'm just wondering what's true?

---

### Post by Floppyjoe on 2007-04-05
> **mlapaglia said:**
> from [http://doc.gwos.org/index.php/RalinkDrivers#Notes_on_the_driver]("http://doc.gwos.org/index.php/RalinkDrivers#Notes_on_the_driver")
says


i have a wusb54g version 4 (ralink drivers), both feisty, edgy, and backtrack 2 match it up with the 2500 driver... shouldn't it use the 2570 drivers??

also, do the rt25xx drivers support packet injection out of the box with feisty, or do i need to patch them?

thanks a lot

I have this device running on my sisters computer, the WUSB54G v4 using ndiswrapper following this guide:
[http://floppyjoes.homeip.net/phpBB2/viewtopic.php?t=21](http://floppyjoes.homeip.net/phpBB2/viewtopic.php?t=21)
I know that kismet does not work with ndiswrapper enabled devices.
Is it easy or even possible to get it working with the native ralink drivers?
I have to blacklist the rt2570 driver using the above mentioned method to get it to work with ndiswrapper.

---

### Post by aarmenaa on 2007-04-05
> **Floppyjoe said:**
> Is it easy or even possible to get it working with the native ralink drivers?
I have a Ralink card (RT73, USB) and I haven't been able to get any of the native Linux drivers to work correctly.  The driver included with Ubuntu 6.10 (edgy) is an old, broken version of the Serialmonkey drivers, the driver that you download from Ralink's site doesn't support the Linux Wireless Extensions, and the [Serialmonkey drivers]("http://rt2x00.serialmonkey.com/wiki/index.php?title=Main_Page") are still *very* beta (at least for my card).  So, I use ndiswrapper to get things working smoothly.  Of course, I'm not trying to inject packets or anything terribly advanced.  Your best bet is probably the Serialmonkey drivers for that type of stuff.

---

### Post by ghjk on 2007-04-12
I have looked at the patches included in the package aircrack-ng that I have in my distrib (Debian Etch), and at the sources of my driver.

When looking both at the patches and the sources we can see that the driver rt2570 has already integrated the patch. And that is coherent with the fact that, now, the patch for rt2570 is only contained in a subdirectory called "old".
Similarly, the patch for rt2500 is not in the main directory but in "old" too.

As for the rt25xx, I can't say, but while I don't see any patch, and while it is the most recient project, I can suppose that the injection is present in it from the beginning.

I hope it would be useful for anybody (though this answer comes a little late I see ^^)

---

