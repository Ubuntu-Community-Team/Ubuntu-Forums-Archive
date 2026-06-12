---
title: "High-capacity packet capture machine"
date: 2019-06-07
forum: Networking &amp; Wireless
---

### Post by mmmzon on 2019-06-07
Hi, 

This is my thread here, trying to see whether there might be a simple solution to my problem. 

I am trying to build a packet capture machine capable of handling 1Gbps and faster data streams. The target is to hit 10 Gbps or more, should hardware allow it. Right now, I am using Cisco UCS M5 server blade, with 2 x Xeon Platinum CPUs, ~380 GB RAM, and 4 x 2TB SSD in RAID 0, making sure there is enough capacity in each and every hardware element to sink that much data without choking. RAID controller is 12 Gbps version again, to make sure there is no choke point. I installed Ubuntu 18.04.2 server version, with minimum packages to lower the system load. 

I am using Melanox MT26448 and Intel X520 NICs with latest supported drivers (both compiled and modprobed into the kernel). 

lspci -v | grep -i eth  
3b:00.0 Ethernet controller: Intel Corporation Ethernet Controller 10G X550T (rev 01)
        Subsystem: Cisco Systems Inc Ethernet Controller 10G X550T
3b:00.1 Ethernet controller: Intel Corporation Ethernet Controller 10G X550T (rev 01)
        Subsystem: Cisco Systems Inc Ethernet Controller 10G X550T
5e:00.0 Ethernet controller: Mellanox Technologies MT26448 [ConnectX EN 10GigE, PCIe 2.0 5GT/s] (rev b0)
d8:00.0 Ethernet controller: Intel Corporation 82599ES 10-Gigabit SFI/SFP+ Network Connection (rev 01)
        Subsystem: Intel Corporation Ethernet Server Adapter X520-2
d8:00.1 Ethernet controller: Intel Corporation 82599ES 10-Gigabit SFI/SFP+ Network Connection (rev 01)
        Subsystem: Intel Corporation Ethernet Server Adapter X520-2

I maxed out receive rings, queue depths, disabled pause in receive and transmit directions, etc. and as far as I can tell, NICs can receive packets at 1 Gbps rate with no dropped packets. However, running tshark and writing directly into the RAIDed SSDs I get ~0.5% packet loss, irrespective of the packet size distribution (fixed versus variable, what size packets are used, etc.). 

It seems like there are a lot of processes in kernel that get capped even at 1 Gbps rate (likely, related with packet analysis). I was hoping there might be a way to either disable all the unnecessary gunk within the kernel, stripping it down to bare minimum to run packet capture and minimize system overhead in the process. Has anybody done any kernel stripping for this purpose? Are there any distros available that might be better suited for this task than a general purpose Ubuntu server? 

Any pointers / thoughts would be really appreciated. 

Thanks in advance !!!!

---

### Post by The Cog on 2019-06-07
If you only want packet capture, maybe you could try tcpdump instead of tshark? I am guessing, but perhaps tshark is doing packet decoding that is not necessary if you only want packet capture. Actually, I thought tshark was for displaying decoded packet contents. tcpdump -w can write standard pcap files straight to disk, with auto file rotation.

---

### Post by mmmzon on 2019-06-07
Thank you for a quick answer. Here is a run example done right now - I am still showing 6202 packets dropped by kernel

tcpdump: listening on enp94s0, link-type EN10MB (Ethernet), capture size 262144 bytes
^C9920928 packets captured
9927132 packets received by filter
[B]6202 packets dropped by kernel

[/B]After disabling flow control and increasing rx ring to 4096, there is no improvement really. 

tcpdump: listening on enp94s0, link-type EN10MB (Ethernet), capture size 262144 bytes
^C9984908 packets captured
9997880 packets received by filter
**12972 packets dropped by kernel**


I will experiment some more with tcpdump to see if I can optimize is some, but there is still kernel caused packet loss.

---

### Post by mmmzon on 2019-06-07
Further experimentation ... 

- file rotation does not seem to improve anything (in fact, seems to get things worse, more packets are dropped by kernel for some reason)

