---
title: "Got a laptop with Intel graphics, questions about driver problems"
date: 2009-09-24
forum: New to Ubuntu
---

### Post by mindtrick on 2009-09-24
This laptop has an integrated Intel graphics card and I've never tried any linux distro on it. I'm willing to try a distro - my first choice is Ubuntu - but I read some stuff about Intel graphics performance issues on the latest release of Ubuntu. Don't know if the problem still prevails, I need some advice. Do you recommend going ahead and installing Jackalope on it, or should I wait for Karmic?

---

### Post by bodhi.zazen on 2009-09-24
Which graphics card exactly ?

---

### Post by MasterNetra on 2009-09-24
> **bodhi.zazen said:**
> Which graphics card exactly ?

+1

If its like mine (see signture) then the main issue you may have in Jaunty is the lack of OpenGL 2.0 support. Otherwise I haven't had any real issues that didn't stim from that. At install the Intel Card maybe blacklisted but after all the updates, its lifted. But yea do post what intel card it is.

---

### Post by HotShotDJ on 2009-09-24
> **mindtrick said:**
> but I read some stuff about Intel graphics performance issues on the latest release of Ubuntu. Don't know if the problem still prevails, I need some advice. Do you recommend going ahead and installing Jackalope on it, or should I wait for Karmic?For many Intel Integrated Graphics chip sets, performance is still an issue in the default Jaunty.  As noted by bodhi.zazen, it depends on which chip set you have in your system.

Using the instructions in [THIS]("http://ubuntuforums.org/showthread.php?t=1130582") thread, I have been enjoying good performance of Ubuntu with my Intel 945GM graphics chip set.  It isn't really that difficult to get a problematic Intel graphics adapter to work well, but it can be time consuming testing at each level (Safe, Optimal, Bleeding Edge) to discover which is best for your system.

The problems seem to be solved in Karmic.  Since it is only 4 weeks or so away, you might want to hold off.  Also, Karmic has some other improvements (ext4 now works without file corruption on power loss and is the default) and [Gnome 2.28]("http://www.gnome.org/press/releases/2009-09-gnome228.html").  On the other hand, by installing Jaunty and working through the performance tweeks in the above link, you'll learn a bit about Ubuntu in the intervening weeks -- something like a "dry run."  Then, when Karmic comes out, you can do a fresh install (to get the benefits of ext4) and you'll already have a good idea what you are doing and what to expect.

I can see valid arguments either way.

---

### Post by mindtrick on 2009-09-24
Oh, sorry. It's X3100, GM965, 384 mb max. 

Does compiz work, @MasterNetra ?

---

### Post by mindtrick on 2009-09-24
> **HotShotDJ said:**
> For many Intel Integrated Graphics chip sets, performance is still an issue in the default Jaunty.  As noted by bodhi.zazen, it depends on which chip set you have in your system.

Using the instructions in [THIS]("http://ubuntuforums.org/showthread.php?t=1130582") thread, I have been enjoying good performance of Ubuntu with my Intel 945GM graphics chip set.  It isn't really that difficult to get a problematic Intel graphics adapter to work well, but it can be time consuming testing at each level (Safe, Optimal, Bleeding Edge) to discover which is best for your system.

The problems seem to be solved in Karmic.  Since it is only 4 weeks or so away, you might want to hold off.  Also, Karmic has some other improvements (ext4 now works without file corruption on power loss and is the default) and [Gnome 2.28]("http://www.gnome.org/press/releases/2009-09-gnome228.html").  On the other hand, by installing Jaunty and working through the performance tweeks in the above link, you'll learn a bit about Ubuntu in the intervening weeks -- something like a "dry run."  Then, when Karmic comes out, you can do a fresh install (to get the benefits of ext4) and you'll already have a good idea what you are doing and what to expect.

I can see valid arguments either way.

Thanks for your time. 

Harware and software problems were what drove me away from linux last year, before that I used linux for one year. I tried many distros but I found Ubuntu the best for support.

I'll wait for Karmic till next month and consider a re-migration based on my experience. Based on what I read so far, I think it will be a keeper. 

Thanks for the help guys. =D>

---

