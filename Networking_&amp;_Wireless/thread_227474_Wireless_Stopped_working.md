---
title: "Wireless Stopped working"
date: 2006-08-01
forum: Networking &amp; Wireless
---

### Post by stormblue on 2006-08-01
I have a Senao card that just stoppped work recently.  I can get connected using the ethernet port.

I am running a script to get it up and running:
```

#/bin/bash
sudo ifconfig eth2 up
sudo iwconfig eth2 essid Thepizzabox
sudo iwconfig eth2 key open ADC8015C8CDC98CA9011CEABA7
sudo dhclient eth2
```

and I get this as output:
```

Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth2/00:02:6f:21:c5:cc
Sending on   LPF/eth2/00:02:6f:21:c5:cc
Sending on   Socket/fallback
DHCPREQUEST on eth2 to 255.255.255.255 port 67
ip length 314 disagrees with bytes received 534.
accepting packet with data after udp payload.
DHCPACK from 192.168.1.1
bound to 192.168.1.3 -- renewal in 22998 seconds.
bluestorm@blackbox-4du8nm:~/Shell Scripts$

```

I am unable to access my router through my wireless card.

here is the iwlist eth2 scan results
```
eth2      Scan completed :
          Cell 01 - Address: 00:0F:B5:ED:7F:D2
                    ESSID:"Thepizzabox"
                    Mode:Master
                    Encryption key:on
                    Frequency:2.412 GHz (Channel 1)
                    Quality:236/0  Signal level:-26 dBm  Noise level:-6 dB
```

Any ideas on what could be the problem?  I think it's been down for about 2 days or so.

---

### Post by amp_man on 2006-08-02
well, just for kicks and giggles, try "sudo iwconfig eth2 mode managed" and then try to connect.

---

### Post by Grog140 on 2006-08-04
I have a siliar problem and when I try that I get back:

```
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Operation not permitted.

```

hmm...

---

### Post by stormblue on 2006-08-04
I tried the managed mode trick, but I found I had to comment out IPv6 stuff becuase of the new kernal it appears.

If you get an error about permissions, try putting "sudo" infront of the command and that should do the trick.

---

### Post by Grog140 on 2006-08-04
I just got mine working, lol....

I read in another thread that he had a key combo that disabled is wireless car via the FN + F2. He discovered that because it had a picture on it that looked like a wireless beacon, mine had NOTHING! So I puched the combo for the hell of it and I have wifi again, WOO.

---

