---
title: "Setting up multiple bridges"
date: 2008-08-18
forum: Networking &amp; Wireless
---

### Post by thegnark on 2008-08-18
Hello,

I'm trying to setup a dedicated headless VirtualBox server, but need some help with the host networking configuration.

Is is possible to create multiple bridges that a single physical interface is bound to? i.e.:
vbox0-br0-eth0
vbox1-br1-eth0
vbox2-br2-eth0

I need host networking on all my virtual machines, so I'm wondering if this is possible in any way or if I'm going about it wrong? Currently I have vbox0-br0-eth0 running, but after I added br1 and tried to addif eth0 to it, obviously I ran into my problem, "device eth0 is already a member of a bridge; can't enslave it to bridge br1."

---

### Post by thegnark on 2008-08-18
quick update:

After searching around some more, I decided to simple bring up the additional interfaces in /etc/network/interfaces then bind them all to br0 at once:

```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet manual

auto vbox0
iface vbox0 inet manual

auto vbox1
iface vbox1 inet manual

auto vbox2
iface vbox2 inet manual

auto br0
iface br0 inet static
        address 192.168.1.40
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1
        bridge_ports eth0 vbox0 vbox1 vbox2
        bridge_fd 9
        bridge_hello 2
        bridge_maxage 12
        bridge_stp off

```This works great, except I can't seem to ping from 192.168.1.101 (ubuntu) to 192.168.1.45 (winxp), HOWEVER, I can ping the other way around. 101 will ping to anything else, including other devices on the subnet and the internets.

My initial thought was to try and put eth0 in promisc as I've seen elsewhere, so I added the following under "iface eth0 inet manual"

```

up ifconfig $IFACE 0.0.0.0 up
up ip link set $IFACE promisc on
down ip link set $IFACE promisc off
down ifconfig $IFACE down
```...which brought everything up as expected, but it didn't seem to fix anything... even after restarting networking on both virtual machines (but not rebooting).

Any thoughts?


EDIT: Not sure what happened, but lost connectivity to 45 from every other computer, so decided it was a problem with that VM rather than 101. Several restarts, removed promisc settings, and it occured to me to disable Windows Firewall.... now working!

---

