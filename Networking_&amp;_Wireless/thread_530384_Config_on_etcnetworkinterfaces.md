---
title: "Config on /etc/network/interfaces"
date: 2007-08-20
forum: Networking &amp; Wireless
---

### Post by satimis on 2007-08-20
Hi folks,


Ubuntu 7.04 lamp server amd64
only one NIC


Connection
Server --> Router --> DSL Modem --> ISP

The router is supplied by ISP and password-locked by ISP.  I suppose 192.168.0.1 is the gateway.  How can I check it?


Fixed IP
220.232.213.178

IP address reserved for server on Router
192.168.0.10

DNS
202.14.67.4/14


$ cat /etc/network/interfaces```

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

```


Now I'll change the second part after "auto eth0" as:```

auto eth0
iface eth0 init static
	address 192.168.0.10
	netmask 255.255.255.255
	network ???
	broadcast ???
	gateway ???
	# dns -* options are implemented by the resolvconf package, if installed
	dns-nemserver 202.14.67.4 204.14.67.14

```

Please advise what shall I enter for
network ???
broadcast ???
gateway ???


Shall I put the fix IP (202.232.213.178) here?  It is for external only.


TIA


B.R.
satimis

---

### Post by jakev383 on 2007-08-20
> **satimis said:**
> Hi folks,


$ cat /etc/network/interfaces```

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

```


Now I'll change the second part after "auto eth0" as:```

auto eth0
iface eth0 init static
	address 192.168.0.10
	netmask 255.255.255.255
	network ???
	broadcast ???
	gateway ???
	# dns -* options are implemented by the resolvconf package, if installed
	dns-nemserver 202.14.67.4 204.14.67.14

```

Please advise what shall I enter for
network ???
broadcast ???
gateway ???



Your netmask will need to be 255.255.255.0
You can probably leave the network and broadcast line out (they should be assumed by the netmask), and enter your gateway as 192.168.0.1 if that's what you're router's IP is.

---

### Post by lloyd_b on 2007-08-20
1. "network" - you don't actually need this (the combination of IP address and netmask provide all the required info), but the correct value would be "network 192.168.0.0"

2.  "broadcast" - also not required, but the typical value would be "broadcast 192.168.0.255"

3.  "gateway" - the IP address of the router: "gateway 192.168.0.1"

As for the nameservers, with a static IP address I'd suggest putting them into the file "/etc/resolv.conf" - just add lines "nameserver 202.14.67.4" and "nameserver 204.14.67.14".

Your router is *probably* on 192.168.0.1, but that isn't guaranteed.  One way to find out for sure:  Boot up with the original (DHCP) configuration, then run the command "route -n" in a terminal window.  It will produce an output something like this:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
```

Note the gateway address in the line starting "0.0.0.0" - that will be the gateway.

Lloyd B.

---

### Post by satimis on 2007-08-20
> **jakev383 said:**
> Your netmask will need to be 255.255.255.0
You can probably leave the network and broadcast line out (they should be assumed by the netmask), and enter your gateway as 192.168.0.1 if that's what you're router's IP is.
Noted with thanks


satimis

---

### Post by satimis on 2007-08-20
Hi Lloyd,


Tks for your advice.


> **lloyd_b said:**
> 1. "network" - you don't actually need this (the combination of IP address and netmask provide all the required info), but the correct value would be "network 192.168.0.0"

2.  "broadcast" - also not required, but the typical value would be "broadcast 192.168.0.255"

3.  "gateway" - the IP address of the router: "gateway 192.168.0.1"

As for the nameservers, with a static IP address I'd suggest putting them into the file "/etc/resolv.conf" - just add lines "nameserver 202.14.67.4" and "nameserver 204.14.67.14".

Noted and thanks


> 
Your router is *probably* on 192.168.0.1, but that isn't guaranteed.  One way to find out for sure:  Boot up with the original (DHCP) configuration, then run the command "route -n" in a terminal window.  It will produce an output something like this:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
```

$ route -n```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0

