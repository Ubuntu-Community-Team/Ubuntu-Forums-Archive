---
title: "Wireless Noobery"
date: 2009-01-06
forum: New to Ubuntu
---

### Post by GoodApollo on 2009-01-06
ok ive read until my eyes crossed and i cant fin what to do in my situation, its prolly been solved but im wondering if someone can walk me through my problem.

ok so I can launch Ubuntu 8.10 no problem, I am running a Asus M50Mv, and i can't access wireless. the options are greyed out. Any suggestions?

---

### Post by Michael.Godawski on 2009-01-06
hi,
have a look at 

[LIST]
[*][http://godawski.oxyhost.com/solvingwireless.html](http://godawski.oxyhost.com/solvingwireless.html)
[/LIST]
and please post the output of these terminal commands:

```
sudo lshw -C network
iwconfig
```

---

### Post by GoodApollo on 2009-01-06
ok it says *-network DISABLED

and ESSID " "

if thats what you are looking for

---

### Post by Michael.Godawski on 2009-01-06
woow :D we need the whole picture.

can you please post the whole output? Use the code brackets to make it more readable #

thank you.

---

### Post by GoodApollo on 2009-01-06
well its on a different computer cause i cant use internet from my compy with ubuntu

any suggestions, sorry for being such a pain.... :(

---

### Post by Michael.Godawski on 2009-01-06
no problem.

Actually I am not at my PC as well. Sitting in the uni lib at a open suse machine with restricted access, so I cannot be of much help either :P.

have you checked the Hardware Drivers as suggested in the guide I posted above?

In the sudo lshw -C network output try to find the exact model/chipset of your wlan card. This would help.

You are not a pain.

---

### Post by GoodApollo on 2009-01-06
ok 

product: RTL8111/8168B PCI Express Gigabit Ethernet controller

and AR92X Wireless Network Adapter (PCI-Express)

:)

---

### Post by Michael.Godawski on 2009-01-06
If you are using the latest version of Xubuntu 8.10 you can try this:

The module is on **[linux-backports-modules-intrepid]("https://help.ubuntu.com/community/UbuntuBackports")** and it's called ath5k. You just need to install the package, either using Synaptic or apt-get, and make sure that is activated on System/Administration/Hardware Drivers.

---

### Post by GoodApollo on 2009-01-06
im using Ubuntu though does that matter?

---

### Post by Michael.Godawski on 2009-01-06
no :D I mixed up threads. Ubuntu of course... sry.

---

### Post by lswest on 2009-01-06
You can also copy the output of commands to a text file, then save it on a thumbdrive, that might make it easier for you.  Just for future reference.

---

### Post by GoodApollo on 2009-01-06
so i downloaded the wireless compatibility package, but im not sure what to do with it

---

### Post by lswest on 2009-01-08
Have you installed it?  (did you use synaptic or apt-get?)  If so, you should navigate to System-->Administration-->Hardware Drivers and there should be an entry there for your wireless card.  Select it and choose "activate".  It may need to download some information off the 'net so a cabled connection might be useful.

I'm not entirely sure, no experience with the ath5k, but judging by what was posted earlier, that seems to be all you need to do.

---

