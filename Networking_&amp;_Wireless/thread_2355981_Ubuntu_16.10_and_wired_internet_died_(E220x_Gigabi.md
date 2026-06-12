---
title: "Ubuntu 16.10 and wired internet died (E220x Gigabit Ethernet  - z170x-gaming 3)"
date: 2017-03-18
forum: Networking &amp; Wireless
---

### Post by khaj2 on 2017-03-18
Dear all,

please do help me, Iam tired of googling. After upgrade from 16.04.01 to 16.10 my wired internet connection just died. (It is by ubuntu, because now iam in dualboot windows on the same internet cable).

Please do help me - what should I download from where a what should i type into the commandline - Iam a Windows programmer, but Linux noob :(

This is 'the info' of everything I googled after seeing my internet connection dead, it should contain the infromation needed.

THank You very much, Iam actually in the process of testing ubuntu to forget windows forewer ;)


```

martin@martin-Lin:/etc/NetworkManager$ sudo service network-manager restart
martin@martin-Lin:/etc/NetworkManager$ ifconfig
enp9s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet6 fe80::428d:5cff:fee7:b729  prefixlen 64  scopeid 0x20<link>
        ether 40:8d:5c:e7:b7:29  txqueuelen 1000  (Ethernet)
        RX packets 96  bytes 6423 (6.4 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 29  bytes 3508 (3.5 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 19  


lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1  (Local Loopback)
        RX packets 46517  bytes 2873462 (2.8 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 46517  bytes 2873462 (2.8 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


martin@martin-Lin:/etc/NetworkManager$ nmcli device show
GENERAL.DEVICE:                         enp9s0
GENERAL.TYPE:                           ethernet
GENERAL.HWADDR:                         40:8D:5C:E7:B7:29
GENERAL.MTU:                            1500
GENERAL.STATE:                          10 (unmanaged)
GENERAL.CONNECTION:                     --
GENERAL.CON-PATH:                       --
WIRED-PROPERTIES.CARRIER:               on
IP4.GATEWAY:                            
IP6.ADDRESS[1]:                         fe80::428d:5cff:fee7:b729/64
IP6.GATEWAY:                            


GENERAL.DEVICE:                         lo
GENERAL.TYPE:                           loopback
GENERAL.HWADDR:                         00:00:00:00:00:00
GENERAL.MTU:                            65536
GENERAL.STATE:                          10 (unmanaged)
GENERAL.CONNECTION:                     --
GENERAL.CON-PATH:                       --
IP4.ADDRESS[1]:                         127.0.0.1/8
IP4.GATEWAY:                            
IP6.ADDRESS[1]:                         ::1/128
IP6.GATEWAY:                            
martin@martin-Lin:/etc/NetworkManager$ ifconfig -a
enp9s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet6 fe80::428d:5cff:fee7:b729  prefixlen 64  scopeid 0x20<link>
        ether 40:8d:5c:e7:b7:29  txqueuelen 1000  (Ethernet)
        RX packets 130  bytes 8463 (8.4 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 29  bytes 3508 (3.5 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 19  


lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1  (Local Loopback)
        RX packets 49605  bytes 3058742 (3.0 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 49605  bytes 3058742 (3.0 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


martin@martin-Lin:/etc/NetworkManager$ sudo lshw -C network
  *-network                 
       description: Ethernet interface
       product: Killer E220x Gigabit Ethernet Controller
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: enp9s0
       version: 10
       serial: 40:8d:5c:e7:b7:29
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi msix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=alx duplex=full latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:132 memory:df100000-df13ffff ioport:d000(size=128)
martin@martin-Lin:/etc/NetworkManager$ lspci
00:00.0 Host bridge: Intel Corporation Skylake Host Bridge/DRAM Registers (rev 07)
00:01.0 PCI bridge: Intel Corporation Skylake PCIe Controller (x16) (rev 07)
00:14.0 USB controller: Intel Corporation Sunrise Point-H USB 3.0 xHCI Controller (rev 31)
00:14.2 Signal processing controller: Intel Corporation Sunrise Point-H Thermal subsystem (rev 31)
00:16.0 Communication controller: Intel Corporation Sunrise Point-H CSME HECI #1 (rev 31)
00:17.0 SATA controller: Intel Corporation Sunrise Point-H SATA controller [AHCI mode] (rev 31)
00:1b.0 PCI bridge: Intel Corporation Sunrise Point-H PCI Root Port #17 (rev f1)
00:1c.0 PCI bridge: Intel Corporation Sunrise Point-H PCI Express Root Port #1 (rev f1)
00:1c.3 PCI bridge: Intel Corporation Sunrise Point-H PCI Express Root Port #4 (rev f1)
00:1c.4 PCI bridge: Intel Corporation Sunrise Point-H PCI Express Root Port #5 (rev f1)
00:1d.0 PCI bridge: Intel Corporation Sunrise Point-H PCI Express Root Port #9 (rev f1)
00:1d.4 PCI bridge: Intel Corporation Sunrise Point-H PCI Express Root Port #13 (rev f1)
00:1f.0 ISA bridge: Intel Corporation Sunrise Point-H LPC Controller (rev 31)
00:1f.2 Memory controller: Intel Corporation Sunrise Point-H PMC (rev 31)
00:1f.3 Audio device: Intel Corporation Sunrise Point-H HD Audio (rev 31)
00:1f.4 SMBus: Intel Corporation Sunrise Point-H SMBus (rev 31)
01:00.0 VGA compatible controller: NVIDIA Corporation GM206 [GeForce GTX 960] (rev a1)
01:00.1 Audio device: NVIDIA Corporation Device 0fba (rev a1)
03:00.0 PCI bridge: Intel Corporation DSL6540 Thunderbolt 3 Bridge [Alpine Ridge 4C 2015]
04:00.0 PCI bridge: Intel Corporation DSL6540 Thunderbolt 3 Bridge [Alpine Ridge 4C 2015]
04:01.0 PCI bridge: Intel Corporation DSL6540 Thunderbolt 3 Bridge [Alpine Ridge 4C 2015]
04:02.0 PCI bridge: Intel Corporation DSL6540 Thunderbolt 3 Bridge [Alpine Ridge 4C 2015]
04:04.0 PCI bridge: Intel Corporation DSL6540 Thunderbolt 3 Bridge [Alpine Ridge 4C 2015]
07:00.0 USB controller: Intel Corporation DSL6540 USB 3.1 Controller [Alpine Ridge]
09:00.0 Ethernet controller: Qualcomm Atheros Killer E220x Gigabit Ethernet Controller (rev 10)
martin@martin-Lin:/etc/NetworkManager$ ^C
martin@martin-Lin:/etc/NetworkManager$ dmesg | grep -i iflagn
martin@martin-Lin:/etc/NetworkManager$ dmesg | grep -i iwlagn
martin@martin-Lin:/etc/NetworkManager$ dmesg | grep -i network
[    0.714099] FUJITSU Extended Socket Network Device Driver - version 1.1 - Copyright (c) 2015 FUJITSU LIMITED
[    2.549851] audit: type=1400 audit(1489865731.360:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=918 comm="apparmor_parser"
[    2.549853] audit: type=1400 audit(1489865731.360:7): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-helper" pid=918 comm="apparmor_parser"
martin@martin-Lin:/etc/NetworkManager$ ^C
martin@martin-Lin:/etc/NetworkManager$ dmesg | grep -i enp9s0
[    0.759784] alx 0000:09:00.0 enp9s0: renamed from eth0
[ 1178.074130] IPv6: ADDRCONF(NETDEV_UP): enp9s0: link is not ready
[ 1178.074958] alx 0000:09:00.0 enp9s0: NIC Up: 1 Gbps Full
[ 1178.075161] IPv6: ADDRCONF(NETDEV_CHANGE): enp9s0: link becomes ready
martin@martin-Lin:/etc/NetworkManager$ dmesg | grep -i eth0
[    0.744418] alx 0000:09:00.0 eth0: Qualcomm Atheros AR816x/AR817x Ethernet [40:8d:5c:e7:b7:29]
[    0.759784] alx 0000:09:00.0 enp9s0: renamed from eth0
martin@martin-Lin:/etc/NetworkManager$ ^C
martin@martin-Lin:/etc/NetworkManager$ dmesg | grep -i atheros
[    0.744418] alx 0000:09:00.0 eth0: Qualcomm Atheros AR816x/AR817x Ethernet [40:8d:5c:e7:b7:29]
martin@martin-Lin:/etc/NetworkManager$ dmesg | grep -i ethernet
[    0.744418] alx 0000:09:00.0 eth0: Qualcomm Atheros AR816x/AR817x Ethernet [40:8d:5c:e7:b7:29]
[    4.509133] Bluetooth: BNEP (Ethernet Emulation) ver 1.3




changed:
etc network interfaces: # interfaces(5) file used by ifup(8) and ifdown(8)
#was: auto lo
#was: iface lo inet loopback
auto enp9s0
iface enp9s0 inet dhcp






martin@martin-Lin:/etc/network$ sudo service network-manager restart
martin@martin-Lin:/etc/network$ sudo lshw -C network
  *-network                 
       description: Ethernet interface
       product: Killer E220x Gigabit Ethernet Controller
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: enp9s0
       version: 10
       serial: 40:8d:5c:e7:b7:29
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi msix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=alx duplex=full latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:132 memory:df100000-df13ffff ioport:d000(size=128)
martin@martin-Lin:/etc/network$ 


martin@martin-Lin:/etc/network$ sudo ifconfig enp9s0 up
martin@martin-Lin:/etc/network$ sudo ifconfig eth0 up
eth0: ERROR while getting interface flags: No such device
martin@martin-Lin:/etc/network$ sudo service network-manager start








cat etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.0.53
martin@martin-Lin:/$ ping 127.0.0.53
PING 127.0.0.53 (127.0.0.53) 56(84) bytes of data.
64 bytes from 127.0.0.53: icmp_seq=1 ttl=64 time=0.026 ms
64 bytes from 127.0.0.53: icmp_seq=2 ttl=64 time=0.040 ms
64 bytes from 127.0.0.53: icmp_seq=3 ttl=64 time=0.040 ms
64 bytes from 127.0.0.53: icmp_seq=4 ttl=64 time=0.042 ms
64 bytes from 127.0.0.53: icmp_seq=5 ttl=64 time=0.041 ms
64 bytes from 127.0.0.53: icmp_seq=6 ttl=64 time=0.041 ms
64 bytes from 127.0.0.53: icmp_seq=7 ttl=64 time=0.041 ms
64 bytes from 127.0.0.53: icmp_seq=8 ttl=64 time=0.041 ms
64 bytes from 127.0.0.53: icmp_seq=9 ttl=64 time=0.041 ms
64 bytes from 127.0.0.53: icmp_seq=10 ttl=64 time=0.040 ms
64 bytes from 127.0.0.53: icmp_seq=11 ttl=64 time=0.038 ms
64 bytes from 127.0.0.53: icmp_seq=12 ttl=64 time=0.040 ms
^C
--- 127.0.0.53 ping statistics ---
12 packets transmitted, 12 received, 0% packet loss, time 11241ms
rtt min/avg/max/mdev = 0.026/0.039/0.042/0.006 ms
nmcli dev show | grep DNS




martin@martin-Lin:/$ nmcli dev show
GENERAL.DEVICE:                         enp9s0
GENERAL.TYPE:                           ethernet
GENERAL.HWADDR:                         40:8D:5C:E7:B7:29
GENERAL.MTU:                            1500
GENERAL.STATE:                          10 (unmanaged)
GENERAL.CONNECTION:                     --
GENERAL.CON-PATH:                       --
WIRED-PROPERTIES.CARRIER:               on
IP4.GATEWAY:                            
IP6.ADDRESS[1]:                         fe80::428d:5cff:fee7:b729/64
IP6.GATEWAY:                            


GENERAL.DEVICE:                         lo
GENERAL.TYPE:                           loopback
GENERAL.HWADDR:                         00:00:00:00:00:00
GENERAL.MTU:                            65536
GENERAL.STATE:                          10 (unmanaged)
GENERAL.CONNECTION:                     --
GENERAL.CON-PATH:                       --
IP4.ADDRESS[1]:                         127.0.0.1/8
IP4.GATEWAY:                            
IP6.ADDRESS[1]:                         ::1/128
IP6.GATEWAY:          




martin@martin-Lin:/$ nslookup google.com
Server:        127.0.0.53
Address:    127.0.0.53#53


** server can't find google.com: SERVFAIL
martin@martin-Lin:/$ sudo service systemd-resolved restart


deleted line dnsmasq from networkManager
restarted the service
stil no internet.


martin@martin-Lin:/etc/NetworkManager$ sudo rm /etc/resolv.conf
martin@martin-Lin:/etc/NetworkManager$ cd ..
martin@martin-Lin:/etc$ cd ..
martin@martin-Lin:/$ sudo rm /etc/resolv.conf
rm: cannot remove '/etc/resolv.conf': No such file or directory
martin@martin-Lin:/$ sudo ln -s ../run/resolvconf/resolv.conf /etc/resolv.conf
martin@martin-Lin:/$ sudo resolvconf -u
martin@martin-Lin:/$ sudo service network-manager restart
martin@martin-Lin:/$ 


sudo service network-manager restart
martin@martin-Lin:/$ sudo service resolvconf restart
martin@martin-Lin:/$ dmesg | grep -e alx
[    0.744418] alx 0000:09:00.0 eth0: Qualcomm Atheros AR816x/AR817x Ethernet [40:8d:5c:e7:b7:29]
[    0.759784] alx 0000:09:00.0 enp9s0: renamed from eth0
[   12.846082]  parport_pc ppdev lp parport ip_tables x_tables autofs4 hid_generic usbhid psmouse alx mdio ahci libahci i2c_hid video hid pinctrl_sunrisepoint pinctrl_intel fjes
[ 1178.074958] alx 0000:09:00.0 enp9s0: NIC Up: 1 Gbps Full
martin@martin-Lin:/$ lsmod | grep -e alx
alx                    36864  0
mdio                   16384  1 alx


```

---

### Post by khaj2 on 2017-03-18
And stackoverflow was faster:
Solved!
[http://askubuntu.com/questions/894418/internet-died-after-ubuntu-16-10-upgrade](http://askubuntu.com/questions/894418/internet-died-after-ubuntu-16-10-upgrade)

---

### Post by saladriel on 2017-03-19
Thank you SO MUCH, that also solved my issue!

---

