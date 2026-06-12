---
title: "wlan does not activate on boot"
date: 2020-05-01
forum: Networking &amp; Wireless
---

### Post by gus_zernial on 2020-05-01
I have Ubuntu Mate 18.04 on an ARM Odroid XU4, with a static wired interface and a dhcp wireless interface. I'm using NetworkManager and wpa-supplicant, and the Mate Control center generates the wired and wireless interface configurations as files in /etc/NetworkManager/system-connections, as well as an /etc/network/interfaces~ file as follows:

# interfaces(5) file used by ifup(8) and ifdown(8)
# Include files from /etc/network/interfaces.d:
source-directory /etc/network/interfaces.d

auto lo
iface lo inet loopback
auto eth0

The wired interface comes up on boot, but the wireless interface does not, as I do not get a response from the wireless interface to a ping to its dhcp address from another system on the LAN.  I believe the driver/module and configuration for the wireless are correct, as I can subsequently bring the wireless up using the following two commands:

$ sudo ip addr flush dev wlan0
$ sudo dhclient -v wlan0

and thereafter ping both interfaces successfully from the other system on the LAN. So my question is: how do I make the system bring the wireless interface up on boot?

Thx, Gus

---

