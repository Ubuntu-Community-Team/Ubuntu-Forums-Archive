---
title: "HP 300-019 wireless - BCM43142 - not working"
date: 2016-03-28
forum: Networking &amp; Wireless
---

### Post by stlu on 2016-03-28
I am trying this little machine out with Xubuntu 15.04 and there is no wireless availability.


```

$ sudo lshw -class net
  *-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 0c
       serial: 60:02:92:58:03:08
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168g-2_0.0.1 02/06/13 ip=192.168.2.47 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:45 ioport:e000(size=256) memory:f7b00000-f7b00fff memory:f0a00000-f0a03fff
  *-network
       description: Network controller
       product: BCM43142 802.11b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=bcma-pci-bridge latency=0
       resources: irq:16 memory:f7a00000-f7a07fff

```

As you can see, despite the wireless card showing in lshw, it does not come up as a device in ifconfig:

```

$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 60:02:92:58:03:08  
          inet addr:192.168.2.47  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::6202:92ff:fe58:308/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3098 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2645 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2290957 (2.2 MB)  TX bytes:348571 (348.5 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:2918 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2918 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:243440 (243.4 KB)  TX bytes:243440 (243.4 KB)

```

---

### Post by Hadaka on 2016-03-28
hi
Your wireless card's BCM43142 PCID is..[14e4:4365]

From a working wired connection,Please open a terminal ctrl/alt/t
Please Copy and paste the following commands one at a time

```
sudo apt-get update
sudo apt-get install bcmwl-kernel-source
sudo modprobe wl
```


if you are still having difficulties,please COPY and paste the below command to a terminal, it will build a file in your home directory called **wireless-info.txt **
```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && chmod +x wireless-info && ./wireless-info
```
Then
Please copy and post the **wireless-info.txt **file to this thread.

---

### Post by Bucky Ball on 2016-03-28
NOTE: 15.04 is no longer supported. Suggest you try with a supported release, 14.04 LTS with support until 2019, 15.10 until halfway through this year. 

You might even want to dabble with 16.04 LTS which is due out in three weeks, but at this point, wouldn't use it as your stable install. 

Good luck.

---

### Post by stlu on 2016-03-30
> **Hadaka said:**
> hi
Your wireless card's BCM43142 PCID is..[14e4:4365]

From a working wired connection,Please open a terminal ctrl/alt/t
Please Copy and paste the following commands one at a time

```
sudo apt-get update
sudo apt-get install bcmwl-kernel-source
sudo modprobe wl
```


if you are still having difficulties,please COPY and paste the below command to a terminal, it will build a file in your home directory called **wireless-info.txt **
```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && chmod +x wireless-info && ./wireless-info
```
Then
Please copy and post the **wireless-info.txt **file to this thread.

That did the trick, thank you!

---

### Post by Hadaka on 2016-03-30
Great ! glad that worked for you.
Buckyball is correct, 15.04 is no longer supported.
I recommend 14.04 its solid and supported for 3 more years.
Lastly thank you for marking your thread solved, it will help
others with a like problem.

---

