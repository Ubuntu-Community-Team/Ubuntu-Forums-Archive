---
title: "Ethernet interface does not start after power outage"
date: 2016-05-12
forum: Networking &amp; Wireless
---

### Post by ruippeixotog on 2016-05-12
I'm running Ubuntu Server 16.04 and I'm with a problem I have no idea what the cause is or where to look for solutions. After a power outage, my server did not connect automatically to the internet and I can't do anything for my network interface to start.

The content of my [FONT=courier new]/etc/network/interfaces[FONT=verdana] is[/FONT][/FONT]:

```

source /etc/network/interfaces.d/*

auto lo

# The loopback network interface
iface lo inet loopback

# The primary network interface
iface eth0 inet static
  address 192.168.1.4
  netmask 255.255.255.0
  gateway 192.168.1.1
  network 192.168.1.0
  broadcast 192.168.1.255
  dns-nameservers 192.168.1.1

```

However, after I boot my computer and log in, [FONT=courier new]ifconfig[/FONT] doesn't show [FONT=courier new]eth0[/FONT]:

```

docker0   Link encap:Ethernet  HWaddr 02:42:9a:be:c6:bf
          inet addr:172.17.0.1  Bcast:0.0.0.0  Mask:255.255.0.0
          inet6 addr: fe80::42:9aff:febe:c6bf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:38 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3106 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2372 (2.3 KB)  TX bytes:1035188 (1.0 MB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:64769 errors:0 dropped:0 overruns:0 frame:0
          TX packets:64769 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1
          RX bytes:4816496 (4.8 MB)  TX bytes:4816496 (4.8 MB)

tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00
          inet addr:10.8.0.1  P-t-P:10.8.0.2  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

veth18919f5 Link encap:Ethernet  HWaddr 5a:54:c4:41:df:3e
          inet6 addr: fe80::5854:c4ff:fe41:df3e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5968 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:648 (648.0 B)  TX bytes:2015684 (2.0 MB)

veth65fbc82 Link encap:Ethernet  HWaddr c6:46:48:b9:e8:fe
          inet6 addr: fe80::c446:48ff:feb9:e8fe/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:30 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6018 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2256 (2.2 KB)  TX bytes:2027168 (2.0 MB)

```

Trying to do [FONT=courier new]ifconfig eth0 up[/FONT] fails with a message "eth0: ERROR while getting interface flags: No such device".

If I run [FONT=courier new]lshw -C network[/FONT], it shows my Ethernet physical device, but in a disabled state:

```

  *-network DISABLED
       description: Ethernet interface
       product: NetXtreme BCM5755 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:3f:00.0
       logical name: enp63s0
       version: 02
       serial: 00:21:5a:5f:f3:60
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.137 duplex=full firmware=5755-v3.29 ip=192.168.9.21 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:31 memory:f3000000-f300ffff
  *-network:0
       description: Ethernet interface
       physical id: 1
       logical name: veth18919f5
       serial: 5a:54:c4:41:df:3e
       size: 10Gbit/s
       capabilities: ethernet physical
       configuration: autonegotiation=off broadcast=yes driver=veth driverversion=1.0 duplex=full link=yes multicast=yes port=twisted pair speed=10Gbit/s
  *-network:1
       description: Ethernet interface
       physical id: 2
       logical name: veth65fbc82
       serial: c6:46:48:b9:e8:fe
       size: 10Gbit/s
       capabilities: ethernet physical
       configuration: autonegotiation=off broadcast=yes driver=veth driverversion=1.0 duplex=full link=yes multicast=yes port=twisted pair speed=10Gbit/s

```

If I run [FONT=courier new]dhclient[/FONT] I am able to connect to the Internet (and make the network card appear as enabled in the previous command), but with a different network interface and with an IP assigned via DHCP - so the problem doesn't seem to be hardware-based. As the server worked well before the power outage, I believe it could be a corrupted file or some file left in an inconsistent state.

Can you help me? I looked through [FONT=courier new]/var/log/syslog[/FONT] and the log of [FONT=courier new]networking.service[/FONT] and I didn't find anything related to this problem, but if you need me to grep some specific text or to show the result of a command or the contents of a file, please tell me. Thank you in advance for any help!

---

