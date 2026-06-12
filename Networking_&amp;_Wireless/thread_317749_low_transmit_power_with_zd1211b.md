---
title: "low transmit power with zd1211b"
date: 2006-12-12
forum: Networking &amp; Wireless
---

### Post by thartley on 2006-12-12
Hi,

I recently got my Airlink USB wireless dongle with a zd1211b chip working with Dapper thanks to the postings here.  Or so I thought.  As long as the laptop is close to the Access Point, it works fine.  It only transmits at 11mbps, but that is to be expected with USB 1.1.  

The problem is that apparently it isn't transmitting with much power because if I move the laptop away from the AP, after about 10 feet it can't ping the AP.  The receive signal strength is 98% - 100%, so the AP is getting to the dongle just fine.

I'm using the zydas r83 version of the driver.

My questions:

What is the typical transmit power for this chip?

How can I determine what mine is tranmitting at?

How can I increase the transmit power?

Would using a different version of the driver make any difference?

Thanks.

Edit -

After digging around on the 'net a little more, I found that there are two options under the *iwconfig* command (*power* and *txpower*) which can be issued that should allow me to determine what the current transmit power setting is and allow me to set the transmit power.  I have come to the conclusion that these options are not available within the driver for this dongle because when I issue either one, I get a message indicating that it is not supported.  I haven't tried the earlier versions of the driver to see if they have this capability.

I gave up using the dongle on the laptop in favor of an Airlink wireless PCMCIA card.  I plugged it in and it almost worked out of the box.  I say almost because I had to fool around a little to remove the wlan0 portion from the Network Configuration area under the System pulldown before the PCMCIA card would show up as ath0 in that dialog box.  It showed up under ifconfig or iwconfig right away (I forget which right now), but it wouldn't actually work until I got rid of the wlan0 stuff.

For my needs, this is actually a better solution on my laptop because I'm not using the PCMCIA slot for anything else, it frees up a USB port for a thumbdrive or mouse, and the PCMCIA dongle is better protected than the USB dongle if it were to get bumped.  The way the USB dongle stuck out from the side of the laptop, it seemed too vulnerable to damage to the connection.

---

