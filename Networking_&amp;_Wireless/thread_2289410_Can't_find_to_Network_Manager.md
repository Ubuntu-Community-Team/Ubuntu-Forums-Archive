---
title: "Can't find to Network Manager"
date: 2015-08-03
forum: Networking &amp; Wireless
---

### Post by steve169 on 2015-08-03
I'm running but still configuring Lubuntu Mini 15.04 from a USB drive.

The final configuration is for my VPN, Private Internet Access (PIA). But I need Network Manager for access.

I've installed both openvpn and openvpn-gnome, but Network Manager doesn't appear in the start menu or the list of applications.

I know it's installed; Lubuntu Software Center says so. So did the PIA installation script when I ran it in Terminal. The script said it installed the configuration files in Network Manager. I can see the ca.crt file in /etc/openvpn.

At one point, the text in Terminal told me that if I wanted to use Network Manager, I'd must delete the reference to p1p5 in /etc/network/interfaces. I did, but then my browser, Midori, stopped working. It resumed working as soon as I restored the p1p5 reference.

So how do I bring up Network Manager? And how do I put it in charge so I can connect to PIA?

Once I do that, I'll be cruising.

[HR][/HR]
Below is information about my installation that might be helpful:
[INDENT][B]In /etc/NetworkManager/VPN/nm-openvpn-service.name:
[/B]
[/INDENT]
[INDENT=2][VPN Connection]
name=openvpn
service=org.freedesktop.NetworkManager.openvpn
program=/usr/lib/NetworkManager/nm-openvpn-service

[GNOME]
auth-dialog=/usr/lib/NetworkManager/nm-openvpn-auth-dialog
properties=/usr/lib/x86_64-linux-gnu/NetworkManager/libnm-openvpn-properties
supports-external-ui-mode=true
supports-hints=true\
[/INDENT]
[INDENT]

**In /etc/network/interfaces:**

[/INDENT]
[INDENT=2]# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

source /etc/network/interfaces.d/*

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto p5p1
iface p5p1 inet dhcp
[/INDENT]
[INDENT]

**In /etc/openvpn/:**

[/INDENT]
[INDENT=2]ca.crt (from Private Internet Access)
[/INDENT]
[INDENT]

**In /etc/run/network/ifstate:**

[/INDENT]
[INDENT=2]p5p1=p5p1
lo=lo
[/INDENT]

---

### Post by nerdtron on 2015-08-03
Have you tried installing network-manager-openvpn? I think that is the package needed to edit openvpn connection through the network manager gui.

---

### Post by steve169 on 2015-08-04
Both network-manager-openvpn and network-manager-openvpn-gnome are installed.

---

### Post by Bucky Ball on 2015-08-04
*Thread moved to **Networking & Wireless**.*

---

### Post by steve169 on 2015-08-14
Problem solved. Many thanks to you all.

---

### Post by Bucky Ball on 2015-08-14
Please mark the thread as solved (see first link in my signature) to help others and relate how you solved your issue ... to help others. Thanks.

---

