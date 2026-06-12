---
title: "Asus WL-106gM PCMCIA wireless card supporting issue"
date: 2007-12-04
forum: Networking &amp; Wireless
---

### Post by pckong on 2007-12-04
Hi,

I just bought a new PCMCIA wireless card with model name: Asus WL-106gM. It can not be detected by NetworkManager. I have been searching help hours after hours. Eventual I found neither software provided by Ubuntu nor NDISwrapper support this W/L card. 

Here I got some more information about this device:
Network standard for Asus WL-106gM is: Pre IEEE 802.11n, backward compatible with 802.11 b/g device. 

I will have to use linux, what can i do? :confused: Any helps will be seriously thanks.

---

### Post by pckong on 2007-12-04
Hi,

I have got some more information on the W/L card,
------------------------------------------------------------------------------------------------------------------------
02:00.0 Ethernet controller: Airgo Networks Inc AGN300 802.11 a/b/g True MIMO Wireless Card (rev 01)
        Subsystem: ASUSTeK Computer Inc. Unknown device 106f
        Flags: medium devsel, IRQ 5
        Memory at 24080000 (32-bit, non-prefetchable) [disabled] [size=128K]
        Memory at 24000000 (32-bit, non-prefetchable) [disabled] [size=512K]
        Capabilities: <access denied>
-------------------------------------------------------------------------------------------------------------------------
Airgo
manufacturer    wlan type 	product ID    host I/F 	    
Belkin               802.11g/n      F5D8010 	 Cardbus      
-------------------------------------------------------------------------------------------------------------------------

HELP :(

---

### Post by go_beep_yourself on 2008-02-03
Did you get it working yet?

---

### Post by justinmiller87 on 2008-03-02
Are you still having issues? If so, try the instructions in my signature. They are an installation guide for Airgo-based Pre-N cards, which the F5D8010 is.

---

