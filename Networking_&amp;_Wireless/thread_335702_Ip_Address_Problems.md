---
title: "Ip Address Problems"
date: 2007-01-10
forum: Networking &amp; Wireless
---

### Post by CameronCalver on 2007-01-10
Hello i have a bit of problems in my network for work and home this is the situation

Home Network

Server Ip= 192.168.1.130
My Comp 192.168.1.130
Other  192.168.1.130 
Router 192.168**.1.1**

Work

About 9 computers all 192.168.0.1 , ,3 ,4 ,5 ,6 etc
Router 192.168.**0.1**
Ubuntu Server 192.168.0.2

My mum has a laptop which goes from work and home but we have a bit of a problem.
She is Windows so if we set her ip to automatic it sometimes picks an ip already in use on the network at work and that causes all chaos with ip conflics and it crashes the network drive and the proxy.
So is there a way to set it so when she is at work it uses one setting and at home another setting at home?

---

### Post by kipeloff on 2007-01-11
What router brands is used in both networks ?

1. One of the method to use the same subnet on both Home and Work networks,
192.168.0.0/24
The following method assume, that you need to change one network workstations IP addresses to the same subnet.
Than particular laptop will use the same address on both locations, and this address will be correct.
I guess other methods are more complicated, it is better to use first method.

---

### Post by dmizer on 2007-01-11
if she's windows xp, you could use the "alternate configuration"

[http://www.microsoft.com/windowsxp/using/mobility/learnmore/russel_02march04.mspx](http://www.microsoft.com/windowsxp/using/mobility/learnmore/russel_02march04.mspx)

so
- set up her primary configuration for her dhcp network at work.
- set up a second static configuration for use at home (in windows alternate configuration)
- disable dhcp in your router at home.

now, when she goes to work it will automatically detect and connect to her dhcp network.  and when she comes home, it will not be able to connect to dhcp, and the alternate profile will kick in and connect her to your static network.

all without her having to touch a thing (once it's configured of course)

---

### Post by CameronCalver on 2007-01-11
Kipelof my home router is a   zxyel prestigue 600 series

---

### Post by CameronCalver on 2007-01-11
Also dmizer at home i want it to be dhcp and at work static so do i do primary dhcp and at work static and at work  turn dhcp off on the router?

---

### Post by CameronCalver on 2007-01-11
Yeh thanks guys for your quick response all is good now both routers are **192.168.0.1**
 :) :KS :)

---

### Post by dmizer on 2007-01-11
well, i realize you've managed to resolve your issue, but just for future reference:

yes, the dhcp needs to be your primary profile.  what happens in windows then is, the computer will search for a dhcp lease.  if it finds one, then it will attach to it.  if it does not find a dhcp lease, then it will look for an alternate profile.

by the way ... for your simple amusement.

i have a bios that errors with the "Error Keyboard Failure Press F1 to continue or DEL to enter setup" on boot when i use my japanese keyboard.  when i press f1 on the keyboard, the computer continues to boot.  the bios errors because of a few special japanese specific keys on the keyboard for which it is not sophisticated enough to recognize, but since the rest of the keys work fine, the error speaks truth.

this is however the single solitary example i have of that error not being completely useless.

---

