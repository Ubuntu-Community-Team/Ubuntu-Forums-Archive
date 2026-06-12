---
title: "Automaticall bridging a bonded interface and adding tap interfaces"
date: 2008-02-03
forum: Networking &amp; Wireless
---

### Post by cfmunster on 2008-02-03
I have Ubuntu 64-bit 7.10 installed on a machine with two NICs. I want to create a bonded interface on the two NICs, bridge the bonded interface, and add tap interfaces for KVM virtual machines. I can get this configuration working manually, but I have not been able to automate it and I was hoping someone could help me.

Here is how I get it running manually:

/etc/network/interfaces

```
auto lo
iface lo inet loopback

auto bond0
iface bond0 inet static
   address 192.168.3.10
   netmask 255.255.255.0
   network 192.168.3.0
   broadcast 192.168.3.255
   gateway 192.168.3.1
   post-up ifenslave bond0 eth0 eth2
```

Then on boot I do this in a shell:

```
sudo su
ifconfig bond0 0.0.0.0 promisc up
brctl addbr br0
brctl addif br0 bond0
ifconfig br0 192.168.3.10 up
route add default gateway 192.168.3.1
tunctl -u nobody -t tap0
ifconfig tap0 192.168.3.11
```

What is the best way to automate this configuration?

Thanks in advance for any thoughts.

SOLVED:

Duh, I just added the additional lines to post-up. Maybe not the best way, but it works.

```

auto lo
iface lo inet loopback

auto bond0
iface bond0 inet manual
   address 192.168.3.10
   netmask 255.255.255.0
   network 192.168.3.0
   broadcast 192.168.3.255
   gateway 192.168.3.1
   post-up ifenslave bond0 eth0 eth2
   post-up sudo ifconfig bond0 0.0.0.0 promisc up
   post-up sudo brctl addbr br0
   post-up sudo brctl addif br0 bond0
   post-up sudo ifconfig br0 192.168.3.10 up
   post-up sudo route add default gateway 192.168.3.1
   post-up sudo tunctl -u nobody -t tap0
   post-up sudo ifconfig tap0 192.168.3.11
```

---

### Post by mindwarp on 2008-07-23
Thank you for the info, this helps a lot.

---

