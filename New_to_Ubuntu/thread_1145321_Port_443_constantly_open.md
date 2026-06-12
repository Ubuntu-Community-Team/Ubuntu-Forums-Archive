---
title: "Port 443 constantly open"
date: 2009-05-01
forum: New to Ubuntu
---

### Post by DhulKarnain on 2009-05-01
Hello there. I'm new to Ubuntu and lovin it. Except for one issue.
Various port checking online service (grc.com, canyouseeme.org and auditmypc.com) all report my **port 443 (https) is open**. 
Well i suspect it has something to do with my router who has been poorly preconfigured by my dsl-iptv provider. anyway, in windows i was able to configure my norton firewall to close that port down, except for communication to addresses i explicitly allow.
However, here in ubuntu i used ufw to deny access to that port but still all the above websites report it is open. i even tried this iptables command:
```
iptables -t nat -I PREROUTING -m tcp -p tcp --dport 443 -j DROP
```but to no avail - the port remains open. what am i doing wrong and how do i close that sensitive port? 
Thanks, guys.

---

### Post by spiderbatdad on 2009-05-01
well if your router is forwarding the port, that is probably why it is reported open. To see if your machine is actually listening:
```
sudo netstat -ntulp
```

---

### Post by DhulKarnain on 2009-05-02
OK, so I've found the solution through windows and I'm posting it here if anyone has the same issue with the Thomson SpeedTouch 780

here it is --> [http://www.speedtouch.net.nz/forum/topic.asp?TOPIC_ID=455](http://www.speedtouch.net.nz/forum/topic.asp?TOPIC_ID=455)  (the last post)

basically it involves typing a few commands in windows telnet (just remember if you're on vista you first have to install telnet through windows features in control panel)

grc.com now shows all ports are in stealth. thanks for the help offered.

---

### Post by perspectoff on 2009-05-02
> **DhulKarnain said:**
> OK, so I've found the solution through windows and I'm posting it here if anyone has the same issue with the Thomson SpeedTouch 780

here it is --> [http://www.speedtouch.net.nz/forum/topic.asp?TOPIC_ID=455](http://www.speedtouch.net.nz/forum/topic.asp?TOPIC_ID=455)  (the last post)

basically it involves typing a few commands in windows telnet (just remember if you're on vista you first have to install telnet through windows features in control panel)

grc.com now shows all ports are in stealth. thanks for the help offered.

Why would you want to close port 443?

That is the port for https, which is the secure channel for internet communications. An Internet browser usually uses port 80 for insecure communications (http) and port 443 for secure communications (https).

If you close that port, much of your browser's traffic will stop.

---

### Post by Alterax on 2009-05-02
I'm not sure how Windows was worked in as a solution.  The problem is your router, not your computers.  I've yet to see a router that runs Windows.

The problem was that you router assumed that you were hosting a secure webpage from within your network.  Hence TCP port 443--the default and standard for HTTPS:// traffic.  If it wasn't forwarding that port to one of your computers, not a problem.  Or if the computer wasn't set with Apache, IIS, or lighthttpd to listen to port 443, then again, no problem.  

Either way, happy to hear you've got it fixed.

---

