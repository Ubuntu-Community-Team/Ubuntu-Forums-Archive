---
title: "Problem with Open Office menus"
date: 2009-04-09
forum: New to Ubuntu
---

### Post by rtowsley on 2009-04-09
Hello, I have installed ubuntu 8.10 and everything works fine except in Openoffice the menus do not have any words. The menus items at the top (File edit and so on) all are just lines (-). The drop-down menus are also the same. I have only found this in all the Open Office programs and in Koffice write. Do I need to turn something on or off? or what? Rich

---

### Post by LowSky on 2009-04-09
Are you using a different theme. Some themes do not play well with Open Office, try switching back to one of the included themes like human, and see if the menus come back

---

### Post by Jakey_TheSnake on 2009-04-09
Try this thread: 

[http://ubuntuforums.org/showthread.php?t=1118747](http://ubuntuforums.org/showthread.php?t=1118747)

---

### Post by rtowsley on 2009-04-09
I tried changing the themes with not change in the menus.

---

### Post by Jakey_TheSnake on 2009-04-09
Okay, my bad, thread above was useless. This one is good: [http://ubuntuforums.org/showthread.php?t=1027622](http://ubuntuforums.org/showthread.php?t=1027622)

> - Problem solved (for me) by running "sudo dpkg-reconfigure fontconfig-config" and selecting "Autohinter", "Always" (for subpixel rendering on my LCD display), and "No" for Enable bitmapped fonts. Then, I changed Ubuntu System/Preferences/Appearance/Fonts to "Subpixel" smoothing. Viola! Problem solved.

---

