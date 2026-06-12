---
title: "Can I direct WUBI installer to .iso file in stead of downloading?"
date: 2010-05-10
forum: New to Ubuntu
---

### Post by spydeyrch on 2010-05-10
Does anyone know how, and if it is even possible, to direct WUBI to use an already existing .iso of ubuntu instead of needing to download it, again? I mean, why would it need to download the .iso of ubuntu when WUBI is already located in/on the same .iso that is being used to start WUBI?

I am trying to install WUBI on a friends computer via a live usb thumb drive. Wubi wants to download the ubuntu .iso but it is already located on the live usb thumb drive. So I am wondering if I can redirect WUBI to use the already existing .iso. My friends ISP is a horrible one, Clear. It is a wireless broadband ISP and it really is a horrible connection.

Any ideas?

I thought that maybe it was downloading the .iso (again) because it is a live usb and not a normal CD. So I tried downloading the  x32 .iso of ubuntu 10.04, hoping that it wouldn't need to re-download the .iso. But I ran into a completely different set of issues there. I started a thread for those issues [here.]("http://ubuntuforums.org/showthread.php?t=1479071")

So, any suggestions on how to re-direct WUBI to use the .iso that it is included on/in or if needs be, to a separate one on the same machine?

Hopefully that is clear enough. Thanks for the help!!

-Spydey :lolflag:

---

### Post by Paqman on 2010-05-10
Yes, that's possible. Just make sure the .iso is in the same folder as wubi.exe when you launch it. Make sure you're selecting the right options (desktop environment, 32/64-bit, etc) for the .iso you've got.

---

### Post by philinux on 2010-05-10
[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20install%20Wubi%20on%20a%20machine%20with%20no%20internet%20connection?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20install%20Wubi%20on%20a%20machine%20with%20no%20internet%20connection?)

---

### Post by spydeyrch on 2010-05-10
Awesome! Thanks guys for the info. I am at work right now so I will have to try it once I get home.

I find it unusual that when using the .iso file to create a live usb thumb drive, and then via that thumb drive, install WUBI, that WUBI wouldn't use the already exisiting files present on the live usb thumb drive.

There must be some changes that take place when converting from the .iso to the liv usb thumb drive that don't allow wubi to use it. Just me rambling out my thoughts. :)

Thanks again.

I will report back later.

-Spydey :KS

---

