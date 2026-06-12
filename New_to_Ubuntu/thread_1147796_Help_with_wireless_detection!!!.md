---
title: "Help with wireless detection!!!"
date: 2009-05-03
forum: New to Ubuntu
---

### Post by VyperX on 2009-05-03
Hello, I am a noob at linux, and I just installed Ubuntu 8.10 (32-bit) on my Toshiba Satellite A215-S4767 but it doesnt detect my wireless crad but I actually have one.

I did lspci -nn and it said that I had this wireless card AR5007EG
any help will be appreciated!

---

### Post by supersonicdarky on 2009-05-03
see [this](http://ubuntuforums.org/showpost.php?p=5112530&postcount=5)

---

### Post by VyperX on 2009-05-04
Does the guide above this post really work?

---

### Post by swoody on 2009-05-04
Heya VyperX!

On my fiancée's Toshiba Satelite the wireless worked out of the box, so you may be lucky in that your driver might come with Ubuntu by default, but it just might not be activated. Try going to System>Administration>Hardware Drivers and check to see if there's a driver in there. If there is, you'll just have to activate it, and then restart your computer for it to work. If there is more than one wireless driver in there, just pick the one that says 'Recommended' and try using that one to start off with.

Let us know if you have any drivers in the 'Hardware Drivers' section, or not - and if they worked to get your wireless up :)

---

### Post by VyperX on 2009-05-04
> **swoody said:**
> Heya VyperX!

On my fiancée's Toshiba Satelite the wireless worked out of the box, so you may be lucky in that your driver might come with Ubuntu by default, but it just might not be activated. Try going to System>Administration>Hardware Drivers and check to see if there's a driver in there. If there is, you'll just have to activate it, and then restart your computer for it to work. If there is more than one wireless driver in there, just pick the one that says 'Recommended' and try using that one to start off with.

Let us know if you have any drivers in the 'Hardware Drivers' section, or not - and if they worked to get your wireless up :)

There's actually one driver, it's activaed  but it just doesnt work:
[http://img21.imageshack.us/img21/7015/atheroshad.png]("http://img21.imageshack.us/img21/7015/atheroshad.png")

---

### Post by swoody on 2009-05-04
> **VyperX said:**
> There's actually one driver, it's activaed  but it just doesnt work

Just to make sure, you've restarted your comp since you activated that driver, correct?


Have you tried out the link that supersonicdarky posted above? You may want to give that a try, and see if it will work for you. Or if you are running 64bit Ubuntu try this one:
[http://ubuntuforums.org/showthread.php?t=512828](http://ubuntuforums.org/showthread.php?t=512828)

or for a 32bit Ubuntu, try this one:
[https://help.ubuntu.com/community/WifiDocs/Driver/Atheros](https://help.ubuntu.com/community/WifiDocs/Driver/Atheros)
If you try this version, make sure to try out the ath5k package it mentions at the very beginning of the page BEFORE you continue on with the rest of the page.

Try those out, and let us know if they work or not. 
It seems like a lot of people have had troubles with the same card, so if none of the above works I'll try to find some more info about that card for you :)

---

### Post by VyperX on 2009-05-04
> or for a 32bit Ubuntu, try this one:
[https://help.ubuntu.com/community/Wi...Driver/Atheros](https://help.ubuntu.com/community/Wi...Driver/Atheros)
If you try this version, make sure to try out the ath5k package it mentions at the very beginning of the page BEFORE you continue on with the rest of the page.


Thank you so much for   your support I finally did it! I'm so happy... I'm glad you could help me...


thank you once again,

Best wishes,

VyperX

---

### Post by swoody on 2009-05-04
Glad it worked for you :)

If you have any other issues with your wireless, or anything else, don't be shy of the forums, there's always a lot of helpful and knowledgable people on here that can help you out with any issue you may have :D

---

