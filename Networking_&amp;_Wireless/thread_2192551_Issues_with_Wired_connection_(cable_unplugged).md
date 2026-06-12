---
title: "Issues with Wired connection (cable unplugged)"
date: 2013-12-08
forum: Networking &amp; Wireless
---

### Post by matthewhunt1984 on 2013-12-08
I'm new to linux and Ubuntu, I'm running a new 12.04 from a Live USB with persistence so I'm able to save settings etc. Laptop is Compaw Presario CQ61-401SA

I've only had this setup a few days and it is mostly working fine. I want to turn it into a media center, so flashed the BIOS so I could enable Wakeup on LAN (Wakeup on PME in BIOS).

However I've never used the wired connection, as the wirless works fine, but i know WoL only works over a wired connection. I also don't have a windows boot, so can't check the connection is windows.

Some hardware info:
```
**lspci -nnk **
02:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 1000 [8086:0084]
    Subsystem: Intel Corporation Centrino Wireless-N 1000 BGN [8086:1315]
    Kernel driver in use: iwlwifi
    Kernel modules: iwlwifi
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
    Subsystem: Hewlett-Packard Company Device [103c:3069]
    Kernel driver in use: r8101
    Kernel modules: r8101
```

At first I thought it might be the driver, as I hear linux can sometime be awkward with those. I downloaded driver from realtek, and installed following the readme that referred to autorun.sh. There were some manual steps such as configuring IPs or MAC addresses, but I wasn't clear if these were optional (so could be related).

However the r8101 driver seems to be getting picked up, and I can see it in the ubuntu "System Settings -> Additional drivers"

ifconfig output
```
ubuntu@ubuntu:/etc$ **ifconfig**
eth0      Link encap:Ethernet  HWaddr c8:0a:a9:58:7b:6d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:401 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2730 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:63150 (63.1 KB)  TX bytes:554736 (554.7 KB)
          Interrupt:43 Base address:0xe000 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:13076 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13076 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:972070 (972.0 KB)  TX bytes:972070 (972.0 KB)


wlan0     Link encap:Ethernet  HWaddr 00:26:c7:1f:0c:d0  
          inet addr:192.168.0.6  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::226:c7ff:fe1f:cd0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3942 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2235 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2340875 (2.3 MB)  TX bytes:518812 (518.8 KB)
```

**System Settings -> Network -> Wired **
Says that **"Cable unplugged.**
The connection has briefly appeared to connect and drop (and there are some packets listed on eth0)

Stating again, I am a beginner to linux, so could have easily made a mistake, or missed a step. Appreciate any support here to get a stable wired network connection

---

