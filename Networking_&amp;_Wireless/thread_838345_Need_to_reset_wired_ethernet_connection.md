---
title: "Need to reset wired ethernet connection"
date: 2008-06-23
forum: Networking &amp; Wireless
---

### Post by Aaron44126 on 2008-06-23
Hello, I'm a new Ubuntu user and I have what I hope is a simple question.

My laptop has a Broadcom 100mbit wired ethernet connection, BCM4401.  From time to time, when I'm transmitting or receiving large amounts of data, it dies out.  (Everything appears to be fine but no data goes through, internet connection dies, etc.)

In Windows when this happened, I would disable and re-enable the device in the device manager and it would start working again.

I had hoped that this was a Windows driver issue and the problem wouldn't reappear on Ubuntu, but unfortunately it has.  So I'm going to have to blame it on the device itself.

So, what I want to know is how can I disable and re-enable the device, or otherwise kick it into working again, without actually rebooting my machine?  I can't find the option in "Network" under administration.  I tried ifdown eth0 but it tells me that "interface eth0 not configured".  If I hibernate the machine and turn it back on then the interface is working again.

Thanks for any response you might have,
 - Aaron

---

### Post by John.Michael.Kane on 2008-06-23
> **Aaron44126 said:**
> Hello, I'm a new Ubuntu user and I have what I hope is a simple question.

My laptop has a Broadcom 100mbit wired ethernet connection, BCM4401.  From time to time, when I'm transmitting or receiving large amounts of data, it dies out.  (Everything appears to be fine but no data goes through, internet connection dies, etc.)

In Windows when this happened, I would disable and re-enable the device in the device manager and it would start working again.

I had hoped that this was a Windows driver issue and the problem wouldn't reappear on Ubuntu, but unfortunately it has.  So I'm going to have to blame it on the device itself.

So, what I want to know is how can I disable and re-enable the device, or otherwise kick it into working again, without actually rebooting my machine?  I can't find the option in "Network" under administration.  I tried ifdown eth0 but it tells me that "interface eth0 not configured".  If I hibernate the machine and turn it back on then the interface is working again.

Thanks for any response you might have,
 - Aaron

To check the Ethernet connection on the box in question enter try the below command.

```
ifstatus eth0 
```

or

```
ip link show eth0
```

Next:

```
ifdown -a
```

Followed by:

```
ifup -a
```

---

### Post by Aaron44126 on 2008-06-23
ifdown doesn't seem to have any effect.  (I just ran ifdown -a and here I am still online... and yeah, I remembered to use sudo and I didn't run ifup right afterwards.)

If I run the more specific ifdown eth0, i get:

ifdown: interface eth0 not configured


Edit:  Potentially useful information?

ip link show eth0
```
6: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast qlen 1000
    link/ether 00:1d:09:c2:93:28 brd ff:ff:ff:ff:ff:ff
```

ifconfig eth0
```
eth0      Link encap:Ethernet  HWaddr 00:1d:09:c2:93:28  
          inet addr:129.62.115.141  Bcast:129.62.115.255  Mask:255.255.252.0
          inet6 addr: fe80::21d:9ff:fec2:9328/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:22169 errors:426 dropped:195 overruns:0 frame:35
          TX packets:6415 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6376979 (6.0 MB)  TX bytes:1118255 (1.0 MB)
          Interrupt:17
```

sudo lshw -C network
```
  *-network               
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:1d:09:c2:93:28
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=129.62.115.141 latency=64 link=yes module=ssb multicast=yes port=twisted pair speed=100MB/s
```

---

### Post by John.Michael.Kane on 2008-06-23
Since ifdown does not seem to work. You can try the below.

```
ifconfig eth0 down
```

```
ifconfig eth0 up
```

---

### Post by sisco311 on 2008-06-23
You can try:
```
sudo /etc/init.d/networking restart
```

---

