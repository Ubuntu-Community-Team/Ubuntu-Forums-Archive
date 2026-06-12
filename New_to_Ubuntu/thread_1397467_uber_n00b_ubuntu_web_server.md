---
title: "uber n00b ubuntu web server"
date: 2010-02-03
forum: New to Ubuntu
---

### Post by jrobles on 2010-02-03
Greetings! This is my first post, but I've been a lurker for a few weeks.

I am fairly new to linux-based operating systems, but I have some decent experience in web development. I am trying to setup my own ubuntu web server at my work so I can eventually serve up websites from there as well. I managed to get Ubuntu installed and apache setup as well as mysql and PHP. Now I need to figure out how I can view my server from home. When I type in my servers IP addy the browser times out. Is there some additional configurations that I need to do to apache?

---

### Post by rickh57 on 2010-02-03
Is your server at work behind a firewall? If so, you'd have to get your IT department to open a port for you.

---

### Post by Hospadar on 2010-02-03
I can almost guarantee you your work network is behind a firewall, I've never worked at a place with public-internet-exposed personal machines, it would be a huge security risk unless properly managed.

One quick way to find out:
Go to a site like [http://www.whatismyip.com/](http://www.whatismyip.com/)
check the ip of your local machine, quickest way is "ifconfig" in a terminal
If the two IP's match, then your machine is exposed publicly, if the two IP's differ, then you are behind a firewall (same basic situation as a home network where all the machines are behind a router).  When the IP's are different it's because the IP the website sees is that of your network switch, and the one you see on your machine is the one given to you by your switch.  You should talk to your IT department about getting them to forward a port for you or give you a static IP so you can get at your machine publicly.  Depending on what policies they have it may be easy or impossible.  I probably wouldn't let someone do it if I was an IT admin unless they had a really good reason.

You could also host a similar site from home, port forward on your router (port 80 for http) and maybe get a dynamic dns service (from someone like dyndns.com).  I've done this at home for my fileserver/mythtv machine.

---

### Post by jrobles on 2010-02-03
looks like I am behind a firewall. I put in a request to get the server out to the public because we are looking to bring out two websites in-house and hosted locally. Which brings me to my second question. If I want to host two websites on one ubuntu box do I need a NIC card for each site that way I have two IP addresses?

---

### Post by jrobles on 2010-02-03
ok, I got the green light to have a port opened but it cant be 80, will any port work?

---

### Post by Iowan on 2010-02-03
Dunno if [this]("http://httpd.apache.org/docs/2.0/vhosts/name-based.html") will help or confuse you. I've also seen ports 81 or 82 used for servers. You'll need to include the port# when you try to access it. [Here]("https://help.ubuntu.com/community/ApacheMySQLPHP") is another help page that might be handy.

---

