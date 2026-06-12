---
title: "Help PLEASE wireless DISPLAY"
date: 2008-03-28
forum: Networking &amp; Wireless
---

### Post by hduong01 on 2008-03-28
Hi, I need some help!!!! I have a dv 2610ca, running vista/ubuntu 7.10, and I have a broadcom 43xx card.  I have enable the restricted network drivers but the wireless is not detected.  any help would be greatly appreciated....Thank you for your time...

device
04:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)
        Subsystem: Hewlett-Packard Company Unknown device 1374
        Flags: bus master, fast devsel, latency 0, IRQ 10
        Memory at fc000000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

---

### Post by hduong01 on 2008-03-28
bump

---

### Post by jcostom on 2008-03-28
First, bumping after less than 1 hour is just plain rude.  Don't do that.  People generally don't help rude forum users.

Second, what's a "dv 2610ca" ?  Never heard of one.

Thirdly, have you read the howtos on using the fwcutter tool to pull the firmware files out of the windows drivers for your card?  The broadcom 43xx series of cards needs firmware dropped in /lib/firmware.

I setup a 43xx-based card several months ago.  It took about 10 minutes to complete, with the help of the guides.

---

### Post by hduong01 on 2008-03-28
well i'm sorry but i was online and i thought i can get quick references from expert ubuntu.

i'm using a hp dv2610ca and i have really exhausted all the resources before posting on the communities.

---

