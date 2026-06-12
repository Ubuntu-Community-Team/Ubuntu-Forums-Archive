---
title: "hosts file not read on 14.04"
date: 2015-03-11
forum: Networking &amp; Wireless
---

### Post by ubu_Leno on 2015-03-11
Ola,

I am trying to build a computer on local network with a url already used on internet by me.

[www.example.com](www.example.com) = 195.195.195.195 on internet

I add to /etc/hosts

```
10.1.1.3 www.example.com
```

when I do  

```
host www.example.com
```

It returns IP for public and not what is in my /etc/hosts.

How do I get it for /etc/hosts to work?

---

### Post by TheFu on 2015-03-11
What does your /etc/nsswitch.conf have inside it? The order matters.```

hosts:          files mdns4_minimal [NOTFOUND=return] dns
```

"files" in the 1st position means /etc/hosts is referenced first when it comes time to lookup the name-to-ip translation.

---

### Post by ubu_Leno on 2015-03-11
I've got files first

```
hosts:          files mdns4_minimal [NOTFOUND=return] dns
```

---

### Post by ubu_Leno on 2015-03-11
interesting that is look like only some cli apps dont work.   "host"   gives public IP, "ping" and "ssh" give the ip in /etc/hosts

---

### Post by TheFu on 2015-03-11
What happens when you **ping [www.example.com](www.example.com)**?  Oops. Didn't see the prior post.
There you have it.  host is a new-fangled command - does the manpage say it ignores the nsswitch.conf settings?  If not, file a bug.

---

