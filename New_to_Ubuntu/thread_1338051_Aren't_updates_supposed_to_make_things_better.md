---
title: "Aren't updates supposed to make things better?"
date: 2009-11-26
forum: New to Ubuntu
---

### Post by YosefKaro on 2009-11-26
Amongst the final updates that I did yesterday, there was a small update for kppp.  I have two broadband dongles; one of them uses wvdial and the other one uses kppp.  The one that uses kppp is my favorite one because it is much faster.  Until now, it was working perfectly.  Now after the update, kppp opens up and then closes immediately: the window to login doesn't stay open.  So I am presently using the one from wvdial.  It looks like I am going to have to uninstall kppp in its entirety and re-install it while keeping a close eye to make sure that it doesn't get updated again.  Man I hate having to do this: it is a lot of work for me to set up my dongles.  Now it looks like I am going to have to do it again unless someone has some idea how to fix this problem.

-Yos

---

### Post by YosefKaro on 2009-11-26
P.S.  When I try running it from terminal, I get the following: (gksudo:3254): GLib-CRITICAL **: g_str_has_prefix: assertion `str != NULL' failed

P.S.S. And when I try running it with sudo, I get this error: kppp: symbol lookup error: /usr/lib/kde4/plugins/styles/oxygen.so: undefined symbol: _ZN9QHashData13detach_helperEPFvPNS_4NodeEPvEPFvS1_Ei

---

### Post by YosefKaro on 2009-11-26
How about that: I just did another kernel upgrade (I'm on Lucid) and somehow that fixed the problem.

-Yos

---

### Post by XCan on 2009-11-26
Good thing it automagically fixed itself. :) Unfortunately, regressions are kind of inevitable from time to time with the kernels growing more and more advanced. :(

---

### Post by philinux on 2009-11-26
> **YosefKaro said:**
> How about that: I just did another kernel upgrade (I'm on Lucid) and somehow that fixed the problem.

-Yos

If you're using lucid expect **major** breakage. Check out the forum.
[http://ubuntuforums.org/forumdisplay.php?f=377](http://ubuntuforums.org/forumdisplay.php?f=377)

---

