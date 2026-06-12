---
title: "ndiswrapper not working correctly"
date: 2007-05-16
forum: Networking &amp; Wireless
---

### Post by chr3681 on 2007-05-16
I am having trouble installing ndiswrapper on Feisty Fawn. I tried:
sudo apt-get install ndiswrapper-utils
when I did this it said to use ndiswrapper-common instead.
So I did and it seemed to run smoothly (sudo apt-get install ndiswrapper-common).
Now though when I try to use ndiswrapper it says that there are no versions of ndiswrapper found.

Any ideas???

Thanks!

---

### Post by renzokuken on 2007-05-16
maybe try installing it with automatix [www.getautomatix.com](www.getautomatix.com)

its pretty easy to install compiling it from source as well so if automatix doesnt work i'll show you how

---

### Post by Jouke74 on 2007-05-16
Automatix for Ndiswrapper? A bit overkill I think.

Does administration > Synaptic package manager 
Ticking both Ndiswrapper-common and -utils does not work?

---

### Post by zekica on 2007-05-16
You can try to:
sudo apt-get install ndiswrapper-utils-1.9

---

### Post by chr3681 on 2007-05-16
sudo apt-get install ndiswrapper-utils-1.9 worked! thanks for the help!

Jouke your method worked too I am new and wasn't aware of that package manager lol. Thanks for opening that up to me!

---

