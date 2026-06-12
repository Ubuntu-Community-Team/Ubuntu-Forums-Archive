---
title: "access the web server from mutiple ip addresses"
date: 2013-10-02
forum: Networking &amp; Wireless
---

### Post by 2600Sam on 2013-10-02
first time posting here and I hope this is the right area to post this question.

I running Ubuntu server 12.04.3 LTS on a headless box I use putty on a windows box to do everything on the server.
Our network here is sectioned off into 5 different IP address for the different areas (i can't change them)

I have 2 network cards installed setup for dynamic ip address (I tried static....epic fail there but I have worked around it) and 5 virtual ip address configured so all the other areas can access the samba and we can ssh into the server from everywhere!

IP address for eth1:   192.168.60.178 (the wireless network)
IP address for eth0:   192.168.1.13 (the main network)

IP address for eth0:0: 192.168.100.101(statics here down)
IP address for eth0:1: 192.168.13.101
IP address for eth0:2: 192.168.50.101
IP address for eth0:3: 192.168.1.101
IP address for eth0:4: 192.168.60.101

No we want to set up the web server with a web page to make the most common area easily accessible and this is where I'm having a problem only the people on the .1.### network can type in the server name in their web browser and get access to the web page, the other networks have to type in the ###.101 ip address to access the web page.
I would like to make it so all the different ip address areas can just type in the server name to gain access so I don't have to run around and tell everybody what ip address to use (because I'm lazy like that)
can this be solved with the server or is this a problem with the routers?
any help would be greatly appreciated!!

---

### Post by 2600Sam on 2013-10-13
anybody have any ideas to help me on this?

---

