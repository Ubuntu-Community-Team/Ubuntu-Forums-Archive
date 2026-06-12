---
title: "wireless card detected, AP detected, what else do I do??"
date: 2007-02-02
forum: Networking &amp; Wireless
---

### Post by jk610 on 2007-02-02
Without Ndiswrapper my usb wireless card is detected by edgy. 

iwlist scan shows networks in my area and one of them is mine.

sudo iwconfig eth1 essid linksys mode Managed


this gives me...

eth1    IEEE 802.11b  ESSID: "linksys"
          Mode: Managed   Channel=1   Access Point: 00:16:B6:1A:C0:94
         Sensitivity=0/200
          Link Quality:0   Signal Level:0   Noise level:0
         Rx invalid nwid:0   Rx invalid crypt:0  Rx invalid frag:0
        Tx excessive retries: 0  Invalid misc:0   Missed beacon:0


So whats next? Its seeing the access point but doesnt seem like its actually grabbing the signal. No internet in ubuntu makes me sad!:confused:

I just noticed that it drops the ESSID and AP after like 5 minutes and puts it back to invalid. Yikes!

---

### Post by MichaelGu on 2007-02-09
I encounter same problem with USB 802.11g of USROBOTICS.

---

