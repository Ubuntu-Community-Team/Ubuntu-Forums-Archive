---
title: "Modem 4G LTE detected as Audio CD"
date: 2016-09-10
forum: Networking &amp; Wireless
---

### Post by lian-alex on 2016-09-10
Hello.

Newbie here. 

I have a modem 4G LTE. When I connect it my OS detecting it as audio CD and do not set up network connection.

I try it in Ubuntu 15.10 and 16.04 and even in Fedora 24. It does not work.

But the modem works great in Windows.

I already try the following things:

1. madwimax driver (does not work)
2. I try to use modemmanager-gui  (the software does not see my usb modem at all)
3. reload  cdc_ethe and rndis modules, Because in modem's system requirements my OS must support it.
4. I read in some forum that is a bug in kernel 4.4.0 Ok, I updated my kernel, but to me it didn't help

Please, help me.

---

### Post by mörgæs on 2016-09-11
Hi, welcome to the fora.

Have you tried a live boot of 16.10 (beta)?

---

### Post by King of Heart 4711 on 2016-09-11
How is the device being connected; USB/mPCIe/ExpressCard/etc.?

---

### Post by Bucky Ball on 2016-09-11
You don't plug it into your computer. It is a mobile, portable modem? You either charge it up or plug it in to a wall socket, switch it on, wait for the lights to go solid, check 'Network Manager' in Ubuntu and you should see the modem's network available for you to connect to.

Plugging it in to your computer is only going to achieve charging it. Unknown what it might see it as, but probably not a modem. It is an independent wireless modem if I am presuming correctly, not designed to provide internet connectivity by plugging it in via USB but wirelessly. It sounds like the same as the unit I have and use for travelling.

---

### Post by lisati on 2016-09-11
The one and only 4G device I have access to (an Android phone) gives me an option to install (Windows) software when I first attach it to my computer by USB cable. I'm wondering if your device is doing something similar. 

The 4G modems I've looked at online generally connect to the computer via ethernet or wifi, not by the USB cable.

---

### Post by Bucky Ball on 2016-09-11
> **lisati said:**
> The 4G modems I've looked at online generally connect to the computer via ethernet or wifi, not by the USB cable.

+1. Did you buy it locked to an ISP in your country? If so, the software is installed already, all you should need to do is plug in to a wall socket with the provided USB charger plug or plug into a computer (or any USB socket on any device) or, if already charged, just switch the device on (probably has a big button right in the middle to do that), wait a bit for the lights on the modem then connect to the network it provides. 

Good luck.

PS: Do you mean this is a 4g ZTE modem portable modem rather than an LTE? LTE is not a brand but a technology as far as I know. 4g ZTE portable modems, on the other hand, are very common. Just checking, but the brand of the modem and the ISP it is locked to, if it is, would be helpful in identifying exactly what this device is.

---

