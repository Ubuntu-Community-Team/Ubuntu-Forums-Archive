---
title: "ATI Graphics driver"
date: 2009-11-04
forum: New to Ubuntu
---

### Post by mosaabJ on 2009-11-04
I am lookign to install the graphics card driver for my computer and my graphics card is ATI Radeon X1650SE which AMD doesn't provide support for but can be downloaded from the AMD website.
but then when installing the driver by writing this:
```
sh ./ati-driver-installer-9-3-x86.x86_64.run
```
[SIZE="4"][COLOR="Red"]An error occurs after doing this and the error is:[/COLOR][/SIZE]
```
Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:2.6.31-14-generic; make sure that the version is being
correctly set by --iscurrentdistro
```
[SIZE="4"][COLOR="Red"]Tyke91 told me that the the driver doesn't recognise your kernel.[/COLOR][/SIZE]

---

### Post by mosaabJ on 2009-11-04
Can someone please help):P

---

### Post by cccy on 2009-11-04
In Synaptic Package Manger , there is a Catalyst Control Center program for controlling ATI graphic cards . Perhaps installing the Catalyst Control Center would solve your problem .

---

### Post by 3rdalbum on 2009-11-04
The new drivers are not compatible with your card, and the old drivers are not compatible with any version of Ubuntu later than 8.10.

If you proceed in trying to install this driver, you will end off breaking your graphical display and you'll end off with just a blank screen.

Are there problems with the open-source ATI driver that is activated by default on Ubuntu?

---

### Post by mosaabJ on 2009-11-04
> **cccy said:**
> In Synaptic Package Manger , there is a Catalyst Control Center program for controlling ATI graphic cards . Perhaps installing the Catalyst Control Center would solve your problem .

I tried that but it just crashed my computer

> **3rdalbum said:**
> The new drivers are not compatible with your card, and the old drivers are not compatible with any version of Ubuntu later than 8.10.

If you proceed in trying to install this driver, you will end off breaking your graphical display and you'll end off with just a blank screen.

Are there problems with the open-source ATI driver that is activated by default on Ubuntu?

Will that install 3D graphics because I tried to follow steps in this web page from UBuntu [https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver") but I failed i just messed up my interface. I don't know if this doesn't work for my computer or if I did something wrong.

---

### Post by mosaabJ on 2009-11-04
Please help me!

---

### Post by JPorter on 2009-11-04
Calm down.


The ONLY driver option for your card on Ubuntu 9.10 is the open source driver, which is quite good and is included by default in Ubuntu.  The most recent stable flavor of that driver (and the Mesa 3D libraries, etc) is available through the Ubuntu X-Swat repo.


ATI abandoned all of the older cards (pre-HD series) last year and won't be supporting them with Catalyst under Linux for future updates.  New ATI cards are fully supported by Catalyst though.

To be clear... the "proprietary" driver does not offer a truly significant increase in performance anyway, on cards which are supported by both drivers.  What specific 3D needs do you have, or is it just a general desire to have the best performance from the card?  The open source driver is actually faster than the proprietary one on most 2D benchmarks.

For in-depth discussion and forum support on ATI cards under linux, the forums at Phoronix are excellent.  Several developers from ATI participate there, as do the radeon open source driver devs.

---

