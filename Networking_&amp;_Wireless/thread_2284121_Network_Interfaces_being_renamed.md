---
title: "Network Interfaces being renamed"
date: 2015-06-27
forum: Networking &amp; Wireless
---

### Post by MACscr on 2015-06-27
OK, so I have to rename two of my interfaces on my trusty servers because of the how the mlxn_en drivers work for for my 10gb nics. It gets confusing because they are named eth0 and eth1, while my main onboard nics are em1 and em2 and i need some consistency amongst my servers. Any, im using the following to rename them:

```
root@stor1:/proc/net/vlan# cat /etc/udev/rules.d/70-persistent-net.rulesSUBSYSTEM=="net", ACTION=="add", ATTR{address}=="00:a0:d1:ed:42:c9", NAME="em2"
SUBSYSTEM=="net", ACTION=="add", ATTR{address}=="00:a0:d1:ed:42:c8", NAME="em1"
SUBSYSTEM=="net", ACTION=="add", ATTR{address}=="00:1e:0b:4c:69:79", NAME="mlx1"
SUBSYSTEM=="net", ACTION=="add", ATTR{address}=="00:1e:0b:4c:69:7a", NAME="mlx2"
```

Which typically works fine, but having an issue occasionally with it and vlans:

```

root@stor1:/proc/net/vlan# cat /proc/net/vlan/config
VLAN Dev name	 | VLAN ID
Name-Type: VLAN_NAME_TYPE_PLUS_VID_NO_PAD
rename8        | 10  | bond0
rename9        | 20  | bond0

```

Maybe they arent even related, but I have no idea why the vlans are no longer coming up and since it says rename, it made me think of the some of the interfaces that are part of that bond. Here is some more info:

```
root@stor1:/proc/net/vlan# cat /etc/network/interfaces
# The loopback network interface
auto lo
iface lo inet loopback


# The primary network interface
auto em1
iface em1 inet manual


auto br0
iface br0 inet static
	address 67.xxxxxxxx
	netmask 255.255.254.0
	gateway 67.xxxxxxx
	dns-nameservers 192.168.0.1 8.8.8.8
	bridge_ports em1
	bridge_fd 0
	bridge_maxwait 0
	bridge_stp off


auto em2
iface em2 inet manual
	bond-master bond0


auto mlx1
iface mlx1 inet manual
	bond-master bond0
        bond-primary mxl1


auto bond0
iface bond0 inet manual
        # jumbo frame support
	#  mtu 9000
        # Load balancing and fault tolerance
	bond-mode balance-alb
	arp_interval 100
	arp_ip_target 192.168.0.10 192.168.0.11
	bond-slaves none


auto br1
iface br1 inet static
	address 192.168.0.100
	netmask 255.255.255.0
        bridge_ports bond0
        bridge_fd 0
        bridge_maxwait 0
        bridge_stp off


auto vlan10
iface vlan10 inet static
	vlan-raw-device bond0
	address 10.0.0.100
	netmask 255.255.255.0


auto vlan20
iface vlan20 inet static
	vlan-raw-device bond0
	address 172.16.0.100
	netmask 255.255.255.0
root@stor1:/proc/net/vlan#
```

---

### Post by Doug S on 2015-06-27
The switch to predictable interfaces names currently has issues, particularly on Ubuntu Server edition.
In the end, the only way I could get predictable repeatable results for all kernels was to have this on my /etc/default/grub line:```
GRUB_CMDLINE_LINUX_DEFAULT="net.ifnames=1 biosdevname=0"
```
See [also]("http://askubuntu.com/questions/628217/use-of-predictable-network-interface-names-with-alternate-kernels") (the answer).

---

### Post by MACscr on 2015-06-28
Yes, but my interfaces are being renamed correctly. I dont get why the vlans are behaving this way.

---

### Post by MACscr on 2015-06-28
Ah, i just had to add DRIVERS=="?*" to my udev rules and it worked. woo hoo

---

