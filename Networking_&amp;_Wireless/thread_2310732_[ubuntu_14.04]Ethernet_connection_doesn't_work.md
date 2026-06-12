---
title: "[ubuntu 14.04]Ethernet connection doesn't work"
date: 2016-01-21
forum: Networking &amp; Wireless
---

### Post by manolis2 on 2016-01-21
Hi to all of you!
My ethernet connection doesn't work.Reading some of the answers that you have already provided I haven't found any solution.The wireless for the time works fine with or without the ethernet cable connected.

The output of
```
     Code:

     sudo lshw -C network 

```


```

  *-network               
       description: Wireless interface
       product: RTL8723BE PCIe Wireless Network Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: wlan0
       version: 00
       serial: ac:d1:b8:0b:b7:5b
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8723be driverversion=3.19.0-25-generic firmware=N/A ip=192.168.1.3 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:19 ioport:4000(size=256) memory:d0500000-d0503fff

```

Thank you in advance for your help.

---

### Post by manolis2 on 2016-01-21
and the output from 
ifconfig -a 

```

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:4818 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4818 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:678112 (678.1 KB)  TX bytes:678112 (678.1 KB)

wlan0     Link encap:Ethernet  HWaddr ac:d1:b8:0b:b7:5b  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::aed1:b8ff:fe0b:b75b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:40625 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30193 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:46205873 (46.2 MB)  TX bytes:4689381 (4.6 MB)


```

---

### Post by Vladlenin5000 on 2016-01-21
It's no surprise it doesn't work. It's a no show in any of your posted outputs. Are you sure it isn't defective?

---

### Post by manolis2 on 2016-01-22
Before the format the ehternet was working properly.So I don't think is defective of something like that.Is there any possibility of being blocked ?

---

### Post by praseodym on 2016-01-22
Lets check
```

lspci -nnk
```

---

