---
title: "Wireless issue"
date: 2006-08-12
forum: Networking &amp; Wireless
---

### Post by Bisen on 2006-08-12
Hi there.

Yesterday i installed Ubuntu 6.06.1 LTS, and everything works great, but not the wlan (except when theres no WPA on the network).

I've installed Network Manager, but it dont find any networks, and theres a little warning-sign in the corner in front of the NM icon.

In the Administration>Networking menu, it finds my network, and the people who lives next door. But i can't find a place to write the WPA key?

Please help me. It's pretty annoying to have a laptop without wlan. :shock:

---

### Post by spd106 on 2006-08-12
For Network Manager to find the wifi interface you need to disable it in the network-admin applet and remove any configuration lines from the /etc/network/interfaces file except for lo.
[https://wiki.ubuntu.com/DapperNetworkManager](https://wiki.ubuntu.com/DapperNetworkManager)

---

### Post by Neobuntu on 2006-08-12
The Network Manager is a cool add on but as I understand it, it's for when you want your laptop to AUTOMATICALLY switch to and from hardwired ethernet when it is phsically plugged into it. When unplugged it uses WiFi. This can be good for work vs. home Internet situations.

So if you want one or the other don't install Network Manager. Just set it do do what you want on boot.

BTW, you have wireless networking, just not wpa. That might depend on your particular device. The good news is two fold.

First Wireless devices are dirt cheap, check ubuntu compatibility first and order one. I got one for $9.99 USD shipped, no tax, no gas (total)!

Second, there are other things you can do besides WPA to make your wireless network more secure. You could set up static addressing (because it's faster booting) and enter your devices MAC addresses where only they can connect. MAC address spoofing MIGHT be beyond the ability of your close by neighbors. Also, when you have proper fire walls(inheirant to GNU/Linux) and file sharing set up properly, The worse case might be the MAC spoofing; close by neighbor could only use your internet bandwidth. If you router is setup correctly, you should be able to monitor this.  

Just my two cent. I'm not recommending unsecure wireless. The fact is though, nothings perfectly secured, especialy wireless.

---

