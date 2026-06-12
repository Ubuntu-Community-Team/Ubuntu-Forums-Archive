---
title: "[SOLVED] Notebook: Howto make a ethernet device work without a cable plugged in ?"
date: 2007-06-16
forum: Networking &amp; Wireless
---

### Post by VMbuseck on 2007-06-16
I've a DELL D510 with a eth0 an a wireless ethernet device. Both are normally configured als dhcp-clients, because the notebook is used in several networks.
I've VMware server (1.0.3) installed an need to have a working ethernet devide eth0 (this is the bridged one) without a cable is plugged into the network card.

I had written some tiny scripts and configuration files to bring up the notebook network during travel and have a 'standalone network' for my kubuntu (6.06 dapper drake) host operation system and its 2 Windows guests:

/etc/network/mobile_interfaces:

[INDENT]auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto eth0
iface eth0 inet static
  address 192.168.13.200
  netmask 255.255.255.0
  network 192.168.13.0
  broadcast 192.168.13.255[/INDENT]

/etc/init.d/mobilenet:

[INDENT]#!/bin/sh
#

# Defaults
INTERFACES="eth0"

case "$1" in
	start)
		/etc/init.d/networking stop

                killall dhclient3

                ifup -a --interfaces=/etc/network/mobile_interfaces

                killall dhclient3

		/etc/init.d/dhcp start
		;;
	stop)
		/etc/init.d/dhcp stop

                ifdown -a --interfaces=/etc/network/mobile_interfaces

		/etc/init.d/networking start
		;;
	*)
		echo "Usage: /etc/init.d/mobilenet {start|stop}"
		exit 1 
esac

exit 0

[/INDENT]

The stuff above only works, if the network device is connected to a hub/switch/router.

**Is there any possibility to emulate a working eth0 device without a cable plugged in the network card ???**

---

### Post by VMbuseck on 2007-06-18
I solved the problem by using alternative way:

In VMware I configured a 2nd ethernet card (type 'host only') and created 2 hardware profiles in the Window guest operation systems.

1. 'Mobile': Just the 'host only' ethernet device is activated
2. 'Full': Just the 'bridged' ethernet device is activated

During boot I just have to take care which profile is selected.

---

### Post by VMbuseck on 2007-06-28
... using NAT networking with VMware. See [http://www.vmware.com/community/thread.jspa?threadID=90155](http://www.vmware.com/community/thread.jspa?threadID=90155)

---

