---
title: "DNS Zone File Configuring"
date: 2008-07-18
forum: Networking &amp; Wireless
---

### Post by scottspencer2 on 2008-07-18
Hello,

So I'm setting up a DNS server on my Ubuntu server and it's up and running swell. 
The only thing I'm curious about is how to put ports into the IP in zone files.

In my "/etc/bind/zones/globaloffice.com.db" file, I have:

globaloffice.com.         IN     NS   ns.globaloffice.com.
www                       IN     A    ip.ip.ip.ip
me                        IN     A    ip.ip.ip.ip2

and I want to add:
wiki                      IN     A    ip.ip.ip.ip:2500

how would I implement this?

Thanks for your help!

---

### Post by kidders on 2008-07-20
Hi there,

> how would I implement this?
You can't.

DNS is for *host* name resolution ... you can't use it to name ports. The concept of a port is protocol-specific anyway, so being able to do so would be pointless.

What are you trying to achieve? Perhaps there's another way of doing it.

---

### Post by scottspencer2 on 2008-07-21
Well, I have a program that when run, goes to port 2500. So if my dns host is [www.me.com](www.me.com), I would need to go to [www.me.com:2500](www.me.com:2500), and would like to change it so I could just go to wiki.me.com

If there's really not a solution, typing in the generic :2500 is fine. Just trying to make everything more user-friendly.

---

### Post by tava0002 on 2008-07-21
If you have a firewall in front of your web servers you should be able to create a redirect rule that will redirect the port 80 traffic to this site to port 2500.  But this also depends on your network topology.

---

### Post by kidders on 2008-07-21
Yep... That, and moving your server to port 80, are your only options.

If all you're after is convenience, you *could* create a placeholder page at [http://www.me.com:80/](http://www.me.com:80/) that redirects to [http://www.me.com:2500/](http://www.me.com:2500/) ... or some variation on that theme.

---

