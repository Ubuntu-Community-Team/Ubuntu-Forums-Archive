---
title: "D-link DWL-650+"
date: 2006-10-04
forum: Networking &amp; Wireless
---

### Post by Klaymen on 2006-10-04
I have only used windows earlier, so i am very new at this. I installed Ubuntu and it seems awsome, but i cant get my wireless connection working... When i try network settings, it only lists the ethernet network and modem. And if i check hardware data, it lists the wireless card, with name, manufacturer and everything. But it cant identify it as to what it is... Any ideas? Do i need to install a driver os something, and if so, how? And where do i get it? Thanks for the help.

---

### Post by tturrisi on 2006-10-04
What version is the dwl650+?  Dlink made several versions of that card using different chipsets, which means different drivers.

---

### Post by Klaymen on 2006-10-04
Uhm... Does it say on the card? It's a PCMCIA-card...

---

### Post by psycho78 on 2006-10-04
yes on the back of the card there is a label about the Revision of the card....
[http://www.dlink.de/?go=jN7uAYLx/oIJaWVTALoeU8H8g50JcLpcX43jIuejxxi6E4R4gL87fcpjZftt4ktOa1aHrUQ9iuNpdKiTzKDjKE8RsuPeb4c=](http://www.dlink.de/?go=jN7uAYLx/oIJaWVTALoeU8H8g50JcLpcX43jIuejxxi6E4R4gL87fcpjZftt4ktOa1aHrUQ9iuNpdKiTzKDjKE8RsuPeb4c=)

---

### Post by Klaymen on 2006-10-04
Oh, okay! H/W: A1  F/W: 1.0

---

### Post by psycho78 on 2006-10-04
check out this?
[http://www.ubuntuforums.org/showthread.php?t=74651&highlight=DWL-G650%2B+HW%3A+A1+FW%3A+1.0](http://www.ubuntuforums.org/showthread.php?t=74651&highlight=DWL-G650%2B+HW%3A+A1+FW%3A+1.0)

---

### Post by tturrisi on 2006-10-04
Dlink made 2 A1 versions of the 650, one has a Prism chipset which should work out-of-the-box and the other has an Atheros chipset.  To use an atheros card install the linux-restricted-modules that match your kernel.  Use synaptic to do this but must first enable the other repositories.

---

### Post by Klaymen on 2006-10-07
Psycho78: I couldn't even do the first point. I tried typing "sudo apt-get install ndiswrapper-source ndiswrapper-utils" int he terminal, but i got a message that ndiswrapper wasn't available, but referred to from another package. Is something wrong with my system, or what am i doing wrong? This is so frustrating, i am starting to give up, and reinstall windows... i need internet, but ubuntu feels so much better... Except this one thing.

tturrisi: I am sorry, but i am very new to this. > To use an atheros card install the linux-restricted-modules that match your kernel. Use synaptic to do this but must first enable the other repositories. That made no sence to me, please explain how to do this?

---

### Post by tturrisi on 2006-10-07
The chipset is the thing on a card that controls it, the brain per se, and determines which driver needs to be used for the device.  In the case of Atheros chipsets, the driver needed is called the madwifi driver.  The madwifi driver is not installed by default in Ubuntu due to its licensing.  But it is available for installation and is included in the package linux-restricted-modules.

These restricted modules (drivers) can be installed using the Synaptic package manager.

1. go to System - Administration - Synaptic
2. go to some menu in synaptic and enable all the repositories (download sources).
3. use reload button
4. look on left for restricted
5. install the restricted package that matches your kernel:
if use kernel 2.6.15.10 then install the restricted package called linux-restricted-modules-2.6.15.10

to find your kernel number open a command and type:
uname -r

---

### Post by Klaymen on 2006-10-07
Do i have to be connected while doing this? I am thinking about the download sources thing... i'll try though, thanks.

---

### Post by Klaymen on 2006-10-07
Crap, didn't work... i got an error message while reloading after enabling the repositories (seems it tried to look for something on the net, and that didn't work without the wireless enabled). There was no "restricted" on the left... :(

---

### Post by tturrisi on 2006-10-07
> **Klaymen said:**
> Crap, didn't work... i got an error message while reloading after enabling the repositories (seems it tried to look for something on the net, and that didn't work without the wireless enabled). There was no "restricted" on the left... :(
use a wired connection to connect...

---

### Post by Klaymen on 2006-10-08
Yeah, i'll try... i wont have i wired connection near me for a few weeks though, so i'll have to do without. Thanks, anyway.

---

### Post by Klaymen on 2006-10-08
Hey, wait! Isn't there any way i could download any of this, or something? On a windows computer, and move it via an iPod or something? Could that work?

---

### Post by karipentti on 2006-11-04
Hi! Same card, same problem here.

Did you give up or is the problem solved?

---

### Post by Klaymen on 2006-11-04
Sorry, i gave up... running windows again... :(

---

