---
title: "Limit speed 500 mbit/sec"
date: 2022-08-17
forum: Networking &amp; Wireless
---

### Post by maxels23 on 2022-08-17
Hello! I noticed that the speed on the server became less, it was 1 Gb / s, it became 500 Mb / s, I don’t even know why. I have already reinstalled nginx, php, nothing helped. The suspicion is already that the Linux kernel has been updated and such a restriction has gone. How to fix?


Linux 5.15.0-46-generic #49~20.04.1-Ubuntu

---

### Post by TheFu on 2022-08-17
How do you know this is the limit for the entire system and not just 1 webapp?  Please show proof.  iperf3 is the normal way to test.
Here's between two different physical systems:
```
$ iperf3 -c hadar
Connecting to host hadar, port 5201
[  4] local 172.22.22.20 port 53468 connected to 172.22.22.6 port 5201
[ ID] Interval           Transfer     Bandwidth       Retr  Cwnd
[  4]   0.00-1.00   sec   114 MBytes   959 Mbits/sec    0    379 KBytes       
[  4]   1.00-2.00   sec   112 MBytes   942 Mbits/sec    0    379 KBytes       
[  4]   2.00-3.00   sec   112 MBytes   **941 Mbits/sec**    0    379 KBytes     
```
that happens to be running  ...
```
$ uname -r
5.16.20-051620-generic
```
Both physical systems have these NICs:
```
$ inxi -N
Network:   Card-1: Intel I211 Gigabit Network Connection driver: igb
           Card-2: Intel 82575GB Gigabit Network Connection driver: igb
```
NICs.  The i211 is being used for this test.

I don't have the exact same kernel your system does on any systems here. Sorry.

So, the first step is to determine which part of the entire stack is causing slowdowns.  Do you have proper systems monitoring like munin or something similar would provide? If you do, you can probably trace back to the exact date when the problem happened, look through any local and external changes (router or switch) upgrades to nail down the system, subsystem, process, driver, HW, involved.

---

### Post by Doug S on 2022-08-18
+1 to the input and suggestions from TheFu.

I'll only add the same test, but with two kernels, the one the OP is using and 6.0-rc1:

First test:

```

doug@s19:~$ uname -a
Linux s19 6.0.0-rc1-stock #1084 SMP PREEMPT_DYNAMIC Wed Aug 17 07:37:58 PDT 2022 x86_64 x86_64 x86_64 GNU/Linux
doug@s19:~$ iperf3 -c s15
Connecting to host s15, port 5201
[  5] local 192.168.111.136 port 54556 connected to 192.168.111.1 port 5201
[ ID] Interval           Transfer     Bitrate         Retr  Cwnd
[  5]   0.00-1.00   sec  12.6 MBytes   106 Mbits/sec    0    273 KBytes
[  5]   1.00-2.00   sec  11.2 MBytes  93.8 Mbits/sec    0    273 KBytes
[  5]   2.00-3.00   sec  11.2 MBytes  93.8 Mbits/sec    0    273 KBytes

```Hey what??? ... debug ... Oh bad port on a network switch.

Second test:
```

Linux s19 6.0.0-rc1-stock #1084 SMP PREEMPT_DYNAMIC Wed Aug 17 07:37:58 PDT 2022 x86_64 x86_64 x86_64 GNU/Linux
doug@s19:~$ iperf3 -c s15
Connecting to host s15, port 5201
[  5] local 192.168.111.136 port 33032 connected to 192.168.111.1 port 5201
[ ID] Interval           Transfer     Bitrate         Retr  Cwnd
[  5]   0.00-1.00   sec   114 MBytes   959 Mbits/sec    0    416 KBytes
[  5]   1.00-2.00   sec   112 MBytes   940 Mbits/sec    0    416 KBytes
[  5]   2.00-3.00   sec   112 MBytes   939 Mbits/sec    0    416 KBytes

```That's better.

Third test, using same kernel as OP:

```

doug@s19:~$ uname -a
Linux s19 5.15.0-46-generic #49~20.04.1-Ubuntu SMP Thu Aug 4 19:15:44 UTC 2022 x86_64 x86_64 x86_64 GNU/Linux
doug@s19:~$ iperf3 -c s15
Connecting to host s15, port 5201
[  5] local 192.168.111.136 port 34022 connected to 192.168.111.1 port 5201
[ ID] Interval           Transfer     Bitrate         Retr  Cwnd
[  5]   0.00-1.00   sec   114 MBytes   953 Mbits/sec    0    352 KBytes
[  5]   1.00-2.00   sec   113 MBytes   946 Mbits/sec    0    352 KBytes
[  5]   2.00-3.00   sec   112 MBytes   938 Mbits/sec    0    352 KBytes

```

