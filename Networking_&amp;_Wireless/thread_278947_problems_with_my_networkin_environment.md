---
title: "problems with my networkin environment"
date: 2006-10-17
forum: Networking &amp; Wireless
---

### Post by spirobit on 2006-10-17
Hello community.

:-k 
I have massive problems with my network environment in Dapper Drake. After the installation of UBUNTU and KUBUNTU and the configuration of my LAN and W-LAN adapter (D-LINK DWL-122 with prism2 chip) the network was working very well. I took this link:
http//wiki.ubuntuusers.de/T-Sinus_111_data
But what's the meaning of this line:
sudo update-rc.d startwlan start 20 2 .? Where is the target-file for this command?
I'm taking static ip adresses and WEP.

After that - unfortunately, i had changed my IP adresses because my laptop was working with the same addresses. And now - i have a big problem:
All my network connections are dead. I don't get a ping on the nework cards itself and no ping to the router.
The network applet is showing me 86% field strength and both adapter and the symbols are blinking.
A check with:
[http://wiki.ubuntuusers.de/MA111DWL122](http://wiki.ubuntuusers.de/MA111DWL122)
was not successful. Also to restart my computer or the network environment (with sudo /etc/init.d/networking restart. Brings the error: Error for wireless request "Set encode" (8B2A): SET failed on device wlan0 and Error for wireless request "Set ESSID" (8B1A): SET failed on device wlan0). Because i tried to change the file /etc/network/interfaces:

auto lo
iface lo inet loopback

iface eth0 inet static
address ...

iface wlan0 inet static
address ...
wireless-essid SSID
wireless-key 45:3d:22:21:37:73:24 ...

...

The routing table (command route) is showing me correct details. This is - now - the content of my /etc/network/interfaces file:
auto lo
iface lo inet loopback

iface eth0 inet static
address 192.160.2.118
netmask 255.255.255.0
gateway 192.160.2.1

iface wlan0 inet static
address 192.160.2.119
netmask 255.255.255.0
gateway 192.160.2.1

auto wlan0
auto eth0

my hosts:
192.160.2.119 mypc
192.160.2.1 router
...

Is it possible to edit the routing table direct?
How can i edit all the requested files or where can i find detailed informations about the configuration files of Dapper Drake or DEBIAN? 
Is it possible to check the complete network environment in a good order? How can i do that?
Is it possible or necessary to reinstall the hole network environment?

Many thanks for your help
spirobit

---

