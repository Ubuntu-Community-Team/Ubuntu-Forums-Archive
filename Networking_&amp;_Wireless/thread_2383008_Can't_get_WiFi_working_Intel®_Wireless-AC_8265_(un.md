---
title: "Can't get WiFi working Intel® Wireless-AC 8265 (unclaimed)"
date: 2018-01-19
forum: Networking &amp; Wireless
---

### Post by jiaman on 2018-01-19
It says unclaimed?

Network card: Intel® Wireless-AC 8265
Ubuntu 16.04.3 server

According to /lib/firmware, iwlwifi-8265-21.ucode  iwlwifi-8265-22.ucode  iwlwifi-8265-27.ucode  iwlwifi-8265-31.ucode are all present.

uname -r
4.4.0-109-generic

No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.3 LTS
Release:    16.04
Codename:    xenial

ifconfig
```

eno1      Link encap:Ethernet  HWaddr 94:c6:91:11:52:f5  
          inet addr:192.168.1.119  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: 2a00:23c4:2137:fe00:96c6:91ff:fe11:52f5/64 Scope:Global
          inet6 addr: fe80::96c6:91ff:fe11:52f5/64 Scope:Link
          inet6 addr: fdaa:bbcc:ddee:0:96c6:91ff:fe11:52f5/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1345 errors:0 dropped:0 overruns:0 frame:0
          TX packets:953 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:665392 (665.3 KB)  TX bytes:140076 (140.0 KB)
          Interrupt:16 Memory:dc300000-dc320000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:176 errors:0 dropped:0 overruns:0 frame:0
          TX packets:176 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:13296 (13.2 KB)  TX bytes:13296 (13.2 KB)
```

sudo lshw -class network
 ```
 *-network UNCLAIMED     
       description: Network controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:3a:00.0
       version: 78
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: memory:dc200000-dc201fff
  *-network
       description: Ethernet interface
       product: Ethernet Connection (4) I219-V
       vendor: Intel Corporation
       physical id: 1f.6
       bus info: pci@0000:00:1f.6
       logical name: eno1
       version: 21
       serial: 94:c6:91:11:52:f5
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=3.2.6-k duplex=full firmware=0.1-4 ip=192.168.1.119 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:126 memory:dc300000-dc31ffff
```

Why is it unconfirmed

---

### Post by chili555 on 2018-01-19
Please run:```
lspci -nn | grep 0280
```The pci.id for your device will be 8086:xxxx or some such. Next, check to see if the version of the driver included in your 4.4.0-xx kernel includes your device:```
modinfo iwlwifi | grep xxxx
```Of course, substitute your actual device ID for xxxx.

We suspect your 4.4.0-xx kernel is a bit old and doesn't cover your 8265 device that is a bit new.

Once we have some details from you, we can suggest a solution.

We suspect it is the famous 24fd.

---

### Post by jiaman on 2018-01-20
Lmao, it is 24fd and the latter modinfo grepped returns nothing. I was looking at [https://ubuntuforums.org/showthread.php?t=2353737](https://ubuntuforums.org/showthread.php?t=2353737) and couldn't find a viable solution.

That said, I just updated it to a 4.8 kernel and have it all working now. My bootloader kept booting into 4.4...

Thanks for your help and answer in the other page

---

### Post by Hadaka on 2018-01-20
Hi, please mark your thread Solved by logging into your thread..,first post
and click Thread Tools [on the right...above join date] then click Solved.
Thank You

---

