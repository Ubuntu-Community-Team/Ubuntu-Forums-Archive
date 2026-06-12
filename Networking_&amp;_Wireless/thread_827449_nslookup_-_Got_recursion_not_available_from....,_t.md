---
title: "nslookup - Got recursion not available from...., trying next server"
date: 2008-06-12
forum: Networking &amp; Wireless
---

### Post by gcornelisse on 2008-06-12
I just built 2 new boxes with Hardy. I built them at home and just let the network configure with DHCP. Today I put them in our racks at the co-lo and changed the interfaces config for static IPs. I also changed the resolv.conf to DNS servers I'm using on other boxes in my racks.  Now these two new boxes are having strange resolv issues while all the older servers with the same configs are not:

ping by domain name
[PHP]ping www.google.com
ping: unknown host www.google.com[/PHP]

ping [www.google.com](www.google.com) by IP
[PHP]ping 72.14.205.103
PING 72.14.205.103 (72.14.205.103) 56(84) bytes of data.
64 bytes from 72.14.205.103: icmp_seq=1 ttl=245 time=21.4 ms
64 bytes from 72.14.205.103: icmp_seq=2 ttl=245 time=21.7 ms
64 bytes from 72.14.205.103: icmp_seq=3 ttl=244 time=20.8 ms[/PHP]

ping another domain
[PHP]ping www.foxnews.com
ping: unknown host www.foxnews.com[/PHP]

nslookup on google.com
[PHP]nslookup www.google.com
;; Got recursion not available from 64.202.167.31, trying next server
;; Got recursion not available from 216.69.185.100, trying next server
Server:         216.69.160.22
Address:        216.69.160.22#53

Non-authoritative answer:
*** Can't find www.google.com: No answer[/PHP]

resolv.conf (these are godaddy's DNS servers)
[PHP]nameserver 64.202.167.31
nameserver 216.69.185.100
nameserver 216.69.160.22[/PHP]

ping Godaddy who's DNS servers I'm using in my resolv.conf
[PHP]ping www.godaddy.com
PING www.godaddy.com (208.109.132.201) 56(84) bytes of data.
64 bytes from corpweb-v101.prod.mesa1.secureserver.net (208.109.132.201): icmp_seq=1 ttl=115 time=73.6 ms
64 bytes from corpweb-v101.prod.mesa1.secureserver.net (208.109.132.201): icmp_seq=2 ttl=115 time=73.0 ms

--- www.godaddy.com ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 73.006/73.320/73.635/0.415 ms[/PHP]

I've never seen this before. I'm not running BIND and I've done very little so far to start installing other packages than what comes by default on the server disk. I've changed the DNS servers to some other ones I know work and I still get the same issue.  Any help would be greatly appreciated.

---

### Post by gcornelisse on 2008-06-13
Forgot to show my interfaces file
[PHP]auto eth0
iface eth0 inet static
        address 208.101.181.101
        gateway 208.101.181.97
        netmask 255.255.255.240[/PHP]

Based on other threads here, almost seems like networking is somehow confused that its not using DHCP anymore.

---

### Post by dietmar46 on 2009-02-24
Hello gcornelisse,

did you solve your preoblem? I have exactly the same.

dietmar46

---

