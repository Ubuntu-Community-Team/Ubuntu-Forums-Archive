---
title: "Default MTU setting changed from 1500 to 576 upgrading to 8.10; this is bad!"
date: 2008-11-05
forum: Networking &amp; Wireless
---

### Post by evilspoons on 2008-11-05
Hi everyone. I'm running a Ubuntu Server system that I just upgraded to 8.10. I originally installed 6.10 and have done each upgrade since.

8.04 was working great. I have two network cards doing NAT. One is connected directly to my cable modem, the other is set with a static IP address and acts as the gateway for the rest of my network.

First of all, the 8.10 upgrade changed both network cards to use a static IP 192.168.0.1. I edited /etc/network/interfaces and corrected eth1 back to DHCP, and that worked. At least, I thought so.

Where my MTU was previously 1500, it is now setting eth1's MTU to 576. This causes a whole bunch of problems - I need it at 1500.

I can manually set eth0 (the static IP) to MTU of 1500 by doing this in /etc/network/interfaces:

```
# The local network interface
auto eth0
iface eth0 inet static
address 192.168.0.1
netmask 255.255.255.0
mtu 1500

```

But the "MTU 1500" command does not work for "iface eth1 inet dhcp". This has been discussed at length in other forum threads for older versions of Ubuntu. I was then told the solution to this is instead using this:

```
# The primary network interface
iface eth1 inet dhcp
pre-up /sbin/ifconfig $IFACE mtu 1500
```

But whenever I bring the network interface online, it sets back to 576. I have to manually run "sudo ifconfig eth1 1500" and then all is well.

Any ideas? Thanks!

---

### Post by cariboo on 2008-11-06
You can use ethtool to set the mtu of you nic. Ethtool is available in the repositories and you can use Add/Remove Programs, Synaptic Package Manager and of course the command line to install it.

Jim

---

### Post by KillaB7 on 2008-12-16
After hours of troubleshooting a colleague and I found a solution to one particular MTU 576 scenario.

NetworkManager is an excellent tool but there are definite bugs with the current implementation in 8.10.
After a reboot, NetworkManager forgets static IP addressing as well as static MTU settings.

Setting the MTU manually with "sudo ifconfig eth0 mtu 1500" also proved futile as long as NetworkManager is still running the show.

The issue in our case ended up being with the DHCP client (dhcp3).  The client default settings request "interface-mtu" from the server and our ISP's DHCP server is set to 576.
You may or may not find this info via "/var/lib/dhcp3/dhclient.eth0.leases" or "/var/lib/dhcp3/dhclient.leases"


To correct this problem, find the following line in "/etc/dhcp3/dhclient.conf":
```

request subnet-mask, broadcast-address, time-offset, routers,
	domain-name, domain-name-servers, domain-search, host-name,
	netbios-name-servers, netbios-scope[COLOR="Red"], interface-mtu[/COLOR];

```

and edit out the "interface-mtu" option:
```

request subnet-mask, broadcast-address, time-offset, routers,
	domain-name, domain-name-servers, domain-search, host-name,
	netbios-name-servers, netbios-scope;

```

---

### Post by Stolen on 2011-10-23
Just ran into this in Oneric.  It was the DHCP client requesting interface-mtu as per the previous poster.  Thanks!

---

