---
title: "WEP Cracking with Broadcom Chipsets?"
date: 2008-04-03
forum: Networking &amp; Wireless
---

### Post by Jason2gs on 2008-04-03
I saw a Howto around here about how to crack WEP keys using the aircrack suite.

However, it mentioned something about having Madwifi already installed. I'm on a Broadcom chip, so I can't use Madwifi.

Is cracking WEP keys with Ubuntu a lost cause to people who aren't using Atheros wireless cards?

Thanks,

-Mike

---

### Post by pseudo-random on 2008-04-03
No but it helps.
Broadcom? AFAIK that requires a kernel recompliation which you need like a hole in the head.
If you've got a PCMIA slot get an orinoco card, it's way more sensitive than a built in Broadcom job.

---

### Post by Jason2gs on 2008-04-03
Well shoot :(

I don't have a PCMIA slot.

What did you mean by "Hole in the head"?

---

### Post by syga on 2008-04-03
I tried using aircrack on my dell with a broadcom, some people claimed it worked, but I never got it to work. 

I use the linksys wusb54g usb wireless adapter. You can pick them up on ebay. Just make sure it's version 4, it will have the ralink chipset. Instructions to download and install the drivers are on the aircrack website.

---

### Post by kevdog on 2008-04-03
Supposedly Ive read aircrack can be used with the b43 restricted drivers (possibly bcm43xx drivers also) although I never tried.  I bought an atheros card that uses madwifi specifically for the purposes of playing around with the aircrack suite.  Its somewhat complicated.  To alleviate some of the confusion I would recommend an atheros based card unless you are into some heavy duty reading. 

And if you are successful with the bcm card, a HOW-TO would be greatly appreciated. 
Good Luck!!

---

### Post by Jason2gs on 2008-04-04
Well, I can still use Airodump-ng, if I want, to do the crack, start to finish. It's just that I can't enable monitor mode, which means I'll have to collect packets for days if I want to get anywhere.

On Aircrack's compatibility page ([here]("http://www.aircrack-ng.org/doku.php?id=compatibility_drivers&s=supported%20wireless%20cards")), and it says that they're working on Broadcom w/ b43 wireless drivers.

Does that include b43legacy, or just b43?

Because I recently installed b43legacy. Let's hope they get it working :)

Edit:Update. I guess I can enable monitor mode, and it does record the packets. It's just that it takes forever.

---

### Post by RelativelyQuantum on 2008-04-04
I was trying this out myself, with no luck even on the install. Ever consider another cracking program?

[http://sectools.org/crackers.html](http://sectools.org/crackers.html)

You might still need to use an external wifi adapter though - might I ask whether you're using a macbook?

---

### Post by Jason2gs on 2008-04-05
I'm not. I'm using a Compaq Presario V5305WM.

---

### Post by tgalati4 on 2008-04-05
I have used KisMac on a powerbook under OS X.  The internal card is based on a Broadcom chipset.  I have also used a pcmcia netgear card which has an atheros chip.  I was able to get both cards into passive (sniffer) mode.  This is needed so that you can passively monitor packets across several channels.  Otherwise the card will constantly send an active ping to find an access point.

KisMac was easy to set up.  Kismet under Ubuntu was an absolute pain to set up, but once done, it worked as well as KisMac.  

Combined with a USB gps and you can walk through an urban area and make a neat map of the wireless hotspots.  I don't advocate WEP cracking, unless it's strickly for academic purposes.

Does anyone know the cracking time difference between a 64-bit and 128-bit WEP key?

---

### Post by Jason2gs on 2008-04-05
Well, I can sniff alright. It's just that it takes forever as it is.

I was told by a friend that if I can't use packet injection, it'll take days of monitoring before you have enough IVs for a clean crack.

---

### Post by kevdog on 2008-04-05
It would depend on the amount of traffic or packets that are being passed on the network you are trying to crack.  With packet injection you can generate traffic (or inject packets to get a response from the router), so it greatly speeds up the time needed to collect enough packets so a statistical analysis can be done to guess and crack the WEP key.  Again with low traffic networks, you should probably buy another card that would support packet injection, such as an Atheros chipset based card supported by the madwifi drivers.

---

### Post by wareagle on 2008-05-08
I have a Broadcom 4306 R3 and I'm using b43 drivers.  I can put it into monitor mode but only if I do it this way:

```
sudo ifconfig eth1 down
sudo iwconfig eth1 mode monitor
sudo ifconfig eth1 up
```

Has anyone been able to do this without disabling the card first?  With the bcm43xx driver in Gutsy, I didn't need to do it.

---

