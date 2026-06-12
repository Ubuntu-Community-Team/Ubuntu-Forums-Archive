---
title: "Firefox imbeded video failure."
date: 2009-05-20
forum: New to Ubuntu
---

### Post by nnjond on 2009-05-20
Hi, can anyone help me?

I can play video at YouTube in FF, but not anywhere else? Such as:

[http://illusioncontest.neuralcorrelate.com/2009/the-break-of-the-curveball/](http://illusioncontest.neuralcorrelate.com/2009/the-break-of-the-curveball/)

Thanks

---

### Post by mapes12 on 2009-05-20
You will need Adobe Flash Player (version 10 is the latest I think). I had a similar problem. I thought I needed an FF plugin but it wasn't their. I found it by searching in Synaptic. I'm not on a Ubu box right no so can't find the exact package name.

---

### Post by nnjond on 2009-05-20
Thanks for your interest. I have Ver. 10 installed.

---

### Post by lovinglinux on 2009-05-20
Check if you have conflicting flash plugins (swfdec or gnash). It's not a good idea to run multiple plugins for the same purpose, since they might conflict with each other.

You could follow [this tutorial](http://ubuntuforums.org/showthread.php?t=766683) to setup your machine for video stuff.

---

### Post by nnjond on 2009-05-20
Thanks 4 your help. have removed those, but no joy?

---

### Post by nnjond on 2009-05-20
Solved by removing Adblock Plus

Thanks

---

### Post by lovinglinux on 2009-05-20
> **nnjond said:**
> Solved by removing Adblock Plus

Thanks

Instead of removing it, you could simply remove the site from Adblock lists or disable Adblock temporarily.

---

### Post by mgmiller on 2009-05-20
> Instead of removing it, you could simply remove the site from Adblock lists or disable Adblock temporarily.

I had a similar problem to the OP and I found that if the adblock extension was installed, but not enabled, I still had the problem.  I had to totally remove the adblock extension to fix the problem.

---

### Post by lovinglinux on 2009-05-20
> **mgmiller said:**
> I had a similar problem to the OP and I found that if the adblock extension was installed, but not enabled, I still had the problem.  I had to totally remove the adblock extension to fix the problem.

Have you tried installing it back?

---

### Post by mgmiller on 2009-05-20
At the time, I tried reinstalling it and the problem instantly returned.  I haven't bothered to reinstall it again since.  I haven't found the pop-ups and junk that intimidating and I have a friend whose web site didn't display correctly for me if I had it turned on anyway.  I guess I just don't miss it.

---

### Post by pcjunkie on 2009-05-21
I had the same problems.

Please install flash player 10.

Fire Fox was reporting 9.xxxx Even though I had 10.
I went into synaptic and removed anything flash including the installer.

I downloaded flash from Adobe, closed FF and installed Flash 10,deb. It worked.

Hope that helps.

---

### Post by mgmiller on 2009-05-21
You really should not have to download an installer off the web.  Flash is in our repositories and works very well.  It is part of the ubuntu-restricted-extras package that also gives you java, mp3 and a pile of other codecs and goodies.  Doing it this way will also keep your flash up to date automatically with the rest of your system.  In fact, afaik, the one you install from our repos is just a pointer to the adobe site, but it has the advantage of keeping everything up to date, where installing from a download as you did, will not keep iteself updated and will require you to periodically uninstall and reinstall newer versions.

---

### Post by lovinglinux on 2009-05-21
> **mgmiller said:**
> You really should not have to download an installer off the web.  Flash is in our repositories and works very well.  It is part of the ubuntu-restricted-extras package that also gives you java, mp3 and a pile of other codecs and goodies.  Doing it this way will also keep your flash up to date automatically with the rest of your system.  In fact, afaik, the one you install from our repos is just a pointer to the adobe site, but it has the advantage of keeping everything up to date, where installing from a download as you did, will not keep iteself updated and will require you to periodically uninstall and reinstall newer versions.

I agree with almost everything on the quote above, except "works very well".

---

### Post by mgmiller on 2009-05-21
> I agree with almost everything on the quote above, except "works very well".

LOL. ok,ok.  On a scale of 0 - 10 I give it about an 8 1/2.  The problem being full screen video.  I have seen a huge improvement in the last year or so, but it's still not perfect.  

I really enjoy using hulu to watch tv shows on a 64 bit AMD 3200+ cpu with 2 gig of ram and 64 bit ubuntu Jaunty hooked up to a 37" LCD TV at 1366 x 768 with an ATI 9600 AGP video card with the open source drivers (fglrx is not available for this older card in Jaunty) compiz enabled and I find that in full screen, there is an occaisional dropped frame, or stuttering, especially on horizontal panning motions.  But on the whole it's very watchable.  Not at all like the "slide show" it was a year and a half ago.

Interestingly, or annoyingly, as the case may be, I have a lot of machines in my office running 32 bit Hardy with integrated SIS video that do full screen flash beautifully.  No compiz, of course, but the regular desktop is smooth as silk.

So I guess, I have to change my statement from "works very well", to "works well".

---

