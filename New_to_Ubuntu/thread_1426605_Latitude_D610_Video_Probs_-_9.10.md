---
title: "Latitude D610 Video Probs - 9.10"
date: 2010-03-10
forum: New to Ubuntu
---

### Post by aberdian on 2010-03-10
All

Just updated to 9.10 and my video has gone all goofy - ATII Catalyst won't work anymore and I can't set my screen resolution to be anything > 1024/768.

I've tried installing the ATI driver (sh ./ati-driver-installer-9.2-x86.x86_64.run) and the package uncompresses and I get

Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:2.6.31-20-generic; make sure that the version is being
correctly set by --iscurrentdistro


Ideas?

Ian

---

### Post by halitech on 2010-03-10
The Dell Latitude has an ATI X300 mobility video card. ATI dropped support for it so the Catalyst driver won't work in anything above 8.10. My guess would be that you will need to create an xorg.conf file and fill it manually to get the resolution you want (guessing 1400x1050)

---

### Post by undecim on 2010-03-10
Don't install ATI's drivers from their website.

Instead go to System -> Administration -> Hardware Drivers.

---

### Post by QIII on 2010-03-10
Don't know that using the AMD/ATI driver in the repos will help.

That card was unceremoniously pitched into AMD/ATI's "legacy" bin before the Catalyst 9.10 driver was specifically made available for the Karmic repos.

(As an aside, it looks like AMD/ATI will do the same thing it has done for a couple of Ubuntu versions:  Get a pre-release version of Catalyst into the repos for Lucid just prior to Lucid's release.  Everyone but Ubuntu users will have to wait.  That driver is supposed to work with the new version of Xserver.)

---

### Post by aberdian on 2010-03-10
> **undecim said:**
> Don't install ATI's drivers from their website.

Instead go to System -> Administration -> Hardware Drivers.
Don't see anything in there when I go in - am I missing something? :)

Says "No proprietary drivers are in use on this system"

---

### Post by halitech on 2010-03-10
you aren't seeing anything in System - Admin - Hardware drivers because that only lists Proprietary drivers which none exist for your card in 9.10.

---

### Post by aberdian on 2010-03-10
> **halitech said:**
> you aren't seeing anything in System - Admin - Hardware drivers because that only lists Proprietary drivers which none exist for your card in 9.10.

Soooo.....I'm screwed then? Or is there a way round it by kludging some other driver in there?

---

### Post by halitech on 2010-03-10
The only driver you can use is the open source driver. If you try to force another driver you'll just end up screwing the system. What resolution are you trying to use?

---

### Post by aberdian on 2010-03-10
> **halitech said:**
> The only driver you can use is the open source driver. If you try to force another driver you'll just end up screwing the system. What resolution are you trying to use?

1280x768

Also got a problem running games under wine and running fspot, but I suspect it's graphics related.....

---

### Post by aberdian on 2010-03-11
> **aberdian said:**
> 1280x768

Also got a problem running games under wine and running fspot, but I suspect it's graphics related.....

Bumpity bump - anyone got any ideas or am I doomed?

---

### Post by halitech on 2010-03-11
got a few ideas:

1. swap out the video card (not feasible or easy on laptops)
2. Try Lucid beta (10.04) and see if it works any better
3. drop back to 8.04 where the ATI driver works
4. settle for what you have

---

### Post by aberdian on 2010-03-11
> **halitech said:**
> got a few ideas:

1. swap out the video card (not feasible or easy on laptops)
2. Try Lucid beta (10.04) and see if it works any better
3. drop back to 8.04 where the ATI driver works
4. settle for what you have
No chance of swapping vid card
The chances of Lucid being any better?
How do I rollback to 8.04 (should be 9.04?)?
Can't settle for what I have, it's worse than windows :)

---

### Post by halitech on 2010-03-11
> **aberdian said:**
> No chance of swapping vid card
didn't think so with it being a laptop
> The chances of Lucid being any better?
who knows, haven't played around with it
> How do I rollback to 8.04 (should be 9.04?)?
Reinstall with an 8.04 cd and no, I meant 8.04. The ATI drivers stopped working as of 8.10
> Can't settle for what I have, it's worse than windows :)
can it really be that bad? ;)

---

### Post by aberdian on 2010-03-11
> **halitech said:**
> 
Reinstall with an 8.04 cd and no, I meant 8.04. The ATI drivers stopped working as of 8.10

Strange, my ATI Catalyst was working in 9.04 which is what prompted the question.

Thanks for all the help though, much obliged! I think I'll see if I still have the 9.04 image as a first step, if I do I'll reinstall from that, otherwise I'll press on and try with Lucid, if that fails I'll step all the way back to 8.04.

---

### Post by halitech on 2010-03-11
last I heard, the Catalyst driver stopped working in 8.10 but maybe you were lucky. Worth a shot I guess

---

### Post by mörgæs on 2010-03-11
When you have experimented with all these versions it would be great if you could add a review in 
[http://www.ubuntuhcl.org/](http://www.ubuntuhcl.org/)

10.04 is here:
[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

and the earlier ones are here:
[http://releases.ubuntu.com/](http://releases.ubuntu.com/)

---

