---
title: "[SOLVED] RAM editing program"
date: 2008-12-28
forum: New to Ubuntu
---

### Post by hyperhopper on 2008-12-28
i know that in windows, there are some programs like Poke, cheat engine and a few others,that let you edit values in ram (often to freeze the value of say, amunition  in games)

is there a program that is similar for linux?

---

### Post by scorp123 on 2008-12-29
> **hyperhopper said:**
> is there a program that is similar for linux? I'd suggest the "GNU Debugger", or "gdb" for short. To install it: ```
sudo apt-get install gdb
```

Red Hat's web site has a tutorial on "gdb", but what they write there should be also valid for Ubuntu:

"Examining Memory"
[http://sources.redhat.com/gdb/current/onlinedocs/gdb_10.html#SEC71](http://sources.redhat.com/gdb/current/onlinedocs/gdb_10.html#SEC71)

---

### Post by Rhubarb on 2008-12-29
There is also a nice terminal based app called scanmem.
This will let you find numbers in ram (such as ammo / health) in most games, and let you change the value.

You get get it thus:
```
sudo aptitude install scanmem
```

There are a few nice tutorials online that tell you how to use the app.

---

### Post by scorp123 on 2008-12-29
> **Rhubarb said:**
> There is also a nice terminal based app called scanmem. Nice! Didn't know that one :D

---

### Post by hyperhopper on 2008-12-29
A can i use apt-get instead of aptitude

B whats the difference between apt-get and apptitude

C is there one with a GUI like poke does?

D if i were to run a windows one (like poke or cheatengine) in wine, would it work?

---

### Post by snova on 2008-12-29
> **hyperhopper said:**
> A can i use apt-get instead of aptitude

B whats the difference between apt-get and apptitude

[http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)

> D if i were to run a windows one (like poke or cheatengine) in wine, would it work?

No.

---

### Post by hyperhopper on 2008-12-29
i got another real stupid question.......

cheatengine is open source..........

would there be a way to take the source and make it work in linux?

---

### Post by snova on 2008-12-29
> **hyperhopper said:**
> i got another real stupid question.......

cheatengine is open source..........

would there be a way to take the source and make it work in linux?

You'd end up pretty much rewriting it.

---

### Post by hyperhopper on 2008-12-29
lol.

well, thanks! 

/thread

---

