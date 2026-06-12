---
title: "Slow wireless on HP laptop"
date: 2006-12-29
forum: Networking &amp; Wireless
---

### Post by tntc1978 on 2006-12-29
I'm using a 8/1 Mbps internet connection, and aren't experiencing any problem on any of my other machines (running Ubuntu 6.10 & Win XP).

But my new laptop is really slow on the internet. I've used these guides:
[http://ubuntuforums.org/showthread.php?t=185174&highlight=4310](http://ubuntuforums.org/showthread.php?t=185174&highlight=4310)
[http://ubuntuforums.org/showpost.php?p=1105667&postcount=218](http://ubuntuforums.org/showpost.php?p=1105667&postcount=218)
[http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)

The first one did it for me, but unfortunately not good enough.
Any thoughts for a novice?

---

### Post by tntc1978 on 2006-12-30
This
```
lspci | grep Broadcom\ Corporation
```

gives me this output
```
03:00.0 Network controller: Broadcom Corporation BCM4310 UART (rev 01)
```

And this
```
iwconfig
```

Gives me this
```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"FRITZ!Box Fon WLAN Annex A"  Nickname:"Broadcom 4311"
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:15:0C:7E:DC:CF   
          Bit Rate=11 Mb/s   Tx-Power=18 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=71/100  Signal level=-63 dBm  Noise level=-69 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.
```

As stated above, I'm on the WLAN (eth1) but it feels like I'm on 128/128 instead of a 8/1 Mbps. Any thoughts?

---

### Post by tntc1978 on 2006-12-30
What else can I tell you, that can help you help me with my problems?

---

