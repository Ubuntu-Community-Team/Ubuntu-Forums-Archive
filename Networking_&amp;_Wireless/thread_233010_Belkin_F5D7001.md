---
title: "Belkin F5D7001"
date: 2006-08-09
forum: Networking &amp; Wireless
---

### Post by alecjw on 2006-08-09
I have a Belkin F5D7001 network card with a broadcom 5 chipst I think it's 5). I can't seem to install it. Here's what i've tried:

First i blacklisted the bcm43xx driver.
I then installed ndiswrapper-utils.
I copied the files for the card from the cd to /wireless/ (bcmwl5.inf and bcmwl5.sys)
I ran in the terminal:```

sudo ndiswrapper -i /wireless/bcmwl5.inf
sudo ndiswrapper -m
```
When i ran ndiswrapper -l, it said that the driver was working and the card was present.
The next time  i booted up my computer, it got to "Configuring network interface" and then stopped there, even when i booted it in recovery mode.

Please, please, please could someone help? This problem is the only thing stopping me from migrating to linux!

Thanks in Adavance
Alec

---

### Post by tagra123 on 2006-08-09
This thread may help. Only one of three of the Belkin cards I have even required the ndiswrapper. 

[http://www.ubuntuforums.org/showthread.php?t=42697](http://www.ubuntuforums.org/showthread.php?t=42697)

---

### Post by alecjw on 2006-08-09
Nope. Still got the same problem. Have to ctrl+c during boot and then the interface doesn't show up. Any other ideas? Anyone?

---

### Post by Dirkomatic on 2006-08-09
I gave up on that card after futzing with it for a week.  bcm43xx wouldn't work; ndiswrapper with bcwlm5 or bcmwl5a never worked...  I tried everything...  I finally broke down and bought a cheap RT2500 based card from newegg.

I still have the card if anyone wants to give it a whirl.  I don't need it anymore... ;)

---

### Post by alecjw on 2006-08-10
> **Dirkomatic said:**
> I gave up on that card after futzing with it for a week.  bcm43xx wouldn't work; ndiswrapper with bcwlm5 or bcmwl5a never worked...  I tried everything...  I finally broke down and bought a cheap RT2500 based card from newegg.

I still have the card if anyone wants to give it a whirl.  I don't need it anymore... ;)
Gonna have to start saving up my pocket money then! Any idea what the cheapest PCI or USB wireless card which works out of the box is?

---

### Post by Dirkomatic on 2006-08-10
The PCI card I got was a NovaTech NV-926W.  It was $22 after shipping.  I haven't tested range or speed yet, but setup was a breeze and it definitely connects.

---

### Post by sidlinux on 2006-08-10
I had problems with those cards some time ago.  Although I got them working with ndiswrapper, it froze my machine after being on for a few hours and had to give it the one finger saluete (press the reset key).  Eventually, I decided to give it up.

Thus, I'll make sure for now, I use a card that has worked out of the box, that is, it's supported by Ubuntu when booting off a live CD with little or no configuration.

Sidney

---

### Post by alecjw on 2006-08-10
I think i'll sell my 7001 on Amazon for £25 or so (seems to be the going price) and get this: [http://www.amazon.co.uk/gp/product/B000ANZJQC/ref=pd_rvi_gw_1/026-3679983-2983619?ie=UTF8](http://www.amazon.co.uk/gp/product/B000ANZJQC/ref=pd_rvi_gw_1/026-3679983-2983619?ie=UTF8)
It is listed as nearly working out of the box, so it should be fine.
Quote wiki WifiDocs/WirelessCardsSupported:
> 
DAPPER: Nearly works out-of-the-box, but had to add "wireless-rate 11M" to /etc/network/interfaces + reboot or two. BREEZY: Works out of the box with breezy. Works well, even with WEP. (Note: Some G520 may use acx100 instead.) HOARY: Rev. B of this card will not work out-of-the-box with Hoary--the madwifi drivers that shipped with Hoary are too old. An updated linux-restricted-modules* package is available  here Note that this package is not officially supported. Some users have reported problems with WPA in the forums.


---

