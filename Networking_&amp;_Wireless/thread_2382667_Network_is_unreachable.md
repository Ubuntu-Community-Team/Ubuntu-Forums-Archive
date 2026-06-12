---
title: "Network is unreachable"
date: 2018-01-16
forum: Networking &amp; Wireless
---

### Post by imanolooo on 2018-01-16
Hi all,

I have a PC with a dual installation of windows and ubuntu. I'm returning to use ubuntu after some time and, I realized that using Ubuntu I can not use internet. I tried to fix it following threads of this forum, but I didn't succeed. So, I tried to make a fresh ubuntu installation 16.04.3, and it's still not working... Then, I ask your help if some of you can help me.

I attach the returns of some commands, maybe they can be used as a clue. I would appreciate any help, because I quite desperate right now. Thanks!

```

imanolooo@imanolooo-PC:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: enp8s0
       version: 06
       serial: bc:ae:c5:e3:4c:1e
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8168e-2.fw latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:36 ioport:c000(size=256) memory:f4104000-f4104fff memory:f4100000-f4103fff

```


```

imanolooo@imanolooo-PC:~$ ping 192.168.0.2
connect: Network is unreachable

```

```

imanolooo@imanolooo-PC:~$ ping www.google.com
connect: Network is unreachable

```



```


imanolooo@imanolooo-PC:~$ ifconfig
enp8s0    Link encap:Ethernet  HWaddr bc:ae:c5:e3:4c:1e  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:537 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:92502 (92.5 KB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:13812 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13812 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1080856 (1.0 MB)  TX bytes:1080856 (1.0 MB)

```


```


imanolooo@imanolooo-PC:~$ sudo vi /etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

```


```


imanolooo@imanolooo-PC:~$ sudo dmesg | grep "eth0"
[    2.752864] r8169 0000:08:00.0 eth0: RTL8168e/8111e at 0xffffb01740655000, bc:ae:c5:e3:4c:1e, XID 0c200000 IRQ 36
[    2.752865] r8169 0000:08:00.0 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[    2.778851] r8169 0000:08:00.0 enp8s0: renamed from eth0

```


```


imanolooo@imanolooo-PC:~$ sudo dmesg | grep "enp8s0"
[    2.778851] r8169 0000:08:00.0 enp8s0: renamed from eth0
[   15.237034] IPv6: ADDRCONF(NETDEV_UP): enp8s0: link is not ready
[   15.457731] r8169 0000:08:00.0 enp8s0: link down
[   15.457741] r8169 0000:08:00.0 enp8s0: link down
[   15.457777] IPv6: ADDRCONF(NETDEV_UP): enp8s0: link is not ready
[   17.089249] r8169 0000:08:00.0 enp8s0: link up
[   17.089260] IPv6: ADDRCONF(NETDEV_CHANGE): enp8s0: link becomes ready
imanolooo@imanolooo-PC:~$ 

```

---

