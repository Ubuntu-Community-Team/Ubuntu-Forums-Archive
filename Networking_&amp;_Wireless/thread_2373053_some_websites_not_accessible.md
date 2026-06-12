---
title: "some websites not accessible"
date: 2017-10-02
forum: Networking &amp; Wireless
---

### Post by fagus2 on 2017-10-02
Hello

Since yesterday (maybe longer) I can 't access the website [www.raspberrypi.org](www.raspberrypi.org) anymore. Other websites are no problem. I can access the site on my phone though. Only on my tree xubuntu 17.04 devices, I get the error message: 

[www.raspberrypi.org’s](www.raspberrypi.org’s) server DNS address could not be found.
DNS_PROBE_FINISHED_NXDOMAIN

It 's not accessible in firefox nor in chromium. I also can 't ping the site.

Could someone please give me a hint on this. I've been searching the net and tried some things but nothing helped. Thanks a lot!

fagus

---

### Post by ajgreeny on 2017-10-02
Can you ping raspberrypi.org or the IP address for the same thing, ie 93.93.130.214?
Here's what I get from the former.
```
ping raspberrypi.org
PING raspberrypi.org (93.93.130.214) 56(84) bytes of data.
64 bytes from 93.93.130.214: icmp_seq=1 ttl=57 time=12.5 ms
64 bytes from 93.93.130.214: icmp_seq=2 ttl=57 time=11.1 ms
64 bytes from 93.93.130.214: icmp_seq=3 ttl=57 time=11.4 ms
64 bytes from 93.93.130.214: icmp_seq=4 ttl=57 time=12.1 ms
64 bytes from 93.93.130.214: icmp_seq=5 ttl=57 time=11.1 ms
```

---

### Post by vasa1 on 2017-10-02
Maybe try a different DNS?

---

### Post by fagus2 on 2017-10-03
ok I solved it by changing dns-server. thanx!

---

### Post by ajgreeny on 2017-10-04
Great news! Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to users searching the forum.

---

