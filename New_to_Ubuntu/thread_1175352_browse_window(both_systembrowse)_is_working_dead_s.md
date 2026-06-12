---
title: "browse window(both system/browse) is working dead slow after upgrading to Ubuntu 9.04"
date: 2009-06-01
forum: New to Ubuntu
---

### Post by mokkai on 2009-06-01
browse window(both system/browser wise) is working dead slow after upgrading to Ubuntu 9.04

today i have upgrade to ubuntu 9.04 (through online)
before that everything is fine
but after upgrading my system browse window is taking 30 seconds to open

for example 
if i write something in gedit text editor after that 
i try to save (click file>save button) then my browse window opening after 30 secs .

the same thing happen for, if i click browse button in firefox (to upload any file) 

any solution ?

---

### Post by danilopopeye on 2009-06-01
I have the same problem and can't find a way to fix it :(

---

### Post by kingaaronj on 2009-06-02
This has been fixed before... There's a package that needs to be removed and I can't remember it for the life of me!

---

### Post by kingaaronj on 2009-06-02
Ah found it.  Remove the "tracker" package.  That's what fixed it for me before.  Interestingly it's only a problem on my XPS 1530 running Jaunty 64bit.  My Dell Vostro 200 doesn't have the same problem and it's running Jaunty 64bit as well.

```
sudo apt-get remove tracker --purge
```

---

### Post by mokkai on 2009-06-03
thanks to all of your reply 

yesterday my update manager ask me to update a package 
name as cron 
here is the synaptic history 

------
Commit Log for Tue Jun  2 07:47:50 2009
Upgraded the following packages:
cron (3.0pl1-105ubuntu1) to 3.0pl1-105ubuntu1.1
------

after this the problem has been solved automaticaly
i don't know what happened....

but now i am fine ...

---

