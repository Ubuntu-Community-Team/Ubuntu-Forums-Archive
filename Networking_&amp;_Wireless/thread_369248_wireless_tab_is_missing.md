---
title: "wireless tab is missing"
date: 2007-02-24
forum: Networking &amp; Wireless
---

### Post by bitman09 on 2007-02-24
I've installed Edgy Eft and having problems configuring my wireless card. The computer only has a wireless card (broadcom) so connecting a hard wired internet connection is not an option. I have successfully installed ndiswrapper 1.8, loaded the driver (bcmwl5.inf) and installed network-manager-gnome. The problem is now the Wireless Connection tab is now missing from the network settings. The only option avail is Modem Connection. The steps I have taken are as follows:

//kernel 2.6.17-10-generic

download bcm4318*.tar.gz
cd ~/Desktop
tar -xf bcm4318*.tar.gz
~/Desktop$ sudo ./ndiswrapper_setup

Ndiswrapper installed succesfully, it then gives intructions for installing a network manager. I chose network-manager-gnome from the synaptic package manager. 

I ran ndiswrapper -l 
Installed driver:
bcmwl5           driver installed, hardware present

I ran iwconfig
lo      no wireless extensions
sit0    no wireless extensions  (these were the only output displayed)

I then opened
sudo gedit /etc/ifteb/
-etho mac 00:30:bd:99:99:c1 arp1

I ran lspci and my card was listed as follows
00:0e.0 Network Controller Broadcom Corporation BCM4306 802.11b/g Wireless Lan Controller (rev 02)

I tried a reboot but that did not help.

I have been using Linux for almost two months, I'm still very lost and confused. If any one could give some guidance on how to resolve this I would be greatly appreciative. Thank You.

---

### Post by spd106 on 2007-02-24
The functions of the network-admin capplet are replaced by Network Manager's nm-applet.

Have a read through this wiki page [https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager)

---

