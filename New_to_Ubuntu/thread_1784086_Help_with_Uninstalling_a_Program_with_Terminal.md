---
title: "Help with Uninstalling a Program with Terminal"
date: 2011-06-16
forum: New to Ubuntu
---

### Post by Fireicee1 on 2011-06-16
I read somewhere else on this forum you could use the code

**sudo aptitude remove (program)**

to uninstall it.  When I try, i get the message

**sudo: aptitude: command not found**

Can I get some help?

---

### Post by andrewc6l on 2011-06-16
Use Synaptic Package Manager to install aptitude and you should get what you need.

---

### Post by Cheesehead on 2011-06-16
Try:
```
sudo apt-get remove (program)
```
apt-get and aptitude are both frontends for dpkg. apt-get is included in Ubuntu. aptitude is not, but is available in the Ubuntu repositories. Both can be installed at once - they do not conflict. They cannot be used at the same time. Packages installed by one can be removed by the other.

---

### Post by Rubi1200 on 2011-06-16
Hi and welcome to the forums Fireicee1 :)

Why install aptitude when you can achieve the same thing with apt-get which is already installed?

If you see commands somewhere which say aptitude just replace with apt-get and away you go.

---

