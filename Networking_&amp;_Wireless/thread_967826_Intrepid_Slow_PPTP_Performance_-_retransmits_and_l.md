---
title: "Intrepid Slow PPTP Performance - retransmits and lost ACKs"
date: 2008-11-02
forum: Networking &amp; Wireless
---

### Post by john_navarro on 2008-11-02
I'm using a fresh install of Intrepid 64bit on a machine with 4GB of memory. I've got a PPTP tunnel running back to work. I quickly noticed that performance was very poor over this link. There are a lot of stalls; web pages take a very long time to render and SSH connections stall a lot. While diagnosing the issue I noticed a lot of packet buffering mesages in the syslog:

```

Nov  2 08:42:41 john00-desktop2 pptp[8338]: nm-pptp-service-8329 log[decaps_gre:pptp_gre.c:414]: buffering packet 1576 (expecting 1575, lost or reordered)
Nov  2 08:42:41 john00-desktop2 pptp[8338]: nm-pptp-service-8329 log[decaps_gre:pptp_gre.c:414]: buffering packet 1577 (expecting 1575, lost or reordered)
Nov  2 08:42:41 john00-desktop2 pptp[8338]: nm-pptp-service-8329 log[decaps_gre:pptp_gre.c:414]: buffering packet 1584 (expecting 1583, lost or reordered)
Nov  2 08:42:41 john00-desktop2 pptp[8338]: nm-pptp-service-8329 log[decaps_gre:pptp_gre.c:414]: buffering packet 1585 (expecting 1583, lost or reordered)
Nov  2 08:42:42 john00-desktop2 pptp[8338]: nm-pptp-service-8329 log[decaps_gre:pptp_gre.c:414]: buffering packet 1589 (expecting 1588, lost or reordered)
Nov  2 08:42:42 john00-desktop2 pptp[8338]: nm-pptp-service-8329 log[decaps_gre:pptp_gre.c:414]: buffering packet 1590 (expecting 1588, lost or reordered)
Nov  2 08:42:42 john00-desktop2 pptp[8338]: nm-pptp-service-8329 log[decaps_gre:pptp_gre.c:414]: buffering packet 1593 (expecting 1592, lost or reordered)
Nov  2 08:42:42 john00-desktop2 pptp[8338]: nm-pptp-service-8329 log[decaps_gre:pptp_gre.c:414]: buffering packet 1594 (expecting 1592, lost or reordered)
Nov  2 08:42:43 john00-desktop2 pptp[8338]: nm-pptp-service-8329 log[decaps_gre:pptp_gre.c:414]: buffering packet 1596 (expecting 1595, lost or reordered)
Nov  2 08:42:43 john00-desktop2 pptp[8338]: nm-pptp-service-8329 log[decaps_gre:pptp_gre.c:414]: buffering packet 1597 (expecting 1595, lost or reordered)

```

My Wireshark packet captures show a lot of retransmissions and duplicate ACK's which appear to be the cause of the performance problems:

```

18	39.050106	172.29.14.101	172.29.17.192	TCP	[TCP Previous segment lost] [TCP segment of a reassembled PDU]
19	39.050145	172.29.17.192	172.29.14.101	TCP	[TCP Dup ACK 15#1] 45754 > http [ACK] Seq=438 Ack=4333 Win=14592 Len=0 TSV=2398754 TSER=75797622 SLE=5777 SRE=6961
29	39.425900	172.29.14.101	172.29.17.192	TCP	http > 45756 [ACK] Seq=1 Ack=453 Win=50540 Len=0 TSV=75797662 TSER=2398760
30	39.747035	172.29.14.101	172.29.17.192	TCP	[TCP Previous segment lost] [TCP segment of a reassembled PDU]
31	39.747055	172.29.17.192	172.29.14.101	TCP	[TCP Dup ACK 25#1] 45756 > http [ACK] Seq=453 Ack=1 Win=5888 Len=0 TSV=2398928 TSER=75797662 SLE=1445 SRE=1705
32	39.834203	172.29.14.101	172.29.17.192	HTTP	[TCP Retransmission] HTTP/1.1 200 OK  (text/html)

```

I'm not sure how to go about further diagnosing this issue. I do know that my laptop does not have this issue - but it's running 32bit Hardy. I'm not sure if this problem is limited to the 64bit release of Intrepid.

Thank you,
John

---

### Post by john_navarro on 2008-11-02
The issue turns out to be when the PPPD deamon creates the tunnel is sets the MTU too large. However I can't figure out how to set the MTU of the PPP tunnel in the nm-applet. So I do it manually after the tunnel is established with "sudo ifconfig ppp0 mtu 1416" - for the curious my eth0 MTU is set to 1468 because I use DSL to get to the internet.

---

### Post by vmikac on 2008-11-25
In /etc/ppp/options file change the line:

#mtu <n>

with

mtu 1416

---

