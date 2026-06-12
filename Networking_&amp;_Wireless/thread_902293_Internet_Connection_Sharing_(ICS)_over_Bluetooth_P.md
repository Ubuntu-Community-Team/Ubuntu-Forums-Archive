---
title: "Internet Connection Sharing (ICS) over Bluetooth Personal Area Network (PAN)"
date: 2008-08-27
forum: Networking &amp; Wireless
---

### Post by ub78 on 2008-08-27
Hi guys,

so I got this old PC (SERVER). I installed ubuntu and connected it to a DSL modem. Ubuntu is great, all working fine!
I want to use this machine as a router (among others..) and share the internet connection with two WinXP machines. These are a desktop (CLIENT-LAN) connected through cable and a laptop (CLIENT-BT) which I'd like to connect through bluetooth.

The SERVER has two ethernet cards and a bluetooth dongle:
**pan0** is the bluetooth dongle enabled for networking services. CLIENT-BT should connect to it but I don't know how to do it yet so I'll write more about this later on, see below...
**eth0** is the first ethernet card connected to a DSL modem and configured as dhcp 
**eth1** is the second ethernet card connected to CLIENT-LAN and configured as:
[INDENT]a static IP 192.168.0.1
Subnet Mask 255.255.255.0[/INDENT]

for the sake of clarity (and it might be useful to others) I got the ICS with CLIENT-LAN working as follows:

**SERVER configuration:**
[INDENT]1) adding the iptables rules
[INDENT]$sudo iptables -A FORWARD -i eth0 -o eth1 -s 192.168.0.0/24 -m state --state NEW -j ACCEPT
$sudo iptables -A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT
$sudo iptables -A POSTROUTING -t nat -j MASQUERADE [/INDENT]

2) enabling routing
[INDENT]$sudo sh -c "echo 1 > /proc/sys/net/ipv4/ip_forward"[/INDENT]

3) adding a firestarter rule allowing incoming connection from CLIENT-LAN (192.168.0.10) (I guess I could have done this manually with iptables but never mind..)

[/INDENT]**CLIENT-LAN configuration:**
[INDENT]IP: 192.168.0.10 (needs to be in eth1 subnet!)
Subnet Mask: 255.255.255.0
Gateway: 192.168.0.1
DNS Server: 192.168.0.1 (not 100% sure though...)
2nd DNS Server: 208.67.222.222 (openDNS)
[/INDENT]

All right, so that should do it.
I'd like to make something similar with the pan0 device. Actually, I'd like to start a NAP :) (Network Access Point) which is visible and recognized by the CLIENT-BT and then connect. However I'm not sure about how to do this as most of the information I got seems to be sligthly outdated:
[LIST]
[*][http://bluez.sourceforge.net/contrib/HOWTO-PAN](http://bluez.sourceforge.net/contrib/HOWTO-PAN)
[*][https://help.ubuntu.com/community/BluetoothSetup](https://help.ubuntu.com/community/BluetoothSetup)
[*][https://help.ubuntu.com/community/PalmBluetoothHowto](https://help.ubuntu.com/community/PalmBluetoothHowto)
[*][http://www.klabs.be/~fpiat/linux/bluetooth/bluetooth_HOWTO.html](http://www.klabs.be/~fpiat/linux/bluetooth/bluetooth_HOWTO.html)
[*][https://bugs.launchpad.net/ubuntu/+source/bluez-utils/+bug/172823](https://bugs.launchpad.net/ubuntu/+source/bluez-utils/+bug/172823)
[/LIST]

I'm using bluez-gnome1.1 ([http://www.bluez.org/bluez-gnome-11/](http://www.bluez.org/bluez-gnome-11/)) and it seems that some services and paths are different with respect to previous versions. 
Also I'm not sure that what previously was contained in the "BlueZ-PAN 1.0" package is now already in bluez-gnome1.1 by default.
Anybody knows?

I would do something like this:
-set the IP of the bluetooth dongle to 192.168.0.2
-somehow share the internet on eth0 (I guess some way as I did with the LAN)
-somehow activate the dongle to listen to incoming BT connections
-set a static IP on the CLIENT-BT bluetooth LAN to 192.168.0.20, otherwise same config. as in the LAN case 
-enable incoming connection from CLIENT-BT (192.168.0.20)

Anybody could tell me how to do it?
All hints are welcome! Thanks!!

---

### Post by ziogelis77 on 2008-08-29
Have you tried these instructions? 
[http://www.howtoforge.com/bluetooth_pand_debian_etch](http://www.howtoforge.com/bluetooth_pand_debian_etch)
I succeeded in setting up a NAP this way, with minor modifications. 

This howto uses a dhcp server instead of static IP, though.

My modifications were, if I remember correctly, something like this: I had to restart  networking for things to start working at some point, as well as start pand using command line (or scrip) - "pand --listen --role=NAP --devup /etc/bluetooth/pan/dev-up"; somehow the options in bluetooth configuration file did not do the trick for me. Also, one of my bluetooth dongles did not work for NAP - I am not sure why, maybe because it was a "no name" dongle with a strange hardware address 11.11.11.11.11. I used microstar dongle with a normal address successfully.

---

