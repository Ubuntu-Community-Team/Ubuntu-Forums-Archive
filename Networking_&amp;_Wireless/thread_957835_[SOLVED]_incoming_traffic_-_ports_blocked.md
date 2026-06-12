---
title: "[SOLVED] incoming traffic - ports blocked?"
date: 2008-10-24
forum: Networking &amp; Wireless
---

### Post by jacksmash on 2008-10-24
Hi,

I've set up apache on my machine, but am unable to accept incoming HTTP traffic. My ISP is Eastlink, and I'm guessing they have blocked all ports for incoming traffic. However, and this is where my question is, if I run uTorrent on a random port, and check this port on canyouseeme.org, it says it can see my service on that port. But as soon as I turn uTorrent off, it can no longer see my service.

So, if my ports are indeed blocked for incoming traffic, then how is it that uTorrent gets around that? And if it can, then I must be able to get around it for HTTP traffic (even if I can't use port 80), no?

Thanks for any insights.

---

### Post by pdwerryhouse on 2008-10-24
My guess is that they are only blocking port 80; my ISP does the same. Try running apache on a different port - 8080, for example.

Obviously this isn't an ideal solution, but short of convincing your ISP to open port 80, there's not much you can do.

---

### Post by jacksmash on 2008-10-24
Ok, well, I tried that and it still doesn't work. Maybe there's something else I'm doing wrong. If my computer is behind a router, is it still safe to try to connect via the IP address detected at whatismyipaddress.com ??

---

### Post by Iowan on 2008-10-24
You set up the router to port-forward to your server?

---

### Post by jacksmash on 2008-10-24
Yes, I've set up port forwarding for HTTP on port 2080, and set up apache on 2080 as well. I know it's set up correctly because I can access it from a machine on my network, but not from outside. canyouseeme.org reports:

Error: I could not see your service on xxx.xxx.xxx.xxx on port (2080)

I understand that most ISP's only block common ports, but maybe mine is different? Eastlink is pretty big out where I am, so I'm sure someone else has come across this. I'll keep searching on google, but so far, no luck.

Cheers.

---

### Post by jacksmash on 2008-10-24
Nevermind!!! I forgot to click the checkmark on my router settings :(

Looks like it's working. Thanks!

---

