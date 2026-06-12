---
title: "The Perfect Ubuntu Card"
date: 2008-03-12
forum: Networking &amp; Wireless
---

### Post by AdHavoc on 2008-03-12
Every single wireless receiver card in my house requires fwcutter or ndiswrapper to be recognized in ubuntu / linux.  I have a WPC11, a WUSB11, and a Broadcom4318.  So, I think I'm going to just go out and buy a good card that works perfectly in ubuntu automatically (i.e. no ndiswrapper, no installing anything, no updating anything).  Does anyone know of any such card?  Here are three categories of cards that I need:

PCMIA (permanent solution for laptops):

PCI (permanent solution for dekstops):

USB (temporary card that could be used for multiple situations):

---

### Post by prshah on 2008-03-13
> **AdHavoc said:**
> Every single wireless receiver card in my house requires fwcutter or ndiswrapper to be recognized in ubuntu / linux.  I have a WPC11, a WUSB11, and a Broadcom4318.  So, I think I'm going to just go out and buy a good card that works perfectly in ubuntu automatically (i.e. no ndiswrapper, no installing anything, no updating anything).  Does anyone know of any such card?  Here are three categories of cards that I need:

PCMIA (permanent solution for laptops):

PCI (permanent solution for dekstops):

USB (temporary card that could be used for multiple situations):

Atheros based chipset cards such as Compex work fine. You can get WLP54G 2A Wireless-G network PCI adapter (that's what I use) and a similar one in miniPCI for laptops (but that requires some internal installation). I am also using NetGear's WG311 PCI card out-of-the-box.

I have not used PCMCIA so I cannot advise on that, but you can use a miniPCI in a PCMCIA adapter.

As far as USB goes, Netgear's WGv111v2 works fine for me (better than in Windows, because it disables the Fast User Switching feature), but now I believe that only WG111v3 is available and I have no clue about that.

---

### Post by stooshbunutu on 2008-04-10
> **prshah said:**
> Atheros based chipset cards such as Compex work fine. You can get WLP54G 2A Wireless-G network PCI adapter (that's what I use) and a similar one in miniPCI for laptops (but that requires some internal installation). I am also using NetGear's WG311 PCI card out-of-the-box.

I have not used PCMCIA so I cannot advise on that, but you can use a miniPCI in a PCMCIA adapter.

As far as USB goes, Netgear's WGv111v2 works fine for me (better than in Windows, because it disables the Fast User Switching feature), but now I believe that only WG111v3 is available and I have no clue about that.

v3 does work, but does require ndiswrapper.

I have written a tutorial for it (link in sig) or go tohttp://helpbuntu.iwarp.com/wireless.html

regards, stooshbunutu

---

