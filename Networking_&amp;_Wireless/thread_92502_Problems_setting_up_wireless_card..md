---
title: "Problems setting up wireless card."
date: 2005-11-19
forum: Networking &amp; Wireless
---

### Post by Wondersaurus on 2005-11-19
I have a Broadcom wireless card (BCM4306 802.11b/g controller, BCM4401 100Base-T), and after some effort have gotten the driver correctly installed and ready.  The problem is that it does not connect to the internet.  iwconfig looks normal except it reports the access point has the MAC address of 00:00:00:00:00:00, which is most probably not right.  Most likely, the problem is that the wireless card is not communicating with my router, and I don't know how to fix it.  How do I fix this?

Included below is the full readout of iwconfig:
lo          no wireless connections

eth0      no wireless connections

wlan0     IEEE 802.11g   ESSID: off/any
             Mode:Managed   Frequency:2.462 GHz  Access Point:  00:00:00:00:00:00
             Bit Rate:54 mb/s    Tx-Power:25 dbm
             RTS thr:2347 B     Fragment thr:2346 B
             Power Management: off
             Link Quality:100/100  Signal level:-10 dBm  Noise level:-256 dBm
             Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
             Tx excessive retries:0  Invalid misc:1222  Missed beacon:0

sit0        no wireless extensions

If any more information is needed, tell me what it is and how to get it.

Wondersaurus Fantabulorus

---

### Post by jliedeka on 2005-11-19
Have you tried manually setting an essid and/or channel?  That should get auto-negotiated but it's worth a try.

Also, are you using WEP or WPA?  You may need to set up a key.

---

### Post by Wondersaurus on 2005-11-19
I haven't tried manually setting the essid or channel.  Both of those seem correct, which is more than reason enough to manually set them, come to think of it.  Of course, I get a "SET failed on device wlan0; operation not permitted" error when I try either.

I'm not using a WEP or WPA.

---

