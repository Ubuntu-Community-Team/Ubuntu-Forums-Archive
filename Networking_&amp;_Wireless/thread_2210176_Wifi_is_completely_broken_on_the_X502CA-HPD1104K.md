---
title: "Wifi is completely broken on the X502CA-HPD1104K"
date: 2014-03-09
forum: Networking &amp; Wireless
---

### Post by weegee205 on 2014-03-09
I recently installed Ubuntu alongside Windows 8 on my "Netbook" (Not really a netbook). The System has 4 GB RAM and a Pentium @ 1.8 GHz, and I knew that would be decent. It was, everything worked great, both OS's booted. But in Ubuntu, it will connect to my wifi, but it will disconnect 5 seconds later for no reason. After this, it fails to see the network I just tried to connect to. I turn on the guest network, and try again, but same result. I cannot get on the internet with Ubuntu 13.10 at all! Oh no!

I used the 64 bit version because Windows was 64 bit on my machine and the processor was as well.

---

### Post by praseodym on 2014-03-09
Please open a terminal with CTRL+ALT+T and show the outputs of:
```

lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
cat /etc/resolv.conf
```
Does LAN work?

---

