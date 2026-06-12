---
title: "Linksys WMP54G wifi - network visible, cannot connect."
date: 2007-09-09
forum: Networking &amp; Wireless
---

### Post by gotrek_3city on 2007-09-09
Hello,

My problem is quite common - I cannot connect to wifi network. I''ll specify details below, but I just wanted to say, that I searched polish forums for help in the first place. I've also looked here and there on other distro's help wiki's. However, no one helped to solve problem at polish ubuntu forum. Dissappointing, is'nt it?

Ok, details: ubuntu 7.04, linksys wmp54g PCI wifi card (v4.1). (the rest of computer tech details are not important here, so lets just skip it...)

I've got a clean install of ubuntu. I can see my wifi  network at network manager, I enter 64/128 hex key... and after a minute or so, the connection is still not established.

Console printout:

[INDENT]
gotrek@gotrek:~$ iwconfig 
lo no wireless extensions. 

eth0 no wireless extensions. 

ra1 RT61 Wireless ESSID:"SpeedTouch96BFB7" Nickname:"" 
Mode:Managed Frequency:2.412 GHz Access Point: 00:14:7F:77:84:93 
Bit Rate=54 Mb/s 
RTS thr:off Fragment thr:off 
Link Quality=88/100 Signal level:-49 dBm Noise level:-79 dBm 
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0 
Tx excessive retries:0 Invalid misc:0 Missed beacon:0 

gotrek@gotrek:~$ dhclient ra1 
There is already a pid file /var/run/dhclient.pid with pid 6698 
Internet Systems Consortium DHCP Client V3.0.4 
Copyright 2004-2006 Internet Systems Consortium. 
All rights reserved. 
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/) 

can't create /var/lib/dhcp3/dhclient.leases: Permission denied 
Can't create /var/run/dhclient.pid: Permission denied 
drop_privileges: could not set group id: Operation not permitted 
gotrek@gotrek:~$ sudo dhclient ra1 
There is already a pid file /var/run/dhclient.pid with pid 6698 
killed old client process, removed PID file 
Internet Systems Consortium DHCP Client V3.0.4 
Copyright 2004-2006 Internet Systems Consortium. 
All rights reserved. 
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/) 

Listening on LPF/ra1/00:16:b6:51:6a:f3 
Sending on LPF/ra1/00:16:b6:51:6a:f3 
Sending on Socket/fallback 
DHCPDISCOVER on ra1 to 255.255.255.255 port 67 interval 7 
DHCPDISCOVER on ra1 to 255.255.255.255 port 67 interval 11 
DHCPDISCOVER on ra1 to 255.255.255.255 port 67 interval 13 
No DHCPOFFERS received. 
No working leases in persistent database - sleeping.
[/INDENT]

Addtionally:
mask 255.255.255.0 
DHCP, DNS servers and gate: 10.0.0.1

Please have a look down here: 
[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys) 
"Works only in Feisty if you put to "blacklist" the "rt61pci" module BEFORE install the card. If not, your computer will freeze often. There is an other module: "rt61" it works fine, with WEP too."

So, I discovered that AFTER trying to connect on my own. Any comments what shall I do?
I've not tried WICD or ndiswrapper yet, because I leave it to the last resort. Moreover, is ndiswrapper included in ubuntu 7.04?

I'm afraid that because of my tries I messed up networking configuration too much, so how can I erase anything to the state as I had on a fresh setup?

---

### Post by kevdog on 2007-09-09
Lets see what driver is currently associated with your card:

lshw -C network

If its not rt61pci then do the following:

echo "blacklist rt61pci" | sudo tee -a /etc/modprobe.d/blacklist

Restart the networking bus (among others)
sudo /etc/init.d/dbus restart

Some info about the rt module would also be useful, b/c Im betting that it would be better to upgrade your driver:
modinfo rt61

---

### Post by gotrek_3city on 2007-09-09
Wow, 
that was fast!:)
just give me half an hour, I'll just have to go home from work and try that.
Will give you results ASAP.

Best regards,
michal

---

### Post by gotrek_3city on 2007-09-09
Ok, here it is.

from lshw I've got:
[INDENT]gotrek@gotrek:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: Marvell Technology Group Ltd.
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@02:00.0
       logical name: eth0
       version: 12
       serial: 00:18:f3:f6:01:d1
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.13 firmware=N/A latency=0 multicast=yes
       resources: iomemory:fe8fc000-fe8fffff ioport:a800-a8ff irq:17
  *-network
       description: Wireless interface
       product: RT2561/RT61 802.11g PCI
       vendor: RaLink
       physical id: 1
       bus info: pci@05:01.0
       logical name: ra1
       version: 00
       serial: 00:16:b6:51:6a:f3
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=RT61STA driverversion=1.1.0 CVS latency=64 multicast=yes wireless=RT61 Wireless
       resources: iomemory:feaf8000-feafffff irq:22
 [/INDENT]

and from modinfo:
[INDENT]
gotrek@gotrek:~$ modinfo rt61
filename:       /lib/modules/2.6.20-15-generic/kernel/ubuntu/wireless/rt2x00-legacy/rt61/rt61.ko
license:        GPL
description:    Ralink RT61 802.11abg WLAN Driver 1.1.0 CVS CVS
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
srcversion:     180F8980D3385B365E8F654
alias:          pci:v00001814d00000401sv*sd*bc*sc*i*
alias:          pci:v00001814d00000302sv*sd*bc*sc*i*
alias:          pci:v00001814d00000301sv*sd*bc*sc*i*
depends:        
vermagic:       2.6.20-15-generic SMP mod_unload 586 
parm:           debug:Enable level: accepted values: 1 to switch debug on, 0 to switch debug off. (int)
parm:           ifname:Network device name (default ra%d) (charp)
[/INDENT]

So, I added rt61pci to blacklist. I've no idea if thats rellevant, but the only option I have under network manager is manual configuration. How can i reset that to initial/old options layout? What would be the next step to fix that wifi connection?

Best regards,
Michal

---

### Post by gotrek_3city on 2007-09-09
small kick to bring it up!:)

really hope for some help people. ANY comments will be appreciated, i promise.

---

### Post by blakegrover on 2007-09-11
I too can not connect with the same card.  I can see the networks but it never connects.

Blake

---

