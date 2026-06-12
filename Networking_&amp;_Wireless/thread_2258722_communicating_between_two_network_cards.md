---
title: "communicating between two network cards"
date: 2014-12-29
forum: Networking &amp; Wireless
---

### Post by Zombir on 2014-12-29
Dear all,

I have a computer with two network cards and I want to communicate between the two WITHOUT having to have a cable between them. I've given them the following IP addresses:

```
eth1 : 192.168.3.1
eth2 : 192.168.2.2

```

I've given these addresses by editing /etc/network/interfaces file to look like this:

```
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
iface eth1 inet static
address 192.168.3.1
netmask 255.255.255.0
iface eth2 inet static
address 192.168.2.2
netmask 255.255.255.0

```

ip forwarding is enabled:

```
root@ceNLab-06:/home/ceadmin# sysctl net.ipv4.ip_forward
net.ipv4.ip_forward = 1



```

The firewall is not turned on:

```
root@ceNLab-06:/home/ceadmin# ufw status
Status: inactive

```

I tried to add an entry to the routing table as follows:

```
root@ceNLab-06:/home/ceadmin# route add -net 192.168.2.0 netmask 255.255.255.0 gw 192.168.2.2 eth1



```

But the result is:

```
SIOCADDRT: Network is unreachable



```

I've googled this error but couldn't find any solution.

Isn't this the way I should proceed to have communication between these two network cards? What is wrong with this?

Thanks in advance.

---

### Post by TheFu on 2014-12-30
The way that 2 NICs talk is over a cable. If you don't have a cable, you won't be talking.  I hope that Linux is smart enough to NOT send traffic over a NIC when the target IP is on the same machine - is that really what you are doing? That is how it reads.

If you want to see bandwidth between 2 NICs but only have 1 PC, use virtual machines and assign 1 NIC to the VM (nowhere else) and the NIC to another VM (and nowhere else) to perform your testing.  Standard Linux bridging allows this.  Of course the hostOS will probably need a 3rd NIC to be on the network or you could share the other 2 NICs, but that would probably corrupt whatever data you want in this very strange setup.

---

