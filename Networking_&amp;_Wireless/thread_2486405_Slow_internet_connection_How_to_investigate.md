---
title: "Slow internet connection How to investigate?"
date: 2023-04-28
forum: Networking &amp; Wireless
---

### Post by marrocs on 2023-04-28
Hi. About 2 days ago the internet on my laptop (dell vostro 3550/Ubuntu 22.04) suddenly became pretty slow. Despite that, the internet is working fine when connect from smartphone (android).  So, how can i investigate the problem? Where to begin?  I tried the following step-by-step and coudn't figure it out>  [https://www.redhat.com/sysadmin/beginners-guide-network-troubleshooting-linux](https://www.redhat.com/sysadmin/beginners-guide-network-troubleshooting-linux)   I appreciate any help.

---

### Post by TheFu on 2023-04-29
Isolate where the issue lies first.
That means forget the internet for now. How fast is the connection between the computer and the router?
How fast is the connection between 2 computers on the same LAN?
Also, test with wired connectivity, don't bother with wifi.  
If you see the wired connection is working great, then it is time to troubleshoot wifi.  That is much harder, since there are lots of things that can slow wifi outside our control (think other devices and neighbors and building materials).
Use **iperf3** to do the testing.

Assuming everything on your LAN is fine, it would also help to know what bandwidth you pay the ISP to provide - up/down and what a speed test results.

for example, I pay for 30/6 Mbps, here's a current speedtest:
```
$ speedtest-cli 
...
Testing download speed................................................................................
Download: 29.53 Mbit/s
Testing upload speed................................................................................................
Upload: 6.16 Mbit/s
```

On my LAN, I see 920 Mbps between physical systems ```

[ ID] Interval           Transfer     Bitrate         Retr
[  5]   0.00-10.04  sec  0.00 Bytes  0.00 bits/sec                  sender
[  5]   0.00-10.04  sec  1.10 GBytes   **938 Mbits/sec**                  receiver
```
and 45 Gbps between virtual machines:
```
[ ID] Interval           Transfer     Bitrate         Retr
[  5]   0.00-10.00  sec  52.9 GBytes  45.5 Gbits/sec    0             sender
[  5]   0.00-10.04  sec  52.9 GBytes  **45.3 Gbits/sec**                  receiver
```

Seems everything is working well.

---

### Post by mIk3_08 on 2023-04-29
> **TheFu said:**
> Isolate where the issue lies first.
That means forget the internet for now. How fast is the connection between the computer and the router?
How fast is the connection between 2 computers on the same LAN?
Also, test with wired connectivity, don't bother with wifi.  
If you see the wired connection is working great, then it is time to troubleshoot wifi.  That is much harder, since there are lots of things that can slow wifi outside our control (think other devices and neighbors and building materials).
Use **iperf3** to do the testing.

Assuming everything on your LAN is fine, it would also help to know what bandwidth you pay the ISP to provide - up/down and what a speed test results.

for example, I pay for 30/6 Mbps, here's a current speedtest:
```
$ speedtest-cli 
...
Testing download speed................................................................................
Download: 29.53 Mbit/s
Testing upload speed................................................................................................
Upload: 6.16 Mbit/s
```

On my LAN, I see 920 Mbps between physical systems ```

[ ID] Interval           Transfer     Bitrate         Retr
[  5]   0.00-10.04  sec  0.00 Bytes  0.00 bits/sec                  sender
[  5]   0.00-10.04  sec  1.10 GBytes   **938 Mbits/sec**                  receiver
```
and 45 Gbps between virtual machines:
```
[ ID] Interval           Transfer     Bitrate         Retr
[  5]   0.00-10.00  sec  52.9 GBytes  45.5 Gbits/sec    0             sender
[  5]   0.00-10.04  sec  52.9 GBytes  **45.3 Gbits/sec**                  receiver
```

Seems everything is working well.
Thanks TheFu for the info. Regards and cheers!

---

