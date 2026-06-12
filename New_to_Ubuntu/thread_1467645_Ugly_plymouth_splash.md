---
title: "Ugly plymouth splash"
date: 2010-04-30
forum: New to Ubuntu
---

### Post by jfreak_ on 2010-04-30
when i installed the proprietary nvidia drivers the splash screen res changed to 600X400.
Now that I have increased the res to 1200X800, the logo is not visible only ubuntu 10.04 is written in a ugly font and small letters, definitly not the type i saw in live CD. Solutions?

---

### Post by QIII on 2010-04-30
The splash screen looked pretty good before you added the proprietary driver, didn't it?

Sigh.

It seems that after installing proprietary drivers, what you have left is the ugly step-sister.

Unfortunately, proprietary drivers are not loaded until after plymouth renders the splash.  I have seen suggested methods for forcing them to be invoked before plymouth, but I'm not going to mess with it.

Open source driver -- pretty plymouth splash.

Proprietary driver -- ugly plymouth splash.

I go for the proprietary driver because the splash screen is but a fleeting irritation.

---

### Post by Sealbhach on 2010-04-30
There's a way to change that in the grub.cfg

[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1451820&page=3](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1451820&page=3)

You'll need to run sudo update-grub afterwards to make sure the change is applied.

.

---

### Post by jfreak_ on 2010-04-30
> **Sealbhach said:**
> There's a way to change that in the grub.cfg

[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1451820&page=3](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1451820&page=3)

You'll need to run sudo update-grub afterwards to make sure the change is applied.

.

That increases the res but the new ubuntu logo has disappeared.

PS: If nothing works then i guess having no splash is better than a ugly splash. How do i remove the splash and go in with text booting?

---

### Post by swoll1980 on 2010-04-30
Plymouth is rough for this release. I'm sure it will all get worked out.

---

### Post by QIII on 2010-04-30
I'd be careful with the change to /etc/default/grub.

For some, it works.  For others, it makes no difference.  For some, it prevents them from getting to the grub menu before the card shuts off signal to the monitor(s) and they simply cannot use their machine without a reinstall.  It is somewhat dependent on hardware.

---

### Post by ufftata on 2010-05-01
try this solution: [http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/](http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/)

worked for me.

---

### Post by jvc26 on 2010-05-01
Quite a few of the proprietary drivers have issues with Kernel Mode Setting, which as far as I can remember is the way that they get the plymouth image pretty and sharp. It was nice on the loadup because the open source drivers will have been used - its probably a matter of time before the proprietary ones catch up. I just have the issue my card runs nearly 20 degrees hotter on the OSS drivers than the proprietary ones!

J

---

### Post by The Fiddler on 2010-05-01
Proprietary drivers are extremely unlikely to ever support KMS, so don't expect a solution on that front.

OSS drivers for Ati recently gained dynamic power control which drops power consumption to levels close to that of proprietary drivers (seriously!) Some people have reported 30W reduction in power consumption using the newest code.

There's some work to be done still, but this should make it to the 2.6.35 kernel.

---

### Post by Sealbhach on 2010-05-01
> **QIII said:**
> I'd be careful with the change to /etc/default/grub.

For some, it works.  For others, it makes no difference.  For some, it prevents them from getting to the grub menu before the card shuts off signal to the monitor(s) and they simply cannot use their machine without a reinstall.  It is somewhat dependent on hardware.

It worked fine for me but I already had the proprietary Nvidia driver installed (the one you get through Hardware Drivers). I hadn't heard anything about it being problematic, so I went ahead and did it.

.

---

