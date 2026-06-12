---
title: "Intel 2915ABG wireless not auto installed"
date: 2008-06-10
forum: Networking &amp; Wireless
---

### Post by Gobd on 2008-06-10
I just installed Ubuntu 8.04 and my Intel 2915 wireless card was not auto installed as far as I can tell. What do I do to get it to work? I open the network tools and all I see is my wired interface. This confuses me because the device is listed as supported and is supposed to work out of the box, and has every other time I have installed Ubuntu. Thanks for any help you guys can offer on getting it to work.

---

### Post by ashubham on 2008-06-10
I had the same problem with my debian system.

I then used ndiswrapper to install wireless drivers for my system. Using ndiswrapper you can load the windows driver for your wireless card.

I do not remember the forum link... but you may google your way out easily.

1. Install ndiswrapper using apt-get or synaptic.
2. go to system -> administration and select wireless windows drivers.
3. then you may download the windows driver for your card and use it with the ndiswrapper app.

google for more details.

---

### Post by Gobd on 2008-06-10
Well ndiswrapper along with the windows driver got my wireless to work, but causes a problem much more major. The instant I try to do anything with my wireless network (connect, or even use the network manager) the computer freezes thus rendering it completely useless. Anyone else  got anything else to try after I finish reinstalling?

---

### Post by Gobd on 2008-06-10
Turns out that a reinstall was all it took. Weird that the install didn't notice the card the first time but worked perfect the second.

---

