---
title: "What is runlevel?"
date: 2010-04-03
forum: New to Ubuntu
---

### Post by karthick87 on 2010-04-03
I have typed runlevel in terminal and it shows the following.What it mean?and what is runlevel?

```
karthick@Learners-desktop:~$ runlevel
N 2
```

---

### Post by TheNerdAL on 2010-04-03
This link might help: [http://en.wikipedia.org/wiki/Runlevel](http://en.wikipedia.org/wiki/Runlevel)

---

### Post by 3rdalbum on 2010-04-04
I don't think Ubuntu actually uses runlevels anymore. I've certainly never needed to use them.

---

### Post by karthick87 on 2010-04-04
How to change the runlevels?

---

### Post by abeisgreat on 2010-04-04
> **3rdalbum said:**
> I don't think Ubuntu actually uses runlevels anymore. I've certainly never needed to use them.

It uses them to the extent that it changes them during boot, I think, and I'd assume the old 0 for shutdown, 1 for single user (that might be what ubuntu does in recovery mode) and such still apply (Thats for Fedora 2, so I'm probably wrong). But as for using them, I've never had to either.

> **getyourkarthick said:**
> How to change the runlevels?

Not only do you not need to, but you probably shouldn't mess with them. I could imagine it breaking your current session.

---

### Post by NightwishFan on 2010-04-04
This command shuts down your machine. I think it is a remnant of Unix-philosophy.
```
init 0
```

---

