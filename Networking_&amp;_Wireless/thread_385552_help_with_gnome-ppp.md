---
title: "help with gnome-ppp"
date: 2007-03-15
forum: Networking &amp; Wireless
---

### Post by strivehosting on 2007-03-15
I need help installing it. Every time i try:
```
sudo apt-get install gnome-ppp
```
and
```
sudo aptitude install gnome-ppp
```
I get an error message saying that it cannot be found. Any other ways to get this program? or to somehow fix the problem?

---

### Post by taurus on 2007-03-15
Maybe you need to enable both universe and multiverse in /etc/apt/sources.list.

Open a terminal and edit /etc/apt/sources.list.

```
gksudo gedit /etc/apt/sources.list
```
Remove the # in front of all the lines with deb at the beginning.  Save it and then run

```
sudo aptitude update
sudo aptitude install gnome-ppp
```

---

### Post by strivehosting on 2007-03-16
Alright, I got it installed. Now, how to I get it to connect?

---

