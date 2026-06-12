---
title: "Remote IP port scan?"
date: 2007-03-17
forum: Networking &amp; Wireless
---

### Post by NJC on 2007-03-17
Surfin' tonight Ubuntu 6.06 and I see a window pop up:

xx.xx.xxx.xx (IP) is trying to access. Refuse? Allow? Of course I refuse. But wtf is that all about??

Of course I might never know if that happened in Win98 but I wonder if I've configured my ISP differently vs Ubuntu. 

Anything I need to do to batton down the hatches further in Ubuntu?

---

### Post by scxtt on 2007-03-17
is "Remote Desktop" running?  Are you on a router?

---

### Post by NJC on 2007-03-17
Hi scxtt;

It appears I did have Remote Desktop activated. I'm 3 weeks into Linux and can't recall if I set that up with intention of having family login remotely but for now I have turned it off. But it was activated ... but a password was required. 

Thanks for your speedy help!

BTW, what methods do people use to troll on other computers? :confused:

---

### Post by scxtt on 2007-03-17
i'm not entirely sure, but i've seen hits in /var/log/messages from semi-random IPs trying to connect to port 22 (ssh) ... i think some people/computers/bots will send out "requests" to standard ports (21/22/23/590*) to see if they get a reply, and then if they do will try to establish a connection ... you're generally not in a whole lot of trouble if your password is strong ...

---

