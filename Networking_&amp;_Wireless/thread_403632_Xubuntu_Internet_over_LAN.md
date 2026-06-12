---
title: "Xubuntu Internet over LAN"
date: 2007-04-07
forum: Networking &amp; Wireless
---

### Post by userthebuntu on 2007-04-07
Hello people,

just today I installed Xubuntu 6.10 on my boxy box and everything went smoothly all the way.
However once trying to surf the web linux-style with the pre-installed Firefoxy I had to understand that I wouldn't be able to connect to the Internet just like that.

I then went to System -> Networking and put my static LAN IP and standard gateway IP.
That didn't help either. Noticeably I am able to connect to my router (which is the standard gateway btw) via telnet. That is I can access my router, configure it and everything but the router just won't give me internet access on that xubuntu box.

Does anyone have a clue? Do you need me to post more specs from file /etc/whatup/noclue/gibberish or anything similar?

Many thanks in advance and Happy Easter!

---

### Post by spd106 on 2007-04-07
Are you able to ping remote servers via ip address? e.g. ```
ping -c 4 82.211.81.186 
```(ubuntuforums.org)

If so then you are probably missing a DNS server. You can add it in network-admin on the DNS tab. Usually best to use your routers IP, though you can always use your ISPs DNS servers directly.

---

