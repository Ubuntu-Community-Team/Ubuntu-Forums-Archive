---
title: "Ethernet connection type/speed"
date: 2008-08-18
forum: Networking &amp; Wireless
---

### Post by yang on 2008-08-18
Hi, is there a way to tell what kind of Ethernet connection I have? (10 base T, 100 base T, GigE, etc.)  Thanks!

---

### Post by mellowd on 2008-08-18
Type this:

```
sudo aptitude install hwinfo
```

When that's done type this:

```
hwinfo --network
```

---

### Post by Iowan on 2008-08-18
See if **lshw** gives needed info - another variation is **lshw -C Network**

---

### Post by yang on 2008-08-18
Here's the output I see:

```

$ hwinfo --network
30: None 00.0: 10701 Ethernet                                   
  [Created at net.125]
  Unique ID: usDW.ndpeucax6V1
  Parent ID: rBUF.bqObZEQ2LuD
  SysFS ID: /class/net/eth0
  SysFS Device Link: /devices/pci0000:00/0000:00:19.0
  Hardware Class: network interface
  Model: "Ethernet network interface"
  Driver: "e1000"
  Driver Modules: "e1000"
  Device File: eth0
  HW Address: 00:19:d1:9a:ec:c1
  Link detected: yes
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #16 (Ethernet controller)

31: None 00.0: 10700 Loopback
  [Created at net.125]
  Unique ID: ZsBS.GQNx7L4uPNA
  SysFS ID: /class/net/lo
  Hardware Class: network interface
  Model: "Loopback network interface"
  Device File: lo
  Link detected: yes
  Config Status: cfg=new, avail=yes, need=no, active=unknown

```

Does this tell me what kind of connection I'm on?

BTW, sorry if I was unclear in my original question - I know I have a GigE controller, but I am wondering what kind of immediate link the controller believes itself to be interfacing with.

---

### Post by yang on 2008-08-18
```

$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 82566DC Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 02
       serial: 00:19:d1:9a:ec:c1
       size: 1GB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.20-k2-NAPI duplex=full firmware=1.1-0 ip=18.138.5.240 latency=0 link=yes module=e1000 multicast=yes port=twisted pair speed=1GB/s

```

Same follow-up question as above....  Is the "speed=" field accurately describing the link?

---

### Post by mellowd on 2008-08-18
> **yang said:**
> 
Same follow-up question as above....  Is the "speed=" field accurately describing the link?

Yes, it's saying it's running at 1gbp/full duplex

---

