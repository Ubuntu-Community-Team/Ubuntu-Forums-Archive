---
title: "NETDEV WATCHDOG: eth0: transmit timed out"
date: 2006-09-10
forum: Networking &amp; Wireless
---

### Post by sc10n on 2006-09-10
Ok. I have seen tons of posts on this problem and i have yet to find a single viable solution. Basically my problem came up after I stood up a new ubuntu 6.06 Server. (AMD Athlon XP 2900+, 1Gb RAM, 500Gb Raid5, Intel GigE NIC). I started transfering large files over the network to populate the file share. During the transfer I noticed that files were "timing out" so upon further inspection of the /var/log/messages I found the following. 

```
Sep 10 02:26:53 localhost kernel: [17184265.092000] NETDEV WATCHDOG: eth0: transmit timed out
Sep 10 02:26:56 localhost kernel: [17184268.172000] e1000: eth0: e1000_watchdog_task: NIC Link is Up 1000 Mbps Full Duplex
Sep 10 02:27:04 localhost kernel: [17184276.176000]   Tx Queue             <0>
Sep 10 02:27:04 localhost kernel: [17184276.176000]   TDH                  <3a>
Sep 10 02:27:04 localhost kernel: [17184276.176000]   TDT                  <3a>
Sep 10 02:27:04 localhost kernel: [17184276.176000]   next_to_use          <3a>
Sep 10 02:27:04 localhost kernel: [17184276.176000]   next_to_clean        <4e>
Sep 10 02:27:04 localhost kernel: [17184276.176000] buffer_info[next_to_clean]
Sep 10 02:27:04 localhost kernel: [17184276.176000]   time_stamp           <10ce4b>
Sep 10 02:27:04 localhost kernel: [17184276.176000]   next_to_watch        <4e>
Sep 10 02:27:04 localhost kernel: [17184276.176000]   jiffies              <10cfb4>
Sep 10 02:27:04 localhost kernel: [17184276.176000]   next_to_watch.status <0>
Sep 10 02:27:06 localhost kernel: [17184278.180000]   Tx Queue             <0>
Sep 10 02:27:06 localhost kernel: [17184278.180000]   TDH                  <3a>
Sep 10 02:27:06 localhost kernel: [17184278.180000]   TDT                  <3a>
Sep 10 02:27:06 localhost kernel: [17184278.180000]   next_to_use          <3a>
Sep 10 02:27:06 localhost kernel: [17184278.180000]   next_to_clean        <4e>
Sep 10 02:27:06 localhost kernel: [17184278.180000] buffer_info[next_to_clean]
Sep 10 02:27:06 localhost kernel: [17184278.180000]   time_stamp           <10ce4b>
Sep 10 02:27:06 localhost kernel: [17184278.180000]   next_to_watch        <4e>
Sep 10 02:27:06 localhost kernel: [17184278.180000]   jiffies              <10d1a9>
Sep 10 02:27:06 localhost kernel: [17184278.180000]   next_to_watch.status <0>
Sep 10 02:27:08 localhost kernel: [17184280.180000]   Tx Queue             <0>
Sep 10 02:27:08 localhost kernel: [17184280.180000]   TDH                  <3a>
Sep 10 02:27:08 localhost kernel: [17184280.180000]   TDT                  <3a>
Sep 10 02:27:08 localhost kernel: [17184280.180000]   next_to_use          <3a>
Sep 10 02:27:08 localhost kernel: [17184280.180000]   next_to_clean        <4e>
Sep 10 02:27:08 localhost kernel: [17184280.180000] buffer_info[next_to_clean]
Sep 10 02:27:08 localhost kernel: [17184280.180000]   time_stamp           <10ce4b>
Sep 10 02:27:08 localhost kernel: [17184280.180000]   next_to_watch        <4e>
Sep 10 02:27:08 localhost kernel: [17184280.180000]   jiffies              <10d39d>
Sep 10 02:27:08 localhost kernel: [17184280.180000]   next_to_watch.status <0>
Sep 10 02:27:10 localhost kernel: [17184282.184000]   Tx Queue             <0>
Sep 10 02:27:10 localhost kernel: [17184282.184000]   TDH                  <3a>
Sep 10 02:27:10 localhost kernel: [17184282.184000]   TDT                  <3a>
Sep 10 02:27:10 localhost kernel: [17184282.184000]   next_to_use          <3a>
Sep 10 02:27:10 localhost kernel: [17184282.184000]   next_to_clean        <4e>
Sep 10 02:27:10 localhost kernel: [17184282.184000] buffer_info[next_to_clean]
Sep 10 02:27:10 localhost kernel: [17184282.184000]   time_stamp           <10ce4b>
Sep 10 02:27:10 localhost kernel: [17184282.184000]   next_to_watch        <4e>
Sep 10 02:27:10 localhost kernel: [17184282.184000]   jiffies              <10d592>
Sep 10 02:27:10 localhost kernel: [17184282.184000]   next_to_watch.status <0>

```

I have seen several solutions that entail turning off ipv6, rolling back from 2.6.15-26-k7 to 2.6-25-k7, turning tos off with ethtool, Nothing has worked. Here is the output of lspci -v for my NIC. Also the board is an ABIT K-7 with a VIA chipset.

```
0000:00:0a.0 Ethernet controller: Intel Corporation 82541PI Gigabit Ethernet Controller (rev 05)
        Subsystem: Intel Corporation: Unknown device 1376
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 193
        Memory at ea000000 (32-bit, non-prefetchable) [size=128K]
        Memory at ea020000 (32-bit, non-prefetchable) [size=128K]
        I/O ports at e000 [size=64]
        Expansion ROM at 40000000 [disabled] [size=128K]
        Capabilities: [dc] Power Management version 2
        Capabilities: [e4] PCI-X non-bridge device.
```

This is a **very** annoying problem and I am very disappointed at how widespread this problem seems to be yet no one has a viable solution. So if by chance someone has had the same problem and has a solution I would appriciate it. Thanks

Sc10n..

---

### Post by 0be1 on 2006-09-10
sc10n;

I too was very disappointed, but please see the following post I just did and see if it fixed your problems. It did mine (thank goodness).

Regards...

0be1

[http://www.ubuntuforums.org/showthread.php?t=254625](http://www.ubuntuforums.org/showthread.php?t=254625)

---

### Post by sc10n on 2006-09-10
> **0be1 said:**
> sc10n;

I too was very disappointed, but please see the following post I just did and see if it fixed your problems. It did mine (thank goodness).

Regards...

0be1

[http://www.ubuntuforums.org/showthread.php?t=254625](http://www.ubuntuforums.org/showthread.php?t=254625)
I'm not sure why this worked. But it seems to have worked. My hats off to you Obe1!

Sc10n!

---

### Post by sc10n on 2006-09-11
Well several days later the same problem returns. I guess I will have to wait for some money to go buy another GigE card. Does anyone have a suggestion? I thought an Intel card would be a good choice. Guess I was wrong. Thanks.

Sc10n!

---

### Post by m1215 on 2006-10-21
i have the same problem with 6.06. if i enable pnpos in the bios the nic card works fine and i can get on the internet. i am still looking for a fix because i dont want pnpos enabled. anyone have an idea on how to correct this.

---

