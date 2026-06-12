---
title: "Help with Netgear WG511v2 54mbps pcmcia card"
date: 2005-07-19
forum: Networking &amp; Wireless
---

### Post by Tommerz on 2005-07-19
Hey everyone,

I've tried without success many of the methods on this forum to get my card working, and was wondering if anyone had any particular methods that have worked for them with this card?

Even after installing what seemed to be correct drivers with ndiswrapper, my card didn't seem to be detected by the os and the lights on the card wouldn't light or anything, suggesting lack of communication.  :-? 

Any ideas or fool/newbie proof methods? Is there a particular driver that has worked well for anyone?

---

### Post by Tommerz on 2005-07-21
*bump*

Any ideas, I'm currently stuck using windows xp and want to use ubuntu as my primary system (but can't without net access!!)

---

### Post by igiugik on 2005-07-27
Your post was 5 days ago, maybe you've got it working, but if not, here's a few things:

First, most, but not all WG511s use prism 54 chipsets, so you don't need ndiswrapper.  That's only for cards with no Linux drivers where you are then forced to use the Windows driver.

Second, do a dmesg at the console and see if it says the prism54 driver is loading successfully.   If it is, next see if dmesg says something about Yenta socket being loaded and lastly check if it says firmware for ethx is being loaded.  Most common problem is the firmware is not loading because it is sometimes not provided (some distros worried about licensing).  

If prism54 driver loadiing, but firmware is not, check /usr/lib/hotplug/firmware to see if there is a file isl3890 in there.  If not, got to prism54 website, or elsewhere, download the latest firmware (its not called isl3890 there, something like " 1.0.3.4.somenthing" , rename it isl3890, and place in  /usr/lib/hotplug/firmware.

---

### Post by erk on 2005-08-03
[QUOTE=igiugik]Your post was 5 days ago, maybe you've got it working, but if not, here's a few things:

First, most, but not all WG511s use prism 54 chipsets, so you don't need ndiswrapper.  That's only for cards with no Linux drivers where you are then forced to use the Windows driver.

Second, do a dmesg at the console and see if it says the prism54 driver is loading successfully.   If it is, next see if dmesg says something about Yenta socket being loaded and lastly check if it says firmware for ethx is being loaded.  Most common problem is the firmware is not loading because it is sometimes not provided (some distros worried about licensing).  

If prism54 driver loadiing, but firmware is not, check /usr/lib/hotplug/firmware to see if there is a file isl3890 in there.  If not, got to prism54 website, or elsewhere, download the latest firmware (its not called isl3890 there, something like " 1.0.3.4.somenthing" , rename it isl3890, and place in  /usr/lib/hotplug/firmware.[/QUOTE]
 The WG511v2 use the Marvell Technology Group Ltd chipset and should not be confused with the previous WG511 versions, they cleary have WG511v2  on the photo of the card on the box, and when you do a lspci -v it says:

0000:02:00.0 Ethernet controller: Marvell Technology Group Ltd.: Unknown device 1faa (rev 03)
        Subsystem: Netgear: Unknown device 4e00



I don't know of any drivers except NDIS that work with them, which sucks as I bought two to use with kismet!

---

### Post by diensthunds on 2005-08-04
Actually there are some of the wg511vs cards (the 32 bit bus ones) that use the Intersil isl3890 factor, I know this because I'm using one right now. And I'm not using the ndis wrappers, I'm using the built in module for the kernel.
output of lspci -v follows:

0000:02:00.0 Network controller: Intersil Corporation Intersil ISL3890 [Prism GT/Prism Duette] (rev 01)
        Subsystem: Netgear: Unknown device 4800
        Flags: bus master, medium devsel, latency 80, IRQ 11
        Memory at d0100000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: <available only to root>

Seems like alot of these cards are just hit and miss regardless of what the card says on it.

---

