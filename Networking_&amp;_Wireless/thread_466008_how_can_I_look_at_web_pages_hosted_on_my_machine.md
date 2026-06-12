---
title: "how can I look at web pages hosted on my machine"
date: 2007-06-06
forum: Networking &amp; Wireless
---

### Post by d.j.schroeder on 2007-06-06
I am using Ubuntu 6.06 and it is running Apache2 and serves a couple of different web pages using name based virtual servers.  I can see the sites no problem from computers outside of my own network so I know it is working.  But, I'd like to be able to see them from the machine that is hosting the pages itself.  In Firefox I can get my default page with [http://127.0.0.1](http://127.0.0.1) but I can't figure out what to enter to be able to get to the other pages.

Suggestions?

---

### Post by pbw on 2007-06-06
[http://localhost/~user/](http://localhost/~user/) should work.

---

### Post by d.j.schroeder on 2007-06-07
It just gives me 404 when I do that.

---

### Post by Mr. C. on 2007-06-08
Your name-based virtual hosts require ... hostnames, not IP addresses.

Let say you have a virtual host named blog.example.com, and your server's IP is 10.0.0.1.  Add blog.example.com to your /etc/hosts file, with your system's LAN (not WAN) IP address, or 127.0.0.1 if you're client and server are the same.  Something like either of these examples:

10.0.0.1        blog.example.com 
127.0.0.1      blog.example.com

Change the IPs as appropriate. 

Then, clients on this machine will be able to correctly translate hostnames to IP, and the URIs will have the virtual host name, so apache will know which virtual host to use.

MrC

---

### Post by d.j.schroeder on 2007-06-08
That did it.  Thanks.

---

