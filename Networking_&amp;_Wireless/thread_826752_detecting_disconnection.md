---
title: "detecting disconnection"
date: 2008-06-12
forum: Networking &amp; Wireless
---

### Post by catacuta on 2008-06-12
Hi there,

I wanted to write a program which periodically checks whether the computer is connected to the internet or not.

Since I'm new to linux environment I couldn't figure out what is the best way of doing this, thus asking you guys, any help would be much appreciated.

thanks..

p.s.: I'm not sure if this is the best forum to ask this question, feel free to direct me to an another one.

---

### Post by Kebabman on 2008-06-12
If it is detecting whether you are connected to the Internet or not, simply send out an ICMP echo to somewhere reliable (eg google.com) and wait for the reply, this can be done using an ICMP socket.

However, if you are wanting to detect whether your computer is connected to a network this is a slightly different problem.

---

### Post by kevdog on 2008-06-12
When you disconnect do you lose your IP address?  Give us an example of when you disconnect to the internet as far as how you personally detect that you are no longer connected.

---

