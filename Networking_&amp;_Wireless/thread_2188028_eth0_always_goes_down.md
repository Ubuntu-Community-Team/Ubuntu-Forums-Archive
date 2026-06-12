---
title: "eth0 always goes down"
date: 2013-11-15
forum: Networking &amp; Wireless
---

### Post by 5vlastkzn on 2013-11-15
My problem is my LAN connection always goes up and down.  Sometimes it works perfectly but a lot of time it doesn't. Here are my  hardware specs:
  
[LIST]
[*]Motherboard: GIGABYTE, GA-X58A-UD7. It comes with 2 Realtek Ethernet PCIe LAN 
[*]Router: Zyxel Keenetic 4G 
[/LIST]
  $ uname -a
```
Linux server-desktop 2.6.32-53-generic-pae #115-Ubuntu SMP Wed Oct 23 17:44:16 UTC 2013 i686 GNU/Linux

```  $ cat /etc/network/interfaces
```
auto lo
iface lo inet loopback
auto eth0
iface eth0 inet dhcp
```

$ cat /etc/dhcp3/dhclient.conf
```

# ... leaving out everything that is commented
request subnet-mask, broadcast-address, time-offset, routers,
    domain-name, domain-name-servers, domain-search, host-name,
    netbios-name-servers, netbios-scope, interface-mtu,
    rfc3442-classless-static-routes, ntp-servers;
    end vendor-class-identifier "MSFT 5.0";
```

$ ifconfig
# ... leaving out eth1 lo etc.
```
eth0      Link encap:Ethernet  HWaddr 1c:6f:65:94:58:cd  
          inet addr:192.168.1.35  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fd58:48c8:2da5:0:1e6f:65ff:fe94:58cd/64 Scope:Global
          inet6 addr: fe80::1e6f:65ff:fe94:58cd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7815 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8640 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5841826 (5.8 MB)  TX bytes:1250252 (1.2 MB)
          Interrupt:32 Base address:0xe000 
```

$ lspci | grep -i ether
```
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
```

$ /usr/sbin/ethtool -i eth0

```
driver: r8168
version: 8.037.00-NAPI
firmware-version: 
bus-info: 0000:07:00.0
```

$ /sbin/lsmod | grep r8168
```
r8168                 240944  0 

```  Some from my log files
  ```
Nov 14 17:18:25 server-desktop kernel: [  964.478260] r8168: eth0: link up
Nov 14 17:18:25 server-desktop kernel: [  964.478492] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Nov 14 17:18:25 server-desktop kernel: [  964.678691] userif-2: sent link down event.
Nov 14 17:18:35 server-desktop kernel: [  964.678694] userif-2: sent link up event.
Nov 14 17:19:25 server-desktop kernel: [ 1024.899257] userif-2: sent link down event.
Nov 14 17:19:36 server-desktop kernel: [ 1024.899260] userif-2: sent link up event.
Nov 14 17:19:36 server-desktop kernel: [ 1035.839137] userif-2: sent link down event.
Nov 14 17:19:36 server-desktop kernel: [ 1035.839141] userif-2: sent link up event.
Nov 14 17:19:36 server-desktop kernel: [ 1035.954788] ADDRCONF(NETDEV_UP): eth0: link is not ready
Nov 14 17:19:36 server-desktop kernel: [ 1036.055765] userif-2: sent link down event.
Nov 14 17:19:42 server-desktop kernel: [ 1036.055767] userif-2: sent link up event.
Nov 14 17:19:42 server-desktop kernel: [ 1041.950400] r8168: eth0: link up
Nov 14 17:19:42 server-desktop kernel: [ 1041.950898] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Nov 14 17:19:42 server-desktop kernel: [ 1042.151099] userif-2: sent link down event.
Nov 14 17:19:43 server-desktop kernel: [ 1042.151103] userif-2: sent link up event.
Nov 14 17:19:43 server-desktop kernel: [ 1042.532152] userif-2: sent link down event.
Nov 14 17:23:48 server-desktop kernel: [ 1042.532155] userif-2: sent link up event.
Nov 14 17:23:48 server-desktop kernel: [ 1287.309445] ADDRCONF(NETDEV_UP): eth0: link     is not ready
Nov 14 17:23:48 server-desktop kernel: [ 1287.320671] userif-2: sent link down event.
Nov 14 17:23:59 server-desktop kernel: [ 1287.320674] userif-2: sent link up event.
Nov 14 17:23:59 server-desktop kernel: [ 1298.301786] r8168: eth0: link up
Nov 14 17:23:59 server-desktop kernel: [ 1298.302014] ADDRCONF(NETDEV_CHANGE): eth0:     link becomes ready
Nov 14 17:23:59 server-desktop kernel: [ 1298.502221] userif-2: sent link down event.
Nov 14 17:24:01 server-desktop kernel: [ 1298.502224] userif-2: sent link up event.
Nov 14 17:24:01 server-desktop kernel: [ 1300.281431] userif-2: sent link down event.

```  
PS: Sometimes the network works fine for a couple of days, then the problem returns again.

---

