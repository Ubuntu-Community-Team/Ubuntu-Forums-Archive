---
title: "Must run restricted driver manager after every reboot - Gutsy + Dell 1521"
date: 2007-11-07
forum: Networking &amp; Wireless
---

### Post by savejonas on 2007-11-07
I have a Dell Inspiron 1521 laptop with the Broadcom Wireless chipset. I got the restricted drivers manager enabled for the wireless firmware, but after I restart the computer, I have to disable the driver and then re-enable the driver to make the system recognize my wireless.
I haven't seen this problem in any other threads. does anyone know what could cause this?
Thanks

---

### Post by savejonas on 2007-11-08
I worked on this all night last night, but no luck. Any ideas?

---

### Post by emja on 2007-11-15
Same problem here with Dell Inspiron 1501. I still can't work out the fix, other than to format and reinstall.

---

### Post by chrisb345 on 2008-03-31
I have the same issue i tried the link below
[http://ubuntuforums.org/showthread.php?t=405990&highlight=1390](http://ubuntuforums.org/showthread.php?t=405990&highlight=1390)

this didn't work for me but maybe it will for you. Otherwise i am having to use a USB dongle for my wireless PLEASE find a fix.

I would have thought ubuntu supported dell wireless drivers.

---

### Post by kxr1der on 2008-03-31
yea especially since dell offers ubuntu on their pc's now

---

### Post by soslug on 2008-04-10
I haven't seen this problem myself but I suspect the firmware drivers rather than the restricted drivers have not been installed.  I have noticed during a Gutsy install  that you can elect to install Firmware drivers during the first installation of restricted drivers, Thereafter you can try to reinstall all you like but you don't get the option for Firmware drivers during a re-install. You could try sudo apt-get remove bcm43x please make sure you are connected to an active lan port before re-installation of restricted drivers ensure you click to download firmware drivers then it should work. hope this helps

---

