---
title: "Confusing - Question regarding packet injection"
date: 2008-06-12
forum: Networking &amp; Wireless
---

### Post by kg87 on 2008-06-12
Ok I have a slight dilemma here. 

I am teaching myself network security. After reading forum after forum im now in a worse place than i started off with. 

It seems people seem to prefer USB rather than say PCI-e, when it comes to packet injection. 

But as far as im aware, Packet injection is not supported by most usb devices. (reference Aircrack-ng)

So therein lies my problem, I've a 3945 intel card and want a replacement. Since the Card is mini PCI-e i presumed a card of the same type would be sufficient. 

ARGH! please help someone !

Thanks in advance

---

### Post by kg87 on 2008-06-12
:confused: bump?

---

### Post by kg87 on 2008-06-12
still no answers?

---

### Post by kg87 on 2008-06-13
? (sorry this might be getting quite irratating for other forum users!)

---

### Post by rlzyoner on 2008-06-13
I've had no issues with packet injection using built-in wireless.
Ca you inject packets using your existing wireless card and aireplay-ng

Run this code from a terminal to start an injection test

aireplay-ng -9 wlan0 (replace wlan0 with the name of your wireless adaptor)

---

### Post by Alacrity on 2008-06-14
kg87,

You should be fine with your wireless card.  But, you probably need to read read read @ aircrack-ng.org.  It primarily depends on the chipset which can be in either a usb, pcmcia, or pci card.  I use all three and different chipsets within Ubuntu and have full injection capability.

When you download or install aircrack-ng 1.0, you will have airdriver-ng within the aircrack-ng suite.  Type in the terminal "airdriver-ng supported" and it will give you a long list of supported chipsets.

Now in VMWare, that software is limited to USB only.....but that is the only limitation I am aware of....

Enjoy.

alacrity

---

### Post by Fingel on 2008-06-14
Its possible to do packet injection with your 3945. I just successfully cracked a wep this weekend with mine. You do however, have to compile and install another driver. 
The reason why people like USB network cards is because that allows you to use both the USB AND the internal, making the whole process 2x faster.
If you need any help PM me.

---