tcpdump: listening on enp94s0, link-type EN10MB (Ethernet), capture size 262144 bytes
^C5372825 packets captured
9962085 packets received by filter
**4589260 packets dropped by kernel**

- increasing buffer size (10G) and limiting capture size (2000 bytes) does not seem to solve the problem, though now I do not see all packets hit the filter for some reason. There are 10 million packets generated, only 9972645 make to capture for some reason?

tcpdump: listening on enp94s0, link-type EN10MB (Ethernet), capture size 2000 bytes
^C9972645 packets captured
9972645 packets received by filter
**0 packets dropped by kernel**

- I checked CPU utilization (via top) and during the capture process even with 1 Gbps, it spikes to around 70-90%, not quite sure why, given that tcpdum is not supposed to decode packets, right?

```
[FONT=courier new]top - 17:27:43 up  1:23,  3 users,  load average: 0.97, 0.45, 0.24[/FONT]
[FONT=courier new]Tasks: 1001 total,   2 running, 565 sleeping,   0 stopped,   0 zombie[/FONT]
[FONT=courier new]%Cpu(s):  0.2 us,  0.5 sy,  0.0 ni, 97.9 id,  0.4 wa,  0.0 hi,  0.8 si,  0.0 st[/FONT]
[FONT=courier new]KiB Mem : 39487139+total, 37073328+free,  2821904 used, 21316192 buff/cache[/FONT]
[FONT=courier new]KiB Swap:  2097148 total,  2097148 free,        0 used. 38955801+avail Mem [/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND                                                                                                                                                [/FONT]
[FONT=courier new] 4545 root      20   0   30100  14028  13128 S  71.3  0.0   0:37.91 tcpdump                                                                                                                                                [/FONT]
[FONT=courier new] 1783 root      20   0       0      0      0 D   6.9  0.0   0:02.82 kworker/u194:3+                                                                                                                                        [/FONT]
[FONT=courier new]  157 root      20   0       0      0      0 S   4.3  0.0   0:44.81 ksoftirqd/24[/FONT]
```[FONT=courier new]    [/FONT]

Any other thoughts?

---

