---
title: "NM-Applet is not showing in notification area..."
date: 2008-02-19
forum: Networking &amp; Wireless
---

### Post by kingpotnoodle on 2008-02-19
I wanted to configure OpenVPN so I installed network-manager-openvpn and went looking for the network manager... and realised I've never had it appear in the notification area since install as far as I can remember.

The NetworkManager and NetworkManagerDispatcher processes are running and under System/Preferences/Sessions/Current Session  I have nm-applet --sm-disable showing with a life belt symbol next to it,

What does -sm-disable do?

I tried removing --sm-disable in Startup Programs entry for Network Manager but when I logged off and back in it still says the same in current sessions... full reboot required?

If I open a terminal and type sudo nm-applet then it appears in notification area but obviously closes when the terminal is closed, and I have none of the supposed VPN menu items when I left click the icon.

So why isn't it starting properly when I log in and where are my VPN options? Any Ideas?

EDIT:

I do have the VPN options if I enable roaming mode...

Thanks in advance :-)

---

### Post by spd106 on 2008-02-22
As you probably have suspected by now, Network Manager (NM) doesn't support static settings, it only does DHCP at the moment. The way NM has been integrated into the desktop is to use the old network-admin for static or manual configuration and basically roaming mode is NM.

So if you want to have static settings I believe you'll have to find another VPN manager, unfortunately I can't really help you with that.

NM 0.7 will have much improved support for these kinds of things, so you might want to give Fedora a try, or maybe test out a Hardy alpha, though they don't recommend that you use it for a production environment yet.

---

