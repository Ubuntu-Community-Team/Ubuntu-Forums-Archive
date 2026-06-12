---
title: "Intermittent browsing - DNS problem?"
date: 2016-03-14
forum: Networking &amp; Wireless
---

### Post by habana on 2016-03-14
A few days ago I started to have problems connecting to the web. It is intermittent but I can always connect to my ISP's home page. Firefox just displays 'Problem loading page' but Chromium displays  DNS_PROBE_FINISHED_BAD_CONFIG which supported my belief that my ISP's DNS server was faulty - it has happened before. I tried changing the DNS primary to 8.8.8.8 with no change. I can quite often perform a Google search but can't access the results. I later discovered that another PC on my network is rock solid so it's obviously not an ISP problem.

I have wired connections to my router so I swapped cables and ports to establish that the problem is with my Ubuntu 15.10 PC. So, is it a hardware or a software problem? It seems unlikely to be a failed network interface (integrated Realtek RTL8111/8168/8411) as I can always communicate with my router and I can ping the IP address of a web page I can't visit. Obviously I googled for a solution but haven't found one that worked for me - many are for older versions of Ubuntu so may not be relevant.

One post suggested updating the network interface driver so I updated the latest from Synaptic and blacklisted the old driver. No change. Another suggestion was to flush the DNS cache using the command:
```
/etc/init.d/nscd restart
```
Again, no change.

I'm afraid I'm stumped.Any advice gratefully accepted.

Herewith the output of several commands. Note there is a second NIC in the machine. I put this in when I thought the motherboard NI may be faulty. The new card is not configured,

```
bill@computer1:~$ dmesg |grep eth[0-9]
[    0.761039] 8139too 0000:03:01.0 eth1: RealTek RTL8139 at 0x000000000001d000, 00:48:54:68:03:72, IRQ 19
[    0.766099] 8139too 0000:03:01.0 enp3s1: renamed from eth1
[    3.440626] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    3.440812] eth0: 0xffffc90000c6e000, 90:2b:34:10:e4:2d, IRQ 27
[    3.678704] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    5.691209] r8168: eth0: link up
[    5.691524] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready

```

```
bill@computer1:~$ sudo lshw -C network
[sudo] password for bill: 
  *-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 06
       serial: 90:2b:34:10:e4:2d
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8168 driverversion=8.040.00-NAPI duplex=full ip=192.168.1.12 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:27 ioport:e000(size=256) memory:f0004000-f0004fff memory:f0000000-f0003fff
  *-network
       description: Ethernet interface
       product: RTL-8100/8101L/8139 PCI Fast Ethernet Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:03:01.0
       logical name: enp3s1
       version: 10
       serial: 00:48:54:68:03:72
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=32 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10Mbit/s
       resources: irq:19 ioport:d000(size=256) memory:f7c00000-f7c000ff
```

```
bill@computer1:~$ ifconfig -a
enp3s1    Link encap:Ethernet  HWaddr 00:48:54:68:03:72  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth0      Link encap:Ethernet  HWaddr 90:2b:34:10:e4:2d  
          inet addr:192.168.1.12  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::922b:34ff:fe10:e42d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18461 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17895 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:16531204 (16.5 MB)  TX bytes:2450815 (2.4 MB)
          Interrupt:27 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:4422 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4422 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:494638 (494.6 KB)  TX bytes:494638 (494.6 KB)

```

```
bill@computer1:~$ more /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1
```


```
bill@computer1:~$ route 
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         Vigor.router    0.0.0.0         UG    100    0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
192.168.1.0     *               255.255.255.0   U     100    0        0 eth0
```

---

### Post by habana on 2016-03-15
After more research I found a note suggesting that dnsmasq  might be my problem. Here is the network manager status, which shows a couple of warnings:

