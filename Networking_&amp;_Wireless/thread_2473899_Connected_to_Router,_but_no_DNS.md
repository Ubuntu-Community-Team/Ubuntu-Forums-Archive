---
title: "Connected to Router, but no DNS"
date: 2022-04-17
forum: Networking &amp; Wireless
---

### Post by culperat on 2022-04-17
I've gone through and installed r8125 and have been able to connect to my router via LAN. But I'm still unable to access google.com.

Using *ifconfig -a* I get:
```

docker0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        inet 172.17.0.1  netmask 255.255.0.0  broadcast 172.17.255.255
        ether 02:42:86:3d:36:bb  txqueuelen 0  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

enp3s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.0.140  netmask 255.255.255.0  broadcast 192.168.0.255
        inet6 fe80::da5e:d3ff:fe82:51e0  prefixlen 64  scopeid 0x20<link>
        ether d8:5e:d3:82:51:e0  txqueuelen 1000  (Ethernet)
        RX packets 107  bytes 28252 (28.2 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 195  bytes 31182 (31.1 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 18  

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 2207  bytes 186627 (186.6 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 2207  bytes 186627 (186.6 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

```

From *cat /etc/network/interfaces* :
```
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
```

From *sudo lshw -C network* :
```

  *-network UNCLAIMED       
       description: Network controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 14.3
       bus info: pci@0000:00:14.3
       version: 11
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
       resources: memory:4331c000-4331ffff
  *-network
       description: Ethernet interface
       product: RTL8125 2.5GbE Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: enp3s0
       version: 05
       serial: d8:5e:d3:82:51:e0
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8125 driverversion=9.008.00-NAPI duplex=full ip=192.168.0.140 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:18 ioport:3000(size=256) memory:43200000-4320ffff memory:43210000-43213fff
```

I am able to ping IP addresses like 8.8.8.8, just not named addresses. So educated guess is something with DHCP, but I'm no network expert. This all happened after changing out my motherboards.

---

### Post by chili555 on 2022-04-18
Please run and post:

```
ls -al /etc/resolv.conf
ls /etc/NetworkManager/system-connections/
```Thanks.

---

### Post by culperat on 2022-04-18
I got the following
```
> ls -al /etc/resolv.conf
lrwxrwxrwx 1 root root 27 Apr 17 05:11 /etc/resolv.conf -> /run/resolvconf/resolv.conf
```
and
```
> ls /etc/NetworkManager/system-connections/
 FlashThunder            'Wired Primary.nmconnection'
 nightvalepubliclibrary  'Wireless Mojo'
```

---

### Post by chili555 on 2022-04-18
Please do:

```
sudo rm -f /etc/resolv.conf
sudo ln -s /run/systemd/resolve/resolv.conf  /etc/resolv.conf
```

Reboot and test.

```
ping -c3 8.8.8.8
ping -c3 www.ubuntu.com
```

---

### Post by culperat on 2022-04-18
That worked! The symbolic link was broken.

---

