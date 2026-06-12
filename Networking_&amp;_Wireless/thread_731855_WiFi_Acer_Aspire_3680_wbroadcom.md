---
title: "WiFi Acer Aspire 3680 w/broadcom"
date: 2008-03-22
forum: Networking &amp; Wireless
---

### Post by mattmenger on 2008-03-22
I'm having issues with getting my wireless drivers recognized.  I saw a similar post from an Aspire 3680 user who was lucky enough to have an Atheros that worked immediately.  I've tried ndiswrapper, but it doesn't like my .inf file from windows.  I'm not all that experienced, so anything you can tell me is appreciated!  My broadcom built-in wifi doesn't want to work.  

Acer Aspire 3680
Intel Celeron M 1.86
2 gig ram
160gb HD
Broadcom 802.11b/g

---

### Post by Sam Lars on 2008-03-22
Are you using Ubuntu 7.10?
What does
```
lspci
```
say that your card is?
If you can find it [here]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list/"), try using the firmware that it links to.
Also, does the card show up in Restricted Drivers?

---

### Post by mattmenger on 2008-03-22
Thanks for the help!  Here's what lspci gives me:

03:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)

I looked it up on the link you sent and I didn't see it there.  

I've tried running ndiswrapper with a .inf file I found on the Acer website, and it accepted the driver but the wireless still didn't work.

---

### Post by bremedios on 2008-03-24
I'm having some issues getting this laptop with the same Broadcom Wifi (802.11g) wireless card to work.  I'm suspecting that it may be a problem with the wifi switch (perhalps it's really a software power switch rather than one that is actually using hardware to enable / disable power to the radios.)

lspci: 03:00.0 Network Controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01).

It will show up in ifconfig / Network Manager as an networking device but is unable to locate any access points or communicate in any fashion over the wireless link.

No matter how many times the wifi switch is toggled (at the front of the laptop) the wifi refuses to work (the light is always off.)  Under Windows XP it has been observed that the Light goes on when the Wifi is off.

Please note, this laptop originally did come with Vista but has since been replaced with Ubuntu 7.10 and Windows XP.  Currently, Windows XP is on this laptop simply for wifi connectivity.

Does anyone have any suggestions?  I would rather not have to install ndiswrapper if I can at all avoid it.

Regards,
Brad.

---

### Post by bremedios on 2008-03-24
It seems that I had missed a step in my configuration which was to enable the firmware under the "System->Administration->Restricted Drivers Manager".

After enabling the firmware and rebooting the laptop everything is now working using the native drivers.

I hope that this helps others as well, more information for Gutsy may be found here:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy)

Regards,
Brad.

---

### Post by mattmenger on 2008-03-24
I'll try that out and see what happens.  With ndiswrapper and a driver from the Acer website, I was able to get Ubuntu to see the card, but it still didn't work.  I haven't tried the Restricted Drivers Manager yet, but I'll let you know if it works for me.  I'm still pretty new to all this!

---

### Post by mattmenger on 2008-03-24
Well, I'm in ubuntu 7.06, and when I go to the Restricted Drivers Manager all I get is "Your Hardware does not need any restriced drivers."

Help!

---

