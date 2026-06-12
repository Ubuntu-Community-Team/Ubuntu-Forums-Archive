---
title: "No internet on wired connection - 14.04"
date: 2014-05-04
forum: Networking &amp; Wireless
---

### Post by davesbrain on 2014-05-04
Ubuntu 14.04LTS 64bit.    Indicator shows wired connection, but pages either don't load at all or extremely slow.   Unplugging the modem for a minute usually helps, but only for a short time.

```
davidjr@desktop:~$  sudo lshw -C network
[sudo] password for davidjr: 
  *-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 01
       serial: 00:1a:4d:5f:ca:53
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=10.0.0.2 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:44 ioport:d000(size=256) memory:f9000000-f9000fff memory:fa800000-fa81ffff
davidjr@desktop:~$ 
```

---

### Post by davesbrain on 2014-05-04
I changed the driver.   We shall see if it holds up.

```
davidjr@desktop:~$ sudo lshw -C network
[sudo] password for davidjr: 
  *-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 01
       serial: 00:1a:4d:5f:ca:53
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8168 driverversion=8.038.00-NAPI duplex=full ip=10.0.0.2 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:44 ioport:d000(size=256) memory:f9000000-f9000fff memory:fa800000-fa81ffff
davidjr@desktop:~$ 

```

---

### Post by smss on 2014-05-04
Whats your mean of wired connection? Are you installed any thing in virtual mode?
place the output of this command:
```

ifconfig

```

---

### Post by davesbrain on 2014-05-05
Seems to be stable so far.   I used this driver:
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#2]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#2")


Here is the output of ifconfig:
```
davidjr@desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1a:4d:5f:ca:53  
          inet addr:10.0.0.2  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:4dff:fe5f:ca53/64 Scope:Link
          inet6 addr: 2601:1:8d00:95:21a:4dff:fe5f:ca53/64 Scope:Global
          inet6 addr: 2601:1:8d00:95:5171:c85b:6510:8718/64 Scope:Global
          inet6 addr: 2601:1:8d00:95:c429:d6b7:914c:5a76/128 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:942543 errors:0 dropped:0 overruns:0 frame:0
          TX packets:475695 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1419002030 (1.4 GB)  TX bytes:32264327 (32.2 MB)
          Interrupt:44 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:935 errors:0 dropped:0 overruns:0 frame:0
          TX packets:935 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:97411 (97.4 KB)  TX bytes:97411 (97.4 KB)

davidjr@desktop:~$ 

```

---

### Post by smss on 2014-05-05
Hey man! I ask you about your installation mode, Now I suppose that you installed it in virtual mode and your settings is in NAT mode. 
So, You have to bridge it to your router, because seems the your windows have some problems in NAT/firewall/etc.
if you want to have NAT for 30 mps speed for internal shares, you could add another Adapter to your virtual machine.

---

### Post by davesbrain on 2014-05-06
Not sure what you mean by installation mode and NAT mode.   I just followed the instructions that were included with the Realtek driver.  Working good so far.

---

### Post by aquatabby on 2014-05-08
Exactly same issue for me - same setup, same problem.

I'll try the new driver you link to below.

Many thanks!

---

### Post by davesbrain on 2014-05-08
Be sure to use the version 8.038.   Hope it helps.

---

### Post by aquatabby on 2014-05-08
I installed the new driver and it seems to be working fine now.

Thanks very much!

---

### Post by davesbrain on 2014-05-08
That's great aquatabby!  Glad it helped you.   :)

---

