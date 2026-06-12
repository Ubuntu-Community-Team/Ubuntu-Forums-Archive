---
title: "RT73 / DWL-G122 C1 driver loading"
date: 2006-11-03
forum: Networking &amp; Wireless
---

### Post by oo00oo on 2006-11-03
Hi,

I had my wireless card (DWL-G122 (v. C1) working perfectly under 6.06 using the RT73 drivers.
I then upgraded to 6.10 and it seems to have a wireless driver for my wireless card built it BUT this wireless driver does not work! The only way to get my wireless driver to work is to remove the default wireless driver (RT73usb) by running

modprob -r rt73usb

then reloading the original rt73 drivers through insmod

insmod rt73.ko

and then the wireless card will work! Is there any way to firstly stop Ubuntu calling the rt73usb driver and secondly run my driver by default?

Thanks alot for your help! Matt

---

### Post by oo00oo on 2006-11-04
Ok I think I have answered the first part of my question myself. To stop the driver loading I can blacklist it as followed:

Open the blacklist file:
sudo gedit /etc/modprobe.d/blacklist

and adding to the end:
blacklist rt73usb

But still not sure how to load my driver rt73 at boot! any ideas? Or even just when the wireless card is inserted?

---

### Post by FrodoB on 2006-11-09
If they are installed correctly they should just load when you insert the device.

See my response to the following post:

[http://www.ubuntuforums.org/showthread.php?t=296281&highlight=rt73](http://www.ubuntuforums.org/showthread.php?t=296281&highlight=rt73)

---

