---
title: "remote ssh access"
date: 2008-02-29
forum: Networking &amp; Wireless
---

### Post by slacker116 on 2008-02-29
I have been trying setup a remote ssh server on one of my home computers, and i am having issues connecting from my external IP I am behind a NAT router, and i have forwarded the correct port(22) on my router to the right host, i can see my port 22 is open at canyouseeme.com/grc.com

I can connect fine in my own network, but i can't seem to connect from outside, it always gives the error 'connection refused' I think it is my router, which is an Actiontec M1000, but i don't what else i can do, i've tried setting my host as a DMZ server, but that doesn't even work, does anyone have ideas?

---

### Post by Mr. C. on 2008-02-29
What is your ListenAddress in sshd_config ?

---

### Post by slacker116 on 2008-03-01
its 22, because i can connect to it inside my network, but just not outside, so i would think that it's a router problem?

---

### Post by Mr. C. on 2008-03-01
That's the Port, not the IP (ListenAddress).  What's the ListenAddress?

---

### Post by xyblor on 2008-03-02
I'm having the exact same problem. 
When I ssh from within the LAN, I can login.
When I try to connect from a remote machine I get "connection refused".

The default sshd_config (/etc/ssh/sshd_config) does not specify any ListenAddress. The manpage for sshd_config says "The default is to listen on all local addresses". 

I read somewhere that you have to use iptables, but I don't know how.

---

### Post by Oldsoldier2003 on 2008-03-02
> **slacker116 said:**
> I have been trying setup a remote ssh server on one of my home computers, and i am having issues connecting from my external IP I am behind a NAT router, and i have forwarded the correct port(22) on my router to the right host, i can see my port 22 is open at canyouseeme.com/grc.com

I can connect fine in my own network, but i can't seem to connect from outside, it always gives the error 'connection refused' I think it is my router, which is an Actiontec M1000, but i don't what else i can do, i've tried setting my host as a DMZ server, but that doesn't even work, does anyone have ideas?

you need to port forward 22 from your router to your ssh server. The result from grc.com is them banging off of the actiontec , not your ssh server.

---

### Post by xyblor on 2008-03-02
> **Oldsoldier2003 said:**
> you need to port forward 22 from your router to your ssh server.

Didn't we already do that?

[QUOTE=slacker116] i have forwarded the correct port(22) on my router to the right host[/QUOTE]

---

### Post by Oldsoldier2003 on 2008-03-03
> **xyblor said:**
> Didn't we already do that?

unless he fiddled with the ssh configuration... if he's getting connection refused its coming from his router because default iptables wont stop the connections. I can say this with a pretty high level of confidence because i just set up ssh, denyhosts, and bastille yesterday on the lLAMP server on my home network. eveerything worked fine until i started adding iptable rules.

---

### Post by xyblor on 2008-03-04
It works for me now. The "solution" was to just try it from a machine that was actually remote. I guess my router doesn't allow those so-called "U-Turn" connections. No messing with iptables or firewall was required.

---

