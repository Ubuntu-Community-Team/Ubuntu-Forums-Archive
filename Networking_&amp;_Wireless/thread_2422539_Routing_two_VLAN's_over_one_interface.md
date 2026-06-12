---
title: "Routing two VLAN's over one interface"
date: 2019-07-09
forum: Networking &amp; Wireless
---

### Post by CrimsonRider on 2019-07-09
I have a fiber internet connection, that offers two VLAN's; 300 for regular internet and VLAN 640 for IPTV. I need to make sure at least one port one Switch B is routing VLAN 640 to my TV Set top box. I am on Ubuntu 18.04.2. 

The fiber internet works nicely, this is the setup;

```
Media Converter
      |
      +--- Ubuntu Server
               |
               +--- Switch A --- Desktop 1
                      |          Desktop 2
                      |          NAS
                      |
                      +--- Wifi ------- Laptop 1
                      |                 Laptop 2
                      |                 Android 1
                      |
                      +--- Switch B --- TV
                                        Steam Link
                                        Set Top Box
```
And this is the network configuration
```
# The primary network interface, Internet
auto enp5s0
iface enp5s0 inet manual

auto enp5s0.300
iface enp5s0.300 inet manual

auto enp5s0.640
iface enp5s0.640 inet manual

auto br1
iface br1 inet dhcp
    dns-namerserver 192.168.40.12 1.1.1.1
    bridge_ports enp5s0.300
    bridge_stp off

# Lan
auto eth0
iface eth0 inet static
	address 192.168.40.12
	netmask 255.255.255.0
```

This works for internet, all devies have regular network connection. But the Set Top Box needs be on VLAN 640. The switches are managed, they should be able to handle that. But getting the Ubuntu server to send VLAN 640 over it's eth0 interface is proving difficult. If I simply add bridge_ports enp5s0.640 to the br1, the br1 gets the IP for VLAN640.

So I am not really sure what to do to fix this. Basically, the Ubuntu server should have internet and deliver that to the whole LAN. And then VLAN640 should be delivered to the Set Top Box only for IPTV.

---

