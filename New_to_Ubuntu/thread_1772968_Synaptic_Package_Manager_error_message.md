---
title: "Synaptic Package Manager error message"
date: 2011-06-01
forum: New to Ubuntu
---

### Post by CaptainSnowman on 2011-06-01
I just tried opening the Synaptic Package Manager for the first time after installing Ubuntu LTS 10.04 yesterday and got the following error message:


E: Type ‘“deb’ is not known on line 54 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialogue to correct the problem.
E: _cache->open() failed, please report.


Could anyone help me please? :)

---

### Post by TeoBigusGeekus on 2011-06-01
```
gksu gedit /etc/apt/sources.list
```
What's line 54?

---

### Post by CaptainSnowman on 2011-06-01
Line 54 is:

“deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main”

---

### Post by TeoBigusGeekus on 2011-06-01
Automatix??!!?? Edgy??!!??

Delete the line immediately, save, exit, run
```
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get update
```
and post back with the outcome.

---

### Post by CaptainSnowman on 2011-06-01
it opened cheers :)

---

