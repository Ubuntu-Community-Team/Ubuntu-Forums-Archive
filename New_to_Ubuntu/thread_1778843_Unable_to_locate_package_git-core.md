---
title: "Unable to locate package git-core"
date: 2011-06-09
forum: New to Ubuntu
---

### Post by fnln on 2011-06-09
I was looking to install Git, but received this error

~$ sudo apt-get install git-core

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package git-core


I'm really new to ubuntu and can't find this error anywhere else on the internet. Everything I've read says this is what I'm meant to do. I don't even know what I'm doing wrong.

Also hi, great forum you guys have here.

---

### Post by ubudog on 2011-06-09
Hi there, welcome to Ubuntu.

What you need to do is enable the universe repository.  Go to System>Administration>Software Sources and click the check box on universe.

Then run:
```
sudo apt-get update && sudo apt-get install git-core
```

---

### Post by fnln on 2011-06-09
Yep, it turned out the updates weren't installed, thanks for the help

---

### Post by ubudog on 2011-06-09
Ah, no problem.  Glad you got it working!

---

