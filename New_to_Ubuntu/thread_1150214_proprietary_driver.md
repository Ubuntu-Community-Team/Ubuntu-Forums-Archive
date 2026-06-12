---
title: "proprietary driver"
date: 2009-05-05
forum: New to Ubuntu
---

### Post by crew51m on 2009-05-05
My new laptop has an ati 3450 mobile card, it is listed in the proprietary list, last time I did this in 7.10, my graphics didnt load, it crashed to a plaid like screen, and locked up, it was an nvidia card, my old toshiba, I had to go into grub on boot and press some keys to revert back to a 600x400 or a 800x600 with xorg or something to at least get the laptop to boot into desktop. Does 9.04 have better support? Has anyone loaded the driver and have a crash or will it just say the driver is not working? If I activate the proprietary driver and the system crashes, how do I get back to the desktop? Would it to be safe to load this? I would like to utilise the 3d. 

I am using a Toshiba A305-6916 

The box says:
No proprietary drivers used on this system
ati/amd proprietary fglrx graphics driver with gray ball (not activated)

ati/amd proprietary fglrx graphics driver
tested by ubuntu developers
license proprietary
3d -accelerated proprietary graphics driver for ati cards

This driver is required to fully utilise the 3D potential of some ATI graphics cards, as well as provide 2D acceleration of newer cards.

---

### Post by Mark Phelps on 2009-05-05
If it offers you the choice of selecting the restricted drivers, they will work with your system.  

What gets folks in trouble is forcing the installation of restricted drivers that are NOT offered, by downloading and installing them manually.

---

### Post by lavinog on 2009-05-05
the driver works for me (ati 3650 and ati 3200)

---

### Post by JK3mp on 2009-05-05
ATI blacklisted an array of there cards with the new Catalyst drivers so check your list against them.

---

### Post by crew51m on 2009-05-05
Yes it is offered, and I think it is a 3650 card, I will check the blacklisted drivers. If I activate the driver and my laptop crashes, anyone know the link to get my desktop to load again, or a simple way to do so? I want to print it out just in case.

---

### Post by lavinog on 2009-05-06
> **JK3mp said:**
> ATI blacklisted an array of there cards with the new Catalyst drivers so check your list against them.

only older cards, if your card is a radeon hd#### you should be fine

---

### Post by Didius Falco on 2009-05-06
Below is the list of cards moved to legacy from ATI. I did a driver search for the Mobility Radeon X300 and it took me to the 9.3 driver, which says:

> Automated installer and Display Drivers for X.Org 6.7, 6.8, 6.9, 7.0, 7.1, 7.2, 7.3, or 7.4


> The following products have been moved to the legacy software support structure (including Mobile and All-in-Wonder Variants):
 ATI Radeon 9500 Series
ATI Radeon 9550 Series
ATI Radeon 9600 Series
ATI Radeon 9700 Series
ATI Radeon 9800 Series
ATI Radeon X300 Series
ATI Radeon X550 Series
ATI Radeon X600 Series
ATI Radeon X700 Series
ATI Radeon X800 Series
ATI Radeon X850 Series
ATI Radeon X1050 Series
ATI Radeon X1300 Series
ATI Radeon X1550 Series
ATI Radeon X1600 Series
ATI Radeon X1650 Series
ATI Radeon X1800 Series
ATI Radeon X1900 Series
ATI Radeon Xpress Series
ATI Radeon X1200 Series
ATI Radeon X1250 Series
ATI Radeon X2100 Series


---

### Post by crew51m on 2009-05-06
If I load the driver and my system crashes, how can I get my desktop back? The last time I did this is with a restricted driver, and my laptop went plaid, I had to press a couple of keys to get into safe mode generic desktop. Will the proprietary driver crash my system like a restricted driver?

---

