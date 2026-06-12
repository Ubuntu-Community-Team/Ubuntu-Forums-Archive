---
title: "What am I doing wrong?!"
date: 2015-11-16
forum: Networking &amp; Wireless
---

### Post by ash_law on 2015-11-16
Hi All,

I am running Ubuntu Server 14.04.3 with 2 x NIC cards.

ETH0 (static IP (outside world to Server) Internet working) and ETH1 (static IP (Server to Windows 10 box) Internet not working). I would prefer that the Windows 10 connection be a DHCP connection (as previously setup via suse & untangle).

The problem is that no matter what I try re: the various help pages surrounding setting up the server as a gateway - I cannot get the windows box to connect to the internet nor can I get the server to show up in my computer on the windows box.

I want to use ubuntu server as a gateway (which is why I have 2 x NIC cards); as a fileserver / backup for the windows box; as a print server and as mail server.

ifconfig:```
eth0      Link encap:Ethernet  HWaddr 00:40:f4:59:3b:4d  
          inet addr:192.168.1.151  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::240:f4ff:fe59:3b4d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:36110 errors:0 dropped:5 overruns:0 frame:0
          TX packets:11909 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:23739594 (23.7 MB)  TX bytes:1399341 (1.3 MB)

eth1      Link encap:Ethernet  HWaddr 00:19:66:0b:d5:2c  
          inet addr:192.168.1.121  Bcast:192.168.1.245  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1172 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1172 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:182029 (182.0 KB)  TX bytes:182029 (182.0 KB)
```

Route:```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         192.168.1.254   0.0.0.0         UG    0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
192.168.1.0     *               255.255.255.0   U     0      0        0 eth1
```

sudo lshw -C network:```
 *-network               
       description: Ethernet interface
       product: DP83815 (MacPhyter) Ethernet Controller
       vendor: National Semiconductor Corporation
       physical id: 8
       bus info: pci@0000:01:08.0
       logical name: eth0
       version: 00
       serial: 00:40:f4:59:3b:4d
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii fibre 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=natsemi driverversion=2.1 duplex=full ip=192.168.1.151 latency=32 link=yes maxlatency=52 mingnt=11 multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:19 ioport:d800(size=256) memory:deeff000-deefffff memory:deee0000-deeeffff


```

/etc/network/interfaces:```
source /etc/network/interfaces.d/*

# The loopback network interface
auto lo eth0 eth1
iface lo inet loopback

# Ext > Svr

iface eth0 inet static
    address 192.168.1.151
    netmask 255.255.255.0
    broadcast 192.168.1.255
    network 192.168.1.0
    gateway 192.168.1.254

# Svr > Win10

iface eth1 inet static
    address 192.168.1.121
    netmask 255.255.255.0
    broadcast 192.168.1.245
    network 192.168.1.0
```

regards,

---

### Post by gordintoronto on 2015-11-16
[https://help.ubuntu.com/community/Router](https://help.ubuntu.com/community/Router)

Did you install Samba?

---

### Post by ash_law on 2015-11-17
Hi gordintoronto,

yes - samba has been installed - it was installed on install of ubuntu server.

---

