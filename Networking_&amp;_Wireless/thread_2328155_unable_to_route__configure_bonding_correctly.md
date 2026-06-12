---
title: "unable to route / configure bonding correctly"
date: 2016-06-17
forum: Networking &amp; Wireless
---

### Post by Derek_Gentle on 2016-06-17
Hello All
I recently had my storage server go belly up, and am in the process of re-configuring the new installation.  I'm running into a problem with setting up the ethernet bonding.  I used to have this running before flawlessly, and in my ignorance did not make a backup of my system config files, so now I am having to do this all over again.

I have followed the directions [here]("https://help.ubuntu.com/community/UbuntuBonding") for setting up mode 4 / LACP:

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).


#eth0 is manually configured, and slave to the "bond0" bonded NIC
auto eth0
iface eth0 inet manual
bond-master bond0


#eth1 is manually configured, and slave to the "bond0" bonded NIC
auto eth1
iface eth1 inet manual
bond-master bond0


#eth2 is manually configured, and slave to the "bond0" bonded NIC
auto eth2
iface eth2 inet manual
bond-master bond0


#eth3 is manually configured, and slave to the "bond0" bonded NIC
auto eth3
iface eth3 inet manual
bond-master bond0


# bond0 is the bonded NIC and can be used like any other normal NIC.
# bond0 is configured using static network information.
auto bond0
iface bond0 inet static
address 192.168.1.151
gateway 192.168.1.100
netmask 255.255.255.0
dns-nameservers 8.8.8.8 8.8.4.4
# bond0 uses standard IEEE 802.3ad LACP bonding protocol
bond-mode 4   
bond-miimon 100
bond-lacp-rate 1
bond-slaves eth0 eth1 eth2 eth3


# The loopback network interface
# auto lo
# iface lo inet loopback


# The primary network interface
# auto eth0
# iface eth0 inet dhcp

```

I have confirmed that my modules entry matches the example:

```

loop
lp
rtc
bonding

```

I've also added Google to [COLOR=#111111][FONT=Consolas]/etc/resolvconf/resolv.conf.d/base[/FONT][/COLOR] and [COLOR=#111111][FONT=Consolas]/etc/resolvconf/resolv.conf.d/tail[/FONT][/COLOR]

After restarting I am unable to ping or route to any internal or external addresses.  I am using a Cisco SGE2000 managed switch with the appropriate LAG settings configured, and I know they work as the only thing that has changed is I've had to replace the OS on my server.  I've likely missed something obvious, but for the life of me, I have no idea what.

Any help and suggestions GREATLY appreciated!
[COLOR=#111111][FONT=Consolas]
[/FONT][/COLOR]

---