### Post by TheFu on 2019-06-07
That top output shows 98% idle.
Please post output using "code tags", so things look like they do in a terminal and columns line up.  AdvEdit (#).

Are the SSDs 32 Gbps NVMe connected versions?  You are correct to look at the pieces, but try to isolate your testing to 1 part of the problem at a time.  Did you already validate that the 10 Gbps NICs come within 90% of that mark?  Same for the SSDs - is the performance for each close to the expected values?

There are faster distros for enterprise use.  [https://www.phoronix.com/scan.php?page=article&item=linux-windows-15&num=8](https://www.phoronix.com/scan.php?page=article&item=linux-windows-15&num=8)

---

### Post by mmmzon on 2019-06-07
> **TheFu said:**
> That top output shows 98% idle.

given that there are 96 cores total, I assume tcpdump is not multithreaded and attaches itself to just one core?

> **TheFu said:**
> Please post output using "code tags", so things look like they do in a terminal and columns line up.  AdvEdit (#).

Done, thanks for the tip

> **TheFu said:**
> Are the SSDs 32 Gbps NVMe connected versions?  You are correct to look at the pieces, but try to isolate your testing to 1 part of the problem at a time.  Did you already validate that the 10 Gbps NICs come within 90% of that mark?  Same for the SSDs - is the performance for each close to the expected values? 

SSDs are SAS 12Gbps units, so given the RAID controller, that seems like a potential choke point in the system. SSDs were tested individually and were able to hit 1GB/s speeds. These are not, unfortunately, NVMe models. I did not want to invest too much money before confirming a setup is viable, i.e., I can hit a few Gbps, before going into a more advanced storage solution. NICs were validates as well (provided I can trust NIC statistics) and exhibit zero drops, i.e., all packets show received, no drops, errors, etc. show up when using "ethtool -S" option. Not sure how else to validate them :)

---

### Post by The Cog on 2019-06-08
If tcpdump can't help you then the only other capture solution I know of is fastcapa but I don't know if that will be good enough for you either. It is designed to forward captured packets to kafka which is a message queueing system that can be read by distributed processing systems.  
[https://metron.apache.org/current-book/metron-sensors/fastcapa/index.html](https://metron.apache.org/current-book/metron-sensors/fastcapa/index.html)
[https://logisland.readthedocs.io/en/latest/tutorials/indexing-network-packets.html](https://logisland.readthedocs.io/en/latest/tutorials/indexing-network-packets.html)
but these look like a rather different solution than yours so I don't know if they would be of any interest to you.

---

### Post by TheFu on 2019-06-08
My only other suggestion would be to ask a question about 10Gbps packet captures on a defcon security list. Those guys live on capturing data and many enterprises capture all ingress/egress data for analysis daily.

---

### Post by mmmzon on 2019-06-08
> **TheFu said:**
> My only other suggestion would be to ask a question about 10Gbps packet captures on a defcon security list. Those guys live on capturing data and many enterprises capture all ingress/egress data for analysis daily.

Will do, thanks! I did notice a lot of enterprises use dedicated (ASIC-based) capture systems, where (seemingly) data from NIC is written directly into storage or streamed out. I was hoping one could strip down kernel or customize it to achieve similar functionality, given that the underlying hardware I use should be more then capable of handling such a data flow. 

Anyway, thank you for all the pointers. I do really appreciate them !

---

### Post by TheFu on 2019-06-08
I found some of information from 2008 about this issue.  

What they did back then was pin the different threads/processes to different CPUs.  One guy tied his multi-threaded disk buffering code directly to the network drivers. Some people used libpcap directly for their captures - again, multi-threaded. There were some kernel patches, but it is unclear if those ever got into the core release.

---

### Post by mmmzon on 2019-06-08
> **TheFu said:**
> I found some of information from 2008 about this issue.  

What they did back then was pin the different threads/processes to different CPUs.  One guy tied his multi-threaded disk buffering code directly to the network drivers. Some people used libpcap directly for their captures - again, multi-threaded. There were some kernel patches, but it is unclear if those ever got into the core release.

I have been trying a similar approach but I think the multi-socket NUMA architecture with Xeon CPUs messes things up. It also seems that new cores have some automated irq balancer running the background that cannot be shut down gracefully - every time I tried to do that, I had kernel panic prop up quickly. I will use a similar approach with a since core mule system to see whether in a non-NUMA architecture this approach can work better. Right now I cannot use much older kernels on M5 platform because of drivers so I feel like I am between a hammer and a wall now :) 

If you happen to run across any newer materials on this topic, let me know. The one I was looking at is here: [https://kukuruku.co/post/capturing-packets-in-linux-at-a-speed-of-millions-of-packets-per-second-without-using-third-party-libraries/](https://kukuruku.co/post/capturing-packets-in-linux-at-a-speed-of-millions-of-packets-per-second-without-using-third-party-libraries/)

---

### Post by mmmzon on 2019-06-11
I did a number of kernel changes (disabled a lot of statistics, watchdogs, etc. within the kernel) and got some performance improvement. I am hitting ~8Mfps @ 64B right now, which corresponds more ot less to close to 5.5 Gbps. 

[ATTACH=CONFIG]283410[/ATTACH]

At any rate, I am likely hitting a limit due to the ksoftirqd thread on core 25. The only way I can see I could squeeze more out of the system would be to somehow spread the load on different cores. I am not sure why a single core would be hammered like this. Any thoughts?

[ATTACH=CONFIG]283411[/ATTACH][ATTACH=CONFIG]283412[/ATTACH]

I did execute the irq load balancing script included in the latest ixgbe driver package (5.5.5) but that did not seem to have changed anything on the CPU load. With the RX/TX threads from the NIC spread across different cores (64 threads on X520 in total, one thread per core), it is not clear to me why I would still have a single thread that loads so heavily on the CPU. Reading about ksoftirqd seems like it is supposed to be there but it is not clear to me why it would be loading a single core if it is somehow related with processing IRQs from NIC (these should be spread across different cores).

---

