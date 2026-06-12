---
title: "networking on server"
date: 2008-12-01
forum: Networking &amp; Wireless
---

### Post by kalios on 2008-12-01
Ive just installed intrepid on my server pc, the server pc has three network interfaces, 2 onboard ones and a pci card.

ive given each interface a temporary static ip

eth0 192.168.0.100
eth1 192.168.0.101
eth2 192.168.0.102

my dilemma started when i wanted to know which one physically was eth0, eth1 etc. so on another machine i ran a constant ping on all three interfaces while pulling out network cables.

to my suprise the first two i pulled out had no effect on the three polling, the 3 pings i had run was still running and pinging so in conclusion the 3 ip's i had associated to eth0 eth1 eth2 all linked to the one card.

so my question is how do i fix?? i altered the interfaces file to static ip's 

any help will be great. thanks

---

### Post by ryry46d9 on 2008-12-01
with all the cables unplugged pug one in and type dmesg you should see 

 eth0: link up, 100Mbps, full-duplex,

and so on 

also 
dmesg | grep eth


 will list them but being how you got two onboard thats a problem

---

### Post by kalios on 2008-12-01
i noticed this 

[   13.345952] udev: renamed network interface eth2_rename to eth1
[   13.451228] udev: renamed network interface eth0 to eth2

on eth1 and eth2 
so im guessing thats the problem . so how do i fix this is the other part anyways..
root@server:~# dmesg | grep eth2
[    7.479539] e1000: eth2: e1000_probe: Intel(R) PRO/1000 Network Connection
[   13.345952] udev: renamed network interface eth2_rename to eth1
[   13.451228] udev: renamed network interface eth0 to eth2
[  260.172592] eth2: link up, 100Mbps, full-duplex, lpa 0x45E1
[  260.173127] bridge-eth2: up
[  260.173674] bridge-eth2: attached
[  271.121272] eth2: no IPv6 routers present
[  553.611006] bridge-eth2: disabling the bridge
[  553.623692] bridge-eth2: down
[  553.623946] bridge-eth2: detached
[  553.677411] eth2: link up, 100Mbps, full-duplex, lpa 0x45E1
[  553.678018] bridge-eth2: up
[  553.697766] bridge-eth2: attached
[  564.393769] eth2: no IPv6 routers present
[  598.893776] bridge-eth2: disabling the bridge
[  598.922535] bridge-eth2: down
[  598.922606] bridge-eth2: detached
[  598.962192] eth2: link up, 100Mbps, full-duplex, lpa 0x45E1
[  598.962712] bridge-eth2: up
[  598.963459] bridge-eth2: attached
[  609.230016] eth2: no IPv6 routers present
[  764.586794] eth2: link down
[  764.587412] bridge-eth2: disabling the bridge
[  764.590037] bridge-eth2: down
[  764.590233] bridge-eth2: detached
[  771.564473] eth2: link up, 100Mbps, full-duplex, lpa 0x45E1
[  771.565060] bridge-eth2: up
[  771.565070] bridge-eth2: attached
[  787.905794] eth2: link down
[  787.910194] bridge-eth2: disabling the bridge
[  787.920025] bridge-eth2: down
[  787.920212] bridge-eth2: detached
[  790.543020] eth2: link up, 100Mbps, full-duplex, lpa 0x45E1
[  790.543462] bridge-eth2: up
[  790.543470] bridge-eth2: attached

for eth2

eth1 is similiar to that

thanks

---

### Post by kalios on 2008-12-01
how does one correct the renamed part in the udev to actually use the hardware and not point to another the eth

---

### Post by Iowan on 2008-12-01
I don't have specifics, but look in the */etc/udev/rules.d* directory.  the files * 70-persistent-net.rules* and *75-persistent-net-generator.rules* might contain some useful information.

---

### Post by kalios on 2008-12-01
thanks 

im very greatful

---

### Post by kalios on 2008-12-02
i can see all three networks listed 

# PCI device 0x8086:0x100e (e1000)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:02:b3:e9:b5:e9", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

# PCI device 0x8086:0x1229 (e100)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:02:b3:e9:b3:18", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x10ec:0x8139 (8139too)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:11:3b:01:16:b2", ATTR{type}=="1", KERNEL=="eth*", NAME="eth2"

at least ubuntu found them, i dont know why its associating chosen eth interfaces with static ip's to one eth

---

### Post by SpaceTeddy on 2008-12-02
[OFFTOPIC]
you cannot have the subnet on multiple devices without bridging them. This will break your routing table and logic within the machine. Either bridge them, or put them in different subnets.
[/OFFTOPIC]

---

