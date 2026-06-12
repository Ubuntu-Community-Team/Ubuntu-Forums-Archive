---
title: "Cannot find Wireless network"
date: 2009-04-24
forum: New to Ubuntu
---

### Post by ConanB on 2009-04-24
Hello everyone,

I´m a new Ubuntu user and I´m still learning to work with Ubuntu. I installed Ubuntu 8 a couple of weeks ago and when I was finished Ubuntu was unable to find my wireless network (at home and at work). Eventhough every other PC can connect to the network. 

I figured out how to fix this problem, with some help from so guy at work. But now that I´ve updated to Ubuntu 9.04 the problem is back. The guy from my work isn´t able to help me (very busy guy). 

Therefor I would like some help from you guys. How can I make my Ubuntu version find my wireless networks? I would need a detailed overview of the steps I need to take. 

It´s an desktop Ubuntu 9.04 version on my Dell laptop inspiron 1521. I was able to post this thread because of my Windows version on the same PC. 

Please help me with this problem..
Thanks,
ConanB

---

### Post by djtnz on 2009-04-24
I'm not sure, but you may need to install some 3rd party drivers for your wireless card, in the menus:

System > Administration > Hardware Drivers

Check to see if there is an appropriate driver for your card?

---

### Post by ConanB on 2009-04-24
> **djtnz said:**
> I'm not sure, but you may need to install some 3rd party drivers for your wireless card, in the menus:

System > Administration > Hardware Drivers

Check to see if there is an appropriate driver for your card?

I´v just tried the above by trying a different driver, but this driver needed to download. Seeing this wasn´t possible I tried deactivating the current one and activating it again. After I did that Ubuntu was able to find the wireless networks and connect to them. 

But when I try to start Fire Fox and go online I get a network error (right away). The router works perfectly. Does anyone have any ideas?

Current driver: Broadcom STA wireless driver. 

Thanks.

---

### Post by acimmarusti on 2009-04-24
open up a terminal and type:

```

lspci -v | grep Network

```

And show me the output

---

### Post by ConanB on 2009-04-24
> **acimmarusti said:**
> open up a terminal and type:

```

lspci -v | grep Network

```And show me the output


The following output came up:
0b:00.0 Network controller: Broadcom corporation BCM4311 802.11b/g WLAN (rev 01)

Thanks...

---

### Post by ConanB on 2009-04-24
The issues has been solved by deactivating and activating my driver. The issue that is still a problem is the switch at my work. I´ll let you know which switch this is asap i´m back at the office.

---

### Post by acimmarusti on 2009-04-24
Ok, try this:

Go to: [http://ubuntu.cafuego.net/dists/hardy-cafuego/broadcom/](http://ubuntu.cafuego.net/dists/hardy-cafuego/broadcom/)

and get the b43-firmware .deb package. Now, install it on your computer (double click) and restart.

That should take care of the wireless issues, hopefully

---

