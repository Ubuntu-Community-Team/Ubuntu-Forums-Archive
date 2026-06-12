---
title: "networking is screwed"
date: 2008-05-24
forum: Networking &amp; Wireless
---

### Post by nzadLithium on 2008-05-24
Hey 

I upgraded to hardy last night. During the install i saw an error and tried to copy / paste it. I tried selct then right click. Didnt work. So I tried ctrl + c. I suddenly realised it was a terminal and was like oh crap. During the remainder of the installation it continually brought up errors about brocken dependencies. When it finished it then said there had been an error. It then proceeded to reinstall everything that didnt get installed from brocken dependencies. All seemed good. I restarted and all seemed to be going. Then i tried the internet. It just sat on looking up website. It seemed if i tried enough occasionally it would load a webpage. I think it did twice in about half an hour of trying to get webpages while screwing round with network manager. 
I couldnt get to go so on another pc I went on ubuntu forums and went to networking. I saw the sticky about setting up net without network manager so I followed that. it seems if I continually type sudo dhclient wlan0 then the internet goes fine for a period of about 10 seconds. 
What is going on and how do I fix it?

It seems I am meant to get this:
```
user@computer:~$ sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:12:17:35:17:10
Sending on   LPF/wlan0/00:12:17:35:17:10
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPOFFER from 192.168.1.1
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.101 -- renewal in 299133 seconds.
```

but I am getting
```
There is already a pid file /var/run/dhclient.pid with pid 8344
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:40:f4:c9:58:cb
Sending on   LPF/wlan0/00:40:f4:c9:58:cb
Sending on   Socket/fallback
DHCPREQUEST of 192.168.1.65 on wlan0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.65 from 192.168.1.1
bound to 192.168.1.65 -- renewal in 40630 seconds.

```
As you can see I am missing a few lines:
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPOFFER from 192.168.1.1
Could these lines missing be the problem?

My routing tables seem to be alright. I think they are same as gutsy.
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0

```

And resolve.conf
search xtra.co.nz
nameserver 202.27.158.40
nameserver 202.27.156.72
nameserver 192.168.1.1
any ideas?

---

### Post by chili555 on 2008-05-24
The differences between the two are trivial; one took longer than the other. In both cases, you connected and got an IP address. What do your ping times look like:```
ping -c3 192.168.1.1
ping -c3 202.27.158.40
ping -c3 74.125.47.147
```Thanks.

---

### Post by nzadLithium on 2008-05-24
Thx for the reply. I figured it out though. I deleted pretty much my whole interfaces file. Then i reset up using network manager. It added the stuff I needed to the file. Then I went through the how to again. It still wouldnt connect. I found it was because i didnt put quotes around the essid. It goes fine finally! :)

---

### Post by nzadLithium on 2008-05-25
Ok i still have the problem. That way fixes it but upon restart its screwed up again. Is there any way I can make these changed permanent other than adding to a boot script? If there isnt then which boot script is best to add them too?

---

### Post by chili555 on 2008-05-25
The way to make the changes permanent is to add them to */etc/network/interfaces*. If this is a stay-at-home comuter, I'd suggest uninstalling Network Manager and dhcdbd. Then set up all your details in *interfaces* similar to this:```
auto lo
iface lo inet loopback

#auto eth0
iface eth0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid myrouter
```Then your network should connect automatically as you boot.

---

### Post by nzadLithium on 2008-05-26
I need some help setting up. No matter how i set it i still have to run all those commands.

This is the output from dhclient (so you can see netmask ip addy etc):
```
Listening on LPF/wlan0/00:40:f4:c9:58:cb
Sending on   LPF/wlan0/00:40:f4:c9:58:cb
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPOFFER of 192.168.1.66 from 192.168.1.1
DHCPREQUEST of 192.168.1.66 on wlan0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.66 from 192.168.1.1
bound to 192.168.1.66 -- renewal in 41280 seconds.
```

this is what i have to run to get it up:
```
sudo ifconfig wlan0 down
sudo dhclient -r wlan0
sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid "linksys"
sudo iwconfig wlan0 key ##########
sudo iwconfig wlan0 mode Managed
sudo dhclient wlan0
sudo ./iptables.sh
```
iptables is for internet sharing.

Heres what I have in my /etc/network/interfaces currently:
```
auto lo 
iface lo inet loopback

auto eth1
auto eth2 (none of these three exist but ubuntu stuck them in so i left)
auto ath0

auto eth0
iface eth0 inet static
address 192.168.1.2
netmask 255.255.255.0 (this is the device I have other pc sharing net connected to)

auto wlan0
iface wlan0 inet dhcp
gateway 192.168.1.1
netmask 255.255.255.255
wireless-key ############
wireless-essid "linksys"
```

any ideas what i've done wrong?

And just as a random question if i'm running a game like quake and I make this pc the server, can I have both the computer connected to my ethernet port plus the other pcs connected through wireless router playing with each other at same time?

Thanks

---

