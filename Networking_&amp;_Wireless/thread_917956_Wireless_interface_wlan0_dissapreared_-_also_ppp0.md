---
title: "Wireless interface wlan0 dissapreared - also ppp0"
date: 2008-09-12
forum: Networking &amp; Wireless
---

### Post by j0natz on 2008-09-12
Hi, 

after doing some stuff with virtualbox (had problems with bridging/hostinterface) suddenly now intel wireless and my option pcmcia card don't work anymore)

Both devices are still shown by lspci but I have no clue how to readd the devies.

Any hints?

Thanks 

Jonas

---

### Post by j0natz on 2008-09-13
Hi,

sorry I found the error. During setup of Virtualbox I had to install a diffrent kernel.

Switching back from the newly installed 2.6.25-19-386 kernel to the 2.6.24-19-generic ones everything works fine again but Virtualbox :)

Thanks again!

Jonas

---

