---
title: "BCM4318: Card works, WPA doesn't"
date: 2008-03-24
forum: Networking &amp; Wireless
---

### Post by Natureshadow on 2008-03-24
Hello,

I know there are loads of threads about that around, but none of them seem to provide a solution.

I have installed ndiswrapper and such followgin the how-to at [http://ubuntuforums.org/showthread.php?t=197102&highlight=bcm4318](http://ubuntuforums.org/showthread.php?t=197102&highlight=bcm4318). The card works fine with WEP, however, WPA doesn't.

I tried that with Wicd and also wit hthe manual method. I can connect to the network without errors, but I can neither send nor receive data.

Does anyone have any idea about that, or tell me where I can find a real solution?

Regards,
Nik

---

### Post by aaaantoine on 2008-03-24
I also have the BCM4318.  In 7.10, the Restricted Drivers manager will download and install the firmware for you.  Using this automated install method, I am able to connect to a WPA network.

Is there a special reason why you need to use ndiswrapper instead?

---

### Post by Natureshadow on 2008-03-24
> **aaaantoine said:**
> I also have the BCM4318.  In 7.10, the Restricted Drivers manager will download and install the firmware for you.  Using this automated install method, I am able to connect to a WPA network.

Is there a special reason why you need to use ndiswrapper instead?

Yes, there is ... because the method you described above didn't work either. Anyway, the GPL bcm43xx driver has some known strange side effects, as can be found on the forums.

-nik

---

