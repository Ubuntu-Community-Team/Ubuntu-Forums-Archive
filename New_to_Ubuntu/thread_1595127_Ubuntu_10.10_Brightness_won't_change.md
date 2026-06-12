---
title: "Ubuntu 10.10 Brightness won't change"
date: 2010-10-12
forum: New to Ubuntu
---

### Post by rs87424 on 2010-10-12
I just upgraded to 10.10 yesterday and when I try to change the brightness using Fn arrowLEFT or arrowRIGHT with my Acer Aspire nothing happens.  My screen is stuck at 100% and its blindingly bright for me it gives me a headache.  The brightness app doesn't work either btw

---

### Post by rs87424 on 2010-10-14
I still haven't found a workaround yet

---

### Post by GabrielYYZ on 2010-10-14
you can try compiz, it has an option under accessibility to control brightness. 

if you don't have it, search for compiz in the software center and download "advanced desktop effects settings (ccsm)" and try it, hopefully, it'll work.

---

### Post by rs87424 on 2010-10-14
I got the software and the brightness does change now.  But the only thing I see that is different is how the dimming effects the graphics compared to normal dimming

---

### Post by morad on 2010-10-26
Hi I am having the same problem with a DELL Precision M6400 laptop.
I have had 9.10 and 10.04 installed on this laptop as well and they both recognised the Fn+up and down arrow keys to reduce or increase the LCD brightness but 10.10 does not do that.

Any suggestions would be very much appreciated.

---

### Post by morad on 2011-01-28
Just install the compiz config and then configure the shortkey for brightness

---

### Post by evangelder on 2011-02-05
using compiz doesn't really work for me.

---

### Post by 3602 on 2011-02-05
Try adjusting the slider in Power Manager. My keyboard shortcuts don't work either but I can change it in Power Manager.

---

### Post by evangelder on 2011-02-05
I've tried power manager but that doesn't adjust anything either.

---

### Post by jonnny_j22 on 2011-02-06
you can try xbacklight:
 
sudo apt-get install xbacklight
 
 
then set 40% or 60% brightness
 
$ xbacklight -set 40
 
$ xbacklight -set 60
 
 
 
you can also look in your bios - my old laptop had display settings that could be set to auto - for windows or 'other' - for linux. Note that for me whichever I chose meant that brightness did not work in the other OS.
 
Not a fix I know, but I have also found you can get round it sometimes by turning the laptop on unplugged.

---

