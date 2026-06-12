---
title: "Weird Networking Problem"
date: 2006-10-31
forum: Networking &amp; Wireless
---

### Post by tanhaa on 2006-10-31
I am getting this weird problem on my xubuntu 6.06 server.

I was trying to go to site1 and I got redirected to site2 completely.  My server name is "server.zonecom.com", I tried several other sites after that, everytime I was taken to [www.zonecom.com](www.zonecom.com) instead.

I'll show you guys how weird this is coming out to be.  Here's my ping result for example "www.myipaddress.com"

PING [www.myipaddress.com](www.myipaddress.com) (209.15.22.127) 56(84) bytes of data.
64 bytes from zonecom.com (209.15.22.127): icmp_seq=1 ttl=241 time=39.4 ms
64 bytes from zonecom.com (209.15.22.127): icmp_seq=2 ttl=241 time=39.4 ms
64 bytes from zonecom.com (209.15.22.127): icmp_seq=3 ttl=241 time=39.4 ms
64 bytes from zonecom.com (209.15.22.127): icmp_seq=4 ttl=241 time=39.4 ms
64 bytes from zonecom.com (209.15.22.127): icmp_seq=5 ttl=241 time=39.6 ms
64 bytes from zonecom.com (209.15.22.127): icmp_seq=6 ttl=241 time=39.5 ms

--- [www.myipaddress.com](www.myipaddress.com) ping statistics ---
6 packets transmitted, 6 received, 0% packet loss, time 5020ms
rtt min/avg/max/mdev = 39.400/39.482/39.634/0.219 ms

================

now here is the nslookup result for [www.myipaddress.com:](www.myipaddress.com:)

Server:		66.158.128.11
Address:	66.158.128.11#53

Non-authoritative answer:
[www.myipaddress.com](www.myipaddress.com)	canonical name = www200.forum.net.
Name:	www200.forum.net
Address: 12.148.220.160

==================

any idea why there is this difference .. while nslookup is finding the correct IP to reach the site, ping goes instead to zonecom.com, so does the browser. 

Please help..

Amit

---

### Post by alaman on 2006-10-31
does your resolve.conf file have additional nameservers listed? you may be looking up to differnet servers.

---

### Post by tanhaa on 2006-10-31
My resolv.conf has two nameservers listed, the ones given by my ISP:

66.158.128.11
66.158.128.131

nothing wrong there I guess.


Amit

---

### Post by alaman on 2006-10-31
can you see if you get different reponses from the servers in your resovle.conf.  for example in nslookup
> server 66.158.128.11
> domainyouarelookingup.com
 
see the results, then

> server 66.158.128.131
> domainyouarelookingup.com
 
and see if you get different results.  btw - I believe dig is now preferred to nslookup

---

### Post by tanhaa on 2006-10-31
Hi alaman

I tried using both the servers with nslookup and i got exactly the same response.  Nslookup is not the problem though, Ping won't route me to the right IP and neither would any other service. 

Nothing takes me to the site, while nslookup shows the right IP for the domain, everything else takes me to a different IP.


Amit

---

### Post by tanhaa on 2006-11-01
anybody else with any ideas .... a nudge in the right direction? :)

TIA

Amit

---

### Post by featherking on 2006-11-01
Do you have a proxy like squid installed? It seems like something is routing your traffic directly to zonecom.com. try running

```
sudo iptables -L
```
and see if there are any forwarding rules, also try to run

```
sudo iptables -L -t nat
```
and lookk for the same thing. Anything that would point http traffic (port 80) to another location

---

### Post by Joeak on 2006-11-01
This is the type of behavior you get on hotel networks where you have to go to their web site and register before you're allowed through their router or proxy to the internet.  Until you register, all your traffic is routed to their internal server.

---

### Post by tanhaa on 2006-11-01
> **featherking said:**
> Do you have a proxy like squid installed? It seems like something is routing your traffic directly to zonecom.com. try running


No, no proxy, no squid. 

> 
```
sudo iptables -L
```
and see if there are any forwarding rules, also try to run

```
sudo iptables -L -t nat
```
and lookk for the same thing. Anything that would point http traffic (port 80) to another location

none of these commands showed any forwarding rules... here is the output:

sudo iptables -L

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination    

sudo iptables -L -t nat

Chain PREROUTING (policy ACCEPT)
target     prot opt source               destination         

