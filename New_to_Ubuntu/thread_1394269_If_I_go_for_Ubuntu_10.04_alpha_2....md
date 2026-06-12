---
title: "If I go for Ubuntu 10.04 alpha 2..."
date: 2010-01-30
forum: New to Ubuntu
---

### Post by eshant_engineer on 2010-01-30
then will I able to upgrade to alpha 3, beta and final release, without any risk or threat? Means I don't want to burn CD again and again. It is not installing through USB flash drive. I have tried nearly everything.

Thank You

---

### Post by louieb on 2010-01-30
Its a crap shoot. may have to reinstall - may not - look at the stickies in the Lucid section of   [Development & Programming]("http://ubuntuforums.org/forumdisplay.php?f=310")

:popcorn: Do you feel lucky?

I've been using Lucid on my laptop (dual boot with Jaunty) since late Dec. Have not had to reinstall yet - but be warned the  updates have been running 10MB to 100MB each day. Stuff breaks - get fixed - breaks again - on and on. But all and all not bad. Give it another 3 months - looks like Lucid will be really good.

---

### Post by skymera on 2010-01-30
> **eshant_engineer said:**
> then will I able to upgrade to alpha 3, beta and final release, without any risk or threat? Means I don't want to burn CD again and again. It is not installing through USB flash drive. I have tried nearly everything.

Thank You

No risk? It's alpha. There's a risk with every update.

I remember running Ubuntu 7.10 alpha, an update for Libc6 borked my system :P

Been running 10.04 Alpha2 for couple weeks now. Rather stable actually.

---

### Post by phillw on 2010-01-30
I've been running 10.04 since rc of Alpha1, worst thing was when several of us tried out a GTK trial & it didn't go too well. Apart from that, and the odd part crashing on itself, it has kept on booting, except for 1 day when quite a few of us had a problem - quicjly solved. So, yeah - 10.04 alpha is quite stable. But, it's not for a production machine - Dual booting it with 9.10 and with a seperate /home partition is a good way. It was suggested to me that I don't use my /home partition all the time for 10.04 - rather that I rsync it over, thus keeping my 9.10 'clean' - should 10.04 decide to do something real bad.

You only need about 10GB of disk space for 10.04, the more testers, the better. Just accept that it will break every so often, so you'll need 9.10 as your fall back installation so you can log on and find out to fix it ;)

Just a note of caution on rsync'ing your /home over from 9.10 to 10.04 ... Make sure FFox is on the same version in both - else, every time you do an rsync to/from 10.04 your FFox will have to check all your add-ons and extensions ! (I'm using 3.6.1 for both systems). Oh, and yeah ... rsync'ing makes it real hard to remember which one you're running lol  You'll get used to issuing ```
uname -a
``` to remind you which one you're on.

So, give it play - If you don't want the massive updates then you can set 10.04 to sync with the server. I find update manager does a reasonable job (Just do **not** accept partial updates - borked mine on day 1 because of that !!).

See you over on the dev forum !!

Regards,

Phill.

---

