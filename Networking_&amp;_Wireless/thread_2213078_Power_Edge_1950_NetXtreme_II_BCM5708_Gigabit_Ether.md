---
title: "Power Edge 1950 NetXtreme II BCM5708 Gigabit Ethernet Network Issues"
date: 2014-03-24
forum: Networking &amp; Wireless
---

### Post by VamPikmin on 2014-03-24
I have a Dell 1950 running ubuntu server 12.10

First issue- dropped packets, how can I troubleshoot this. I'm mainly using this server for backups (nfs)

```

eth1      Link encap:Ethernet  HWaddr 00:15:c5:e5:86:db
          inet addr:192.168.131.21  Bcast:192.168.131.255  Mask:255.255.255.0
          inet6 addr: fe80::215:c5ff:fee5:86db/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18293510016 errors:0 dropped:4322 overruns:0 frame:0
          TX packets:23526388324 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:19734810079398 (19.7 TB)  TX bytes:32008602841236 (32.0 TB)


```

```

sudo lshw -class network
  *-network
       description: Ethernet interface
       product: NetXtreme II BCM5708 Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth1
       version: 11
       serial: 00:15:c5:e5:86:db
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 66MHz
       capabilities: pcix pm vpd msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=bnx2 driverversion=2.2.1 duplex=full firmware=7.6.15 bc 7.4.0 UMP 1.1.9 ip=192.168.131.21 latency=64 link=yes mingnt=64 multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:112 memory:f4000000-f5ffffff
  *-network
       description: Ethernet interface
       product: NetXtreme II BCM5708 Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 11
       serial: 00:15:c5:e5:86:d9
       capacity: 1Gbit/s
       width: 64 bits
       clock: 66MHz
       capabilities: pcix pm vpd msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=bnx2 driverversion=2.2.1 firmware=7.6.15 bc 7.4.0 UMP 1.1.9 latency=32 link=no mingnt=64 multicast=yes port=twisted pair
       resources: irq:111 memory:f8000000-f9ffffff


```

Second issue - only one card works at a time, no matter if static or dhcp is used. I can only ping one interface. At the moment eth1 is active, if I down it and reup eth0 everything will be fine. It's just when both are connected only one will ping

---

### Post by varunendra on 2014-03-24
Hi VamPikmin !

For the first issue - 4322 dropped packets against 18293510016 received ones is such a tiny ratio that I wouldn't bother even if it were a thousand times higher. :)

For the second issue - Are these both onboard adapters?

One of them seems to be "down" in your above output. Have you checked the BIOS to make sure there is no funny feature there doing this?

Can you manually bring it up (without disabling the other one)? Try -
```
sudo ifconfig eth0 down
sudo ifconfig eth0 up
```

I assume you are using /etc/network/interfaces file only to configure your network. Can we see its contents? -
```
cat /etc/network/interfaces
```

Any other places where you might have put additional codes/scripts to control the interfaces or their configuration?

---

### Post by VamPikmin on 2014-03-25
Hi Varunendra,

First of all thanks for you reply. I won't worry about the discarded packets anymore.

/etc/network/interfaces

```

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
#iface eth0 inet dhcp
iface eth0 inet static
address 192.168.131.26
netmask 255.255.255.0

auto eth1
iface eth1 inet static
address 192.168.131.21
netmask 255.255.255.0
gateway 192.168.131.1


```

Am I meant to use gateway for eth0 as well? I can ping 192.168.131.26 from the server itself but nothing from a remote host. I would like to use this second nic just for redundancy, or even load balancing if that's possible
I can manually bring the interface up and down

---

### Post by varunendra on 2014-03-25
I don't know if load balancing is even possible the way you want. I'm not even familiar with the kind of network configuration you have done.

When you did "sudo ifconfig down/up", did its link become active? Check the output of "sudo lshw -C network" again and see if it shows "**link=yes**".

If both interfaces can be made active at the same time (I believe this is hardware dependent, but I may be wrong), the 'redundancy' part will be automatically implemented with your current setup. But I can't say a word about 'load balancing'.

Oh, and it is certainly NOT necessary to define gateway for both interfaces, but if you want redundancy on the Internet connectivity as well, then yes, you Must define gateway for both. At any given time, only one of the interfaces would be used for gateway anyway.

So the key question is - can you enable the "link" on both interfaces anyhow? And..
..when you start the system with both cables connected to the router/switch, does the link appears to be automatically disabled on one of them?

---

### Post by tgalati4 on 2014-03-25
Perhaps you want to bond the interfaces:  [https://help.ubuntu.com/community/UbuntuBonding](https://help.ubuntu.com/community/UbuntuBonding)

---

### Post by VamPikmin on 2014-03-25
These adapters are onboard. After I have left work yesterday and brought up eth0 I couldn't ping it's IP from my pc. Came back this morning, it's looking good and all of a sudden I can. I would like to restart the box after the backup has finished and see if both IPs will be reachable once the system boots.

Will look into bonding as well

Guys thank you!

---

### Post by VamPikmin on 2014-03-25
All good upon restart, I'm really not sure what caused it not to work in the first place. I have reserved both IPs on the DNS server and set static

---

