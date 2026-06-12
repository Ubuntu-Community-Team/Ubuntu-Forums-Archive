---
title: "Troubles with ATI driver installation"
date: 2010-07-20
forum: New to Ubuntu
---

### Post by yur15t on 2010-07-20
need help!

when i turn on my ubuntu 10.04 it is in sleep mode (just blank black screen  and nothing happens). seems that this problem appeared after i installed  proprietary ATI driver.

I have Radeon HD5470. tried to install drivers from amd.com, same happened.

Does anyone has an idea how to fix it?

thanx

---

### Post by J V on 2010-07-20
Get rid of the proprietary drivers... ATI have been known to make crap linux drivers, and the open source ones are very good in comparison...

In fact, most ATI drivers for linux don't even work with a linux distro more than 2 years old cause of an xorg update...

---

### Post by yur15t on 2010-07-20
and... can i somehow restore my system?

---

### Post by clhsharky on 2010-07-20
yur15t

You may need to run in terminal
```
sudo aticonfig --initial
```
after installing fglrx.
restart

The OSS has no 2D or 3D aceleration for the ATI Radeon HD5xxx cards yet.

To remove fglrx
```
sudo dpkg --purge xorg-driver-fglrx
sudo dpkg-reconfigure xserver-xorg
```
restart

Sharky

---

### Post by QIII on 2010-07-20
> **J V said:**
> Get rid of the proprietary drivers... ATI have been known to make crap linux drivers, and the open source ones are very good in comparison...

In fact, most ATI drivers for linux don't even work with a linux distro more than 2 years old cause of an xorg update...


OK.  OK.  OK.

Enough with the out-dated FUD.  I'm getting tired of repeating myself.   Not trying to be a grumpy old fart.

ATI is no longer ATI, but AMD/ATI.  AMD bought ATI in 2007.  AMD/ATI's drivers are absolutely fine, with the proviso below.

ATI did produce crap drivers.  AMD/ATI does not.

AMD is a member of the Linux Foundation and is committed to the Linux platform.  AMD/ATI has a particular sweet spot for Ubuntu, making its most recent drivers available for the Ubuntu repos at each Ubuntu release before they are even available for general consumption.  

This has caused Phoronix to publish snide headlines like "AMD/ATI gives the candy to Ubuntu again."

Just as with nVidia, there are certain AMD/ATI cards that are problematic.  Both companies suffer from the same issue.  All of my machines with AMD/ATI cards suspend and suspend-to-disk just fine.  That may not be true for all cards.  I'm sure you will find similar complaints for some nVidia cards.  

Can we just stop the "ATI sux and nVidia is perfect" thing?  The choice is now simply one of preference, not performance.

Here's the proviso:  The problem with xorg affects older cards that have been "legacied" and for which AMD/ATI is no longer providing driver updates.  In case you think that AMD/ATI is the only OEM who has done this, try running an nVidia GeForce2 MX400 card from Jaunty forward.

---

### Post by clhsharky on 2010-07-20
QIII

+1

Sharky

---

