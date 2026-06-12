---
title: "Compiz crashes easily after upgrade to Jaunty?"
date: 2009-12-19
forum: New to Ubuntu
---

### Post by vaiocomputer on 2009-12-19
I have Ubuntu on my laptop (Core 2 T8300 Penryn, 3 GB, 250 GB HD, ATI Mobility Radeon X2300) ( [http://www.laptopmag.com/review/laptops/gateway-c-142xl.aspx](http://www.laptopmag.com/review/laptops/gateway-c-142xl.aspx) ) and after the update to Jaunty Compiz crashes way too easily.  

Before, aside from a blinking and xorg-crashing Google Earth and playing video in Compiz, it would crash every once a while to the point which I had to be careful with the mouse cursor and not do too many graphical things at once (playing with multiple compiz effects, etc.), but now, it crashes like every 20 minutes, making Compiz almost unusable.  So I followed a guide for the "radeonhd" driver which didn't apparently do anything.  

I miss the Catalyst Control Center driver uninstalled after the Jaunty upgrade. There's a new version of fglrx this month at the AMD site, but I found compiling and installing it too complicated for my Ubuntu skills.  Would using that help Compiz?

+Also, my hardware detecting software on Ubuntu detects my graphics card as Mobility Radeon X2100 not X2300.  Is that a problem?

---

### Post by vaiocomputer on 2009-12-20
This is important. Please take notice and respond.

---

### Post by rCXer on 2009-12-20
Can you give more details?  When you say crash, do you mean that ubuntu freezes or does the screen go blank?

Have you tried disabling compiz? To do this:  System -> Preferences -> Appearance.  Under the "Visual Effects" tab, select "None"

---

### Post by vaiocomputer on 2009-12-21
Ubuntu freezes literally half way into doing an animation, everything on screen, including mouse cursor, video, and etc. freezes.

---

### Post by omskates on 2009-12-21
This might be a dumb question but have you run update and upgrade after the version upgrade to make sure its running latest available kernal & X version?  Also possibly reinstalling compiz through synaptic then rebooting would be a harmless tactic.

---

### Post by rCXer on 2009-12-21
Ok I did a bug search of [ubuntu bugs](https://bugs.launchpad.net/).  I could not find anyone with ATI Mobility Radeon X*** with your exact problems.  Try searching there and consider filing a bug report.

Another question, does compiz work when you try a karmic live cd?  Upgrades often break the OS. A clean install of karmic or a downgrade to Jaunty may fix the problems.

Make sure you disable visual effects as suggested above.

---

### Post by omskates on 2009-12-21
> **rCXer said:**
>  Upgrades often break the OS. Yeah, why is that?...............so annoying.

---

### Post by vaiocomputer on 2009-12-22
I reinstalled Compiz and the got the newest kernel installed, and no difference.  The Live CD works fine, but then again, it is the barebones Ubuntu, so I kinda expected that.  I'm not willing to downgrade, might as well use Metacity, which never crashes, or even KDE, which crashes only sometimes, than compiz.

I looked at the Ubuntu bugs link to launchpad and I found a confirmed bug, but its only for KDE kwin, which also crashes for my computer, but not nearly as problematically as Compiz, which is really the main issue.

[https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/446845](https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/446845)

---

