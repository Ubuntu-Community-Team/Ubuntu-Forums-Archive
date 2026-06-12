---
title: "wifi on ubuntu server 20.04"
date: 2020-06-02
forum: Networking &amp; Wireless
---

### Post by lgerra on 2020-06-02
Heya peeps

i'm quite new to ubuntu server but i was thinking installing it on a rig i have lying around, problem is that i can't connect it with ethernet, only wifi, 
I went through the installation process without internet but now i don't find how to setup wireless .. halp please

---

### Post by CelticWarrior on 2020-06-02
[https://unix.stackexchange.com/a/555961](https://unix.stackexchange.com/a/555961)

Please ignore the specificity of the question (19.10 and Raspberry Pi). It should be the same.

---

### Post by lgerra on 2020-06-02
thanks, i tried with different edits but no change, i have my phone as basic access-point for the moment just to get all configured so basically it's just a regular AP right ??

---

### Post by CelticWarrior on 2020-06-02
The WiFi device must have working drivers, of course. Most are natively supported but some aren't.

---

### Post by lgerra on 2020-06-02
just tried plugging it on my laptop which is ubuntu 20.04 desktop and works fine

---

### Post by SeijiSensei on 2020-06-02
I really think you should use an Ethernet cable. Just put the server next to your router and connect them.  Once it's up you're going to be connecting to it over SSH anyway.

Production servers should always be hard-wired and have a static IP address.

Alternatively use a desktop version of Ubuntu. Servers have no GUI and server-specific applications. You can add the applications manually to a desktop version as you need them, e.g., install the lamp-server^ package to get Apache, PHP, and MySQL.

---

### Post by lgerra on 2020-06-02
As i said i can't use an Ethernet cable even if i would like to.

Iwent to the "easy way" and got on the desktop version, (I'll maybe try in a vm or later and update this if i get a solution for the others.)

sorry for disturbing, thanks anyway

---

