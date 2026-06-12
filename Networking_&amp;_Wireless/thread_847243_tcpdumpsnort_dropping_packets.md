---
title: "tcpdump/snort dropping packets"
date: 2008-07-02
forum: Networking &amp; Wireless
---

### Post by cgr122 on 2008-07-02
Hello, I recently had and IDS setup running snort on FedoraCore8. Because of problems with updates, I decided to rebuild ids using ubuntu 8.04 which I think handles updates much better. I got everything setup and it is detecting alerts but I noticed not as many as I used to get (16/day vs 200/day on Fedora). After looking into it more, I noticed a lot of packets are being dropped. Running tcpdump for about 20 seconds I had these results:

802 packets captured
1243 packets received by filter
441 packets dropped by kernel

Snort reports similar statistics when run on the console. My server has two nic cards, one of which has no ip address since I am mirroring on the switch all incoming/outgoing traffic entering/leaving our network. My interfaces file is setup as :

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.1.206
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.205

# The snort sniffing interface
auto eth1
iface eth1 inet dhcp

I'm not sure why this is a problem in Ubuntu but was not an issue in Fedora. In the googling I have done, the problem seems to be mostly cause by a slow processor (733 Mhz) but then why was it fine in Fedora. In watching `top`, my cpu runs between .5 - 4% even with snort/barnyard/mysql/apache all running. Memory 235560/840236 used and 0/778232 swap space used. I'm wondering if it is a driver or configuration issue. Here is the output of lshw -C network if it is any help.

root@linuxids:~# lshw -C network
  *-network
       description: Ethernet interface
       product: 82557/8/9/0/1 Ethernet Pro 100
       vendor: Intel Corporation
       physical id: 5
       bus info: pci@0000:01:05.0
       logical name: eth1
       version: 08
       serial: 00:50:8b:ea:01:16
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=full firmware=N/A latency=66 link=yes maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=100MB/s
  *-network
       description: Ethernet interface
       product: 3c905 100BaseTX [Boomerang]
       vendor: 3Com Corporation
       physical id: 3
       bus info: pci@0000:00:03.0
       logical name: eth0
       version: 00
       serial: 00:60:08:97:af:7b
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=full ip=192.168.1.206 latency=64 link=yes maxlatency=8 mingnt=3 module=3c59x multicast=yes port=MII speed=100MB/s

Thank you for any help as I would prefer to keep ubuntu on the server rather than rebuild in fedora.

---

### Post by wkimberly on 2009-02-02
I believe we are having the same problem. Did you find a solution to this problem?

---