---

### Post by maxels23 on 2022-08-18
> **TheFu said:**
> How do you know this is the limit for the entire system and not just 1 webapp?  Please show proof.  iperf3 is the normal way to test.
Here's between two different physical systems:
```
$ iperf3 -c hadar
Connecting to host hadar, port 5201
[  4] local 172.22.22.20 port 53468 connected to 172.22.22.6 port 5201
[ ID] Interval           Transfer     Bandwidth       Retr  Cwnd
[  4]   0.00-1.00   sec   114 MBytes   959 Mbits/sec    0    379 KBytes       
[  4]   1.00-2.00   sec   112 MBytes   942 Mbits/sec    0    379 KBytes       
[  4]   2.00-3.00   sec   112 MBytes   **941 Mbits/sec**    0    379 KBytes     
```
that happens to be running  ...
```
$ uname -r
5.16.20-051620-generic
```
Both physical systems have these NICs:
```
$ inxi -N
Network:   Card-1: Intel I211 Gigabit Network Connection driver: igb
           Card-2: Intel 82575GB Gigabit Network Connection driver: igb
```
NICs.  The i211 is being used for this test.

I don't have the exact same kernel your system does on any systems here. Sorry.

So, the first step is to determine which part of the entire stack is causing slowdowns.  Do you have proper systems monitoring like munin or something similar would provide? If you do, you can probably trace back to the exact date when the problem happened, look through any local and external changes (router or switch) upgrades to nail down the system, subsystem, process, driver, HW, involved.
In iperf3 everything is fine. The problem is only with the webserver. Why the speed has become lower, I do not know. But on a local network between computers, if you throw off files, then the speed is normal.

```
Accepted connection from 192.168.1.149, port 62450
[  5] local 192.168.1.224 port 5201 connected to 192.168.1.149 port 62451
[ ID] Interval           Transfer     Bitrate
[  5]   0.00-1.00   sec   108 MBytes   903 Mbits/sec
[  5]   1.00-2.00   sec   113 MBytes   949 Mbits/sec
[  5]   2.00-3.00   sec   113 MBytes   949 Mbits/sec
[  5]   3.00-4.00   sec   113 MBytes   947 Mbits/sec
[  5]   4.00-5.00   sec   113 MBytes   949 Mbits/sec
[  5]   5.00-6.00   sec   113 MBytes   949 Mbits/sec
[  5]   6.00-7.00   sec   113 MBytes   949 Mbits/sec
[  5]   7.00-8.00   sec   113 MBytes   947 Mbits/sec
[  5]   8.00-9.00   sec   113 MBytes   949 Mbits/sec
[  5]   9.00-10.00  sec   113 MBytes   949 Mbits/sec
[  5]  10.00-10.05  sec  5.76 MBytes   948 Mbits/sec
- - - - - - - - - - - - - - - - - - - - - - - - -
[ ID] Interval           Transfer     Bitrate
[  5]   0.00-10.05  sec  1.10 GBytes   944 Mbits/sec                  receiver

```It's only a problem with the webserver. Nginx 1.22 and php 7.4.30
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=290881&stc=1[/IMG][COLOR=#FFFFFF][FONT=Helvetica]7.4.30[/FONT][/COLOR]

---

### Post by TheFu on 2022-08-18
a) please don't post huge images.  Some of use pay for internet by the "byte".
b) Setup a static website under nginx and see what the performance is.

I'm seeing 44.5MB/s  pulling a ~ 100MB file through nginx here.  That's only 346 Mbps.  he nginx access goes through my WAN router, because I use name-based SNI to get to the correct website. If I go directly ... gotta figure out how to do that ... got it.
I'm seeing 174MB/s (1392 Mbps) directly.  So, it is the WAN router limits causing my slowdown.  Could that be the same for you?  If only the kernel is different and you see the same slowdown, I'd check the path that the packets are going on each system.  Verify traceroute goes how you think under both kernels.

Because I'm curious, using scp, I'm seeing 189.5MB/s (1705 Mbps).  This is between a virtual machine running nginx and the hostOS.  Between 2 different VMs, the scp is 200 MB/s (1600 Mbps), which is a little unexpected.

Don't know if this helps. Just some other alternative explanations, since SNI might be used 1 way, but not the other?  My iperf3 never uses SNI, for example.

---

