---
title: "Please help, aMule won't start"
date: 2008-12-26
forum: New to Ubuntu
---

### Post by AlmoG on 2008-12-26
Running from terminal gives this output:

> 
Initialising aMule
Checking if there is an instance already running...
There is an instance of aMule already running
Raising current running instance.


I can see no aMule running on any of the panels and i have tried:
'ps -ef | grep amule'
and still nothing...

This is a fresh installation of aMule from Applications --> Add/Remove... --> aMule

I'm using ubuntu 8.04

can anyone help?

---

### Post by taurus on 2008-12-26
```
ps -A
```

---

### Post by AlmoG on 2008-12-26
OK this is weird... I have removed amule and deleted the .aMule directory from my home folder, restarted and installed again, now it works.

thanks anyhow :)

---

