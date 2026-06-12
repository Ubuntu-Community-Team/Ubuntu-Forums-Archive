---
title: "[SOLVED] AR5007EG with MadWifi -&amp;gt; Device Not Detected"
date: 2007-08-29
forum: Networking &amp; Wireless
---

### Post by bmartin on 2007-08-29
[COLOR="Red"]**This method is deprecated. I recommend [the native linux driver]("http://ubuntuforums.org/showthread.php?t=792158") instead.**[/COLOR]

I have a built-in Atheros AR5007EG chipset which is supposedly supported by MadWifi (according to claims at madwifi.org). I downloaded/compiled/installed MadWifi (and removed ndiswrapper).

No ath0 or wifi0 interfaces show up under **iwconfig**. dmesg doesn't say anything about my wireless device. **lsmod | grep ath** indicates that the appropriate kernel modules have been loaded. **sudo ifconfig ath0 up** says that the device doesn't exist.

The chipset works with ndiswrapper and the appropriate Windows drivers.

Any ideas?

---

### Post by kevdog on 2007-08-29
lshw -C network --- does this even list the device as disabled??

---

### Post by bmartin on 2007-08-29
I don't think so. Here's what I got:
```
*-network UNCLAIMED
description: Ethernet controller
product: Atheros Communications, Inc.
vendor: Atheros Communications, Inc.
physical id: 0
bus info: pci@02:00.0
version: 01
width: 64 bits
clock: 33MHz
capabilities: cap_list
configuration: latency=0
resources: iomemory:b0200000-b020ffff irq:19
```

---

### Post by kevdog on 2007-08-29
I dont own an atheros card, but what is it with all these atheros cards that are supposed to be supported by madwifi that simply  ARE NOT?

You tried installing the linux-restricted-modules for your kernel version??  This basically installs madwifi drivers (however I dont know if this is any different than what you did).

Here is what I pulled from the madwifi site.  Although its listed under the compatibilty section, the following suggests that its support by ndiswrapper (not madwifi).  Im not sure since this is kind of cryptic:

Atheros AR5007EG ¶
Chipset:	AR2425 / AR5007EG
URL:	[http://atheros.com/pt/AR5007EG.htm](http://atheros.com/pt/AR5007EG.htm)
Supports:	802.11b 802.11g
Interface:	PCI-Express x1
Device Information:	Ethernet controller: Atheros Communications, Inc. Unknown device 001c (rev 01),Subsystem: AMBIT Microsystem Corp. Unknown device 3065
Notes:	not supported by HAL as of 2007.04.28 - resturns Hal status 13
Notes:	Suported by ndiswrapper with windows driver, but some user reports crash problems
Notes:	Instructions about how to use the windows driver + ndiswrapper
Notes:	works fine with ndiswrapper, using old drivers, search ubuntu forums

---

### Post by bmartin on 2007-08-29
> **kevdog said:**
> I dont own an atheros card, but what is it with all these atheros cards that are supposed to be supported by madwifi that simply  ARE NOT?
Well, new hardware comes out all the time, and the Atheros specs were released a long time ago; new cards surely require some reverse-engineering.

> **kevdog said:**
> You tried installing the linux-restricted-modules for your kernel version??  This basically installs madwifi drivers (however I dont know if this is any different than what you did).
Yep.

> **kevdog said:**
> Here is what I pulled from the madwifi site.  Although its listed under the compatibilty section, the following suggests that its support by ndiswrapper (not madwifi).  Im not sure since this is kind of cryptic
I think you're right. I'll stick with ndiswrapper. It's been stable, but for some reason it fails to work at about 40% signal strength. I need to be pretty close to the AP to use it.

Sorry for wasting your time. I should've bothered to read the notes, even after I saw it listed on the supported devices page.

I just bought a bunch of wireless USB devices with antennae on them for $20 apiece (plus shipping) [here]("http://www.gearxs.com/gearxs/product_info.php?cPath=77&products_id=8455"). I'll probably sell them for a profit :) They have an Ralink chipset; I believe they require either the RT2570 or ndiswrapper approach.

---

### Post by kevdog on 2007-08-29
I dont know a lot about madwifi except all atheros chipsets are not supported.  Ive seen that from other posters in the forum that had to result to ndiswrapper.

As far as the usb devices -- since they are ra chipsets - I would recommend installation of serial monkey rt drivers if you wanted to "experiment".  This thread is the "bible" for ra chipsets:
[http://ubuntuforums.org/showthread.php?t=400236&highlight=serialmonkey](http://ubuntuforums.org/showthread.php?t=400236&highlight=serialmonkey)

Ive got a crappy broadcom chipset 4306.  It doesnt cause me a lot of problems, however Im in the same boat that I need ndiswrapper.  Despite what people say Im not sure what the best chipset to buy is.
Broadcom,Atheros,ra most of these work in one manner or another (native driver or ndiswrapper). Prism, rtl a little bit more problematic to set up -- cant speak on performance.  Nothing is ideal in this world!

---

### Post by bmartin on 2007-08-29
I have a Broadcom BCM4318 in this computer. The range is good (using ndiswrapper). Some people have had great success with the firmware. I changed my script to recommend everyone to use ndiswrapper, though, because many people have strange problems with the firmware. I haven't seen much activity at the bcm43xx page.

Thanks for the link; I bookmarked it. I have a USB stick that uses the RT73 kernel module. It works pretty well. I've had good range with Broadcom and Ralink, but bad range with Atheros.

---

### Post by kevdog on 2007-08-29
I gave up on the bcm43xx driver too -- ndiswrapper is theoretically faster, but will revisit the issue when the 54Mb/sec version is available.  Id like to try that along with aircrack for packet injection. (Cant do this with ndiswrapper).  No idea however when a stable 54Mb/sec bcm43xx driver will be available.

---

