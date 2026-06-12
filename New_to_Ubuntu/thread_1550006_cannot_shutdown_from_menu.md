---
title: "cannot shutdown from menu"
date: 2010-08-10
forum: New to Ubuntu
---

### Post by al.adab on 2010-08-10
hello

all of a sudden I can neither shut down nor restart Ubuntu 10.04 from the shutdown menu (located on the top panel, on the right). On the same menu, "Hibernate" and "Suspend" seem to always work. 

If I enter *sudo halt* in terminal, the system does shut down...

I found [https://bugs.launchpad.net/ubuntu/+source/consolekit/+bug/571314](https://bugs.launchpad.net/ubuntu/+source/consolekit/+bug/571314) but I'm not sure the issue is related...

can you please help? thanks

---

### Post by al.adab on 2010-08-13
er...anyone? It now happens every now and then. Like right now...I was wondering if it doesn't occasionally shut down when something (but what exactly? I only use firefox + openoffice) is working in the background or the like...

---

### Post by dazvansgillio on 2010-08-13
I have had a similar problem. What I found was if Open office Quickstarter was running ithe computer would not shutdown. If you closed the Quickstarter it would then allow it to shutdown.
Maybe this will help you.

---

### Post by al.adab on 2010-08-13
thanks dazvansgillio 
I've disabled it. I'll post an update on this in a couple of days. 
Any idea why the Quickstarter should interfere with the shutdown menu?

---

### Post by jonnywombat on 2010-08-13
> **al.adab said:**
> thanks dazvansgillio 
I've disabled it. I'll post an update on this in a couple of days. 
Any idea why the Quickstarter should interfere with the shutdown menu?

For more info.. [https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/562027]("https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/562027")

---

### Post by al.adab on 2010-08-15
it looked like it really was the cause. Thanks!

---

