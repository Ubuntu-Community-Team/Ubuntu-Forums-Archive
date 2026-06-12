---
title: "Network interface id and mac address change on every boot"
date: 2008-01-05
forum: Networking &amp; Wireless
---

### Post by Junho Ryu on 2008-01-05
Hello,

First, I noticed Mac address change whenever I restart ubuntu.
I tried macchanger to fix the mac address, but I wasn't able to configure it using eth0.
When I typed ifconfig, the interface identifier was eth14.
After rebooted system again, network interface is eth15 now.

Is it a known issue, or can it be a hardware problem? I'm using onboard Lan on GIGABYTE GA-M68SM-S2. Is it possible to verify whether H/W has changed its mac address?

Junho

---

### Post by rosell on 2008-01-06
Hi,
I got exactly the same behavior yesterday when moving my system to a Gigabyte motherboard (GA-M56S-S3). I have surfed around a lot and it seems to be a problem with the forcedeth driver, I have version 0.60. I'm running Ubuntu 7.10 (Gutsy). Until it is fixed I have made a workaround.

$ ethtool -i eth0
driver: forcedeth
version: 0.60
firmware-version: 
bus-info: 0000:00:06.0

# uname -a
Linux media 2.6.22-14-server #1 SMP Tue Dec 18 08:31:40 UTC 2007 i686 GNU/Linux

This behavior gives two main problems.
1. The name of the interface change on each reboot. eth0->eth1->eth2 and so on making it not possible to set a static IP-address in /etc/network/interfaces.
2. When using DHCP the machine gets a new IP-address on each reboot. DHCP server sees it as a new machine.

I have found that Ubuntu uses udev and has a script (/etc/udev/75-persistent-net-generator.rules) that checks for new interfaces and creates interface names for new detected ones. These names are written to /etc/udev/70-persistent-net.rules and the file contains a number of lines like this (address different and the names number increasing ):

# PCI device 0x10de:0x0450 (forcedeth)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:00:6c:80:f7:45", NAME="eth1"

The ATTRS{address} referrers to the MAC-address that is new on each time and NAME is the new created interface name.

**My workaround:**
Add this line to /etc/udev/70-persistent-net.rules

SUBSYSTEM=="net", DRIVERS=="forcedeth*", NAME="eth0"

And remove all other lines.

Note that this might make a conflict in some way if there are more than one network interface that utilies the forcedeth driver. In that case it may be possible to separate them using the PCI address. Not tested that.

To get the MAC-address not changing I have the following configuration in /etc/network/interfaces

auto eth0 static
iface eth0 inet static
address 192.168.0.2
netmask 255.255.255.0
gateway 192.168.0.3
hwaddress ether 00:e0:4c:12:34:56

It is the hwaddress ether that is important.

If you want to use DHCP this would work (not tested):
auto eth0
iface eth0 inet dhcp
hwaddress ether 00:e0:4c:12:34:56

/rosell

---

### Post by Junho Ryu on 2008-01-07
Beautiful, it works! :KS

In my case the path to 70-persistent-net.rules is /etc/udev/rules.d/70-persistent-net.rules

---

