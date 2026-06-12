---
title: "Linksys WUSB11 2.8 problems"
date: 2006-08-27
forum: Networking &amp; Wireless
---

### Post by evulc on 2006-08-27
I have a compaq presario 900 laptop with a linksys wusb11 2.8.
I have tried all the different faq's (ndis driver, atmel driver, berlios driver), tried it with a hub and without too! I still get the same crappy non-working behavior.

the weird part is, it worked the second i plugged it in to my desktop machine with the exact same ubuntu 6.06. I didn't even need to install the atmel-firmware package, it just worked. I was able to configure the network in gnome and everything just worked.

Anyone???

---

### Post by evulc on 2006-08-27
here's the relevant part of iwconfig:

```
wlan0     IEEE 802.11-DS  ESSID:"newc"  Nickname:"okuwlan"
          Mode:Managed  Frequency:2.457 GHz  Access Point: Not-Associated
          Bit Rate:11 Mb/s   Tx-Power=15 dBm
          Retry limit:8   RTS thr=1536 B   Fragment thr=1536 B
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

Access Point: Not-Associated is the part that shows the problem, it shows up no matter which of the driver setups I tried.

---

### Post by svenkatesan on 2008-01-08
I too have this problem.
With ndiswrapper it worked in 7.04  but not in 7.10.
No error and module loading but still can't connect.

---

