---
title: "OpenVPN working, what next?"
date: 2006-09-19
forum: Networking &amp; Wireless
---

### Post by dwight on 2006-09-19
I have installed OpenVPN and am able to open a tunnel to a remote host. I am also able to ping via the remote host:
```
> ping -I tun0 www.google.com 
PING www.l.google.com (64.233.183.103) from 192.168.1.66 tun0: 56(84) bytes of data.
64 bytes from 64.233.183.103: icmp_seq=1 ttl=239 time=2060 ms
64 bytes from 64.233.183.103: icmp_seq=2 ttl=239 time=1115 ms
64 bytes from 64.233.183.103: icmp_seq=3 ttl=239 time=111 ms
64 bytes from 64.233.183.103: icmp_seq=4 ttl=239 time=60.1 ms

```
The question is, how do I proceed from here? What do I need to do in order to have my requests sent via tun0 not eth0 as they are now if I do not supply the -I parameter to ping?

---

### Post by JohnW on 2006-09-22
```
$ route
```
What does that display?

What are the ip addresses of your two networks? Can you ping a machine on the other network?

---

### Post by dwight on 2006-09-22
Thanks for your reply, but I have managed to sort things out. I had forgotten to add the machines I need to acces to /etc/hosts. Now that I've done that everything works like a dream. :)

---

