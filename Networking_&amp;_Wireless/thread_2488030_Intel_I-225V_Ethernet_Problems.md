---
title: "Intel I-225V Ethernet Problems"
date: 2023-06-21
forum: Networking &amp; Wireless
---

### Post by Shibblet on 2023-06-21
I have a Minisforum HX90G that has an Intel I-225V Ethernet Adapter.  I have a 2.5g Cable Modem connection. 

I have noticed that downloading in Kubuntu 23.04 is significantly slower than it should be.

I have done some searching, and it seems that the I-225V is problematic in Linux, but I can't seem to find any solution.

When I am downloading updates, or larger files, I get a top-speed of 18.0mbps
This is most noticeable in applications like Steam when I am downloading larger files.

My ISP Tells me to run their speed-test, and it looks just fine.  2.5g Download and 75m Upload is exactly what I am paying for.
 
[ATTACH=CONFIG]292409[/ATTACH]

Can anyone help?

---

### Post by TheFu on 2023-06-21
The remote system gets to decide how much bandwidth they will provide to clients.  I limit all clients to my websites to 1 Mbps transfers, so they don't hog bandwidth.
If your ISP says you are getting what you pay for, then the issue is upstream and outside your control.

Have you tested transfers inside your LAN?  Use iperf3 between 2 wired, Linux, systems to troubleshoot.  For example, 
```
$ iperf3 -c istar
Connecting to host istar, port 5201
[  5] local 172.22.22.6 port 43844 connected to 172.22.22.20 port 5201
[ ID] Interval           Transfer     Bitrate         Retr  Cwnd
[  5]   0.00-1.00   sec   114 MBytes   958 Mbits/sec    0    355 KBytes       
[  5]   1.00-2.00   sec   112 MBytes   937 Mbits/sec    0    355 KBytes       
[  5]   2.00-3.00   sec   113 MBytes   946 Mbits/sec    0    355 KBytes       
[  5]   3.00-4.00   sec   112 MBytes   939 Mbits/sec    0    355 KBytes       
[  5]   4.00-5.00   sec   112 MBytes   943 Mbits/sec    0    372 KBytes       
[  5]   5.00-6.00   sec   112 MBytes   938 Mbits/sec    0    372 KBytes       
[  5]   6.00-7.00   sec   112 MBytes   942 Mbits/sec    0    387 KBytes       
[  5]   7.00-8.00   sec   112 MBytes   944 Mbits/sec    0    424 KBytes       
[  5]   8.00-9.00   sec   112 MBytes   941 Mbits/sec    0    424 KBytes       
[  5]   9.00-10.00  sec   112 MBytes   941 Mbits/sec    0    424 KBytes       
- - - - - - - - - - - - - - - - - - - - - - - - -
[ ID] Interval           Transfer     Bitrate         Retr
[  5]   0.00-10.00  sec  1.10 GBytes   943 Mbits/sec    0             sender
[  5]   0.00-10.04  sec  1.10 GBytes   **938 Mbits/sec**                  receiver

iperf Done.
```
That test was between 2 Ubuntu servers with Intel I211 Gigabit Network connections. **938Mbps** is pretty good for a 1 Gbps network. There is a little overhead that reduces the total throughput, so I'll never, ever, see 1 Gbps until I put in 2.5Gbps or 10 Gbps switches, cables, NICs.  From the system to my OPNSense router running a BSD (with less good drivers), I see only 232 Mbits/sec.  That's actually less than my fibre internet connection supports (300/300), so I may need to do a little research on this.  Prior tests had the router getting over 600 Mbps, so something has changed with all the patches over the last few years.  Linux network drivers for my hardware are better and people are seeing nearly Gbps speeds with Linux, but not with BSD. Something about the drivers. Hummmm.

So, I wasn't testing the APU2 as intended.  Seems it is designed to spread the available bandwidth across multiple connections, 
```
[ ID] Interval           Transfer     Bitrate
[  5]   0.00-10.02  sec   300 MBytes   251 Mbits/sec                  receiver
[  8]   0.00-10.02  sec   159 MBytes   133 Mbits/sec                  receiver
[ 10]   0.00-10.02  sec   301 MBytes   252 Mbits/sec                  receiver
[ 12]   0.00-10.02  sec   154 MBytes   129 Mbits/sec                  receiver
[SUM]   0.00-10.02  sec   913 MBytes   **765 Mbits/sec**                  receiver
```
That's higher than I expected. Nice.  The testing was for 4 separate threads.  Total bandwidth is highlighted. That's on on the LAN. More than I could expect from a 2013 cheap, low power (12W), x86_64, system.

Between VMs running on the same system, I see much, much, higher speeds - over 25Gbps - but that doesn't use any network hardware or ethernet wires.

---

### Post by Shibblet on 2023-07-03
Perhaps I should restate my problem:

In Kubuntu 23.04, I download around 18Mbps.
In Windows, the download speed is around 125Mbps, and I've seen it jump up to 250Mbps before.

Why is it so much slower in Linux?

---

### Post by TheFu on 2023-07-04
> **Shibblet said:**
> Perhaps I should restate my problem:

In Kubuntu 23.04, I download around 18Mbps.
In Windows, the download speed is around 125Mbps, and I've seen it jump up to 250Mbps before.

Why is it so much slower in Linux?

What does iperf3 show?  Generic downloaders can have all sorts of reasons for being slower.  Get specific on the exact tool used. Also, the storage involved will likely matter too. Downloading to a USB2 flash drive will be much slower than downloading to a Gen4 NVMe SSD. If there is RAID involved, the RAID level will matter to write performance greatly too.

[https://blog.jdpfu.com/2010/10/27/file-copy-performance-for-large-files](https://blog.jdpfu.com/2010/10/27/file-copy-performance-for-large-files) Shows how much tuning some settings can matter.  
[https://blog.jdpfu.com/2011/10/17/hdd-performance-tuning-and-results](https://blog.jdpfu.com/2011/10/17/hdd-performance-tuning-and-results) Same here, across multiple different HDDs connected to different computers with USB2, USB3, straight SATA and RAID5 connected storage.

---

