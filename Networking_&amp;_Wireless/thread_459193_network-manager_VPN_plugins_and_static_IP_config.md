---
title: "network-manager VPN plugins and static IP config"
date: 2007-05-30
forum: Networking &amp; Wireless
---

### Post by Explodinglemur on 2007-05-30
I'm trying to make use of the gnome-network-manager VPN plugins (openvpn and vpnc specifically) on my office desktop.  I have it manually configured with a static address, we do not use DHCP here.  I can't get the VPN menu to show up.  If I set my network device to roaming mode, the VPN menu shows up, but then obviously my network interface no longer works.  How can I make use of the VPN plugins using a manually-configured network interface?

(I don't need these VPN connections up all the time, only when performing some troubleshooting tasks, which is why I'd like to be able to bring them up/down easily through network-manager)

---

### Post by kehan on 2008-05-07
I'm having this issue too - subscribing

---

### Post by chuck7 on 2008-05-20
Same thing for me. And It bugs me a lot. If anybody has a workaround for that issue, it would be greatly appreciated.

Thanks.

---

### Post by scorp123 on 2008-05-22
Guys, if you use PPTP (aka "Windows VPN") take a look at this URL:

[http://kutuma.blogspot.com/2007/05/vpn-in-ubuntu.html](http://kutuma.blogspot.com/2007/05/vpn-in-ubuntu.html)


What the author of that blog article suggests is that you create a PPP profile using "pptpconfig" and then launch it using the "pon" shell command. You could also create a nice launcher icon for this so you'd launch it with a click of a mouse button.

I haven't yet had the time to try this but this looks like a good workaround.

---

