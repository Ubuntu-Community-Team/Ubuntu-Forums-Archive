---
title: "Where is my current running jboss instance home"
date: 2009-08-18
forum: New to Ubuntu
---

### Post by kwakhyok on 2009-08-18
Hello,
I tried to run a jboss server from a directory I referred and found that another jboss instance was already running when my ubuntu starting up. Is there any command that I can use to check where is this instance's home?

---

### Post by kpkeerthi on 2009-08-18
Look in System -> Admin -> System Monitor or **gnome-system-monitor** from command line. I guess it would be listed as **Java**. You should be able to kill the process from GNOME system monitor

---

### Post by kwakhyok on 2009-08-18
Hi, kpkeerthi,
thanks for your reply. I didn't find any java-related process listed in system-monitor. However, when i type [http://localhost:8080](http://localhost:8080) it just shows jboss is running.

---

### Post by kwakhyok on 2009-08-18
> **kwakhyok said:**
> Hi, kpkeerthi,
thanks for your reply. I didn't find any java-related process listed in system-monitor. However, when i type [http://localhost:8080](http://localhost:8080) it just shows jboss is running.

Well, I found the problem. I cleaned the cache and it disappeared.

Thanks.

---

