---
title: "Netgear WG511v2 install probs"
date: 2007-01-21
forum: Networking &amp; Wireless
---

### Post by Moffind on 2007-01-21
Having some problems with the Netgear WG511v2 (china) card.

Installed so far using Dapper, Ndiswrapper-1.34 and Marvell driver *Libertas 802.11b/g Wireless v2.3.0.19* from [http://www.station-drivers.com/page/marvell.htm](http://www.station-drivers.com/page/marvell.htm).

Using the all the Netgear drivers from the CD didn't work.

Using *ndiswrapper -l*I get the message: 

mrv8ka51 : driver installed
        device (11AB:1FAA) present (alternate driver: mrv8k)

So it can find the card and the driver, but there's no light on the card.

I blacklisted a number of items early on:

 *prism54*
 *islsm_pci*
 *islusb*
 *isl3886*

is this correct?


I've done a *modprobe* for ndiswrapper and rebooted.

I'm not sure what to do next?

Running through the *iwconfig* nothing happens.....help please, simple step by step instructions if you can I'm new to all this.

Thanks Moff

---

### Post by foofi22 on 2007-03-12
Hi Moff

I have managed to get my Wg511v2 working on my Dapper comp.  Although from your post I noticed you are using ndiswrapper 1.34, I am currently using 1.8 and I recommend you update using ```
sudo apt-get install ndiswrapper-utils-1.8
```

 I also found the Netgear drivers do not work, I am using the mrv8335 driver.  Doing this managed to get the light on the card blinking but not connecting to my AP. (Ihad to do some extra stuff after this which I will tell you when you get this stage)  Your blacklist looks similar to mine (I'm not on my comp atm) but I would recommend adding mrv8k to your blacklist and finding the file mrv8k and deleting it. Again I found the mrv8335 driver works, sorry I can't remember exactly where I got it but if you like I can try emailing it to you.

---

