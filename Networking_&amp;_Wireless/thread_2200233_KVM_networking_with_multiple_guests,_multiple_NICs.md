---
title: "KVM networking with multiple guests, multiple NICs one one network"
date: 2014-01-18
forum: Networking &amp; Wireless
---

### Post by BarryDocks on 2014-01-18
I initially posted this in the visualization section but didn't really get any useful replies so I am hoping someone here might help.
Original post [http://ubuntuforums.org/showthread.php?t=2198227]("http://ubuntuforums.org/showthread.php?t=2198227")

I am having a bit of trouble configuring a stable network with multiple linux guests each on individual NICs all on the same network, in fact I am not sure if what I am doing is the most effective method to achieve what I want.

So here is the goal:

Host OS is ubuntu 12.04 LTS 64bit headless running on HP Prolient ML115 AMD Quad core with 8GB (MAX) RAM and 4gigabit NICS
eth0 - WAN
eth1, eth2, eth3 - LAN

Guest 1:
Zentyal 2.2 (ubuntu 10.04) 64bit acting as a gateway, dhcp server, DNS server, etc for the local network with 2 virtio NICs
eth0 bridged to the WAN 
eth1 bridged to the LAN

Guest 2:
OpenMediaVault (debian 6?) 64bit acting as a file server to the LAN with 1 virtio NIC
eth0 bridged to the LAN

Guest 3: 
Ubuntu 6.06 64 bit with MYSQL 4.1 (needed for legacy purposes) on the LAN with e1000 NIC (virtio is not supported in this version of ubuntu)
eth0 bridged to the LAN

I initially wanted a bonded interface on the host but rapidly gave up on this as it would also involve creating virtual adapters of the bond, ie one for each guest?
So my interfaces file on the host looks like this:
```

auto lo
iface lo inet loopback

##########################
##WAN interface & bridge##
auto eth0
iface eth0 inet manual

auto br0
iface br0 inet dhcp
  bridge_ports eth0
  bridge_stp off
  bridge_fd 0
  bridge_maxwait 0
##########################

##########################
##LAN interfaces & bridge##
auto eth1
iface eth1 inet manual

auto eth2
iface eth2 inet manual

auto eth3
iface eth3 inet manual

auto br1
iface br1 inet static
  address 10.0.0.1
  netmask 255.255.255.0
  bridge_ports eth1 eth2 eth3
  bridge_stp off
  bridge_fd 0
  bridge_maxwait 0
##########################


```

This would work initially but a simple reboot of the host and then there would be no connections to the LAN for the host or any guests and the LEDs in the host NICs just bink rapidly.  The NICs are a mix of both broadcom and Intel.

I am not entiely sure what is going wrong or if there is a better way of doing it, possibly with an internal host network that breaks out to the LAN?

In the meantime I have gone back to Virtualbox but the network performance is about a 1/3 of KMV :-(

---

### Post by matt_fussell2 on 2014-10-08
I think the issue you're having is that you need to bond the interfaces before you bridge them.

See this article for ethernet bonding:
[https://help.ubuntu.com/community/UbuntuBonding](https://help.ubuntu.com/community/UbuntuBonding)

From there, you have to bridge the bonded interface - I'm actually trying to work on this at the moment.

---

