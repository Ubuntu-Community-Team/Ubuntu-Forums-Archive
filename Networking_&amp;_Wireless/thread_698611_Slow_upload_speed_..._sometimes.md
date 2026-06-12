---
title: "Slow upload speed ... sometimes"
date: 2008-02-16
forum: Networking &amp; Wireless
---

### Post by costre on 2008-02-16
I am running **Gutsy 7.10** on an **athlon 64 3200 2core**. It's a pretty much brand new system, out of the box two weeks ago. 

About my **integrated** network adapter:

01:00.0 Ethernet controller: **Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet **controller (rev 01)
        Subsystem: ASRock Incorporation Unknown device 8168
        Flags: bus master, fast devsel, latency 0, IRQ 19
        I/O ports at b800 [size=256]
        Memory at f96ff000 (64-bit, non-prefetchable) [size=4K]
        Expansion ROM at f96c0000 [disabled] [size=128K]
        Capabilities: [40] Power Management version 2
        Capabilities: [48] Vital Product Data
        Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable-
        Capabilities: [60] Express Endpoint IRQ 0
        Capabilities: [84] Vendor Specific Information


I'm using **LinuxDC++** for p2p-networking. 
I am using a 10Mbit connection, connected to hubs where only 10Mbit is allowed, from lots of different ISP's though.

I get good speeds when I download, most of the time. There are bound to be bottlenecks between some peers of course. 

My **upload speed** through DC++ is **horrible**. I get between 20-30 kbyte/sec, allthough it looks as if it starts out at perhaps 300-400 kbyte/sec, and then drops rapidly. 

I get **good upload** speed when people are using my FTP-server. 

Are there settings in Ubuntu that can solve this? 
Should I install the 64-bit DC++? 
Could it be a port problem? 
Could it be my ethernet adapter? (It worked good in XP, though.)

I have searched for a solution, and ethernet speed seems to be a big issue with Ubuntu. Hopefully there will be a solution :)

---

### Post by costre on 2008-04-01
I changed ISP, and the problem is gone. All is well :)

---

