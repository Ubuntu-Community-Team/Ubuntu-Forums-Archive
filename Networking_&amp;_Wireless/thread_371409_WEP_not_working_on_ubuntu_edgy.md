---
title: "WEP not working on ubuntu edgy"
date: 2007-02-26
forum: Networking &amp; Wireless
---

### Post by jeet on 2007-02-26
My machine's wireless setup which had been working for a while, is not working anymore. I had switched off the m/c off for a few days ago and installed and configured samba. When I start the machine it seems to get dhcp address from my dhcp server (another linux box) but soon after if i run ifconfig, the wireless interface (wlan0) does not
have the ip anymore. I can see in the logs of the m/c running dhcp server
that the dhcp discover request came and address was offered as per following
log messages:

Feb 24 19:44:57 nangal dhcpd: DHCPDISCOVER from 00:40:05:b3:75:ab via eth0
Feb 24 19:44:57 nangal dhcpd: DHCPOFFER on 192.168.1.236 to
00:40:05:b3:75:ab via eth0

Also when I run "sudo dhclient eth1" I see in dhcp server m/c offering ip
address but nothing happens on the ubuntu m/c that needs dhcp address.

Also running "sudo iwconfig wlan0" shows all the settings on the wireless
interface are ok.

 My machine has a Dlink 520+ wireless adapter card that has
acx100 chipset and I have WEP enabled on my wireless router.


What could be going wrong here? I am sure I must have changed something that
I do not remember that is causing this problem.

---

