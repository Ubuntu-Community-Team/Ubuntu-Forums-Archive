---
title: "Run on Proxy on localhost"
date: 2008-12-04
forum: New to Ubuntu
---

### Post by sharpdust on 2008-12-04
Hello,

I have a proxy server that I would like all my traffic through my browser (Firefox) to run through. I am doing this because I want that proxy server to monitor all the HTTP traffic that is running through my computer.

I set up the proxy server to have it's host be "localhost", port 8080.
That works.

Then I tell Firefox to do the same thing under 
Edit--> Preferences--> Advanced--> Network--> Settings--> Manual Proxy Configuration 
by typing "localhost" for the HTTP proxy and using port 8080.

However, when I actually try to load a page it keeps timing out. What am I doing wrong here.

---

### Post by DGortze380 on 2008-12-04
> **sharpdust said:**
> Hello,

I have a proxy server that I would like all my traffic through my browser (Firefox) to run through. I am doing this because I want that proxy server to monitor all the HTTP traffic that is running through my computer.

I set up the proxy server to have it's host be "localhost", port 8080.
That works.

Then I tell Firefox to do the same thing under 
Edit--> Preferences--> Advanced--> Network--> Settings--> Manual Proxy Configuration 
by typing "localhost" for the HTTP proxy and using port 8080.

However, when I actually try to load a page it keeps timing out. What am I doing wrong here.

sounds to me like you've told your proxy that it's a proxy listening on 8080 ... and your client that IT is the proxy listening on 8080.

---

