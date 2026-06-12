---
title: "How to I listen to port 23 locally?"
date: 2007-06-17
forum: Networking &amp; Wireless
---

### Post by barney_1 on 2007-06-17
Hi there,

I'm trying to run a program called TWXProxy through wine.  It needs to be able to listen to 127.0.0.1:23 but when I start the program I get: "Unable to bind a listening socket on port 23".

When I run nmap --open 127.0.0.1 I get:
```
Starting Nmap 4.20 ( http://insecure.org ) at 2007-06-17 11:30 CDT
Interesting ports on localhost (127.0.0.1):
Not shown: 1687 closed ports
PORT     STATE SERVICE
22/tcp   open  ssh
80/tcp   open  http
111/tcp  open  rpcbind
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
608/tcp  open  sift-uft
631/tcp  open  ipp
2049/tcp open  nfs
6543/tcp open  mythtv
6544/tcp open  mythtv

Nmap finished: 1 IP address (1 host up) scanned in 0.187 seconds

```

How can I open up port 23 for local listening on address 127.0.0.1? (I'm running feisty)

Thanks!

---

