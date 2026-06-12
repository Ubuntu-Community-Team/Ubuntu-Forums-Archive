---
title: "&quot;Hardware Drivers&quot; does not show proprietary driver for Radeon"
date: 2009-09-07
forum: New to Ubuntu
---

### Post by tomsen_san on 2009-09-07
Hi there, 
I have an Ati Radeon X800 SE (R420) and I am on Kubuntu 9.04. I am having issues with the open source radeon driver and would like to try the proprietary one. I went into "Hardware Drivers" but I do not have any entries for drivers there that I could enable. Is there a way to trigger detection of possible drivers again?

---

### Post by Perfect Storm on 2009-09-07
AFAIK, ATI have stop'd the support of older cards in their drivers.

---

### Post by tomsen_san on 2009-09-09
> **Artificial Intelligence said:**
> AFAIK, ATI have stop'd the support of older cards in their drivers.

Uh, if that's the reason, ok ... my system is getting a little outdated I have to admit. Didn't know there is the most recent driver behind that little control. I don't think it was like this in 8.10. I think they referenced a fixed version of the driver for the life of the ubuntu version. *sigh* So I can try manually to install the most recent proprietary driver than ...

Thanks anyway

---

### Post by 3rdalbum on 2009-09-09
> **tomsen_san said:**
> So I can try manually to install the most recent proprietary driver then ...

You can try, but it won't work with your card. And the older driver won't work with the newer Xorg version in Jaunty.

---

### Post by tomsen_san on 2009-10-15
> **3rdalbum said:**
> You can try, but it won't work with your card. And the older driver won't work with the newer Xorg version in Jaunty.

:( Right. I think there recently was an update of the Ati driver for legacy cards though. Maybe that one will work with my Xorg version. The question is how do I find out before I attempt to install? ;-)

---

### Post by Mark Phelps on 2009-10-15
> **tomsen_san said:**
> :( Right. I think there recently was an update of the Ati driver for legacy cards though. Maybe that one will work with my Xorg version. The question is how do I find out before I attempt to install? ;-)

I checked that so-called update and it was the same as the legacy v9.3 catalyst files -- in other words, no update.

So, the situation has not changed -- there is no ATI restricted driver that will work with your card and the Xorg version supplied with Ubuntu 9.04 and newer. If you try to force the installation of current restricted drivers, you will corrupt your display setup and will end up having to remove the drivers from the command line and replace them with the open source drivers.

---

### Post by ikisham on 2009-10-15
Yes, go back to 8.10 or, better still, to [Hardy (8.04)]("http://www.ubuntu.com/GetUbuntu/download") as it'll be supported till apr/2011.

Only you'll have to use Ubuntu since Kubuntu doesn't give support anymore.

---

### Post by clhsharky on 2009-10-15
HI tomsen_san

What issues are you having, there might be help for them.

---

### Post by ikisham on 2009-10-16
Look, one simple fix for you is to get a GeForce series 6. It uses the latest & greatest nVidia driver and all will be ok.

---

