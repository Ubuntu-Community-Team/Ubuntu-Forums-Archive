---
title: "Wireless Connection Issue"
date: 2008-09-04
forum: Networking &amp; Wireless
---

### Post by Sarj on 2008-09-04
Hello! 
I am new at ubuntu! I like ubuntu very much.However I have problem connecting through 2wire usb.
I have found these error messages in user log?
Sep  4 18:22:38 lolly-powertoy dhcdbd: Started up.
Sep  4 18:22:40 lolly-powertoy dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Sep  4 18:22:44 lolly-powertoy dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Sep  4 18:22:44 lolly-powertoy dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Sep  4 18:22:44 lolly-powertoy dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Sep  4 18:22:44 lolly-powertoy dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.interface_mtu
Sep  4 18:24:42 lolly-powertoy dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Sep  4 18:24:42 lolly-powertoy dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Sep  4 18:24:42 lolly-powertoy dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Sep  4 18:24:42 lolly-powertoy dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.interface_mtu
Sep  4 18:25:08 lolly-powertoy dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Sep  4 18:25:08 lolly-powertoy dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Sep  4 18:25:08 lolly-powertoy dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Sep  4 18:25:08 lolly-powertoy dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.interface_mtu
Sep  4 18:25:24 lolly-powertoy dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.reason
Sep  4 18:25:46 lolly-powertoy dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.host_name
Sep  4 18:25:46 lolly-powertoy dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.nis_domain
Sep  4 18:25:46 lolly-powertoy dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.nis_servers
Sep  4 18:25:46 lolly-powertoy dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.interface_mtu

I ran terminal and found following issues?

lolly@lolly-powertoy:~$ dhclient wlan0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

can't create /var/lib/dhcp3/dhclient.leases: Permission denied
Can't create /var/run/dhclient.pid: Permission denied
drop_privileges: could not set group id: Operation not permitted
lolly@lolly-powertoy:~$ 

I am able to connect through wired internet but with wireless no!#-o

---

### Post by Crafty Kisses on 2008-09-05
Post the results of this command: ```
lshw -C network
```

---

### Post by Sarj on 2008-09-05
Thank you for helping me!!
Today amaizingly i was able to connect two times! I do not know what i did anyhow here is lshw -c network results?
 *-network               
       description: Ethernet interface
       product: 82801BA/BAM/CA/CAM Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 03
       serial: 00:03:47:ff:4d:9e
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=half firmware=N/A latency=32 link=no maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=10MB/s
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:60:b3:58:82:e6
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+wlanuig driverversion=1.52+2Wire,04/08/2004, 2.3.1.3 ip=192.168.1.68 link=yes multicast=yes wireless=IEEE 802.11g
 
My wireless network does not start automaticall when i rebbot or turn on computer.
thank you!

---

