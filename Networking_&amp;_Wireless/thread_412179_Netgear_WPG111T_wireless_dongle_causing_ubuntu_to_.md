---
title: "Netgear WPG111T wireless dongle causing ubuntu to crash"
date: 2007-04-17
forum: Networking &amp; Wireless
---

### Post by mstep on 2007-04-17
Right- this is driving me crazy. I haven't used Linux for a couple of years and the other day I decided to install Ubuntu on an old system. It uses a Netgear WG111T wireless usb dongle. Little did I know how much Ubuntu HATES wireless of all forms, particularly this form it seems.

After hours of tinkering and getting frustrated, I eventually managed to get it working (if anyone needs help with this since there's not much around on the net for v6.10, I'd be happy to post a guide). 

However, after about 5 minutes my whole system crashed. I can start up with the usb dongle plugged in, but it's only a short matter of time before the next crash. When I start without plugging in the dongle, things are fine (except obv. no internet access whatsoever), if then I plug it back in, after a while, things eventually grind to a halt. I've tried reinstalling Ubuntu, but to no avail.

I am loving Ubuntu at the moment, it's been a delight to use after my first brush with Linux (Debian- not fun to install OR update when you're still a newbie), but if I can't resolve this issue then I'm going to have to switch to something else and that's something I really don't want to do.

Any help would be hugely appreciated! :D

---

### Post by mstep on 2007-04-18
*bump* I could really use some help here!

---

### Post by DraeLee on 2007-04-18
your not the only one.  I install the drivers from the disk and it says hardware present but soon as I see that (in ndisk) the system freezes up.  Its reallllly annoying to say the least. any help would be appreciated.

---

### Post by mstep on 2007-04-29
Well it's reassuring to know that I'm not alone. It's just frustrating that after all the trials of getting it to work, finally I have internet access, only to have it snatched away again. :(

---

### Post by rizwanjavaid on 2007-04-30
I had loads of problems getting wireless to work under 6.10. I found that ndiswrapper was broken and had trouble upgrading it to the latest version. So what I did was to downgrade to 6.06 and then use the ndiswrapper that came with it. It worked a treat and also I have WPA-PSK enabled thru wpa_supplicant.

Anyone needing any help with it let me know. By the way my wireless card is the USB Netgear WG111T.

Regards,
Riz

---

