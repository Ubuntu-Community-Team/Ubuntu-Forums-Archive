---
title: "edimax 802.11g PCMCIA wireless card"
date: 2007-02-18
forum: Networking &amp; Wireless
---

### Post by orko3001 on 2007-02-18
Hi, I have a edimax 802.11g PCMCIA wireless card and can't get it to work. Thats with a supplied rt73 driver. 

I have been trying different options. This one [http://ubuntuforums.org/archive/index.php/t-355310.html](http://ubuntuforums.org/archive/index.php/t-355310.html) works as far as sudo "cp -v Makefile ./Makefile" where I get the error "`Makefile' and `./Makefile' are the same file", which seems obvious really.

System / Administration / Networking

The network can be detected by this but when I try it just ticks back and forward. I have tryed with and without WEP and I can turn my ethernet on and off with this. 

iwconfig says:

```
ra0       RT61 Wireless  ESSID:""
           Mode:Auto  Channel:8  Bit Rate=54 Mb/s
           RTS thr:off   Fragment thr:off
           Link Quality=0/70  Signal level:-121 dBm  Noise level:-111 dBm
           Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
           Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

not sure what to do :( 

Cheers for any support.

PS i am using Gnome on Ubuntu 6.06

---

### Post by orko3001 on 2007-02-18
Ok sused this one out myself :)  Installing in root seems to help. And by root I don't mean sudo or su. Also, and this may be it, you have to completely disable, deactivate, unenable the ethernet connection or it causes a conflice.

:guitar:

---

