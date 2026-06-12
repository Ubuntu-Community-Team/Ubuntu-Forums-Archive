---
title: "is an upgrade from 8.10 to 9.04 possible?"
date: 2009-04-24
forum: New to Ubuntu
---

### Post by Matt26 on 2009-04-24
can i perform an upgrade of ubuntu 8.10 to 9.04 without having to reformat my hard drive?

if so, are there official instructions on how to do this?

thanks.

---

### Post by BslBryan on 2009-04-24
Detailed instructions on this website:

[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

---

### Post by pbpersson on 2009-04-24
Of course you can upgrade

1.  Backup all your important data, just in case
2.  Go to System-->Administration-->Update Manager
3.  Install all updates for your machine so your 8.10 version is current
4.  At the top of the window, click on "upgrade"

---

### Post by suprecook on 2009-04-24
Yes you can: [http://www.ubuntugeek.com/upgrade-ubuntu-810-intrepid-ibex-to-ubuntu-904-jaunty-jackalope-beta.html](http://www.ubuntugeek.com/upgrade-ubuntu-810-intrepid-ibex-to-ubuntu-904-jaunty-jackalope-beta.html)

I'm actually doing it right now :)

---

### Post by ROUBOS on 2009-04-24
yes, but be careful. Check yout graphics card. I did it and my ATI x1950pro is not compatible. Had to format and go back to 8.10

---

### Post by Matt26 on 2009-04-25
> **pbpersson said:**
> Of course you can upgrade

1.  Backup all your important data, just in case
2.  Go to System-->Administration-->Update Manager
3.  Install all updates for your machine so your 8.10 version is current
4.  At the top of the window, click on "upgrade"

i guess my timing was off a bit- i see the upgrade option there now, thanks.

---

### Post by Spiritous on 2009-04-25
> **Matt26 said:**
> can i perform an upgrade of ubuntu 8.10 to 9.04 without having to reformat my hard drive?

if so, are there official instructions on how to do this?

thanks.

Knock yerself out!

I think the above posts show how :), though the one about graphics cards I must say is true if you have quite a old card / very new, I'd check it out before you upgrade, though its not incredibly important unless like I said, old / new...

---

### Post by lukeinvancouver on 2009-04-25
> **Spiritous said:**
> ... the one about graphics cards I must say is true if you have quite a old card / very new, I'd check it out before you upgrade, though its not incredibly important unless like I said, old / new...

I got a cheap Intel Atom with integrated graphics.

Would you know if there are any problems? (I'm running 8.10 and downloaded 9.04, which I would like to install.)

---

### Post by PuddingKnife on 2009-04-25
I just upgraded and now compiz effects are very choppy.  :(

---

### Post by caro on 2009-04-25
> **PuddingKnife said:**
> I just upgraded and now compiz effects are very choppy.  :(

PuddingKnife, you probably have an Intel graphics card.  If so, this is a known bug and there are severals threads and wikis on things you can try to resolve it.  I reverted back to the Intrepid Xorg driver and all was well!

---

### Post by lukeinvancouver on 2009-04-25
> **caro said:**
> PuddingKnife, you probably have an Intel graphics card.  If so, this is a known bug and there are severals threads and wikis on things you can try to resolve it.  I reverted back to the Intrepid Xorg driver and all was well!

Would you know if the same holds true for an Intel Atom MB with integrated graphics?

---

### Post by caro on 2009-04-25
> **lukeinvancouver said:**
> Would you know if the same holds true for an Intel Atom MB with integrated graphics?
I haven't heard it mentioned so far but that doesn't mean that it doesn't.  (I think they are actively trying to re-architect the intel drivers and that's causing the problem on intel.)

---

