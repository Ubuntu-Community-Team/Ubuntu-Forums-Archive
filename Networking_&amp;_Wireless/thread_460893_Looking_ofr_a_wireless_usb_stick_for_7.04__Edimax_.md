---
title: "Looking ofr a wireless usb stick for 7.04  Edimax 54 Mbps Wireless USB stick"
date: 2007-06-01
forum: Networking &amp; Wireless
---

### Post by pfwd.tech on 2007-06-01
Hi im haveing no luck with my Belkin wireless usb stick so i would like to purchase one that i can get working without much tampering. 
is this ok [http://www.linuxemporium.co.uk/products/wireless/#pid88171](http://www.linuxemporium.co.uk/products/wireless/#pid88171)
[B]Edimax 54 Mbps Wireless USB stick

[/B][COLOR=Black]It says it will work with ubuntu 6.10 but not 7.04 Feisety Fawn.  Does anybody have this?[/COLOR]




---

### Post by steeleyuk on 2007-06-01
According to their site:

> Feisty wireless is now largely fixed, and we are updating our support CD. The new CD will be available later this week (w/e 12th May), please bear with us until then, or ring for help.

---

### Post by pfwd.tech on 2007-06-01
Could you send me a link to that page.  I find the site a bit uneasy to navigate

---

### Post by steeleyuk on 2007-06-01
[http://www.linuxemporium.co.uk/products/wireless/](http://www.linuxemporium.co.uk/products/wireless/)

The Feisty comment above is in the section 'Ralink RT2561 and RT2571 chipsets'.

I'll see if I can find more conclusive info on this because I'm after the PCI version.

EDIT
This thread may be useful if you do get that USB stick. [http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236)

---

### Post by pfwd.tech on 2007-06-01
Yeah i ws trying that guide with my current Belkin stick but with no luck so im after a quick out of the box solution

---

### Post by Arvi Pingus on 2008-07-22
> **pfwd.tech said:**
> Yeah i ws trying that guide with my current Belkin stick but with no luck so im after a quick out of the box solutionFrom kernel at least 2.621.7 the Belkin 54G is recognized. Mine is up and running now.
The stick is manufactured with 3 different chip sets.
Mandrivalinux 2008.1 (Spring) recognizes the stick and installs the correct module RT73. Works out of the box
Puppy Linux 4.0.0 recognizes the stick but installs the (in my case wrong) module RT25xx.
Removing the module and insmod the RT73 brought it alive.

There is also a chip used that needs the Prism54 module.

So give it a try before supporting your local hardware store.:)

---

