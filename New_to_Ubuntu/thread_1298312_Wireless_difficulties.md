---
title: "Wireless difficulties"
date: 2009-10-22
forum: New to Ubuntu
---

### Post by donaldshelton on 2009-10-22
I just downloaded and installed the Ubuntu 9.10

I remember that the atheros wireless card doesn't work  

I tried the following but no luck:

sudo vi /etc/modprobe.d/blacklist

blacklist ath_pci
blacklist ath_hal

What else do people recommend?

don

---

### Post by GimmeCoffe on 2009-10-22
You can try ndiswrapper...

~GimmeCoffe

---

### Post by donaldshelton on 2009-10-22
Could you please post instructions on the ndiswrapper???

---

### Post by GimmeCoffe on 2009-10-22
Check your network adapter with "lspci -v" and post it. It should be similar to:

02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
        Subsystem: Dell Unknown device 0005
        Flags: bus master, fast devsel, latency 64, IRQ 18
        Memory at dfbfe000 (32-bit, non-prefetchable) [size=8K]

~GimmeCoffe

**EDIT: **Sorry, I didn't see the tag. Let me post the instructions.

---

### Post by GimmeCoffe on 2009-10-22
Check this out: [http://www.ubuntugeek.com/atheros-5007eg-with-madwifi-on-i386-platform.html](http://www.ubuntugeek.com/atheros-5007eg-with-madwifi-on-i386-platform.html)

Let me know if it works.

Best regards,
~GimmeCoffe

---

### Post by drpjkurian on 2009-10-25
> **donaldshelton said:**
> I just downloaded and installed the Ubuntu 9.10

I remember that the atheros wireless card doesn't work  

I tried the following but no luck:

sudo vi /etc/modprobe.d/blacklist

blacklist ath_pci
blacklist ath_hal

What else do people recommend?

don

Hi
Please visit my thread
[http://ubuntuforums.org/showthread.php?t=1240781](http://ubuntuforums.org/showthread.php?t=1240781)
It might help you

With
Regards
Dr Kurian

---

