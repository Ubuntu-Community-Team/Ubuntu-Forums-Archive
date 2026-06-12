---
title: "Eee PC 901 RT2860 Wireless Issues"
date: 2010-07-25
forum: New to Ubuntu
---

### Post by spacmarine2000 on 2010-07-25
Hi

Completely new to Ubuntu and the whole Linux scene, so go easy on me! Just installed Ubuntu 10.04 on my Eee PC 901 after getting progressively frustrated by the boxed OS, pleasantly surprised by how much faster and more efficient Ubuntu is :) (Using the full desktop version not the netbook remix)

Just as I started getting to work with it however, it disconnected my wireless network after about 5 minutes of connection and now refuses to connect to it, despite the fact it can see it and many others. I've determined, after much clueless searching, that I have a Ralinktech RT2860 wireless card in my machine, something that apparently has a lot of trouble with Ubuntu. I've searched many forums and websites since, looking for a solution, and all so far have been complete dead ends, with either too complex language so I don't know whether its a solution or not, or just disappearing into un-answered obscurity. I could really do with some help with this from a beginners standpoint, if someone could explain to me a solution it would be much appreciated, at my wits end!

Desperately, Spacmarine2000

---

### Post by spacmarine2000 on 2010-07-25
Not entirely sure what the rules are on bumping, but I really need some help with this, its driving me nuts! Every fix I try to find, for instance this promising looking one on here 

[http://ubuntuforums.org/showthread.php?t=966185](http://ubuntuforums.org/showthread.php?t=966185)

fails miserably with a broken link for downloading drivers from Ralinktech ](*,) Please help me!

---

### Post by gsoundsgood on 2010-08-19
now it's very easy to solve this issue (wireless not working on some models of eee-pc):

if you can get a functioning connection via LAN, you can simply download the package *linux-backports-modules-wireless-2.6.32-24-generic* from the repositories:

```
sudo apt-get install linux-backports-modules-wireless-2.6.32-24-generic
```

or you can download it from here on any computer and just install on your eee-PC:
[http://packages.ubuntu.com/lucid/linux-backports-modules-wireless-2.6.32-24-generic]("http://packages.ubuntu.com/lucid/linux-backports-modules-wireless-2.6.32-24-generic")

tested on eee pc-901, wireless now working flawlessly

---

### Post by sledhead on 2010-09-14
I tried this, and at first it did not work for me. When I checked my new router settings, I found I had enabled WPA _and_ WPA2. I was only able to connect after changing the router configuration for WPA2 only.

:p

---

