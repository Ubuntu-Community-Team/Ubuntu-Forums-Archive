---
title: "Help: Ubuntu Switching Net Connections On Its Own"
date: 2005-08-07
forum: Networking &amp; Wireless
---

### Post by lauri on 2005-08-07
Hi!

I have four connections on my laptop (integrated LAN, PCMCIA LAN, WLAN and modem) that work well in general. The problem is that when I'm using wired LAN card, Ubuntu switches to WLAN every now and then. If I just deactivate WLAN from the network settings, it changes the connections so that if WLAN was eth1 and inactive, it becomes eth0 and active while the wired LAN becomes inactive eth1.

This sounds like a small problem but is enough to render Ubuntu useless for me when giving presentations etc.

Also, Ubuntu spends about a minute "Configuring network interfaces" every time I boot my machine.

Thanks,

Lauri

---

### Post by PeP on 2005-08-09
[QUOTE=lauri]Hi!

I have four connections on my laptop (integrated LAN, PCMCIA LAN, WLAN and modem) that work well in general. The problem is that when I'm using wired LAN card, Ubuntu switches to WLAN every now and then. If I just deactivate WLAN from the network settings, it changes the connections so that if WLAN was eth1 and inactive, it becomes eth0 and active while the wired LAN becomes inactive eth1.

This sounds like a small problem but is enough to render Ubuntu useless for me when giving presentations etc.

Also, Ubuntu spends about a minute "Configuring network interfaces" every time I boot my machine.

Thanks,

Lauri[/QUOTE]

IIRC ifrename assigns an interface name to a mac address.

It might help you there :-)
it seams quite easy to configure:
# /etc/iftab
 # interface 1
eth0* mac 00:0D:88:*
eth1* mac 00:0D:EA:*

where ethx is the name you give to the interface and 00:0D:88:*  is something that match only this interface mac address (HWadress field from ifconfig)

---

