---
title: "Gutsy: 26 character wep wireless connection won't connect"
date: 2008-01-06
forum: Networking &amp; Wireless
---

### Post by mhenoklu on 2008-01-06
I recently installed Ubuntu Gutsy Gibbon at my parents' place and got the wireless working great. Now I am at school where they have a wireless connection with a 26 character WEP key. 
My printer that didn't work in my Vista installation works beautifully in my Ubuntu installation. So I set it up and sat there trying different settings to connect to the wireless network. Eventually it connected and I got online. The next day it would not connect, although it works fine in my Vista installation (which I am using to write this). 
I tried for hours to get it to connect and rebooted several times, but it will not connect. It would try to connect and then ask for the key, so I put it in and it would try for a while, then ask for the key again. 
I don't understand why it was able to connect once, but still needed the key the next time and still refused to connect.
 Does anyone have any suggestions?

---

### Post by MariusSilverwolf on 2008-01-06
It could be a variety of things, really, most of which depend on the chipset of the wireless card you're using.

What eventually worked for me was following the suggestions in this sticky post: [http://ubuntuforums.org/showthread.php?t=564419](http://ubuntuforums.org/showthread.php?t=564419)

I use Network Manager on my desktop, with the RT2250 drivers, and have my Wireless Set to manual configuration with the WEP Key saved using a static IP.  Every couple of days I get a lag where my system won't get online, but by changing the last octet of the address -- say from 192.168.1.100 to 192.168.1.101 -- I'm right back up and running.

On my laptop, which used a different chipset, I dumped Network Manager for WICD, and use that to handle my WEP connection at home with no problems.  WICD should be in your Synaptic packages, but if it's not, look here for information: [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

Good luck!

---

### Post by ubutufan on 2008-01-06
Edit /etc/network/interfaces. Make sure that the file has ONLY the following lines

auto lo
iface lo inet loopback

Nothing else. Save and reboot.

By the way I agree with the suggestion of using Wicd

---

### Post by mhenoklu on 2008-01-06
Hey, thanks for replying. I didn't install WICD because I don't have a wired connection to internet here. However, I followed the instructions from [http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188). 
When I typed in:  lshw -C network
It spit out:

*-network DISABLED
       description: Wireless interface
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth1
       version: 01
       serial: 00:1a:92:3d:f7:a8
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.22-14-gener

When I typed: sudo ifconfig eth1 up
SIOCSIFFLAGS: No such device

When I typed: sudo dhclient eth1

There is already a pid file /var/run/dhclient.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
SIOCSIFFLAGS: No such device
SIOCSIFFLAGS: No such device
Listening on LPF/eth1/00:1a:92:3d:f7:a8
Sending on   LPF/eth1/00:1a:92:3d:f7:a8
Sending on   Socket/fallback
receive_packet failed on eth1: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
send_packet: Network is down
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

I don't know what it means by 'DISABLED' nor repeatedly saying 'Network is down', but they don't seem to be normal nor good. 
It doesn't seem like a driver problem because it worked fine on another connection and worked once on this connection.

---

