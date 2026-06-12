---
title: "How i can check bandwidth routing to a Country"
date: 2015-07-28
forum: Networking &amp; Wireless
---

### Post by buffalo2 on 2015-07-28
I'm rouring from Vietnam to Korea.
How I can check speed between Vietnam and Korea?

---

### Post by dino99 on 2015-07-28
Give it a try

[http://www.speedtest.net/](http://www.speedtest.net/)

---

### Post by SeijiSensei on 2015-07-29
You can also install **traceroute** and point it at a machine in Korea.  It will report each router it encounters along the way and the time it took.  For example, here's the results when I trace a route to Google's DNS server at 8.8.8.8:
```

$ traceroute 8.8.8.8
traceroute to 8.8.8.8 (8.8.8.8), 30 hops max, 60 byte packets
 1  DD-WRT (192.168.100.1)  0.394 ms  0.431 ms  0.478 ms
 2  192.168.1.1 (192.168.1.1)  1.219 ms  1.228 ms  1.239 ms
 3  lo0-100.BSTNMA-VFTTP-301.verizon-gni.net (96.230.114.1)  9.036 ms  10.428 ms  10.429 ms
 4  T1-0-0-9.BSTNMA-LCR-22.verizon-gni.net (130.81.171.70)  16.073 ms T1-0-0-10.BSTNMA-LCR-21.verizon-gni.net (130.81.191.116)  13.109 ms T1-0-0-9.BSTNMA-LCR-22.verizon-gni.net (130.81.171.70)  16.061 ms
 5  * * *
 6  0.ae4.XL4.NYC1.ALTER.NET (140.222.226.37)  18.929 ms 0.ae3.XL3.NYC1.ALTER.NET (140.222.226.31)  17.921 ms 0.ae4.XL4.NYC1.ALTER.NET (140.222.226.37)  21.775 ms
 7  0.xe-11-3-3.GW13.NYC1.ALTER.NET (152.63.19.122)  16.868 ms 0.xe-11-1-0.GW13.NYC1.ALTER.NET (152.63.29.230)  19.654 ms 0.xe-10-1-1.GW13.NYC1.ALTER.NET (152.63.19.45)  19.679 ms
 8  google-gw.customer.alter.net (204.148.18.206)  19.602 ms  19.608 ms  23.947 ms
 9  64.233.175.43 (64.233.175.43)  17.093 ms 64.233.175.63 (64.233.175.63)  19.642 ms 64.233.175.45 (64.233.175.45)  21.998 ms
10  google-public-dns-a.google.com (8.8.8.8)  21.897 ms  21.940 ms  21.630 ms

```
The first two entries are routers in my office.  From step 3 onward, it's tracing packets over the Internet.  The machine with "* * *"  does not reply to the ICMP ping service that traceroute uses.  If you don't care to see the hostnames associated with each router, running "traceroute -n" just reports their IPs.

---

