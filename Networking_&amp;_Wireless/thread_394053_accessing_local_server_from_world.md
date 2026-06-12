---
title: "accessing local server from world"
date: 2007-03-26
forum: Networking &amp; Wireless
---

### Post by Kulgan on 2007-03-26
I have a very standard setup:

"world" -> modem -> router -> three computers

I have a server running on one of these three computers that is accessible from the others. Works fine. The issue is configuring the network to allow connections from outside. I have DMZ set up on the router to the correct local IP, in this case 192.168.0.104. And I guess that it's the NAPT that does wrong. 

I have tried several things. 
a) set "default server" to 192.168.0.1 (router's IP, would presumably forward with DMZ to 192.168.0.104).
b) set "default server" to 192.168.0.104.
c) make a new NAPT connection to 192.168.0.1
d) make a new NAPT connection to 192.168.0.104

None of the above work. 

Modem is Thompson Speedtouch 510, router d-link DI-524UP, if that helps at all. 

I quite obviously have an internet connection :D

What haven't I tried?
thanks!

-K

---

### Post by cyberdork33 on 2007-03-26
You probably need to use the "world" IP. You say that the router IP is 192.168.0.1, but that is it's IP on the LAN, it should have an IP assigned by your ISP. Look in the router config for this IP. 

Also, instead of using DMZ, you might look into only forwarding the certain ports that you need. This will allow your router Firewall to catch most of the traffic that is not wanted.

---

### Post by Kulgan on 2007-03-26
hmm... I don't think I have understood the concept of NAPT, then....

I have 
Protocol : tcp
Inside IP: 192.168.0.1(or 104)
Outside IP: 0.0.0.0
Inside Port: 80
Outside Port: 80

With that, I would expect it to take everything from 'world' and send it to the "inside IP". Or do you mean that the "inside IP" has to be what the *modem* refers to it as?

---

