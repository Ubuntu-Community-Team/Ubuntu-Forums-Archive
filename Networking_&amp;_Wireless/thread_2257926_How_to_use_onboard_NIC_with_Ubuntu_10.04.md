---
title: "How to use onboard NIC with Ubuntu 10.04?"
date: 2014-12-23
forum: Networking &amp; Wireless
---

### Post by david.aldrich.ntml on 2014-12-23
I have a Dell OptiPlex 7020 running Ubuntu 10.04.  The computer has an onboard NIC and two Intel PCIExpress NICs.  I need two network connections: one using DHCP connected to the office LAN and one with a static IP address on a small private subnet. Currently, things only work if I use the two PCIExpress NICs and not the onboard NIC.  However, I want to use the onboard NIC so that I can use Wake On Lan and release a PCIExpress card for other purposes.  I want to connect the office LAN to the onboard NIC but, if I do so, that connection does not work.  I would be grateful for some help to fix this please.

Here is some background info:

> > lspci -nn |grep Eth
00:19.0 Ethernet controller [0200]: Intel Corporation Device [8086:153a] (rev 04)
01:00.0 Ethernet controller [0200]: Intel Corporation 82574L Gigabit Network Connection [8086:10d3]
03:00.0 Ethernet controller [0200]: Intel Corporation 82574L Gigabit Network Connection [8086:10d3]

> > cat /etc/network/interfaces
auto lo
iface lo inet loopback
auto eth0
iface eth0 inet dhcp
auto eth1
iface eth1 inet static
address 192.168.1.111
netmask 255.255.255.0
gateway 192.168.1.1

I have executed:

> sudo /etc/init.d/networking restart

but then I just see repeated DHCPDISCOVER messages (if the onboard NIC is connected to the office LAN).

Any suggestions please?

---

### Post by chili555 on 2014-12-23
First of all, 'networking restart' is deprecated. The preferred method is:```
sudo ifdown eth0 && sudo ifup -v eth0
```...or eth1 as needed.

Second, if you declare a static address for eth1, you also need DNS nameservers:```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet static
address 192.168.1.111
netmask 255.255.255.0
gateway 192.168.1.1
dns-nameservers 192.168.1.1
```I'd restart both interfaces and check:```
ifconfig
ping -c3 www.ubuntu.com
```

---

### Post by kpatz on 2014-12-23
What's the output of **ls -l /sys/class/net** ?  This will tell you which NIC is eth0, eth1, etc.  The entry that symlinks to something containing "00:19.0" will be the onboard NIC.

For example (this is from one of my boxes, so the numbers will be different):
```

kpatz@zuul ~ $ lspci -nn | grep Ether
01:07.0 Ethernet controller [0200]: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 [1317:0985] (rev 11)
01:0c.0 Ethernet controller [0200]: 3Com Corporation 3c905C-TX/TX-M [Tornado] [10b7:9200] (rev 78)
kpatz@zuul ~ $

kpatz@zuul ~ $ ls -l /sys/class/net
total 0
lrwxrwxrwx 1 root root 0 2014-12-23 11:29 eth0 -> ../../devices/pci0000:00/0000:00:1e.0/0000:01:07.0/net/eth0
lrwxrwxrwx 1 root root 0 2014-12-23 11:29 eth1 -> ../../devices/pci0000:00/0000:00:1e.0/0000:01:0c.0/net/eth1
lrwxrwxrwx 1 root root 0 2014-12-23 11:29 lo -> ../../devices/virtual/net/lo
kpatz@zuul ~ $

```

In my example, you can see that the ADMtek NC100 is eth0, and the 3Com is eth1.

To get the MAC addresses, use the command **ifconfig -a | grep HWaddr**

---

### Post by david.aldrich.ntml on 2014-12-23
Thanks for your advice.  I took both interfaces down and up again using the commands you suggested.  For eth0 I see:

> No DHCPOFFERS received

A strange thing is that if I then do ifconfig, eth0 still shows the MAC address of the PCIExpress card that is no longer connected.

---

### Post by david.aldrich.ntml on 2014-12-23
> **kpatz said:**
> What's the output of **ls -l /sys/class/net** ?  This will tell you which NIC is eth0, eth1, etc.

I can't paste the output here because the network isn't working but the output appears to show that both eth0 and eth1 are connected to pci devices.

---

### Post by chili555 on 2014-12-23
> A strange thing is that if I then do ifconfig, eth0 still shows the MAC address of the PCIExpress card that is no longer connected.Please try:```
sudo rm /etc/udev/rules.d/70-persistent-net.rules
```Reboot and check again.

---

### Post by kpatz on 2014-12-23
> **david.aldrich.ntml said:**
> I can't paste the output here because the network isn't working but the output appears to show that both eth0 and eth1 are connected to pci devices.They'll show up as PCI devices regardless if they're onboard or on a card.  The million dollar question is, which is eth0 and which is eth1?  Or, more specifically, what's the "eth#" name of the onboard NIC?  We know the onboard is 00:19.0 based on the output of your lspci -nn command.  So try: **ls -l /sys/class/net | grep "00:19.0"** .  I bet the onboard NIC isn't eth0 and that's why your DHCP isn't working.

---

### Post by david.aldrich.ntml on 2014-12-23
The output of **ls -l /sys/class/net**  shows that eth0 is connected to:

00:01.0 net/eth0

and eth1 is connected to:

00.1c.4 net/eth1

The output of **ls -l /sys/class/net | grep "00:19.0"** is nothing.

ifconfig -a shows only eth0 and eth1.

---

### Post by kpatz on 2014-12-23
Sounds like you removed one of the cards, right?  Re-run **lspci -nn |grep Eth** and see what you get.  They should match up with the /sys/class/net entries.

---

### Post by david.aldrich.ntml on 2014-12-24
> **kpatz said:**
> Sounds like you removed one of the cards, right?  Re-run **lspci -nn |grep Eth** and see what you get.  They should match up with the /sys/class/net entries.

Actually, I think the entries do not match up:

> 
-> ls -l /sys/class/net
total 0
lrwxrwxrwx 1 root root 0 2014-12-24 08:28 eth0 -> ../../devices/pci0000:00/0000:00:01.0/0000:01:00.0/net/eth0
lrwxrwxrwx 1 root root 0 2014-12-24 08:28 eth1 -> ../../devices/pci0000:00/0000:00:1c.4/0000:03:00.0/net/eth1
lrwxrwxrwx 1 root root 0 2014-12-24 08:28 lo -> ../../devices/virtual/net/lo
[~]
-> lspci -nn | grep Eth
00:19.0 Ethernet controller [0200]: Intel Corporation Device [8086:153a] (rev 04)
01:00.0 Ethernet controller [0200]: Intel Corporation 82574L Gigabit Network Connection [8086:10d3]
03:00.0 Ethernet controller [0200]: Intel Corporation 82574L Gigabit Network Connection [8086:10d3]
[~]


Also, one of the interfaces is unclaimed:

> -> sudo lshw -C network
*-network
       description: Ethernet interface
       product: 82574L Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 00
       serial: 68:05:ca:17:fd:4f
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.0.2-k2 duplex=full firmware=1.8-0 ip=172.29.68.48 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:16 memory:f7dc0000-f7ddffff memory:f7d00000-f7d7ffff ioport:e000(size=32) memory:f7de0000-f7de3fff memory:f7d80000-f7dbffff(prefetchable)
  *-network UNCLAIMED
       description: Ethernet controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       version: 04
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list
       configuration: latency=0
       resources: memory:f7e00000-f7e1ffff memory:f7e3d000-f7e3dfff ioport:f080(size=32)


Any thoughts please?

---

