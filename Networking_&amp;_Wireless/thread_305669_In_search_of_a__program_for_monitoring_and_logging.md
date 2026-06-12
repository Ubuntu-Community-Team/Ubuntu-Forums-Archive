---
title: "In search of a  program for monitoring and logging network traffic."
date: 2006-11-23
forum: Networking &amp; Wireless
---

### Post by NickWilsdon on 2006-11-23
Hi all,

I'm looking for a way of monitoring and logging the traffic going in/out of our network. I need to see this by each internal IP/machine and save the figures daily. 

I've been trying a whole load of different programs (vnstat, darkstat, traffic-vis etc.). None seem to log the data we need (preferably presented via a web page). 

Zabbix looks interesting but I'm having no luck setting that up. My best hope was bandwidthd - but that path has ended at the moment (Syntax Error "syntax error" on line 13 when trying to start).

Has anyone got any other suggestions for applications?

Thanks!

---

### Post by tommcd on 2006-11-24
Have you tried just using netstat? I just read an article on it and it seems like it would suit your needs. The traffic can be saved to a text file like this:
netstat --inet -a -c > netstat.txt
See this article:
[http://linuxplanet.com/linuxplanet/tutorials/5633/1/](http://linuxplanet.com/linuxplanet/tutorials/5633/1/)

---

