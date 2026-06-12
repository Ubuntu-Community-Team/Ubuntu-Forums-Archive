---
title: "Wifi management?"
date: 2005-09-07
forum: Networking &amp; Wireless
---

### Post by Strife on 2005-09-07
So I've been Googling around a lot lately in an attempt to find some sort of wireless management tool like NetworkManager, except one that works (I get ridiculous "somethingerother not found" errors even though they do exist when I try to run autogen.sh from CVS).

Alas, the only thing even *close* to what I want seems to be WiFi Radar, which is terrible due to the excessive list of things that you have to do just to get it to run. (Besides this, once I got it to where it was *supposed* to work, it decided that it wasn't going to be able to get an IP address even though it could detect my network).

So I ask: Do other alternatives exist? Or how can I get around these "x.m4 not found" issues when trying to compile NetworkManager?

---

### Post by mlomker on 2005-09-07
You've ruled out command-line solutions, then?  I use a combination of ifplugd, wpa_supplicant, and resolvconf to good effect.

---

### Post by ssck on 2005-09-08
[QUOTE=Strife]So I've been Googling around a lot lately in an attempt to find some sort of wireless management tool like NetworkManager, except one that works (I get ridiculous "somethingerother not found" errors even though they do exist when I try to run autogen.sh from CVS).

Alas, the only thing even *close* to what I want seems to be WiFi Radar, which is terrible due to the excessive list of things that you have to do just to get it to run. (Besides this, once I got it to where it was *supposed* to work, it decided that it wasn't going to be able to get an IP address even though it could detect my network).

So I ask: Do other alternatives exist? Or how can I get around these "x.m4 not found" issues when trying to compile NetworkManager?[/QUOTE]

have u tried gtkwifi ?

---

### Post by Strife on 2005-09-08
As for CLI options, I have largely ruled them out for the reason you implicitly stated: You have to (as far as I can tell) use a combination of tools. But beyond this, it would be really handy to have a status icon at all times (my laptop is for getting work done, not for screwing around with it constantly... that's what the desktop is for).

As for gtkwifi... I tried it yesterday, and it seems a bit buggy in terms of connecting. Basically I would click connect, and nothing would happen, not even an error message saying I couldn't connect.

Really, I would love to get NetworkManager working... I just don't understand why it can't find what is very clearly there when I try to build it...

---

### Post by idrailgag on 2007-10-29
This should do the trick:
[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

It is very easy to install, everything is automatic when setting up.  It gives you much more control over what happens with wifi connectivity.

---

### Post by Lambert on 2007-10-29
> **idrailgag said:**
> This should do the trick:
[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

It is very easy to install, everything is automatic when setting up.  It gives you much more control over what happens with wifi connectivity.

wow. You dragged up an old thread....

---

