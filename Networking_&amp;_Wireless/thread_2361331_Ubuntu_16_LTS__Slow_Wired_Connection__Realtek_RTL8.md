---
title: "Ubuntu 16 LTS | Slow Wired Connection | Realtek RTL8111/8168/8411"
date: 2017-05-15
forum: Networking &amp; Wireless
---

### Post by ciaruscuro on 2017-05-15
Hello World! 

I'm having some problem on my New Bought Desktop.  I've already installed ubuntu more than 5 times in different laptops and  computers(got some little experience but still an amatuer). But this  time I got a problem. 

It seems my Network driver :
01:00.0  Ethernet controller [0200]: Realtek Semiconductor Co., Ltd.  RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168]  (rev 0c)
is not functioning well. 

My wired connections is very Slow. My normal internet is around 4mbps - 6mbps. 
but in this ubuntu 16 desktop  it's only running in .20mbps - 1.40mbps. 

I've already tried countless forums. 
like : 
downloading the newest driver,
update and install,
disabling the Ipv6

please help me reach the maximum speed of my internet. 
I'm running wired connection to the router btw not via wifi.

here are some of the information that might help

--------------------------------------------------------------------------
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 0c)
        Subsystem: Biostar Microtech Int'l Corp RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
        Flags: bus master, fast devsel, latency 0, IRQ 35
        I/O ports at e000 [size=256]
        Memory at fea00000 (64-bit, non-prefetchable) [size=4K]
        Memory at e0800000 (64-bit, prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: r8168
        Kernel modules: r8168
--------------------------------------------------------------------------------------
kernel version :  4.8.0-36-generic
-------------------------------------------------------------------------------------
enp1s0    Link encap:Ethernet  HWaddr b8:97:**:**:**:**
          inet addr:192.168.254.106  Bcast:192.168.254.255  Mask:255.255.255.0
          inet6 addr: fe80::220e:b6ea:2a83:f1cd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:89959 errors:0 dropped:0 overruns:0 frame:0
          TX packets:88179 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:105640124 (105.6 MB)  TX bytes:9185237 (9.1 MB)
          Interrupt:35 Base address:0xc000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:4462 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4462 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1
          RX bytes:442847 (442.8 KB)  TX bytes:442847 (442.8 KB)
-----------------------------------------------------------------------------------------

Specs : 

  processor: 'AMD A10 7860k R7 Graphics 12 Cores 4.0 GHZ',
  motherboard: 'EmaxxA70 FM2+ Directx12',
  ram: '8GB DDR3 Kingston(x2)  ',
  hdisk: '500GB HDD SATA'

-----------------------------------------------------------------------------------------

Please Help, I've been stuck for about a week already.

---

### Post by howefield on 2017-05-15
Welcome to the forums, thread moved to the "*Networking & Wireless*" forum, probably a better fit.

---

### Post by FernandoRueda on 2017-05-15
I have the same problem as you but with a nic 10 times slower, a netgear 100mbits/s fa510 pcmcia card on a pentium 3 laptop. I too run at 1mbit/s. I tried manually adjusting the speed of the card on the /etc/interfaces/network I think it is the location and a guide with ethtool but nothing solves it. I tried setting manually the MTU to 1500bytes too. If I find an answer I'll post it here. My thread is also on this section of the forum.

---

### Post by ciaruscuro on 2017-05-15
well thanks for the reply. Please do post the answer here if you found it. 
kinda hard developing website with slow connection haha

---

