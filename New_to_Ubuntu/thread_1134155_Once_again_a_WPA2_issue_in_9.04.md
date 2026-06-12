---
title: "Once again a WPA2 issue in 9.04"
date: 2009-04-23
forum: New to Ubuntu
---

### Post by lodravah on 2009-04-23
Ubuntu 9.04 on MSI Wind - WPA2 - issue.

Hey all.

This is a repost of a previous one.

Just ran a Live-session from my USB, and sadly I still have a problem with logging in to a WPA2-encrypted wireless network run from a Mac-router.. I get hex in the "password"-field and endless attempts at login. 

I did get some instructions from a helpful forum-member, but the construction of a wpa_supplicant was a bit technical for me. So I decided to wait for 9.04 to see what happened. And exactly the same was the result. It did recognize the Ralink RT2700-wireless without installing any drivers, and that is good. I'm guessing that wireless will work most of the time, but I'd like to get rid of my D-Link G-USB WiFi Dongle that I've been using since I nuked XP from my Wind.

So, I ask if anyone else have this problem. And I wonder if anyone has an "how-to" for making a wpa_supplicant - file.

Also, Bluetooth did not seem to want to be activated using the Fn-F11.

Would appreciate any help on this.

Other than that 9.04 looks great

---

### Post by kmoz on 2009-04-24
Seeing the exact same issue on an Acer InspireONe - my WPA2 code is being converted to hexadecimal, and endless login attempts ensue.  Detecting other networks just fine.

---

### Post by Peter09 on 2009-04-24
Your passphrase is always hexadecimal, the alphanumeric phrase that you type in is just for convenience.

The problem is with the driver. 

Lokk at this thread for the Aspire One
[http://ubuntuforums.org/showthread.php?t=1105218](http://ubuntuforums.org/showthread.php?t=1105218)

It may be that the MSI WInd is similar

---

### Post by kmoz on 2009-04-24
yep, ty that post is what did it for me, forced it to use athk5 driver.

---

### Post by spydon on 2009-04-24
I got the same problem with eeepc 901, with 9.04.
I didn't have the problem in 8.10 but I might have fixed it there...

---

