---
title: "[SOLVED] Netgear WG111v2 Problems"
date: 2008-04-26
forum: Networking &amp; Wireless
---

### Post by doorknob60 on 2008-04-26
Well, using both ndiswrapper and the default p54usb module, I can get it to scan for networks and it sees my network and my neighbors' so everything should be working fine. But, when I try to get an IP with DHCP, it just doesn't work (very well). Using ndiswrapper, I've only gotten it to work once, and it worked great....until I restarted, and I couldn't get it to work again. Using the p54usb module, it always connects, but then it disconnects a few minutes later, and you need to pull the adapter out, plug it back in, and reconnect to gt back on the internet for a few minutes. This is on my new (but very old) laptop with these specs:

Qompaq Presario 1600s
64 MB of RAM (soon to be upgraded)
AMD K6 400mhz
5 GB Hard Drive
Fluxbuntu 7.10
Netgear WG111v2 USB Wireless adapter

I've tried the Ubuntu Wiki, many guides on the forums and other sites, but nothing seems to be working right (I'm pretty experienced in troubleshooting with wireless and ndiswrapper, I had many problem's on my parents' laptop with Broadcom...bleck) :(

Here's some terminal output when it tries to connect with ndiswrapper:

```

root@presario:/media/cdrom0/ndis5# dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:14:6c:2b:01:ad
Sending on   LPF/wlan0/00:14:6c:2b:01:ad
Sending on   Socket/fallback
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
ip length 576 disagrees with bytes received 577.
accepting packet with data after udp payload.
DHCPOFFER from 192.168.1.1
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
ip length 576 disagrees with bytes received 577.
accepting packet with data after udp payload.
DHCPOFFER from 192.168.1.1
DHCPREQUEST on wlan0 to 255.255.255.255 port 67

root@presario:/media/cdrom0/ndis5# 

```

It just repeats that forever, and that one time that it worked, it went for a few minutes then just worked. When it uses the p54usb driver, the first time it connects quickly like it should, then subsequent times it does just what ndiswrapper does. Could it be the age of my computer, because I got it working on my dad's AMD64 perfectly with the driver it defaulted to without problems for hours (it has built in wifi, I was just testing this. Yes, I disabled the built in). Also, it seems to kinda work on my desktop, but last time I tried it, it crashed it randomly, but the point is, that I need wireless badly because I can't connect it to ethernet because it doesn't have an ethernet port...Help Please!!

---

### Post by doorknob60 on 2008-04-26
Bump!

---

### Post by nojjy on 2008-04-28
Bump bump!

---

### Post by doorknob60 on 2008-04-28
Feel free to keep bumping this topic if you're having the same problem, but I just bought a PCMCIA Card with an Atheros chipset and it works wonderfully (Netgear WG511T) so I won't bee looking back here much if at all.

---

### Post by glibik on 2008-09-09
Can't help you with trouble shooting your particular issue, sorry.  
All I can do is tell you that I have a WG111v2 USB adaptor and it worked out-of-the-box with Gutsy Gibbon, and is still working fine with Hardy Heron on my Dell Latitude D810.

AFAIK ndiswrapper is not being used.  During the OS install and after, I didn't have to do anything at all specific to the adaptor on the laptop.  I only needed to configure my access point to accept packets from the adaptor's MAC address.

---

### Post by doorknob60 on 2008-09-09
OLD THREAD!!! Gravedigger...I solved this problem like...5 months ago. I bought a PC Card so I didn't have to use it's one and only USB port, the USb adapter works fine on other computers. Anyways, I probably should've marked this solved though. Tim to do that.

---

