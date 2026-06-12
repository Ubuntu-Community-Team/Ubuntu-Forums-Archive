---
title: "rt2500usb Wireless Problem"
date: 2007-04-25
forum: Networking &amp; Wireless
---

### Post by SnoutUK on 2007-04-25
Hiya guys! I gots me a little problem!

I was using 6.10 Edgy for a while, using ndiswrapper and the windows drivers for my Belkin USB WIFI Stick. as mentioned in the title here it uses the rt2500 chipset. Any way, end of the story it worked great! The time then came to upgrade to 7.04 Feisty Fawn! Soon as it rebooted after the upgrade my wireless would no longer work! ndiswrapper says the hardware and drivers are fine. But the network manager shows no networks and it fails to connect manually!

Anyone got any ideas how to get around this??

Thanks

---

### Post by SwaroopKunduru on 2007-04-25
Hi All,

This exactly is my problem. I did a clean install also I did not see wireles card in network manager Please look at my attachment.

Regards,

Swaroop.

---

### Post by SnoutUK on 2007-04-25
So glad to see im not alone in this world lol! I heared a clean install would work fine.
I just noticed that Feisty tried installing the wrong drivers. So feisty installed the wrong driver, thus the USB wouldnt work and it completely ignored my ndiswrapper. So later im going to try doing a clean install from the CD WITHOUT my USB device plugged in. When its installed, plug it in, do the ndiswrapper stuff, and hope for the best!

---

### Post by cliff01 on 2007-04-25
I did a clean install without my Belkin stick plugged in. I then plugged it in and  "lsusb -v" showed it listed, but it's not functional. I'm going to try a clean install with it plugged in.... or just go back to Edgy. Linuxant worked for me there.

---

### Post by SnoutUK on 2007-04-25
> **cliff01 said:**
> I did a clean install without my Belkin stick plugged in. I then plugged it in and  "lsusb -v" showed it listed, but it's not functional. I'm going to try a clean install with it plugged in.... or just go back to Edgy. Linuxant worked for me there.

Did you try using ndiswrapper?

---

