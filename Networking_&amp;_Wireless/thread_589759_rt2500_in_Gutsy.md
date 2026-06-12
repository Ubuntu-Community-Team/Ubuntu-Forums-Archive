---
title: "rt2500 in Gutsy"
date: 2007-10-24
forum: Networking &amp; Wireless
---

### Post by renzokuken on 2007-10-24
i read somewhere (forgot where!!) that wireless cards based on ralink rt2500 chipsets are supported by default and should work out of the box now with Gutsy.

is this true, and if so does it work for both 32 and 64 bit Gutsy???

---

### Post by odiseo77 on 2007-10-29
Hi, well, to answer your question, I think Gutsy changed from the legacy rt2500 driver to the integrated rt2x00 driver, but it seems it's not working good for everyone (have a look at [this]("http://ubuntuforums.org/showthread.php?t=582033&highlight=rt2500")). However, not everything is lost, you can always follow [this guide]("http://ubuntuforums.org/showthread.php?t=584657&highlight=rt2500") if you want to use the native linux driver, or [this one]("http://ubuntuforums.org/showthread.php?t=564419") if you want to use ndiswrapper (I personally prefer using the native linux driver). 

Regards.

---

### Post by renzokuken on 2007-10-30
thanks for the reply odiseo, i managed to get it working fine with the native driver (serialmonkey one !?!)

---

