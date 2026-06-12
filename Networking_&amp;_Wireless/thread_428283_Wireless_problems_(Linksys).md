---
title: "Wireless problems (Linksys)"
date: 2007-04-30
forum: Networking &amp; Wireless
---

### Post by Mooseus on 2007-04-30
I currently installed Ubuntu 6.10 with the intention of upgrading to Feisty once I've established an internet connection. Problem is my wireless connection doesn't work. I'm currently using a notebook Linksys Wireless-G adapter . model number WPC54G, version 2.0.  I theorized that the problem may be I haven't installed any drivers but the problem is the site only has windows drivers. Where would I find the Linux equivalent?

---

### Post by footloose123 on 2007-04-30
Hi,

The wireless-g is actually the ralink 2500 linksys just rebranded it. Its the same card I have and it is supported out of the box with Feisty. It will show up as ra0.

ps. It had problems connecting for me but I installed the 2.6.20-15.27 version kernel and all was fine after that.

---

### Post by Mooseus on 2007-04-30
so the best thing to do would be to install fiesty? How do I go about installing this 2.6.20-15.27 version kernel, with 6.10 or can I only do it with Fiesty?

---

### Post by footloose123 on 2007-04-30
Hi, 

I don't know anything about 6.10 as 7.04 is my first time with ubuntu. however the default kernel installation for me was a package called "kernel-generic" which was version 2.6.20.15.14. The package I installed to get wireless working is called "linux-image-2.6.20.15-lowlatency" which is version 2.6.20-15.27.There is also a generic version but the lowlatency one is better for desktop interactivity.

---

### Post by dmizer on 2007-04-30
edgy should support your card out of the box.

otherwise, with edgy ... you can also try ndiswrapper.  i wrote a howto here: [http://ubuntuforums.org/showthread.php?t=324148](http://ubuntuforums.org/showthread.php?t=324148)

---

### Post by footloose123 on 2007-04-30
Hi 

One last piece of help. I had a look at a site that lists the packages in 6.10 and its kernel (2.6.17) doesn't have the ralink driver as part of it. So you need to look for "rt2500" in the packages. It looks like the diver comes in source form so you will need to compile it, or follow dmizer's help.

---

### Post by dmizer on 2007-04-30
the wpc54g v2 does not have the ralink chipset.  it has the acx111 chipset.

---

### Post by footloose123 on 2007-04-30
I'm going to have to change my nick to footinmouth :oops: I have the wmp54g wpc... damn it. sorry dude. but my advice about the kernel still stands if you end up with mystery problems connecting.

Thanks dmizer for point that out.

---

### Post by rustybronco on 2007-04-30
My wpc54g v2 worked out of the box with edgy and fiesty.

---

### Post by MeeMaw on 2007-04-30
Mooseus-
Linksys put a number of chipsets in their wireless cards (mine was a Ralink chipset, but some are Broadcom, and there are a couple others) - please determine which chipset you have (typing   
lspci     
in a terminal should do it) - post the results so we can help you.
Some of them work out of the box with Linux drivers and some need ndiswrapper....
:)

---

### Post by Mooseus on 2007-04-30
ok I typed that lspci command in the terminal and these were my results:

00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:04.0 CardBus bridge: Texas Instruments PCI1450 (rev 03)
00:04.1 CardBus bridge: Texas Instruments PCI1450 (rev 03)
00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 03)
00:08.0 Multimedia audio controller: ESS Technology ES1978 Maestro 2E (rev 10)
00:09.0 Ethernet controller: Intel Corporation 82557/8/9 [Ethernet Pro 100] (rev 09)
00:09.1 Serial controller: Agere Systems LT WinModem
01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility P/M AGP 2x (rev 64)
02:00.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface

---

### Post by dmizer on 2007-04-30
> **Mooseus said:**
> ok I typed that lspci command in the terminal and these were my results:

02:00.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface

as i indicated before, your card has the acx111 chipset.  this card is supported in edgy as well as feisty.  i use ndiswrapper, and the directions for that can be found in the link i gave earlier.

alternatively, you can use native firmware.  the edgy native firmware works out of the box if you install feisty with the card inserted.  otherwise you have to change the firmware.  you can use this link as a guide for changing the firmware: [http://ubuntuforums.org/showthread.php?t=233565](http://ubuntuforums.org/showthread.php?t=233565)

---

