---
title: "web server is slow to get a first connection with..."
date: 2008-07-11
forum: Networking &amp; Wireless
---

### Post by isellapples on 2008-07-11
hi, got a bit of a problem with speed - basically its taking a ridiculous amount of time to initially connect to my ubuntu (apache2) webserver (sometimes upto 5 mins of trying), but once you finally get connected for the first time its pretty fast. I've checked active connections and logs, dont think theres anything unusual going on in them, and its got very low traffic on it at the moment

heres the details (not sure what is important to know...)

Ubuntu 8.04
apache2
dynamic dns using ddclient and Zoneedit - 3 dns sites (NY, TX and Germany)
guarddog firewall
8Mb broadband
simple html welcome page - database lookups etc are on later pages
server is behind a router, but setup on PPP Half Bridge which (I think) creates the illusion there is no router...

at first it seems like its the dns lookup thats running slow, but theres no difference if you type the ip address directly into the address bar....

---

### Post by AliTabuger7 on 2008-07-11
It does sound like its some kind of dns thing, although I cannot imagine what if IP's do the same thing.

Have you tried doing "localhost"/"127.0.1.1" from the host?

Does it matter what webpage you use to get the initial connection?

---

### Post by isellapples on 2008-07-11
yep, those work fine. Its also connected to a LAN and all the computers on that can connect to it fine as well. 

and no it doesnt matter which page you hit first, if and when you finally manage to get it then its all fine. But since ive posted this thread, ive been remote desktop-ed into my uni network testing it and i havent managed to get any connection at all which is a new low.


EDIT: the site is zionic.co.uk, 89.242.89.208 . if anyone could test, see if they can connect, and let me know how fast it is(nt) i would really appreciate it as i can only actually test it from one other location, which isnt the best!

---

### Post by isellapples on 2008-07-11
urgh, i made an absolute SCHOOLBOY error. I went and added a computer to the DMZ, and it appears the router kept redirecting traffic to that instead of the server on the PPP half bridge. Disabled the DMZ and i think its all working fine now (again, would appreciate it if someone else could test and let me know... link in the above post)

---

### Post by AliTabuger7 on 2008-07-12
It does not seem that you have this fixed yet. I'm in the US, so I was expeciting it to load slow, but it's almost not at all. It's been about 2 mintues and still hasn't.

I ran a traceroute and this is what I came up with
> 12  gig-5-1-rtr001.hex.opaltelecom.net (62.24.254.46)  123.473 ms  106.181 ms  107.874 ms
13  gig-9-1-rtr001.bre.opaltelecom.net (62.24.254.9)  110.048 ms  111.785 ms  113.765 ms
14  78.151.225.34 (78.151.225.34)  109.937 ms  109.964 ms  111.710 ms
15  78.151.228.194 (78.151.228.194)  113.669 ms  113.667 ms  117.594 ms
16  89.240.63.98 (89.240.63.98)  153.090 ms  153.084 ms  154.941 ms
17  * * *
18  * * *
19  * * *
20  * * *
21  * * *
22  * * *
23  * * *
24  * * *
25  * * *
26  * * *
27  * * *
28  * * *
29  * * *
30  * * *

The last 3 went really slow and then nothing. That one cut off at 30, but i changed the prams for traceroute and it still stops at "89.240.63.98". Whois says that is a UK address, and if i had to guess your ISP.

Does guarddog edit iptables? I've ran into some troubles with the ubuntu firewall blocking some of my ports by default. Sometimes it seems that theres more than one running.

Firewall seems like the most obvious answer at this point. Something on either your router or your ubuntu computer is blocking internet traffic but not lan.

---

