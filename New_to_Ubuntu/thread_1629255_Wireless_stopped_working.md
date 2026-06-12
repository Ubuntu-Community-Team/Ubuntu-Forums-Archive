---
title: "Wireless stopped working"
date: 2010-11-23
forum: New to Ubuntu
---

### Post by cameron_schultz on 2010-11-23
Hey there, I'm currently running Ubuntu 10.10, and I love it so far. However, my computer hibernated, and when I logged back in, the wireless no longer worked.  I tried to /etc/init.d/networking restart but that did not help, even after I restarted my computer. I have an Nvidia MCP67 network card, but for some reason it disabled after the hibernation. How can i restart/enable this again?

thank you in advanced :)

---

### Post by ptn107 on 2010-11-24
Sometimes it just takes a minute before it attempts to reconnect.  If it's not even trying then there's a problem.  This is most notable in laptops that suspend of hibernate.  We'll just have to add something to /etc/modules.   Can you post the output of:

```
lspci -v
```

---

