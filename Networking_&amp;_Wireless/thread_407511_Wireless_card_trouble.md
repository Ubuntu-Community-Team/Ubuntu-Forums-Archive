---
title: "Wireless card trouble"
date: 2007-04-12
forum: Networking &amp; Wireless
---

### Post by Dr Zolygon on 2007-04-12
ok so ive just gotten ubuntu installed and running but i cannot figure out how to get an internet connection. I have gone to the network settings and it appears to recognize my card and i have edited the properties but i cant get it to connect. One thing is that on windows it is required to have the driver installed so i am assuming it is probably the same for ubuntu. But im a noob and dont know how to run the installer off the disk and im not even sure if it supports linux. Oh and i also ran pppoeconf in the terminal and it recognizes the card but fails to connect. Any help is appreciated. So far i like ubuntu and once i get this internet problem out of the way i should be able to do a lot more with it.

btw my card is a linksys wireless-g PCI adapter model no. wmp54gs and my router is a linksys also(dont remember exact name and to lazy to find out).

this is off topic but ive noticed that scrolling and the moving of windows is really slow and chuggy. Is this because i dont have a linux driver installed for my graphics card? Its 8800gts( dont know if that helps). Anyways ill try downloading a linux driver as soon as this internet problem is fixed.

thanks.

---

### Post by renzokuken on 2007-04-12
here is a simple guide for your wireless problems. [http://ubuntuforums.org/showthread.php?t=381594](http://ubuntuforums.org/showthread.php?t=381594)
windows drivers are only compatible in linux when using ndiswrapper.

as for your grafix problems, you have an nvidia card so for best performance you need to install the official nvidia linux drivers. the Envy script makes this very easy for you. have a look at the Projects and Guides sections of [www.albertomilone.com](www.albertomilone.com)

---

### Post by chili555 on 2007-04-12
I believe you will set up PPPoE in your router so you don't have to configure it in your computer. Your Linksys router, running Linux, already has pppoeconf!

---

