---
title: "Gigabit Lan running at 100 Mbit"
date: 2014-03-29
forum: Networking &amp; Wireless
---

### Post by Jon_Schulberger on 2014-03-29
I have a server running Ubuntu Server 12.04 LTS and I cannot seem to get the gigabit lan functioning correctly. Basically the NIC is recognized as being gigabit however my actual transfer speeds seem to stay between 10 and 13 MB/s when transferring over sftp. I've attempted to transfer files from Ubuntu to Windows and my speeds are like I said. On the exact same network, I can transfer at full gigabit speeds (~125 MB/s) from Windows to Windows using a separate computer. As far as I can tell, both the network and the cables I am using are completely fine. 

I'm not sure what else to look at here considering I've gone through as many forum posts as I can find relating to my issue.

Below is as much info as I can think of. Please let me know if there's anything else I can provide.

[System Info]
> OS: Ubuntu Server 12.04 LTS
Kernel: 3.8.0-37-generic
NIC: Broadcom Corporation NetXtreme BCM5705_2

[ifconfig output]
> eth0 

      Link encap:Ethernet  HWaddr 00:16:36:16:bb:fa
              inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
              inet6 addr: fe80::216:36ff:fe16:bbfa/64 Scope:Link
              UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
              RX packets:1133936 errors:0 dropped:0 overruns:0 frame:0
              TX packets:2106910 errors:0 dropped:0 overruns:0 carrier:0
              collisions:0 txqueuelen:1000
              RX bytes:167111644 (167.1 MB)  TX bytes:2949869304 (2.9 GB)
              Interrupt:17

lo

   Link encap:Local Loopback
              inet addr:127.0.0.1  Mask:255.0.0.0
              inet6 addr: ::1/128 Scope:Host
              UP LOOPBACK RUNNING  MTU:65536  Metric:1
              RX packets:8171 errors:0 dropped:0 overruns:0 frame:0
               TX packets:8171 errors:0 dropped:0 overruns:0 carrier:0
              collisions:0 txqueuelen:0
              RX bytes:1817409 (1.8 MB)  TX bytes:1817409 (1.8 MB)

[ethtool eth0 output]
> Supported ports: [ TP ]
Supported link modes:   
10baseT/Half 10baseT/Full
                                                              100baseT/Half 100baseT/Full
1000baseT/Half 1000baseT/Full

Supported pause frame use: No
Supports auto-negotiation: Yes
Advertised link modes: 
 10baseT/Half 10baseT/Full
                                                               100baseT/Half 100baseT/Full
                                                               1000baseT/Half 1000baseT/Full

Advertised pause frame use: Symmetric
Advertised auto-negotiation: Yes
Link partner advertised link modes: 
 10baseT/Half 10baseT/Full
                                               100baseT/Half 100baseT/Full
                                                                                            1000baseT/Full

Link partner advertised pause frame use: Symmetric
Link partner advertised auto-negotiation: Yes
Speed: 1000Mb/s
Duplex: Full
Port: Twisted Pair
PHYAD: 1
Transceiver: internal
Auto-negotiation: on
MDI-X: off
Supports Wake-on: g
Wake-on: g
Current message level: 0x000000ff (255)
                               drv probe link timer ifdown ifup rx_err tx_err
Link detected: yes

[Disk Speed Check]
> dd if=/dev/zero bs=1024k of=tstfile count=1024

1024+0 records in
1024+0 records out
1073741824 bytes (1.1 GB) copied, 17.0523 s, 63.0 MB/s

[iperf - Ubuntu as client]
> 
------------------------------------------------------------
Client connecting to 192.168.1.9, TCP port 5001
TCP window size: 21.0 KByte (default)
------------------------------------------------------------
[  3] local 192.168.1.2 port 57612 connected with 192.168.1.9 port 5001
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0-10.0 sec   655 MBytes   549 Mbits/sec

---

### Post by tomearp on 2014-03-29
What are you using for file transfers between the two windows machines?

[This post]("http://stackoverflow.com/questions/8849240/why-when-i-transfer-a-file-through-sftp-it-takes-longer-than-ftp") has an interesting answer (the top one) from a software developer describing the interaction of the various flow control mechanisms that arise as a result of using sftp.

---

### Post by Jon_Schulberger on 2014-03-29
That is a fantastic link to be honest. I knew SFTP had to have some overhead but I didn't realize it was that hurtful to my transfer speeds. Based on that post, I decided to set up SMB just for LAN use and see how much the default SFTP config degraded my speed.

SMB maintains a steady 65 MB/s while SFTP still only gets around 15 MB/s or so. It's ridiculous but I guess that's the price users pay for security. I'll attempt to integrate the HPN-SSH patch this weekend and report back with the speed differences.

Thanks for the link, that definitely helped open my eyes as to what was going on.

---

