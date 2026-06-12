---
title: "ipw3945 no wifi signal"
date: 2007-06-14
forum: Networking &amp; Wireless
---

### Post by raitm on 2007-06-14
Hi,

I installed Ubuntu 7.04 on my clevo based laptop. I made fresh install with winxp dualboot.
Wireless card: 3945ABG.

In winxp intel wireless utility find my neighbours wifi. It works fine with signal level 1 of 5. Intel utility said signal quality is good or very good

Now i made reboot to Ubuntu and in same place there are not any wireless areas in range.

is ubuntu sensitivity or policy so high and it not display low wireless signals?
Sometime it find and 1 time i have been connected to my neighbours wifi with ubuntu, but after restart it still not found signal.

Kernel ...20.16

---

### Post by visik7 on 2007-07-02
same problem here I'm going slightly mad

---

### Post by yakkeh on 2007-07-02
I'm getting a similar problem wih my ipw3945... but it USED to work good, until I updated from edgy to feisty today.
At a certain point it asked me to install the restricted modules for better featured video card (7600 Go). Since then, I'm having the worst nightmare with this card!

The signal is strong but the problems are as follows(only in Ubunty Feisty):
- No DHCP, only static IP configurations work
- When I go to the network settings, my wireless card sometimes says "Wired" ... wth?? I wouldn't be bothered if it weren't that I couldn't fill in the SSID.
- 90% of the time there's no signal detected. It just comes and goes as it pleases. ifup and ifdown work (i think) but have no effect on the connection.

I have no WEP or WAP enabled on my wireless router (i know...) and there's only 1 other wireless network in range on a different channel.

Is there any way to roll back the drivers for this card to the previous ones? Is there any way to only use the restricted modules for my graphics card and the previous ipw3945 driver for my net?

I'm pretty sure something simple is wrong and I prefer to avoid downloading the whole ubuntu cd and going through a whole new installation process.

---

