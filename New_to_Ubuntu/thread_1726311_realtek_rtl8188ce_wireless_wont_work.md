---
title: "realtek rtl8188ce wireless wont work"
date: 2011-04-11
forum: New to Ubuntu
---

### Post by rodger101us on 2011-04-11
i have a satellite l6750-57106 laptop i just installed ubuntu 10.4 2.6.32-30-generic x86_64 with a realtek rtl8188ce wireless that i cannot get to work i have tried every thing from the win 7 driver install to manual install and it still does not show up any help would be great 

p.s. i am some what new and key by key directions would be helpfull



02:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8176 (rev 01)
        Subsystem: Realtek Semiconductor Co., Ltd. Device 8184
        Flags: bus master, fast devsel, latency 0, IRQ 11
        I/O ports at d000 [size=256]
        Memory at ff600000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel modules: r8192ce_pci

03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
        Subsystem: Toshiba America Info Systems Device fd00
        Flags: bus master, fast devsel, latency 0, IRQ 27
        I/O ports at c000 [size=256]
        Memory at d0104000 (64-bit, prefetchable) [size=4K]
        Memory at d0100000 (64-bit, prefetchable) [size=16K]
        Capabilities: <access denied>

rodger101us@rodger101us:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

rodger101us@rodger101us:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 1c:75:08:7d:d5:de  
          inet addr:192.168.1.7  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::1e75:8ff:fe7d:d5de/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:50945 errors:0 dropped:0 overruns:0 frame:0
          TX packets:29919 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:70348095 (70.3 MB)  TX bytes:3010062 (3.0 MB)
          Interrupt:27 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

---

### Post by wolfen69 on 2011-04-11
Make sure you have a wired net connection and go to system>administration>hardware drivers and see if a driver is offered.

---

### Post by rodger101us on 2011-04-11
no there isnt

---

