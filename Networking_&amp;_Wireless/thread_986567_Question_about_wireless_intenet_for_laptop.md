---
title: "Question about wireless intenet for laptop"
date: 2008-11-18
forum: Networking &amp; Wireless
---

### Post by sbriggman on 2008-11-18
Hi,

I have a Compaq Presario V5101us. I tried to use internet in ubuntu and it wouldn't work. The wireless buttons arn't clickable. It's like it's not picking up the signal. It tried punching in the name of the network and the wep key and it still wouldn't work.

I went to the help menu and asked it what to do. It said to enter a command and this was the terminal's response

*-network:0 DISABLED
description: Wireless interface
physical id: 2
logical name: wlan0
serial: 00:14:a5:7b:3d:21
capabilities: ethernet physical wireless
configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
*-network:1 DISABLED
description: Ethernet interface
physical id: 3
logical name: pan0
serial: ee:b2:17:4e:d1:65
capabilities: ethernet physical
configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
ubuntu@ubuntu:~$ *-network:0 DISABLED

So, it says it's disabled... well... how do I enable it. When I go into windows, wireless works fine. Just ubuntu won't let me use it. What should I do.

---

### Post by spiderbatdad on 2008-11-18
What version are you running, please? You might try disabling wep for now. It isn't working consistently in 8.10 yet. WEP is fundamentally worthless anyway...it is not better than nothing by all accounts.

---

### Post by sbriggman on 2008-11-18
I just downloaded Ubuntu from this site, so the newest version.

I can't take off wep because my Dad wants it on.

---

### Post by spiderbatdad on 2008-11-18
well try this:
```
sudo iwconfig eth1 essid Name_of_your_AccessPoint ##note your wireless interface maybe wlan0 instead of eth1...or wifi0, run iwconfig first to see.
sudo iwconfig eth1 key xxxxxxxxxx
sudo ifconfig eth1 up
sudo dhclient
```

---

