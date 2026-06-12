---
title: "Cant get SpeedTouch 121g to work with Ndiswrapper"
date: 2007-02-16
forum: Networking &amp; Wireless
---

### Post by Mexxus on 2007-02-16
Hi,

I try to get my wireless USB SpeedTouch 121g device to work with Ndiswrapper, and i'm using this nice howto to help me trough it:

[http://www.ubuntuforums.org/showthread.php?t=245651&highlight=speedtouch+121g](http://www.ubuntuforums.org/showthread.php?t=245651&highlight=speedtouch+121g)

Nice. I installed NDiswrapper-utils-1.8 and installed the .inf file into ndiswrapper. After i checked ndiswrapper -l, it says "driver present", but no "hardware present". I tryed to place the device in an other USB port, but is doesn't work. the light on the device isn't on either.

Somebody knows why this thing doesn't say "hardware present"?

By the way, I'm using a fresh install of Ubuntu Edgy Eft with reps from DVD-Rom.

---

### Post by Floppyjoe on 2007-02-16
How many different .inf files were on the CD you installed the driver from?
Or did you get drivers from elsewhere.
If there are different versions for lets say windows 2000, XP,98 etc., then maybe try a .inf and .sys file from a different version of Windows OS.
The driver you are using with ndiswrapper doesn't recognize your device so you'll need to try a different driver.inf file if that is possible.

Edit: Also make sure if there is a .bin file there it should also be in the folder where you install the driver from.

---

