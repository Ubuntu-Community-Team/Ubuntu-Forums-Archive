---
title: "No Network After New Install of Xubuntu"
date: 2017-01-16
forum: Networking &amp; Wireless
---

### Post by Rick St. George on 2017-01-16
After fresh install of Xubuntu v16.04LTS on old Emachine W5233, we get no Network. 
Access is to Router which works fine for other computers and wifi.
Here is some output ....

```

annette@annette-945GCT-M3:~$ ifconfig
enp1s5    Link encap:Ethernet  HWaddr 00:1e:90:42:6c:2a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:69 errors:0 dropped:1 overruns:0 frame:0
          TX packets:1598 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6476 (6.4 KB)  TX bytes:265731 (265.7 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:46436 errors:0 dropped:0 overruns:0 frame:0
          TX packets:46436 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:3626112 (3.6 MB)  TX bytes:3626112 (3.6 MB)

annette@annette-945GCT-M3:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL-8100/8101L/8139 PCI Fast Ethernet Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 5
       bus info: pci@0000:01:05.0
       logical name: enp1s5
       version: 10
       serial: 00:1e:90:42:6c:2a
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=32 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10Mbit/s
       resources: irq:20 ioport:ec00(size=256) memory:fdeff000-fdeff0ff
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.

annette@annette-945GCT-M3:~$ ip link ls
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN mode DEFAULT group default qlen 1
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: enp1s5: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast state DOWN mode DEFAULT group default qlen 1000
    link/ether 00:1e:90:42:6c:2a brd ff:ff:ff:ff:ff:ff


annette@annette-945GCT-M3:~$ ip route show

annette@annette-945GCT-M3:~$ ls /sys/class/net
enp1s5  lo

annette@annette-945GCT-M3:~$ cat /etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


```

What do you think guys???

Thanks!
Rick

---

### Post by praseodym on 2017-01-17
Hi,

"normally" this device loads two drivers, so blacklist the wrong one:
```

echo "blacklist 8139cp" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Reboot.

The shown 8139too is the correct one.

---

### Post by Rick St. George on 2017-01-17
That did it ... Thanks a Million !!!

Case closed.

;-)

---

