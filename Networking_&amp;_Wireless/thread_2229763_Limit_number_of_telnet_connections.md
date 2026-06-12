---
title: "Limit number of telnet connections"
date: 2014-06-15
forum: Networking &amp; Wireless
---

### Post by Marius_Hov_Lauritz on 2014-06-15
Hello everyone!

I'm running Ubuntu server as a router to my network, and it's brilliant!

Because I'm a retro computer fan, I'm running my old BBS on an Amiga Computer behind the Ubuntu firewall (which is by the way written manually with IPTABLES).
There is a standard forward of port 23 back to the local IP-address to the Amiga.

The problem lately is that infected computers out there are acting like zombies trying to access computers around the world by using telnet looking for weak spots. The problem here is that every time a computer out there tries this, it triggers one of the telnet-nodes at the Amiga, and if this happens to frequently, the nodes will crash.

I have recorded some attempts with tcpdump on the server, and tried to access the IPs that's knocking on my door. They seem to be private persons with WAN access to modems with standard passwords and even companies with standard passwords where I'm able to even view their surveillance cameras! (wtf?!) :)

So my question is... is there any possible way to limit telnet connections pr IP for a given time? Let's say only one open telnet connection pr IP, and if this happens too frequently: ban the IP.

I can view the attempts on the Amiga and I can see lines like "root root" "guest guest" and even some lines starting with "\\X\xxxxx\xxxx" which might be hacking attempts on old Windows servers or something like that...

---

