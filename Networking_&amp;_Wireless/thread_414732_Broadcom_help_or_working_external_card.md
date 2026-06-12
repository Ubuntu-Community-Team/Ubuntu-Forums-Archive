---
title: "Broadcom help or working external card?"
date: 2007-04-20
forum: Networking &amp; Wireless
---

### Post by xhentil on 2007-04-20
I have a Dell Latitude d620 with a Dell Truemobile 1390 (Broadcom 4311) running Feisty.

I've tried everything from the bcm43xx-fwcutter to ndiswrapper with appropriate bcm drivers. Thanks to the cutter, I can see wireless networks, with signal strength, but I cannot connect. The network here is my schools, so I cannot access much beyond the key. Network Manager asks me for the key, and after I give it, it will try to connect, then bounce back to wired network.

Wicd didn't work either.

So my question is, does anyone else have any ideas? I never got ndiswrapper to work in Edgy either, so I don't know if perhaps I'm doing something wrong. Inevitably something goes wrong along the way and it never works.

Baring that, does anyone know of an external PCMCIA card that works out of the box with Feisty? I know Atheros chipsets tend to work, but I've seen some problems around as well. Any advice would be welcome.

Honestly, without wireless access on my laptop, Linux has me hamstrung and I'll just move back to my XP partition, which makes me sad.

EDIT: I should also mention that Feisty does read my onboard wireless correctly in lspci, which is a step up from Edgy.

---

### Post by teddmeister2 on 2007-04-24
Have you tried it out on any non protected wireless connections?

What kind of key is the one for your school?  I know that I've had trouble finding the right setting for a WEP key.  Also, have you installed wpa-supplicant and enabled it, if the key is supposed to be WPA?  If not, there's a howto here: [http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html](http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html)

If your trouble is actually with the driver install, could you post output for the following command:
```
ndiswrapper -l
```

---

