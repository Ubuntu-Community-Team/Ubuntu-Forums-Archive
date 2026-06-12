---
title: "A little problem"
date: 2011-06-01
forum: New to Ubuntu
---

### Post by joe0134 on 2011-06-01
Hey people i am having a problem im running ubuntu 11.04 but every once in a while it will black screen and log me out then i haft to log back in so im kinda loosing work what im doing.

---

### Post by Laforge129 on 2011-06-01
> **joe0134 said:**
> Hey people i am having a problem im running ubuntu 11.04 but every once in a while it will black screen and log me out then i haft to log back in so im kinda loosing work what im doing.

Sounds like your computer is automatically logging you out due to inactivity? Does this happen when your on the system or when it is idle?

---

### Post by joe0134 on 2011-06-01
no i get logged out when im not doing nothing for a while but like just i was searching the internet and a black screen came up and then it's like it restarted my laptop.

---

### Post by Laforge129 on 2011-06-01
> **joe0134 said:**
> no i get logged out when im not doing nothing for a while but like just i was searching the internet and a black screen came up and then it's like it restarted my laptop.

Have you checked the logfile for any hints to as to what is causing the problem??

[http://www.cyberciti.biz/faq/ubuntu-linux-gnome-system-log-viewer/](http://www.cyberciti.biz/faq/ubuntu-linux-gnome-system-log-viewer/)

---

### Post by joe0134 on 2011-06-01
I am in the logs files witch one should i take a look at.

---

### Post by Laforge129 on 2011-06-01
> **joe0134 said:**
> I am in the logs files witch one should i take a look at.

I would look at: 
```
/var/log/apport.log
```

---

### Post by joe0134 on 2011-06-01
> **Laforge129 said:**
> I would look at: 
```
/var/log/apport.log
```
i don;t see that

---

### Post by Laforge129 on 2011-06-01
> **joe0134 said:**
> i don;t see that

Sorry it took so long, I was doing some other stuff.   

I would just go through each directory and see what logs there are.   That is just my experience, something has to be giving an error somewhere for it to be doing that.   Check your logs first and then tell me if there are any that looks suspicious and post them here!

---

