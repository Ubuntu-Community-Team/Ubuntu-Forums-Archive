---
title: "Can't access admi menu on Ubuntu version"
date: 2006-11-25
forum: Networking &amp; Wireless
---

### Post by alimovz on 2006-11-25
Hello,

I have no idea what's happening, but when I run say apt-get update, it tries to connect to us.archive.ubuntu.com which is correct as that is what it has in the /etc/apt/source.list file, but it thinks that us.archive.ubuntu.com's ip address is 1.0.0.0. So it tries to connect to this ip, which of course it cannot. What the heck? Why doest it resolve to that ip? 
Everything is working, I mean I can access stuff on the internet with no problem, I can ping anytning, it's only the apt utility that is freaking out? Do you guys have nay suggestions? 

Thank you.:confused:

---

### Post by ThrobbingBrain66 on 2006-11-25
i would suggest editing your sources.list file and removing all country designations...so, just remove all the "us." from each line

in practice you would
```
gksu gedit /etc/apt/sources.list
```
then make all your changes, and then
```
sudo apt-get update && sudo apt-get upgrade
```

that should solve your issue.

---

