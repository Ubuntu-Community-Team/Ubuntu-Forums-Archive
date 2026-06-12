---
title: "Travelmate 4400 with a Broadcom AirForce One wireless not working."
date: 2007-03-07
forum: Networking &amp; Wireless
---

### Post by MJewkes on 2007-03-07
Hello everyone,

I am posting this message using Xubuntu 6.06 32bit on an Acer Travelmate 4400 Notebook (Turion) over an ethernet cable.

I am using a Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

I am trying to get my wireless card on this computer to work. Right now, the wireless card does not show up on the network-admin panel. 

ndiswrapper is up to date, and -l says
bcmwl5          driver present

Furthermore, I have updated my pci.ids

There are a few issues that I am aware of. I know that BCM4318 cards are notorious on Ubuntu, and, in addition, this Acer model's wireless antenna is turned off until you enable it with acer_acpi. I have been fiddling with ndiswrapper, the acer_acpi package, etc, but I have had no luck. Please help!

I have read a number of tutorials out there, but to no avail. 

Thanks,
Matthew

---

### Post by needy on 2007-03-07
I have an Acer 1000 with the same wireless card and I was able to get it to work without changing any acpi settings.

---

### Post by Floppyjoe on 2007-03-07
> **MJewkes said:**
>  
ndiswrapper is up to date, and -l says
bcmwl5          driver present

Furthermore, I have updated my pci.ids


It should say hardware present here too if you have the correct driver for your card.
What do you mean by updated pci.ids?

---

### Post by MJewkes on 2007-03-07
> It should say hardware present here too if you have the correct driver for your card.
Hmm... It doesn't. What does that mean?

> What do you mean by updated pci.ids?
Updates my pci.ids file with the one here
[http://pciids.sourceforge.net/](http://pciids.sourceforge.net/)

---

### Post by Floppyjoe on 2007-03-07
Did you download your drivers from the Acer site? If you are using a driver from somewhere else it may not be designed to work with your card.

---

### Post by MJewkes on 2007-03-07
Hey Sloppyjoe,
I followed the tutorial in your signature, as well as the tutorial for enabling acer_acpi, and i have my wireless working now!
Thanks!
Matthew

:guitar:

---

