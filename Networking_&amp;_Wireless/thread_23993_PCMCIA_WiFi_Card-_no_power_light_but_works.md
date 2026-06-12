---
title: "PCMCIA WiFi Card- no power light but works?"
date: 2005-04-04
forum: Networking &amp; Wireless
---

### Post by sb73542 on 2005-04-04
Hello,

This is going to sound really dumb, but I'm confused about whether or not my WiFi card is working.  I just got a new (used) IBM Thinkpad 600 and put Ubuntu 4.10 on it.  I borrowed a friend's rt2500 chipset 802.11g card to see if my pcmcia slots work before I buy any cards of my own.  I don't have a wireless network nearby, but I figured that the card would light up and it would just say it couldn't find a signal.  But here's where I'm confused and curious:

I set up the card with ndiswrapper and loaded the drivers and modules.  It appeared to be a success.  The "Link" light on the card briefly flashed when I plugged it in (but it is now off), and I now have a wlan0 device.  Ndiswrapper tells me the hardware for the driver I installed is present.  But for some reason the "PWR" light on the card isn't lit up.  Any idea why?  And what's up with the "Link Quality" below?  I can guarantee that there are no other 802.11x devices nearby, I live in the middle of nowhere, no neighbors.  I do have a cordless phone.  :mrgreen:   I guess I could run to a coffee shop with WiFi if it looks like it's worth trying.

iwconfig:
wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Auto  Frequency:2.412GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:11Mb/s   Tx-Power:20 dBm   Sensitivity=-120 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:100/100  Signal level:136/154  Noise level:0/154
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:33   Missed beacon:0

ifconfig:
wlan0     Link encap:Ethernet  HWaddr 00:10:A7:2C:DE:6C
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::210:a7ff:fe2c:de6c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:1404 (1.3 KiB)
          Interrupt:11 Memory:10c00000-10c01fff


Any ideas?  Besides getting off my couch and driving to the coffee shop?  I guess I'll have to get used to it, this will be my only hope of broadband....  8)   Thanks for the help!

---

### Post by dusty on 2005-07-23
your story is almost the same as mine.
i got my rt2500 chipset to seemingly run under ndiswrapper.

however, ifconfig says its there i can't seem if get the card to turn on.
i also can't get it to search for near by networks.

so what am i doing wrong?

did you figure your issue out?

---

