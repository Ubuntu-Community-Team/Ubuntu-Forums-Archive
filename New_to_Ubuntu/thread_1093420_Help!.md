---
title: "Help!"
date: 2009-03-11
forum: New to Ubuntu
---

### Post by milanistastar on 2009-03-11
Hi!

I'm an absoulute begginer concerning Linux and Ubuntu.
I got this message while try to get into Synaptic Package Manager.
> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E: _cache->open() failed, please report.

What should I do?Please help me!

---

### Post by LowSky on 2009-03-11
just like the error says

open a terminal and type

```
sudo dpkg --configure -a
```

---

### Post by milanistastar on 2009-03-11
I've pasted it to terminal what should I do now?

---

### Post by bailbath on 2009-03-11
As you maybe a beginner you maynot know where the terminal is!
Applications-Accessories-Terminal
Then copy and paste the code as LowSky suggests.
Let us know how it goes and mark it solved if it is.
Ian

---

### Post by feelshift on 2009-03-11
Start Synaptic (it should run fine now) ;)

---

### Post by LowSky on 2009-03-11
hit enter, and then run this command

```
 sudo apt-get update && sudo apt-get upgrade
```

everything should be fine after that and your system will be up to date

---

### Post by milanistastar on 2009-03-11
I got this code..

Setting up libc6 (2.8~20080505-0ubuntu7) ...
/var/lib/dpkg/info/libc6.postinst: 263: Syntax error: "(" unexpected (expecting "fi")
dpkg: error processing libc6 (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 libc6

---

### Post by achase79 on 2009-03-11
After running the command from LowSky, you should be able to open synaptic

---

### Post by milanistastar on 2009-03-11
Everything works perfectly now!!!Thanks guys!But there'll be more n00b questions:D

---

### Post by presence1960 on 2009-03-11
> **milanistastar said:**
> Everything works perfectly now!!!Thanks guys!But there'll be more n00b questions:D

So be it. Everyone here was a noob at one time. The only dumb question is the one you do not ask.

---

