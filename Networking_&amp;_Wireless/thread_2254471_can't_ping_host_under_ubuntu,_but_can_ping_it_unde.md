---
title: "can't ping host under ubuntu, but can ping it under windows"
date: 2014-11-27
forum: Networking &amp; Wireless
---

### Post by marchello_lippi2 on 2014-11-27
Hi all, 

Got wierd issue. 

I can not ping local host by its dns name under ubuntu. 
But I do can ping it under my virtual windows xp machine! 

Our admin says it can be because I got 8.8.8.8 in list of dns 

$ nm-tool 

says that I got 

    DNS:             10.51.0.9
    DNS:             10.100.100.10
    DNS:             10.100.100.11
    DNS:             8.8.8.8

I receive list of dns from dhcp, not manually... I hope... 

But my virtual windows xp machine receives them from dhcp too... 

What is it and how to solve? 

Ubuntu 14.04.1 LTS

---

### Post by marchello_lippi2 on 2014-11-27
$ nslookup plspro-cluster.prod.exp.quad.local 10.100.100.11
Server:         10.100.100.11
Address:        10.100.100.11#53

Name:   plspro-cluster.prod.exp.quad.local
Address: 10.100.56.160
Name:   plspro-cluster.prod.exp.quad.local
Address: 10.100.56.159
Name:   plspro-cluster.prod.exp.quad.local
Address: 10.100.56.155

$ arp -a plspro-cluster.prod.exp.quad.local
plspro-cluster.prod.exp.quad.local: unknows host

$ dig @10.100.100.10 plspro-cluster.prod.exp.quad.local

; <<>> DiG 9.9.5-3-Ubuntu <<>> @10.100.100.10 plspro-cluster.prod.exp.quad.local
; (1 server found)
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 39551
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 3, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 4000
;; QUESTION SECTION:
;plspro-cluster.prod.exp.quad.local. IN A

;; ANSWER SECTION:
plspro-cluster.prod.exp.quad.local. 3600 IN A   10.100.56.155
plspro-cluster.prod.exp.quad.local. 3600 IN A   10.100.56.160
plspro-cluster.prod.exp.quad.local. 3600 IN A   10.100.56.159

;; Query time: 140 msec
;; SERVER: 10.100.100.10#53(10.100.100.10)
;; WHEN: Thu Nov 27 17:58:01 EET 2014
;; MSG SIZE  rcvd: 111


It seems that 8.8.8.8 is my default dns... but why?

---

