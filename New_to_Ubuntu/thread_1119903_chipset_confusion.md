---
title: "chipset confusion?"
date: 2009-04-08
forum: New to Ubuntu
---

### Post by gibxam on 2009-04-08
Hello,

I'm a bit confused about what the difference is between a wireless card, a chipset and a driver. I know that a wireless card is the physical hardware that is used to connect to a wireless network, such as a Netgear MA101 ver B wireless card. But I don't really understand what a chipset is and how it applies to connecting to a wireless network. Is it like the firmware of the wireless card? From what I've been reading there are some chipsets that are more compatible with Linux but I don't really understand how exactly it is associated with the wireless card. I'm in the same grey area with wireless drivers, from using windows for years I know that you need to install drivers for just about every single piece of hardware, is this like the chipset of the wireless card? If anyone can clear this up for me, or point me to some reading that I could do, it would be appreciated.

Thank you for your time,

Max

---

### Post by LowSky on 2009-04-08
hope my explanation helps

A Card is the entire thing, some companies like Netgear, will sell a a card with differnet chipset under the same name with maby a different revision for instance the Netgear Wireless card model 100 rev B might have a different chipset as Netgear Wireless card model 100 rev C.

Chipsets are the internal guts of the card. the little microchips and wires.

Drivers are the software the operating system uses to talk to the card. Without the drivers no communication will take place. Just like a car with no driver you are not going anywhere.

Windows has a limited list of preinstalled drivers. It realies  on the companies that manufacturer the equiptment to produce the drivers. With Linux the manufacturers never made driver so Linux developers had to make their own, and so they were added to the Linux Kernel (main software). That is why some cards work better than others, even some that may be made by the same company. It all comes down to the choice of the chipset and hopefully availble drivers.

---

### Post by gibxam on 2009-04-08
Thanks LowSky this helps clear things up for me. So the wireless card is the physical device, and the chipset is the physical hardware inside the wireless card, and the drivers are the software that goes with the respected Card/Chipset.

Then if I wanted to configure my wireless card to connect my laptop to the internet/home network I would use the command lspci to get information about my Card/Chipset and then use that information to download the appropriate drivers?

---

### Post by LowSky on 2009-04-08
most card will work, if not there are two thing to try

1. Go to System > Admin > Restricted Drivers and if you see a driver click to activate it, a simple restart and you could be working with wireless.

2. if not open a terminal, type the lspci command (or lsusb if its a usb device), then copy the info here and we may be able to help

---