Chain POSTROUTING (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination     


:-S

---

### Post by tanhaa on 2006-11-01
> **Joeak said:**
> This is the type of behavior you get on hotel networks where you have to go to their web site and register before you're allowed through their router or proxy to the internet.  Until you register, all your traffic is routed to their internal server.


Interesting point.  You are right, but I don't have any proxy and my router is definitely not routing my traffic.  And some sites work, for example, from the linux box, I can go to [http://www.ubuntu.com](http://www.ubuntu.com), but when I try to go [www.ubuntuforums.org](www.ubuntuforums.org), it routes me again to [www.zonecom.com](www.zonecom.com).

Amit

---

### Post by alaman on 2006-11-01
could you post of packets so we can see what is happening at the network layer?  for example, sudo tcpdump -n -v  then try to access a problem site.

---

### Post by tanhaa on 2006-11-01
> **alaman said:**
> could you post of packets so we can see what is happening at the network layer?  for example, sudo tcpdump -n -v  then try to access a problem site.

A little long TCP DUMP.

I did a few things while running the tcpdump command:
accessed:  [www.ubuntuforums.org](www.ubuntuforums.org), [www.myipaddress.com](www.myipaddress.com), [www.zoneocm.com](www.zoneocm.com) (a domain that doesn't exist) and pinged both ubuntuforums and myipaddress.  Also ran nslookup on [www.ubuntuforums.org](www.ubuntuforums.org)

look at this entry in the tcpdump:

15:40:06.035901 IP (tos 0x0, ttl  64, id 14094, offset 0, flags [DF], proto: UDP (17), length: 61) 192.168.1.99.32874 > 66.158.128.11.53:  3974+ A? [WWW.MYIPADDRESS](WWW.MYIPADDRESS). (33)
15:40:06.079761 IP (tos 0x0, ttl  61, id 44758, offset 0, flags [DF], proto: UDP (17), length: 136) 66.158.128.11.53 > 192.168.1.99.32874:  3974 NXDomain 0/1/0 (108)
15:40:06.079859 IP (tos 0x0, ttl  64, id 14105, offset 0, flags [DF], proto: UDP (17), length: 73) 192.168.1.99.32874 > 66.158.128.11.53:  2180+ A? [WWW.MYIPADDRESS.zonecom.com](WWW.MYIPADDRESS.zonecom.com). (45)
15:40:06.122211 IP (tos 0x0, ttl  61, id 44766, offset 0, flags [DF], proto: UDP (17), length: 171) 66.158.128.11.53 > 192.168.1.99.32874:  2180 1/3/1 [WWW.MYIPADDRESS.zonecom.com](WWW.MYIPADDRESS.zonecom.com). (143)
===============
here's another one:

15:39:53.039800 IP (tos 0x0, ttl  64, id 10844, offset 0, flags [DF], proto: UDP (17), length: 61) 192.168.1.99.32873 > 66.158.128.11.53:  18477+ A? [WWW.ZONEOCM.COM](WWW.ZONEOCM.COM). (33)
15:39:53.134217 IP (tos 0x0, ttl  61, id 42095, offset 0, flags [DF], proto: UDP (17), length: 134) 66.158.128.11.53 > 192.168.1.99.32873:  18477 NXDomain 0/1/0 (106)
15:39:53.134402 IP (tos 0x0, ttl  64, id 10869, offset 0, flags [DF], proto: UDP (17), length: 73) 192.168.1.99.32873 > 66.158.128.11.53:  55945+ A? [WWW.ZONEOCM.COM.zonecom.com](WWW.ZONEOCM.COM.zonecom.com). (45)
15:39:53.174938 IP (tos 0x0, ttl  61, id 42112, offset 0, flags [DF], proto: UDP (17), length: 171) 66.158.128.11.53 > 192.168.1.99.32873:  55945 1/3/1 [WWW.ZONEOCM.COM.zonecom.com](WWW.ZONEOCM.COM.zonecom.com). (143)
====================

---

### Post by tanhaa on 2006-11-01
and here's the dump when i accessed ubuntu.com from the browser:

15:51:28.228043 IP (tos 0x0, ttl  64, id 53560, offset 0, flags [DF], proto: UDP (17), length: 60) 192.168.1.99.32878 > 66.158.128.11.53:  44088+ A? [WWW.UBUNTU.COM](WWW.UBUNTU.COM). (32)
15:51:28.228207 IP (tos 0x0, ttl  64, id 53560, offset 0, flags [DF], proto: UDP (17), length: 60) 192.168.1.99.32879 > 66.158.128.11.53:  39639+ AAAA? [www.ubuntu.com](www.ubuntu.com). (32)
15:51:28.264518 IP (tos 0x0, ttl 128, id 19866, offset 0, flags [none], proto: UDP (17), length: 78) 192.168.1.110.137 > 192.168.1.255.137: NBT UDP PACKET(137): QUERY; REQUEST; BROADCAST
15:51:28.338751 IP (tos 0x0, ttl  61, id 61000, offset 0, flags [DF], proto: UDP (17), length: 120) 66.158.128.11.53 > 192.168.1.99.32879:  39639 0/1/0 (92)
15:51:28.338925 IP (tos 0x0, ttl  64, id 53587, offset 0, flags [DF], proto: UDP (17), length: 72) 192.168.1.99.32879 > 66.158.128.11.53:  38841+ AAAA? [www.ubuntu.com.zonecom.com](www.ubuntu.com.zonecom.com). (44)
15:51:28.340208 IP (tos 0x0, ttl  61, id 61001, offset 0, flags [DF], proto: UDP (17), length: 199) 66.158.128.11.53 > 192.168.1.99.32878:  44088 1/3/3 [WWW.UBUNTU.COM](WWW.UBUNTU.COM). A 82.211.81.166 (171)
15:51:28.379898 IP (tos 0x0, ttl  61, id 61010, offset 0, flags [DF], proto: UDP (17), length: 135) 66.158.128.11.53 > 192.168.1.99.32879:  38841 0/1/0 (107)
15:51:28.380163 IP (tos 0x0, ttl  64, id 53598, offset 0, flags [DF], proto: UDP (17), length: 60) 192.168.1.99.32879 > 66.158.128.11.53:  40616+ A? [www.ubuntu.com](www.ubuntu.com). (32)
15:51:28.389098 IP (tos 0x0, ttl  61, id 61013, offset 0, flags [DF], proto: UDP (17), length: 199) 66.158.128.11.53 > 192.168.1.99.32879:  40616 1/3/3 [www.ubuntu.com](www.ubuntu.com). A 82.211.81.166 (171)
15:51:28.389382 IP (tos 0x0, ttl  64, id 1151, offset 0, flags [DF], proto: TCP (6), length: 60) 192.168.1.99.37019 > 82.211.81.166.80: S, cksum 0xdc3e (correct), 3050689823:3050689823(0) win 5840 <mss 1460,sackOK,timestamp 19976544 0,nop,wscale 2>

---

### Post by alaman on 2006-11-01
Hi Tanhaa - do you have any search or domain settings in your resolv.conf?  It appears that zonecom.com is being added to the end of the request.

---

### Post by tanhaa on 2006-11-01
> **alaman said:**
> Hi Tanhaa - do you have any search or domain settings in your resolv.conf?  It appears that zonecom.com is being added to the end of the request.

I know that's what's happening alaman.. :( 
but really, there is no setting in resolv.conf except for the two DNS entries.

I can't figure out why every request is getting zonecom.com added at the end.  What else would control this if not resolv.conf?

Amit

---

### Post by alaman on 2006-11-01
the only 2 places I know to look (unless you a dns server running locally) are the /etc/resolv.conf and /etc/hosts. You may check your /etc/host.conf and  /etc/hostname - but I'm only guessing.  Can anyone else help?

---

### Post by tanhaa on 2006-11-01
> **alaman said:**
> the only 2 places I know to look (unless you a dns server running locally) are the /etc/resolv.conf and /etc/hosts. You may check your /etc/host.conf and  /etc/hostname - but I'm only guessing.  Can anyone else help?


my host.conf says:

order hosts,bind
multi on

my etc hostname doesn't have anything but the hostnames really... nothing out of the ordinary that I thought at least

I'm not running dns server on the box, but I did install ispconfig.  After the install, this problem did not occur.  I had to do a reboot after about 15 days and when the system came back online, this problem started happening.

---

### Post by featherking on 2006-11-02
any why is everything using UDP instead of TCP, something aint right..

---

### Post by alaman on 2006-11-02
yes, UDP is correct for dns lookups.  UDP is generally used for lookups and TCP is usually used for larger exchanges (like zone transfers).  On the ispconfig, I'm pretty weak.  I suggest trying to see if/what application is running DNS on the box (netstat -an, lsof -i, ps -ef) for ispconfig - then check its config file.  I suspect you'll find the solution there.  If you would like to post some of the info, I'll try to help.

---

### Post by alaman on 2006-11-02
thinking about this a bit more...you may be missing a "." at the end of a dns record entry in your bind setup.

---

### Post by tanhaa on 2006-11-02
What files should I paste here for you to check?  I'm not really sure about bind settings.  I know bind is running, I found it just now... but the thing is, even after stopping bind, i still kept on having the same problem

Amit

---

### Post by alaman on 2006-11-02
you are probably looking for a file called zonecom.com.  I would try /var/named/zone/ and see if you have an internal and/or external directory.  The file is probably in there.

---

### Post by tanhaa on 2006-11-03
> **alaman said:**
> you are probably looking for a file called zonecom.com.  I would try /var/named/zone/ and see if you have an internal and/or external directory.  The file is probably in there.

/var/named/zone is not there

I do have bind in

var/lib/named/etc/bind/

but there are no zones ... no zonecom.com file either.  

my named.conf file is very simple too

zone "."  going to db.root

and 
zone "0.0.127.in-addr.arpa"
going to db.127

that's about it

also, my /var/lib/named/var/cache/bind is empty
there is nothing in my cache either

Amit

---

