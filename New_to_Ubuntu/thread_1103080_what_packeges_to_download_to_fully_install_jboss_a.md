---
title: "what packeges to download to fully install jboss and use it"
date: 2009-03-22
forum: New to Ubuntu
---

### Post by Dalal on 2009-03-22
hi everybody
i want to deploy a site (servlets,jsp,ejb3) on jboss 4 AS .
i have been using windowx xp and every thing is simple (double click and every thing is done for u )

but i need to use this with ubuntu 8.10 intrepid ibex so 
i found many packages having jbosss in their  names but which to download (all or some ).
please help me 

REGARDS
thnx in advance.

---

### Post by yeats on 2009-03-22
Have you tried to install just jbossas4?

---

### Post by llamabr on 2009-03-22
I'd probably do an

```
sudo apt-get install jbossas4
```

and go from there.  apt will fill in the dependencies, and you can install additional packages as you find applications that you desire.

---

### Post by tinny on 2009-03-23
Ive been trying to install this jbossas4 package as well with no luck, I now know why!

From the readme file of the package

/usr/share/doc/jbossas4/README.Debian

> 
jbossas4 is currently in a very alpha stage of packaging. I can be used
to build other libraries depending on JBoss like libhibernate3-java but
it is not complete and cannot be used as an application server yet.


!?!?!?! What is this package do in a stable release??? Disappointing

---

### Post by tinny on 2009-03-23
I am inquiring about this problem over hear... [https://answers.edge.launchpad.net/ubuntu/+source/jbossas4/+question/65115](https://answers.edge.launchpad.net/ubuntu/+source/jbossas4/+question/65115)

---

