---
title: "need some help with ssh and xdmcp"
date: 2006-11-20
forum: Networking &amp; Wireless
---

### Post by mbirkis on 2006-11-20
hi!
I just got my ssh tunnel working, like this:
ssh -R 2222:localhost:22 address.to.tunnelpoint

then i just from my work computer do:
ssh address.to.tunnelpoint
and to establish the tunnel i do from the tunnelpoint:
ssh localhost -p 2222

the result is i get access to my home computer from my work computer.

the one thing i would like is to get xdmcp running through this tunnel, but i am clueless as to how to get this to work.

Help would be much appreciated! :)

---

### Post by dmizer on 2006-11-20
how about vnc instead:
```
vncviewer -via account@ipaddress localhost:0
```

---

### Post by mbirkis on 2006-11-20
thank you for the reply.

so all i have to do is install vnc server on my home computer, and from the ssh tunnel apply the code in your reply.

i will try the vnc solution, but i really wan't to try using xdmcp so that when i log in from gdm on my laptop i get my desktop from my home computer.

---

