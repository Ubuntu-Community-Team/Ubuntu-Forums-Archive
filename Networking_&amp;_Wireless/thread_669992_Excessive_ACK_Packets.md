---
title: "Excessive ACK Packets"
date: 2008-01-16
forum: Networking &amp; Wireless
---

### Post by dbarbour on 2008-01-16
Just setup a new Ubuntu box and am transferring all of my media files over to it... at least that's the idea. It takes over 2 minutes to transfer a 4MB mp3 across my LAN. I'm copying from Windows to Linux and getting the following when I run *tcpdump* on eth0:

```
..........
22:50:35.556222 IP dbarbour-server.dbarbour.dyndns.org.microsoft-ds > 192.168.137.51.datametrics: P 4621:4701(80) ack 3841260 win 65535
22:50:35.556684 IP 192.168.137.51.datametrics > dbarbour-server.dbarbour.dyndns.org.microsoft-ds: P 3841260:3841406(146) ack 4701 win 65000
22:50:35.557105 IP dbarbour-server.dbarbour.dyndns.org.microsoft-ds > 192.168.137.51.datametrics: P 4701:4840(139) ack 3841406 win 65535
22:50:35.557541 IP 192.168.137.51.datametrics > dbarbour-server.dbarbour.dyndns.org.microsoft-ds: P 3841406:3841451(45) ack 4840 win 64861
22:50:35.557616 IP dbarbour-server.dbarbour.dyndns.org.microsoft-ds > 192.168.137.51.datametrics: P 4840:4879(39) ack 3841451 win 65535
22:50:35.558092 IP 192.168.137.51.datametrics > dbarbour-server.dbarbour.dyndns.org.microsoft-ds: P 3841451:3841531(80) ack 4879 win 64822
22:50:35.558160 IP dbarbour-server.dbarbour.dyndns.org.microsoft-ds > 192.168.137.51.datametrics: P 4879:4983(104) ack 3841531 win 65535
22:50:35.558372 IP 192.168.137.51.datametrics > dbarbour-server.dbarbour.dyndns.org.microsoft-ds: P 3841531:3841605(74) ack 4983 win 64718
22:50:35.558439 IP dbarbour-server.dbarbour.dyndns.org.microsoft-ds > 192.168.137.51.datametrics: P 4983:5063(80) ack 3841605 win 65535
22:50:35.583658 IP 192.168.137.51.datametrics > dbarbour-server.dbarbour.dyndns.org.microsoft-ds: P 3841605:3841741(136) ack 5063 win 64638
22:50:35.584504 IP dbarbour-server.dbarbour.dyndns.org.microsoft-ds > 192.168.137.51.datametrics: P 5063:5167(104) ack 3841741 win 65535
22:50:35.584871 IP 192.168.137.51.datametrics > dbarbour-server.dbarbour.dyndns.org.microsoft-ds: P 3841741:3841815(74) ack 5167 win 64534
22:50:35.585008 IP dbarbour-server.dbarbour.dyndns.org.microsoft-ds > 192.168.137.51.datametrics: P 5167:5247(80) ack 3841815 win 65535
22:50:35.586083 IP 192.168.137.51.datametrics > dbarbour-server.dbarbour.dyndns.org.microsoft-ds: P 3841815:3842013(198) ack 5247 win 64454
22:50:35.586603 IP dbarbour-server.dbarbour.dyndns.org.microsoft-ds > 192.168.137.51.datametrics: P 5247:5386(139) ack 3842013 win 65535
..........

```

A bit excessive on the ack packets, no? Any ideas on tracking that issue down? A Samba deal, maybe?

---

