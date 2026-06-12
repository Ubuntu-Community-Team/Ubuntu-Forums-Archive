---
title: "Atheros Wireless not working"
date: 2009-08-20
forum: New to Ubuntu
---

### Post by labrat256 on 2009-08-20
I've just installed 9.04 on my Toshiba Equium, dual booted with Vista. I'm trying to use my inbuilt Atheros AR242x, without much luck. Lshw -C network recognises that it is there but says it is disabled. I'm unable to post the exact output due to typing this on my iTouch. It works fine in Vista.

Firstly, it's definately switched on at the hardware switch; I've checked and when swithed off, an LED goes out. As far as I can tell, it's not switched off from windows. When that happens the LED also goes out. That covers both things help tells me to do. If it were switched off in the software, I also doubt it would work on my other OS.

Under hardware drivers, I've activated the madwifi alternate Atheros driver, that's not helped. I've searched the forums and found nothing applicable with anything new I haven't tried. Any ideas anyone?

Labrat256

---

### Post by sandyd on 2009-08-20
[http://www.ubuntugeek.com/how-to-get-atheros-ar5007eg-or-ar242x-wireless-cards-may-be-other-models-working-in-ubuntu-810-intrepid-ibex.html](http://www.ubuntugeek.com/how-to-get-atheros-ar5007eg-or-ar242x-wireless-cards-may-be-other-models-working-in-ubuntu-810-intrepid-ibex.html)

probably will work with 9.04 too.

EDIT: wait, they will. they have instructions for jaunty there.

EDIT2: wait, you said its regonized? well... i don't have much experience with wireless networks and i don't know if 9.04 has the drivers for that card installed by default, but perhaps all you need to do is

```

ifconfig wlan1 up
ifconfig wlan0 up

```
if that doesn't work, just pretend i din't write that.

---

### Post by lkraemer on 2009-08-21
labrat256,
I know the AR242x Wifi wasn't supported for 8.04, but I was thinking
9.04 and later versions worked from the LiveCD.  I have a laptop with
the Atheros AR242x Wifi, and I am using 8.04.3 LTS with the madwifi drivers.
[http://snapshots.madwifi-project.org/](http://snapshots.madwifi-project.org/)

But, I'm not familiar with what worked out of the box with 9.04.

I guess you could try the madwifi drivers with 9.04.
I had posted this a while back.  Use it as a reference.
[http://ubuntuforums.org/showthread.php?t=988691&highlight=CQ50-139nr](http://ubuntuforums.org/showthread.php?t=988691&highlight=CQ50-139nr)

I'd suggest you burn a CDRW of 9.04 and 9.10 Alpha 4 and boot those
LiveCD's to see if it works from the LiveCD. Then search for HOWTO:
or AR242x.


lkraemer

---

### Post by labrat256 on 2009-08-21
I've fixed this now! I followed both method 1 and method 2 at [http://www.ubuntugeek.com/how-to-get-atheros-ar5007eg-or-ar242x-wireless-cards-may-be-other-models-working-in-ubuntu-810-intrepid-ibex.html](http://www.ubuntugeek.com/how-to-get-atheros-ar5007eg-or-ar242x-wireless-cards-may-be-other-models-working-in-ubuntu-810-intrepid-ibex.html) as instructed by carlee.

After rebooting, I then had the same problem as [http://ubuntuforums.org/showthread.php?t=1016453](http://ubuntuforums.org/showthread.php?t=1016453). I followed the advice there and followed [http://blog.hyperandy.com/2008/11/01/atheros-ar242x-ubuntu-810-ibex/](http://blog.hyperandy.com/2008/11/01/atheros-ar242x-ubuntu-810-ibex/) as instructed by Jimro on that thread.

Once I'd done that and rebooted, all was fine! If anybody has the same problem, I'd follow all the instructions here.

Thanks all,

labrat256

P.S. I also followed carlee's EDIT 2 partway during my messing. It may have helped, it may have not, I'm not sure. > ifconfig wlan1 up did nothing but > ifconfig wlan0 up did something, albeit I don't know enough to know what yet. If anybody with the same problem follows the other advice without result, try them.

---

