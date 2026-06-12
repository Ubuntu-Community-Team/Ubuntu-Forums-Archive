---
title: "i'm connected to ISP but can't browse"
date: 2005-05-04
forum: Networking &amp; Wireless
---

### Post by Hi_Ho on 2005-05-04
Hi people, i need you help
I'm using a Speedtouch Adsl PPPoE modem. I can connect to the ISP, but I can't browse or ping. The DNS are correct beacuse they are the same that a got from my ISP
Please help me

---

### Post by kvidell on 2005-05-04
[QUOTE=Hi_Ho]Hi people, i need you help
I'm using a Speedtouch Adsl PPPoE modem. I can connect to the ISP, but I can't browse or ping. The DNS are correct beacuse they are the same that a got from my ISP
Please help me[/QUOTE]
What does your resolv.conf file look like?
> cat /etc/resolv.conf
If it says "search" in it you might want to try removing that (not the whole line, just the word)
- Kev

---

### Post by Hi_Ho on 2005-05-05
[QUOTE=kvidell]What does your resolv.conf file look like?

If it says "search" in it you might want to try removing that (not the whole line, just the word)
- Kev[/QUOTE]

my resolv.conf look like this:

search lan
nameserver 10.0.0.138


i remove the word "search" but nothing changes... i can't surf the net.

 :neutral:

---

### Post by kvidell on 2005-05-05
[QUOTE=Hi_Ho]my resolv.conf look like this:

search lan
nameserver 10.0.0.138


i remove the word "search" but nothing changes... i can't surf the net.

 :neutral:[/QUOTE]
 Remove the word "lan" as well, my mistake.

---

### Post by Hi_Ho on 2005-05-05
poloux@beathouse:~$ sudo pon dsl-provider
Password:
Plugin rp-pppoe.so loaded.
RP-PPPoE plugin version 3.3 compiled against pppd 2.4.2
poloux@beathouse:~$ plog
May 04 01:25:40 localhost pppd[7628]: RP-PPPoE plugin version 3.3 compiled against pppd 2.4.2
May 04 01:25:40 localhost pppd[7681]: pppd 2.4.2 started by root, uid 0
May 04 01:25:40 localhost pppd[7681]: PPP session is 33322
May 04 01:25:40 localhost pppd[7681]: Using interface ppp0
May 04 01:25:40 localhost pppd[7681]: Connect: ppp0 <--> eth0
May 04 01:25:40 localhost pppd[7681]: Couldn't increase MTU to 1500
May 04 01:25:40 localhost pppd[7681]: Couldn't increase MRU to 1500
poloux@beathouse:~$ plog
May 04 01:26:00 localhost pppd[7681]: Cannot determine ethernet address for proxy ARP
May 04 01:26:00 localhost pppd[7681]: local IP address 82.51.25.17
May 04 01:26:00 localhost pppd[7681]: remote IP address 192.168.100.1
May 04 01:26:00 localhost pppd[7681]: primary DNS address 200.72.1.5
May 04 01:26:00 localhost pppd[7681]: secondary DNS address 200.72.1.11

i know that the DNS address are OK because i use that address in Mandrake with no problem

---

### Post by Hi_Ho on 2005-05-05
[QUOTE=kvidell]Remove the word "lan" as well, my mistake.[/QUOTE]

I'll try this!!.. thanks!

---

### Post by alastair on 2005-05-05
nameserver 10.0.0.138

That nameserver line is odd (assuming it is not superceded elsewhere via PPP) - it's a private address. Do you have a system or router doing DNS at 10.0.0.138?

---

### Post by Hi_Ho on 2005-05-05
[QUOTE=alastair]nameserver 10.0.0.138

That nameserver line is odd (assuming it is not superceded elsewhere via PPP) - it's a private address. Do you have a system or router doing DNS at 10.0.0.138?[/QUOTE]


Hi alastair and thanks for your help

when i remove "lan" from resolv.conf the namreserver was not the same and become  the DNS address from my ISP

now i can surf in the internet but i can see only one page (in my case i go to [www.google.cl](www.google.cl)) and i can't see no more sites

the connection is running but became so slow

help my again please!!!

---

### Post by alastair on 2005-05-05
Is it just firefox/web?

Try a "ping" on an IP address e.g. when I ping "www.google.com" I see :

64 bytes from 66.249.87.99: icmp_seq=0 ttl=252 time=255 ms
64 bytes from 66.249.87.99: icmp_seq=1 ttl=252 time=249 ms
64 bytes from 66.249.87.99: icmp_seq=2 ttl=252 time=243 ms

Try :

ping 66.249.87.99

Then try :

ping [www.google.com](www.google.com)

What about pinging your DNS server :

ping 200.72.1.5

I see :

64 bytes from 200.72.1.5: icmp_seq=0 ttl=243 time=388 ms
64 bytes from 200.72.1.5: icmp_seq=1 ttl=243 time=407 ms
64 bytes from 200.72.1.5: icmp_seq=2 ttl=243 time=414 ms
64 bytes from 200.72.1.5: icmp_seq=3 ttl=243 time=432 ms

---

### Post by alastair on 2005-05-05
Maybe it's IPv6 lookup?

In Firefox - go to :

about:config

In the search box, type "ipv6" and double-click to disable (make "true") :

network.dns.disableIPv6  ( make --> true)

Does that help?

---

