---
title: "Ubuntu 10.04 LTS and ATi drivers"
date: 2010-09-01
forum: New to Ubuntu
---

### Post by Jagermikester on 2010-09-01
Hi folks,

First off I'm a complete noob with Ubuntu and the whole Open Source thing but so far I'm loving it. I'm trying to install the Ati drivers for my Radeon HD5450 but not having much luck. Now I'm all for following instructions on these things but clearly I'm missing something obvious.

I'm using the instructions from the pdf [here]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_cat108-inst.pdf")

So far I've:
Uninstalled the ATI CatalystTM Proprietary Driver using sh ./fglrx-uninstall.sh
Rebooted
Then gone through the Automatic Driver Installation Option and all OK until step 7 which tells me to run /usr/bin/aticonfig --initial  but all I get then is
/usr/bin/aticonfig: No supported adaptors detected ???

Everthing has gone exactly as the instructions until this point and now I'm lost. Please can some one point me in the direction of where to go next? This is only my second time using the Terminal so can anyone kind enough to help please be gentle.

Many many thanks

Jager

---

### Post by andrewthomas on 2010-09-01
You should install fglrx through System > Administration > Additional Drivers

---

### Post by clhsharky on 2010-09-01
Jagermikester

This may help
[http://ubuntuforums.org/showpost.php?p=9778046&postcount=5](http://ubuntuforums.org/showpost.php?p=9778046&postcount=5)


Sharky

Welcome to forums

---

### Post by alphacrucis2 on 2010-09-01
> **andrewthomas said:**
> You should install fglrx through System > Administration > Additional Drivers

That wont work if you want the latest version from AMD (which you do unless you also want to patch the xserver to bypass the dreaded ATI backclear problem).

---

