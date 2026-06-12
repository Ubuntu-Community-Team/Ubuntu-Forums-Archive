---
title: "http://packages.ubuntu.com/ IS DOWN!!"
date: 2008-06-29
forum: Networking &amp; Wireless
---

### Post by cccccccc on 2008-06-29
Hellou, dont know where to post it. but is seems that [http://packages.ubuntu.com/](http://packages.ubuntu.com/) is pretty down for a while.
  Dont want to make a mass, but how can be all servers for such a big comunity down? If this happened in company I work, my boss would kill me:). And we have 6 employees:) People, STOP hacking Ubuntu!!!

---

### Post by wo_shi_big_stomach on 2008-06-29
As of 1500 UTC 29 June 2008, it's reachable from Southern California:

levi:~ $ host packages.ubuntu.com
packages.ubuntu.com has address 91.189.94.219

levi:~ $ ping 91.189.94.219
PING 91.189.94.219 (91.189.94.219): 56 data bytes
64 bytes from 91.189.94.219: icmp_seq=0 ttl=43 time=175.463 ms

levi:~ $ telnet 91.189.94.219 80
Trying 91.189.94.219...
Connected to sulfur.canonical.com.

/wsbs

---

### Post by ibutho on 2008-06-29
The site times out for me although I can ping the IP address and get a response.

---

### Post by cccccccc on 2008-06-29
> **ibutho said:**
> The site times out for me although I can ping the IP address and get a response.

the same me here in EU. ping works, but page no go... also forum was disabled for few minutes...

---

### Post by sdoyle on 2008-06-29
Site down for me.

Cannot traceroute from Dallas or Phoenix (shown below).

traceroute to packages.ubuntu.com (91.189.94.219), 30 hops max, 40 byte packets
 1  x.x.x.x (x.x.x.x)  0.401 ms  0.379 ms  0.611 ms
 2  206.123.64.121 (206.123.64.121)  9.591 ms  9.587 ms  9.579 ms
 3  ge-6-18.car1.Dallas1.Level3.net (8.9.232.73)  27.299 ms  27.294 ms  27.287 m                                               s
 4  * * *
 5  ae-92-92.ebr2.Dallas1.Level3.net (4.69.136.149)  10.989 ms  10.720 ms  10.706 ms
 6  ae-6.ebr3.NewYork1.Level3.net (4.69.137.122)  35.435 ms  47.669 ms  47.660 ms
 7  ae-83-83.csw3.NewYork1.Level3.net (4.69.134.106)  35.886 ms  45.684 ms ae-73-73.csw2.NewYork1.Level3.net (4.69.134.102)  41.674 ms
 8  ae-91-91.ebr1.NewYork1.Level3.net (4.69.134.77)  38.173 ms ae-61-61.ebr1.NewYork1.Level3.net (4.69.134.65)  37.457 ms ae-81-81.ebr1.NewYork1.Level3.net (4.69.134.73)  37.435 ms
 9  ae-43.ebr2.London1.Level3.net (4.69.137.73)  106.667 ms ae-44.ebr2.London1.Level3.net (4.69.137.77)  105.891 ms ae-42.ebr2.London1.Level3.net (4.69.137.69)  105.379 ms
10  ae-1-100.ebr1.London1.Level3.net (4.69.132.117)  108.618 ms  118.904 ms  116.661 ms
11  ae-2.ebr2.London2.Level3.net (4.69.132.145)  108.400 ms  108.383 ms  108.687 ms
12  ae-26-54.car2.London2.Level3.net (4.68.117.112)  106.160 ms ae-26-56.car2.London2.Level3.net (4.68.117.176)  105.156 ms  106.913 ms
13   (195.50.121.2)  107.665 ms  108.659 ms  107.162 ms
14  gw0-0-gr.canonical.com (91.189.88.10)  106.920 ms  106.913 ms  106.659 ms
15  * * *
16  * * *
17  * * *
18  * * *
19  * * *
20  * * *

traceroute to packages.ubuntu.com (91.189.94.219), 30 hops max, 40 byte packets
 1  hosted-by.serve.com (x.x.x.x)  0.640 ms  0.425 ms  0.472 ms
 2  ge7-20.fr4.phx3.llnw.net (69.28.174.241)  0.552 ms  0.384 ms  0.232 ms
 3  ve4.fr3.phx2.llnw.net (69.28.172.141)  0.689 ms  0.674 ms  0.733 ms
 4  tge1-3.fr3.dal.llnw.net (69.28.171.130)  27.835 ms  27.914 ms  27.709 ms
 5  tge5-3.fr3.ord.llnw.net (69.28.171.198)  54.721 ms  60.403 ms  51.722 ms
 6  ve6.fr4.ord.llnw.net (69.28.172.42)  51.663 ms  56.882 ms  51.789 ms
 7  tge11-3.fr3.lga.llnw.net (69.28.171.194)  86.134 ms  79.419 ms  78.898 ms
 8  tge1-2.fr3.lon.llnw.net (69.28.171.126)  152.478 ms  150.623 ms  150.558 ms
 9  po3-0-cr0.thn.uk.as6908.net (195.66.225.32)  150.671 ms  150.556 ms  346.576 ms
10  canonical-gw.datahop.net (195.72.130.230)  151.117 ms  151.132 ms  151.051 ms
11  gw0-0-gr.canonical.com (91.189.88.10)  151.166 ms  151.092 ms  151.147 ms
12  * * *
13  * * *
14  * * *
15  * * *
16  * * *
17  * * *

---

### Post by cccccccc on 2008-06-29
so they solved it!

---

### Post by sdoyle on 2008-07-03
packages.ubuntu.com is down right now.

Same results from traceroutes as I did above...

---

### Post by shirsch on 2008-07-26
Ditto today, July 26.  Unable to use getlibs as a result.  Is there any alternative way to have getlibs lookup its references?

---

