---
title: "Ubuntu Wired Connection drops often, don't know why."
date: 2014-11-11
forum: Networking &amp; Wireless
---

### Post by will-trumble on 2014-11-11
Hey, i'm using Ubuntu 14.04 LTS and i have a wired connection that drops frequently when i play games on multiplayer, i have tried to fix this but im stuck, it seems to do fine when just using Firefox or Spotify. Does anyone have an idea why this is happening other computers using this ethernet cable work fine, i've also tried using other ethernet cables and rebooting the modem. I'll post some information below.


 *-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 0c
       serial: 44:8a:5b:ce:8c:ee
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168g-2_0.0.1 02/06/13 ip=10.0.0.28 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
       resources: irq:52 ioport:d000(size=256) memory:fe900000-fe900fff memory:d0900000-d0903fff


eth0      Link encap:Ethernet  HWaddr 44:8a:5b:ce:8c:ee  
          inet addr:10.0.0.28  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: 2601:1:8b80:4de:20f5:ec2a:259a:fef/64 Scope:Global
          inet6 addr: 2601:1:8b80:4de:468a:5bff:fece:8cee/64 Scope:Global
          inet6 addr: fe80::468a:5bff:fece:8cee/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12757 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6195 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:15736259 (15.7 MB)  TX bytes:710167 (710.1 KB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:153 errors:0 dropped:0 overruns:0 frame:0
          TX packets:153 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10929 (10.9 KB)  TX bytes:10929 (10.9 KB)
  

If you know whats wrong please help.

---