```
bill@computer1:~$ service NetworkManager status -l
&#9679; NetworkManager.service - Network Manager
   Loaded: loaded (/lib/systemd/system/NetworkManager.service; enabled; vendor preset: enabled)
   Active: active (running) since Tue 2016-03-15 18:40:53 AEST; 2h 47min ago
 Main PID: 641 (NetworkManager)
   CGroup: /system.slice/NetworkManager.service
           &#9500;&#9472; 641 /usr/sbin/NetworkManager --no-daemon
           &#9500;&#9472;1518 /sbin/dhclient -d -q -sf /usr/lib/NetworkManager/nm-dhcp-helper -pf /run/sendsigs.omit.d/net...
           &#9492;&#9472;1529 /usr/sbin/dnsmasq --no-resolv --keep-in-foreground --no-hosts --bind-interfaces --pid-file=/...

Mar 15 18:40:56 computer1 dnsmasq[1529]: **[B]warning: no upstream servers configured**[/B]
Mar 15 18:40:56 computer1 NetworkManager[641]: <info>  (eth0): Activation: successful, device activated.
Mar 15 18:40:56 computer1 NetworkManager[641]: **<warn>  dnsmasq appeared on DBus: :1.60**
Mar 15 18:40:56 computer1 NetworkManager[641]: <info>  Writing DNS information to /sbin/resolvconf
Mar 15 18:40:56 computer1 dnsmasq[1529]: setting upstream servers from DBus
Mar 15 18:40:56 computer1 dnsmasq[1529]: using nameserver 202.144.176.10#53
Mar 15 18:40:56 computer1 dnsmasq[1529]: using nameserver 202.144.176.9#53
Mar 15 18:41:00 computer1 NetworkManager[641]: <info>  startup complete
Mar 15 18:41:03 computer1 NetworkManager[641]: <info>  WiFi hardware radio set enabled
Mar 15 18:41:03 computer1 NetworkManager[641]: <info>  WWAN hardware radio set enabled
```

I have no idea what to do about them. The IP addresses are the DNS addresses specified by my ISP.

---

### Post by habana on 2016-03-15
OK. A bit more research and I may have found the solution. It appears that dnsmasq is not needed for most applications and can be disabled, see [http://biscuit.ninja/blog/dns-resolution-problems-in-ubuntu](http://biscuit.ninja/blog/dns-resolution-problems-in-ubuntu)

As suggested, I commented out the line dns=dnsmasq in  /etc/NetworkManager/NetworkManager.conf and restarted Network Manager  ```
service NetworkManager restart
```

Here is the new Network Manager status:

```
bill@computer1:~$ service NetworkManager status -l
&#9679; NetworkManager.service - Network Manager
   Loaded: loaded (/lib/systemd/system/NetworkManager.service; enabled; vendor preset: enabled)
   Active: active (running) since Tue 2016-03-15 21:52:42 AEST; 34min ago
 Main PID: 2958 (NetworkManager)
   CGroup: /system.slice/NetworkManager.service
           &#9500;&#9472;1529 /usr/sbin/dnsmasq --no-resolv --keep-in-foreground --no-hosts --bind-interfa...
           &#9500;&#9472;2958 /usr/sbin/NetworkManager --no-daemon
           &#9492;&#9472;3007 /sbin/dhclient -d -q -sf /usr/lib/NetworkManager/nm-dhcp-helper -pf /run/sen...

Mar 15 21:52:42 computer1 NetworkManager[2958]: <info>    plen 24 (255.255.255.0)
Mar 15 21:52:42 computer1 NetworkManager[2958]: <info>    gateway 192.168.1.1
Mar 15 21:52:42 computer1 NetworkManager[2958]: <info>    server identifier 192.168.1.1
Mar 15 21:52:42 computer1 NetworkManager[2958]: <info>    lease time 259200
Mar 15 21:52:42 computer1 NetworkManager[2958]: <info>    nameserver '202.144.176.10'
Mar 15 21:52:42 computer1 NetworkManager[2958]: <info>    nameserver '202.144.176.9'
Mar 15 21:52:42 computer1 NetworkManager[2958]: <info>  (eth0): DHCPv4 state changed unknown...nd
Mar 15 21:52:42 computer1 dhclient[3007]: bound to 192.168.1.12 -- renewal in 118119 seconds.
Mar 15 21:52:52 computer1 NetworkManager[2958]: <info>  WiFi hardware radio set enabled
Mar 15 21:52:52 computer1 NetworkManager[2958]: <info>  WWAN hardware radio set enabled
```

So far everything is back to normal. My question now is: I upgraded to 15.10 back in October. What happened to cause this problem now? Anyway I will monitor things for a day or two and mark as solved if all goes well.

---

