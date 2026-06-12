---
title: "PPPoE"
date: 2008-11-17
forum: Networking &amp; Wireless
---

### Post by CMR_98823 on 2008-11-17
Why is this so difficult to configure on Ubuntu?

I ran terminal, sudo pppoeconf.

It's still not connecting. Is there a reason why Ubuntu is so limited on how much you can do with network configuration.

---

### Post by sirjoebob on 2008-11-18
What version are you running. I believe that PPPoE setup in 8.10 is supposed to be a snap with the built in network manager.

---

### Post by CMR_98823 on 2008-11-18
> **sirjoebob said:**
> What version are you running. I believe that PPPoE setup in 8.10 is supposed to be a snap with the built in network manager.

Sorry, I'm running 8.10...and I'm not finding anywhere a GUI to set up PPPOE.

---

### Post by superprash2003 on 2008-11-18
post output of ifconfig from the terminal.. it maybe cause you arent getting an ip

---

### Post by sirjoebob on 2008-11-18
If you right click on the network manager icon and go to edit connections, there is an option for DSL. That may do it. I have a cable connection so i cant check for you but I imagine that would do it.

---

