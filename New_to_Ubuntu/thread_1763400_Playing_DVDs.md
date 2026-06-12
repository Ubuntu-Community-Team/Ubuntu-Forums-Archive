---
title: "Playing DVDs"
date: 2011-05-20
forum: New to Ubuntu
---

### Post by dwhite on 2011-05-20
I have installed the "restricted extras" from the software center and I cannot play DVDs with Movie Player, i've attached a screenshot of the error message I get (this has been ongoing for the past few months i usually like to try and figure out but this one has me stumped)  not really sure where to go next, any suggestions would be appreciated. perhaps i need some proprietary software? (like Fluendo)

probably unrelated but have some trouble with java, for example can't play MineCraft due to fact whenever I try i get a "need java to play" type error message.

running 11.04 here (but this problem with DVDs existed before i upgraded)

---

### Post by dniMretsaM on 2011-05-20
For Java, you need to install sun-java6-jdk or sun-java6-jre. Search for Sun Java in synaptic and you'll find it. For playing DVDs, you need a package that I cant remember the name of. It has 'css' in the name though. Search around for it.

---

### Post by philinux on 2011-05-20
> **dwhite said:**
> I have installed the "restricted extras" from the software center and I cannot play DVDs with Movie Player, i've attached a screenshot of the error message I get (this has been ongoing for the past few months i usually like to try and figure out but this one has me stumped)  not really sure where to go next, any suggestions would be appreciated. perhaps i need some proprietary software? (like Fluendo)

probably unrelated but have some trouble with java, for example can't play MineCraft due to fact whenever I try i get a "need java to play" type error message.

running 11.04 here (but this problem with DVDs existed before i upgraded)
See this.
[http://medibuntu.org/index.php](http://medibuntu.org/index.php)

Then the repository howto. Once you've got the medibuntu repo active you can install libdvdcss2 and either w32codecs or w64codecs depending on your install.

Personally for DVD's I prefer VLC over totem.

---

### Post by Rasa1111 on 2011-05-20
This is what I do every time I do a new install..
Once I have restricted extras installed, I use these 2 commands,
and I can then play any DVD, in movie player, vlc, etc. 

2 easy commands..

```
sudo apt-get install libdvdread4

```(this may already be installed- it will tell you), So you'd just need the next command if so

```
sudo /usr/share/doc/libdvdread4/install-css.sh
```Close terminal

Pop in a DVD, and watch it pop up! lol :)

good luck.

---

### Post by dwhite on 2011-05-20
Dear dniMretsaM, philinux, and Rasa1111,

thanks very much for the help, works like a charm!

doug

oh and phil, your computer is on fire...just saying

---

### Post by philinux on 2011-05-20
> **dwhite said:**
> Dear dniMretsaM, philinux, and Rasa1111,

thanks very much for the help, works like a charm!

doug

oh and phil, your computer is on fire...just saying

It's Smokin !!!

---

