---
title: "How to Set up a wireless connection from terminal"
date: 2007-08-20
forum: Networking &amp; Wireless
---

### Post by Diabolis on 2007-08-20
I have to switch back and forth between 2 different wireless connections. Every time that I need to switch I go to the network manager and do it manually. Now I'm tired of it, so I though I could write a little scrip called "connection". It will check in which connection I'm working and then just switch to the one that is not being used. I found out that this command will do the switch.
```
sudo iwconfig eth1 essid network2
```
I tried that and it worked, but I haven't figured out **how to feed the wep key through terminal**.

---

### Post by beachreader on 2007-08-20
me too. hit and miss I finally got it to work. go figure!! no one replies to my inquires either.

---

### Post by kevdog on 2007-08-21
Try looking at 
man iwconfig

It will answer your question

WEP is configured
sudo iwconfig <interface name> key XXXXX

The man pages will talk about use of key indexes (indices) if this is important to you

---

