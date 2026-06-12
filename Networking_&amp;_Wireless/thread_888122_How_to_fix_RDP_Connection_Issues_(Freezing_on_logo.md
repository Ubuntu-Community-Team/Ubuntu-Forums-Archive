---
title: "How to fix RDP Connection Issues (Freezing on logon)"
date: 2008-08-12
forum: Networking &amp; Wireless
---

### Post by cobra741 on 2008-08-12
Hi Everyone. 

I'm sure there are quite a few people out there that already know this but after looking for weeks for a solution to the issue of RDP (Windoze Terminal Services) freezing at the windows logon screen I've finally found an answer and thought i'd share it. 

Essentially it comes down to TCP window auto-tuning.
From what i understand the rdesktop client pushes too much data through the pipe and windows throws a hissy-fit and ends up dropping the connection. 

This can quite easily be fixed by editing your /etc/sysctl.conf file and adding the following line

```
net.ipv4.tcp_window_scaling=0
```

Hope that helps some of you out as much as it helped me. 

Cheers,

---

### Post by do27 on 2010-04-23
thank you very much ...
this is my first reply in this forum.
your fix seems to work and you helps me very much, i use rdesktop always to connect win servers from my ubuntu 9.10 64 ...

executing rdesktop from cli it works ...
now i try using gnome-rdp

thanks again

---

### Post by baronKarza on 2011-03-10
Great post!
Thank you very much. It saved me a lot of headache...

---

### Post by narcisgarcia on 2012-07-12
Thanks, works for me on Lubuntu 12.04 using rdesktop (now doesn't cause kernel panic)

---

### Post by wildmanne39 on 2012-07-12
Hi, this is an old thread so it has been closed, please do not post in threads that are a year or more old, and thanks for sharing.

---

