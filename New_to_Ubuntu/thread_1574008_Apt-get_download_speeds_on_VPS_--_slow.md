---
title: "Apt-get download speeds on VPS -- slow?"
date: 2010-09-13
forum: New to Ubuntu
---

### Post by fathom1 on 2010-09-13
Hello, new to forum, but all my google searches keep bringing me here.
Running Hardy heron on my vps and using apt-get to install packages through putty. 
I noticed the download speed indicated in the terminal was pretty slow using a public connection as compared to my home network connection. Does this download speed depend on my upload speed? 
I've been searching for information on how the data was transferred from repo to server. Judging from the vps's download speed, it looks like the path is: repo -->my computer(terminal client) --> VPS. Is that right? If so, is there any way to have the vps download straight from the repo?
 
I guess it might answer my question when I get home and use my home connection but I thought I'd ask.
 
Edit:
When I VNC into the VPS, the download speeds are upwards of 20 mbits/sec on a 1 MB file  so it must be routing data through the terminal client.

---

### Post by bodhi.zazen on 2010-09-13
> **fathom1 said:**
> Hello, new to forum, but all my google searches keep bringing me here.
Running Hardy heron on my vps and using apt-get to install packages through putty.  
I noticed the download speed indicated in the terminal was pretty slow using a public connection as compared to my home network connection.  Does this download speed depend on my upload speed?  
I've been searching for information on how the data was transferred from repo to server.  Judging from the vps's download speed, it looks like the path is: repo -->my computer(terminal client) --> VPS.  Is that right?  If so, is there any way to have the vps download straight from the repo?
 
I guess it might answer my question when  I get home and use my home connection but I thought I'd ask.

No, apt-get downloads direct to your VPS.

What technology for VPS ? My openvz and LXC VPS are as fast as the connection allows.

---

