---
title: "MoCA network speeds?"
date: 2022-04-27
forum: Networking &amp; Wireless
---

### Post by kurt18947 on 2022-04-27
Hello

Are there any other MoCA network users here? I have an installation consisting of a Verizon ONT (optical network terminal), a TP-Link C7 router running DD-WRT, 2 Motorola MM 1000 MoCA adapters and one TP-Link 8 port switch. The Motorola adapters are MoCA 2.0 bonded with a theoretical throughput around 1 Gb./sec. This setup has been working reliably for several years. I became curious about network speed and learned about iperf3. When using the command ```
iperf3 c192.168.1.xxx
``` I get speeds of around 700 Mb/sec. If I append a -u switch to the end of the above command, iperf shows slightly over 1 Gb./sec. The -u command uses UDP rather than TCP-IP for the test, or at least that's how I understand it.

Does anyone know the reason for this discrepancy? I believe TCP-IP has more overhead than UDP but that much? Or is there some configuration that could be improved? The only other nodes on this network are a Tivo unit and 2 tivo minis. There were no TVs on during this test. Thank you for any thoughts on this.

---

### Post by TheFu on 2022-04-27
TCP is a 2-way connection and has  the overhead of that connection.
UDP is a fire-at connection with ZERO guaranteed delivery.

With an ethernet connection, my GigE systems, which is all the computers, see 922 Mbps.
I don't have MoCA, but my Powerline 600 Mbps devices actually return 220 Mbps in the same room and about 62 Mbps between floors.

I typically run iperf3 this way:

Server: iperf -s
Client iperf -c <server-ip or hostname>

BTW, between a client virtual machine and the server as the VM host, I'm seeing:
```
$ iperf3 -c hadar 
Connecting to host hadar, port 5201
[  5] local 172.22.22.3 port 43852 connected to 172.22.22.6 port 5201
[ ID] Interval           Transfer     Bitrate         Retr  Cwnd
[  5]   0.00-1.00   sec  2.95 GBytes  25.3 Gbits/sec    0   2.14 MBytes       
[  5]   1.00-2.00   sec  2.81 GBytes  24.1 Gbits/sec    0   2.14 MBytes       
[  5]   2.00-3.00   sec  2.88 GBytes  24.7 Gbits/sec    0   2.26 MBytes
```
Removing that entire physical layer really speeds things up. ;)

An $ iperf3 -uc hadar 
is much slower. Just 1.05 Mbits/sec ... meh ... even for exactly the same client and server.

Moving to a different system that goes through a GigE  switch  
```
$ iperf3 -c hadar
Connecting to host hadar, port 5201
[  4] local 172.22.22.4 port 36418 connected to 172.22.22.6 port 5201
[ ID] Interval           Transfer     Bandwidth       Retr  Cwnd
[  4]   0.00-1.00   sec   114 MBytes   957 Mbits/sec    0    380 KBytes       
[  4]   1.00-2.00   sec   112 MBytes   941 Mbits/sec    0    380 KBytes   
```

Again, the UDP test is just 1.05 Mbits/sec.

I have to ask. Could it be that you are misreading the output?  I'm pretty certain that 941Mbits/sec is much larger than 1.05 Mbits/sec and that's what I'm seeing here.

---

### Post by kurt18947 on 2022-05-01
Thanks for your reply. Yeah, it's probable that I mis-typed on the Mb Gb thing. I'm still happier with wired vs. wireless for non-mobile devices. I was just wondering if I have something mis-configured.

---

