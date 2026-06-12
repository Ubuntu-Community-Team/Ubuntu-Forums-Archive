---
title: "(Lubuntu) Was this normal?"
date: 2016-06-28
forum: Networking &amp; Wireless
---

### Post by musicalrose6084 on 2016-06-28
Hi all this is my first time posting in the forums but I have used ubuntu, ubuntu mate and lubuntu before. I did go back to windows for awhile in all honesty. So after I saw that 16.04 came out I decided to switch back to linux and use Lubuntu sicne well my cpu doesn't meet the 2ghz requirements. Anyway I put the new lubuntu 16.04 on a usb using universal usb installer. SInce when I tried rufus it said it would download an old version of syslink for some odd reason. So had to use universal usb installer. 

Anyway I made the usb I booted it up and choose try lubnutu without installing. Everything worked except the wifi. So figured maybe it would work if I installed it, So I installed it and got a lot of errors saying it couldn't connect to servers during the install. Figured mostly do to no wifi. So it gets done installing I boot it up and find that wifi was installed and working. 

So wondering is the USB not supposed to have wifi? I remember in 14.04 it did on the usb but now it doesn't, So wondering is that normal or should I make a new usb?

---

### Post by bearlake on 2016-06-28
Hi, not all can be loaded into memory from try live.
It seems your wifi driver was in the installation install and was installed on your media during installation.
Just enjoy the install without making a new usb.

---

### Post by musicalrose6084 on 2016-06-28
Ah OK I made a new USB just in case and yeah you are probably right the same thing happened. So I guess it is normal anyway thanks for responding and sorting it out.

---

### Post by X-RED_Tech on 2016-06-28
The previous post isn't really helpful so I'll try to make things clear for you while taking the chance to educate you and other user.

First things first, > [COLOR=#000000]So wondering is the USB not supposed to have wifi?[/COLOR]
The answer is no, it isn't.
The installation media (as well as the installed system) has support for a vast array of different hardware parts but it can't possibly support out of the box each and every piece of hardware out there. No OS can!
Some hardware requires proprietary (closed source) drivers and/or firmware and some aren't even legal to distribute with the Ubuntu installation media. Many WiFi devices are affected by this and yours is probably one of them.
So, not having out of the box support for a certain piece of hardware doesn't mean there's something wrong with your installation media. 

I suggest you temporarily use an alternative internet connection - Ethernet(LAN cable) or other - and follow this preliminary troubleshoot instructions (the sticky thread in this section): [http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)

---

