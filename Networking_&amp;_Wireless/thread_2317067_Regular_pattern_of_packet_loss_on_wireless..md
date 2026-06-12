---
title: "Regular pattern of packet loss on wireless."
date: 2016-03-13
forum: Networking &amp; Wireless
---

### Post by Starbeamrainbowlab on 2016-03-13
I've been having a bit of trouble with my internet connection recently, and I've just had time to properly diagnose the problem. It turns out that while there is an issue with my internet connection, there is also an issue with the wireless card in my laptop. I am getting a regular pattern of packet loss. Here's an example output from ping -O  <another host on my local network>:

no answer yet for icmp_seq=1524
no answer yet for icmp_seq=1525
no answer yet for icmp_seq=1526
no answer yet for icmp_seq=1527
64 bytes from wa-in-f102.1e100.net (64.233.184.102): icmp_seq=1528 ttl=45 time=46.8 ms
64 bytes from wa-in-f102.1e100.net (64.233.184.102): icmp_seq=1529 ttl=45 time=50.5 ms
64 bytes from wa-in-f102.1e100.net (64.233.184.102): icmp_seq=1530 ttl=45 time=48.9 ms
64 bytes from wa-in-f102.1e100.net (64.233.184.102): icmp_seq=1531 ttl=45 time=47.5 ms
64 bytes from wa-in-f102.1e100.net (64.233.184.102): icmp_seq=1532 ttl=45 time=50.6 ms
64 bytes from wa-in-f102.1e100.net (64.233.184.102): icmp_seq=1533 ttl=45 time=48.3 ms
64 bytes from wa-in-f102.1e100.net (64.233.184.102): icmp_seq=1534 ttl=45 time=47.1 ms
no answer yet for icmp_seq=1535
no answer yet for icmp_seq=1536
no answer yet for icmp_seq=1537
no answer yet for icmp_seq=1538
no answer yet for icmp_seq=1539
no answer yet for icmp_seq=1540
no answer yet for icmp_seq=1541
no answer yet for icmp_seq=1542
64 bytes from wa-in-f102.1e100.net (64.233.184.102): icmp_seq=1543 ttl=45 time=50.2 ms
64 bytes from wa-in-f102.1e100.net (64.233.184.102): icmp_seq=1544 ttl=45 time=50.0 ms
64 bytes from wa-in-f102.1e100.net (64.233.184.102): icmp_seq=1545 ttl=45 time=47.4 ms
64 bytes from wa-in-f102.1e100.net (64.233.184.102): icmp_seq=1546 ttl=45 time=50.1 ms
64 bytes from wa-in-f102.1e100.net (64.233.184.102): icmp_seq=1547 ttl=45 time=50.1 ms
64 bytes from wa-in-f102.1e100.net (64.233.184.102): icmp_seq=1548 ttl=45 time=48.5 ms
64 bytes from wa-in-f102.1e100.net (64.233.184.102): icmp_seq=1549 ttl=45 time=51.6 ms
64 bytes from wa-in-f102.1e100.net (64.233.184.102): icmp_seq=1550 ttl=45 time=49.6 ms
no answer yet for icmp_seq=1551
no answer yet for icmp_seq=1552
no answer yet for icmp_seq=1553
no answer yet for icmp_seq=1554
no answer yet for icmp_seq=1555
no answer yet for icmp_seq=1556
no answer yet for icmp_seq=1557
no answer yet for icmp_seq=1558
64 bytes from wa-in-f102.1e100.net (64.233.184.102): icmp_seq=1559 ttl=45 time=50.2 ms
64 bytes from wa-in-f102.1e100.net (64.233.184.102): icmp_seq=1560 ttl=45 time=50.2 ms
64 bytes from wa-in-f102.1e100.net (64.233.184.102): icmp_seq=1561 ttl=45 time=48.6 ms
64 bytes from wa-in-f102.1e100.net (64.233.184.102): icmp_seq=1562 ttl=45 time=47.2 ms
64 bytes from wa-in-f102.1e100.net (64.233.184.102): icmp_seq=1563 ttl=45 time=46.7 ms
64 bytes from wa-in-f102.1e100.net (64.233.184.102): icmp_seq=1564 ttl=45 time=48.5 ms
no answer yet for icmp_seq=1565
no answer yet for icmp_seq=1566
no answer yet for icmp_seq=1567
no answer yet for icmp_seq=1568
no answer yet for icmp_seq=1569
no answer yet for icmp_seq=1570
no answer yet for icmp_seq=1571
no answer yet for icmp_seq=1572
no answer yet for icmp_seq=1573

It goes 6-8 on, and then 6-8 off, with 53% packet loss over 1500 packets.

I've seen a wireless info script around these forums whilst looking for solutions, so I've run it and you can see the results here: [http://hastebin.com/ofarobakum](http://hastebin.com/ofarobakum)

Does anyone know what is going on here?

Thanks.

**Update:** If I use a different wireless adapter, I do not have this problem.

---

