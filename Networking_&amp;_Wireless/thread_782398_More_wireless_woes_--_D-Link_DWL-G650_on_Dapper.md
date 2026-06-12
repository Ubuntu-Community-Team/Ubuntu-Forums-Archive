---
title: "More wireless woes -- D-Link DWL-G650 on Dapper"
date: 2008-05-04
forum: Networking &amp; Wireless
---

### Post by songspring on 2008-05-04
Hello all--Running Obuntu 6.06 on a Toshiba Satellite 1805, and having problems getting my wireless D-Link DWL-G650 going.  Hoping you all can help.  This is the 3rd card I've tried, and supposedly it works "out of the box."

I'm really a noob as well, but I hope this info is a start:

> sp@satellite1805:~$ sudo lshw -C network
Password:
  *-network
       description: Ethernet interface
       product: 82557/8/9 [Ethernet Pro 100]
       vendor: Intel Corporation
       physical id: a
       bus info: pci@00:0a.0
       logical name: eth0
       version: 0d
       serial: 00:00:39:59:91:a6
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=e100 driverversion=3.4.14-k4-NAPI duplex=full firmware=N/A ip=192.168.1.118 link=yes multicast=yes port=MII speed=100MB/s
       resources: iomemory:f7efe000-f7efefff ioport:ef40-ef7f iomemory:f7ec0000-f7edffff irq:11
  *-network
       description: AR5001-0000-0000
       product: Wireless LAN Reference Card
       vendor: Atheros Communications, Inc.
       physical id: 0
       version: 00
       slot: Socket 0
       resources: irq:11
  *-network
       description: Wireless interface
       product: AR5212 802.11abg NIC
       vendor: Atheros Communications, Inc.
       physical id: 1
       bus info: pci@02:00.0
       logical name: ath0
       version: 01
       serial: 00:13:46:a0:24:63
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci driverversion=0.9.6.0 (EXPERIMENTAL) multicast=yes wireless=IEEE 802.11
       resources: iomemory:22000000-2200ffff irq:11


I'm happy to do whatever anyone suggests to try to get this thing going, and gratefully so.  Thanks so much.

Susan

---

### Post by chili555 on 2008-05-05
NetworkManager, which is installed by default, will not allow a wireless connection, if wired has a good connection with an IP address, which you do:```
ip=192.168.1.118 link=yes
```Please see here: [https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager) and, especially this:> The computer should use the wired network connection when it's plugged in, but automatically switch to a wireless connection when the user unplugs it and walks away from the desk. Likewise, when the user plugs the computer back in, the computer should switch back to the wired connection. The user should, most times, not even notice that their connection has has been managed for themPlease detach the wire and restart networking:```
sudo /etc/init.d/networking restart
```Does your wireless come to life?

---

### Post by songspring on 2008-05-05
Hi Chili! :KS Thanks so much for your response.  I had uninstalled Network Manager as I read somewhere to do that.  I reinstalled it, and followed the instructions on the page you referred me to, and voila!  I'm online wirelessly.  I'm amazed it could have been that simple all along.  I've been working on this thing for days.

Thank you very, very much.  If you are ever in Chico, CA, I'll cook you up some dinner, buy you a beer, whatever you like.  I am absolutely delighted.  

Many blessings to you!

Susan

:)

---

### Post by chili555 on 2008-05-05
Glad it's working for you! Thanks for your kind comments.

Prime beef, medium, and a gin martini with extra olives. Thanks for the very kind invitation.

---

### Post by songspring on 2008-05-05
Dinner sounds wonderful.  I haven't had prime rib or a gin martini (with extra olives) in ages.  I'm so glad I finally asked for help, and that you were there to provide it.  It's damn hard to figure out how to do things when you don't know your way around the OS.  Now, thanks to you, I can play around with the OS and get to know a thing or two, and possibly be able to help someone else.

When I was trying to get a Netgear WG511 working on this machine, I had called an independent computer tech neighbor of mine and he said he knew nothing of Ubuntu that he only worked on systems where he could make money.  When I mentioned this to my son (another geek) and a couple of techs at work, they all thought that was short-sighted thinking.  My son said, "He may want to rethink that because Dell is shipping out sytems with Ubuntu on it now."  

Hey, if the neighbor guy is going his route, that just makes room for me once I get myself up to speed and confident.  Right?

Thanks again for your help, Chili.  Prime rib and martinis are easily gotten in Chico.  Just give me a heads up and you're on for dinner.  My treat.

Best to you,
Susan

---

### Post by soch on 2008-05-18
After unchecking the "Ebable roaming mode" for the wirless "atho" properties, I get the errror "unknown hardware address type 801" for wifi when I run the cmd:

sudo /etc/init.d/networking restart

 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.ath0.pid with pid 7086
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi1: unknown hardware address type 801
wifi0: unknown hardware address type 801
wifi1: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:05:4e:41:99:8f
Sending on   LPF/ath0/00:05:4e:41:99:8f
Sending on   Socket/fallback
There is already a pid file /var/run/dhclient.ath0.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi1: unknown hardware address type 801
wifi0: unknown hardware address type 801
wifi1: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:05:4e:41:99:8f
Sending on   LPF/ath0/00:05:4e:41:99:8f
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by Ryuhayabusa on 2009-04-30
I'd recommend upgrading to hoary. This got WEP and WPA-PSK working for me.

---

