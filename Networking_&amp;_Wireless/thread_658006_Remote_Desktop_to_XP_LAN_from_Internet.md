---
title: "Remote Desktop to XP LAN from Internet"
date: 2008-01-04
forum: Networking &amp; Wireless
---

### Post by jmvidalvia on 2008-01-04
There's a lot of information on how to connect to remote descktops within the LAN or over Internet, but most of them regarding ONE box. But, 
¿which would be the best way to get a remote desktop form Internet to any of the PC's with XP in a LAN?
There's a Debian server in that LAN, with Samba, ssh, etc..
Thanks a lot!

---

### Post by ubutufan on 2008-01-04
> **jmvidalvia said:**
>  the best way to get a remote desktop form Internet to any of the PC's with XP in a LAN?
There's a Debian server in that LAN, with Samba, ssh, etc..
Thanks a lot!

Not sure if I understand what your question is. If you want to connect to a given machine which is part of a LAN, you need to open up a port in the router. If it is a XP machine then it communicates over port 3389. You declare this port as accessible to the router configuration and then you define which IP it should forward the remote connection request.
Again I am not sure I understand your question

---

### Post by jmvidalvia on 2008-01-04
Yes, you are right.
But I have 30 PC to eventually connect to: I can not forward 30 ports in my router.
That's my problem...
Thanks!

---

### Post by ubutufan on 2008-01-04
I will give you the guidelines for two machines. You expand to as many as needed.

First all machines must obtain manual IP and need to be under the same subnet Example
machine 1 has IP 100.100.100.1
machine 2 has IP 100.100.100.2

In your router now
machine 1
open (for example) port 50001. Make it point at port 3389 at IP 100.100.100.1
machine 2
open (for example) port 50002. Make it point at port 3389 at IP 100.100.100.2

and so on and so forth.

It should get you working. You just need to know which machine has what IP

I should also mention that if you want to connect to a specific machine (say machine2) you give this address

xx.yy.zz.ww:50002

xx.yy.zz.ww is the actual IP of your lan


Let me know if this is clear to you

---

### Post by jmvidalvia on 2008-01-04
Thank you! Absolutely clear.
But I am sorry to insist: my router can just redirect 12 ports, no more, and I have 30 PC's.
What about Iptables...?
Thanks again!

---

### Post by ubutufan on 2008-01-04
You then need to install VPN to the 30 XP machines.

This will allow you to connect to the one you choose

---

### Post by ubutufan on 2008-01-04
Try the TightVNC

---

### Post by jmvidalvia on 2008-01-04
I was afraid VPN was one of the solutions...:(
I tried VPN in the past with linux with a lot of efforts and few results.
Thanks a lot again for your help.

---

### Post by metoor30 on 2008-01-04
You could always open a port for remote desktop to one XP machine and then use that XP machine to either remote desktop or VNC to the other 29 machines.  It seems like a backwards way to do things, but it should work.  

Another way, if you cannot port forward, is a VPN.  I would highly recommend a VPN because it is not a great idea to have an XP machine accessible in anyway from the internet.  Sonicwall has some cheap solutions that are very robust for an office or home gateway.  I have used a TZ170 for a consulting job that I did and it worked great.  If cost is a concern, you can always setup a linux box on your LAN that could act as a VPN server.  You just have to make sure that your router can forward ipsec.

---

### Post by jmvidalvia on 2008-01-04
> **ubutufan said:**
> Try the TightVNC
Does it make any difference using TightVNC or VNC viewer?
It seems that port forwarding problems are the same?
Aren't they?

---

### Post by jmvidalvia on 2008-01-04
> **metoor30 said:**
> You could always open a port for remote desktop to one XP machine and then use that XP machine to either remote desktop or VNC to the other 29 machines.  It seems like a backwards way to do things, but it should work.
That's what I was trying to do, but with my Debian server instead of a XP box.

> **metoor30 said:**
> Another way, if you cannot port forward, is a VPN.  I would highly recommend a VPN because it is not a great idea to have an XP machine accessible in anyway from the internet.  Sonicwall has some cheap solutions that are very robust for an office or home gateway.  I have used a TZ170 for a consulting job that I did and it worked great.  If cost is a concern, you can always setup a linux box on your LAN that could act as a VPN server.  You just have to make sure that your router can forward ipsec.
Thanks a lot for the recommendation: I'll take a look.

---

### Post by metoor30 on 2008-01-04
By the way, neither tightVNC nor VNC are encrypted.  It would not be a good idea to use this to connect to computers over the internet without some kind of ssh tunnel or VPN.  FYI.

---

### Post by jmvidalvia on 2008-01-04
> **metoor30 said:**
> By the way, neither tightVNC nor VNC are encrypted.  It would not be a good idea to use this to connect to computers over the internet without some kind of ssh tunnel or VPN.  FYI.
;)

---

### Post by ubutufan on 2008-01-04
I have used extensively in my office TightVNC only. There are no issues.

---

### Post by metoor30 on 2008-01-04
> **ubutufan said:**
> I have used extensively in my office TightVNC only. There are no issues.

Within the office is fine, I used it in the past until I started using something encrypted for security reasons.  Any VNC, unless it is encrypted (ultraVNC), is insecure.  It is not meant to be an Internet facing service.  You can have it up and working fine, but it is a huge security hole to have this available to the Internet.

---

### Post by jmvidalvia on 2008-01-07
Solved!
```
vncviewer -via user@host localhost:0
```

:)

---

