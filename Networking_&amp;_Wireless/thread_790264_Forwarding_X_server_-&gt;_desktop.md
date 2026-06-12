---
title: "Forwarding X server -&gt; desktop"
date: 2008-05-11
forum: Networking &amp; Wireless
---

### Post by sDoky on 2008-05-11
Hi guys, I've got a little problem. I am trying to get to work transport of X server over ssh from my server to my desktop. I got to work transporting from my 
Ubuntu 8.04 LTS hardy to another desktop, even windows. However I'm unable to solve this problem: I have an Ubuntu 7.10 server on my local network, it is running no GUI (I think it is called init3, not sure though), I am accessing it just over ssh. Everything is just fine, however when I run 
```
# sdoky@sdoky-desktop:~$ ssh 10.0.0.10 -l sdoky -X
```and
```
# sdoky@sdoky-server:~$ gedit
# cannot open display:
# sdoky@sdoky-server:~$
```Any suggestions? Thanks

---