```
So the gatewasy is "192.168.0.1"
> 
Note the gateway address in the line starting "0.0.0.0" - that will be the gateway.

What is the difference between "gateway" and "gateway address"?  Thanks


B.R.
satimis

---

### Post by lloyd_b on 2007-08-21
> What is the difference between "gateway" and "gateway address"? Thanks

None, really.  Sorry if I confused you (I certainly confused myself with that one...).

Properly speaking, the "gateway" is the device itself (i.e. the router), while the "gateway address" is the IP address for that device.  But when setting up a network, references to "gateway" or "gateway address" both resolve to the same thing - the IP address of the gateway device.

> $ route -n
Code:

```
Kernel IP routing table
Destination     Gateway         Genmask         Flas Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
```

So the gateway is "192.168.0.1"

Correct.  I expected that to be the address, since the "x.x.x.1" address is typically the gateway for a network, but it's nice to have confirmation.

So:
```
auto eth0
     address 192.168.0.10
     netmask 255.255.255.0
     gateway 192.168.0.1
```

And have the DNS nameservers in the resolv.conf file.  This should give you a working network.  

Lloyd B.

---

### Post by satimis on 2007-08-21
Hi lloyd,


I tried following combinations.  Unfortunately all failed.

/etc/network/interfaces```

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 init static
        address 192.168.0.10
        netmask 255.255.255.0
        gateway 192.168.0.1

```

```

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
        address 192.168.0.10
        netmask 255.255.255.0
        gateway 192.168.0.1

```

```

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0
        address 192.168.0.10
        netmask 255.255.255.0
        gateway 192.168.0.1

```

```

auto eth0
     address 192.168.0.10
     netmask 255.255.255.0
     gateway 192.168.0.1

```


$ sudo /etc/init.d/networking restart```

 * Reconfiguring network interfaces...                                          /etc/network/interfaces:10: misplaced option
ifdown: couldn't read interfaces file "/etc/network/interfaces"
/etc/network/interfaces:10: misplaced option
ifup: couldn't read interfaces file "/etc/network/interfaces"
                                                                         [fail]

```


What will be the line "iface eth0 init static" used for?  Tks.


I have only one NIC.  However this is a Virtual Machine with VMware running on Ubuntu 7.04, the host OS.

Shall I add an additional NIC for the VM ?


If NO, on /etc/network/interfaces```

# The VMs network interface
auto eth0
iface eth0 inet static
	address ???
	netmask	???
	gateway ???

```
What shall I enter there?  Tks.

> 
Properly speaking, the "gateway" is the device itself (i.e. the router), while the "gateway address" is the IP address for that device.  But when setting up a network, references to "gateway" or "gateway address" both resolve to the same thing - the IP address of the gateway device.

Noted.



Edit: * * * * *

Sorry, I made a typing mistake on "inet" (mistyped it as "init")

Following /etc/network/interfaces works:```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.0.10
        netmask 255.255.255.0
        gateway 192.168.0.1

```

$ sudo /etc/init.d/networking restart```

 * Reconfiguring network interfaces...                                   [ OK ] 

```

It needs the line "iface eth0 inet static"


B.R.
satimis

---

### Post by lloyd_b on 2007-08-21
My apologies - I was up late, and wasn't thinking too clearly.  Yes, it *should* have been:
```
iface eth0 inet static
```

I have no experience with VMware, so I don't know what (if any) special requirements it may have.

Other than that, it looks like everything is configured correctly now.  Have you tried actually *using* the network to see if it's working?

Lloyd B.

---

### Post by satimis on 2007-08-21
Hi lloyd,


> 
Other than that, it looks like everything is configured correctly now.  Have you tried actually *using* the network to see if it's working?

Yes.  The network seems working w/o problem.  Internet browsing is possible.

I'll continue installing other OS later.  Tks.


B.R.
satimis

---

