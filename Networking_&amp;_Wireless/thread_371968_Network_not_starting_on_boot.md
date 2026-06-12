---
title: "Network not starting on boot"
date: 2007-02-27
forum: Networking &amp; Wireless
---

### Post by toddhd on 2007-02-27
I apologize if this is a dumb question, I'm still trying to figure out Linux networking. The other day, I figured out how to get my PC online using WPA-PSK (see [http://ubuntuforums.org/showthread.php?t=370826](http://ubuntuforums.org/showthread.php?t=370826)) but now I have one more problem. When I reboot my PC, the network does not startup automatically. In order to start it, I go into terminal and type:

sudo /etc/init/d/networking restart

And after a minute of running through some various processes, it starts.

How can set this up so that I don't have to do this each time?

Thanks for any help you can offer.

---

### Post by maestrobwh1 on 2007-02-27
I have the same issue... I think.  I have to open wlassistant, and click my network to get it to connect.  I put a thread out yesterday.

---

### Post by toddhd on 2007-02-27
After reading some more posts, I've seen people ask for the following info, so I might as well post it now. Most of the posts I see regarding this issue were related to some bug in 6.06 - I am working on 6.10 with all the updates run. Not sure what the problem is - wish I wasn't  such a linux noob.

todd@todd-laptop:~$ sudo ifdown eth1
There is already a pid file /var/run/dhclient.eth1.pid with pid 4726
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:16:6f:36:58:51
Sending on   LPF/eth1/00:16:6f:36:58:51
Sending on   Socket/fallback
DHCPRELEASE on eth1 to 192.168.1.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.

todd@todd-laptop:~$ sudo ifup eth1
There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:16:6f:36:58:51
Sending on   LPF/eth1/00:16:6f:36:58:51
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 18
DHCPOFFER from 192.168.1.1
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.5 -- renewal in 35342 seconds.
todd@todd-laptop:~$ 

Here is my interfaces file. I commented out the things I don't use.

auto lo
iface lo inet loopback

#auto eth0
#iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
wpa-driver wext
wpa-conf managed
wpa-ssid SeaburyDesign
wpa-ap-scan 1
wpa-proto WPA
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk 3fd41f81a7999ca38602767e209d3024f1f6581aa8fac33d642bd5e5b49116f9

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp

---

