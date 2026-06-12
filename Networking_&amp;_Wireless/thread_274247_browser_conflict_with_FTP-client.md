---
title: "browser conflict with FTP-client?"
date: 2006-10-09
forum: Networking &amp; Wireless
---

### Post by mojoman on 2006-10-09
Hi,

I've run into a weird network problem with Dapper on my new computer (an Asus M2N-E with AMD64 2,2 Ghz) and my server (running on the dapper server edition).

Connectivity feels a bit off, i.e. it takes a while to connect, but once it finds what it's looking for speed is ok but if I'm running an ftp-client connected to my server I can't get on the Internet using a brower at the same time (any browser, or at least the three I tried). However, I can ping external sites from the terminal. :confused:  What's weird is that I can ping for example [www.google.com](www.google.com) but I can't reach it with a browser. Also, I can get on the Internet using a browser when connected to another, external ftp-site. :confused: 

I use static IP so there isn't any conflict with that. I'm using a netgear router and VDSL-connection. My network proxy is set as direct internet connection. 

Does any one have any ideas on this?

Thanks in advance
/Mojoman

---

### Post by mojoman on 2006-10-14
Thought I just say that solved the problem in case anyone with the same problem search. Turned out that the configuration for my Internet connection wasn't accurate (I had used the one Dapper set up automatically). For some reason the value for my default gateway was given as my preferred DNS :confused: . Once I changed this connectivity was much better and the programs don't conflict.
/Mojoman

---

