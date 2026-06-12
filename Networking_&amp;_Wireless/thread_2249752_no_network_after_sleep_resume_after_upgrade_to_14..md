---
title: "no network after sleep resume after upgrade to 14.10"
date: 2014-10-24
forum: Networking &amp; Wireless
---

### Post by DanCar on 2014-10-24
I upgraded to 14.10 and my system is good after fresh start.  But after sleep and then resume my network doesn't work.
if I try ping 8.8.8.8 I get a message:
connect: Network is unreachable

If I add to /etc/network/interfaces the following
auto eth0
iface eth0 inet dhcp

and then do
sudo ifdown eth0 && sudo ifup eth0

then my browser works but not pidgin im client.

Need help.

Below is some info from my system:
sudo lshw -numeric -C network
Yields nothing.
```

grep -i eth lshw.txt -C 3
             configuration: driver=snd_hda_intel latency=0 maxlatency=5 mingnt=2
             resources: irq:21 memory:efff4000-efff7fff
        *-bridge
             description: Ethernet interface
             product: MCP55 Ethernet [10DE:373]
             vendor: NVIDIA Corporation [10DE]
             physical id: 11
             bus info: pci@0000:00:11.0
             logical name: eth0
             version: a3
             serial: 04:4b:80:80:80:03
             size: 1000000000
             capacity: 1000000000
             width: 32 bits
             clock: 66MHz
             capabilities: bridge pm msix msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 duplex=full ip=192.168.1.15 latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=1Gbit/s
             resources: irq:42 memory:efffa000-efffafff ioport:ec00(size=8) memory:efff9000-efff90ff memory:efff8000-efff800f

```
```

ip link
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN mode DEFAULT group default
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP mode DEFAULT group default qlen 1000
    link/ether 04:4b:80:80:80:03 brd ff:ff:ff:ff:ff:ff

```

---

### Post by overdrank on 2014-10-24
Moved to  Networking & Wireless

---

### Post by DanCar on 2014-10-31
I was able to get network fully operation after sleep resume by restarting network manager.
sudo /etc/init.d/network-manager restart

---

