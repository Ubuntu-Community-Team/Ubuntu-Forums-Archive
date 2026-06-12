---
title: "Graphics problems with intel driver on g45"
date: 2009-07-18
forum: New to Ubuntu
---

### Post by reldruH on 2009-07-18
Hello. I recently built a computer with an intel g45 graphics card in it and installed jaunty, which is using the intel driver. But even with compositing disabled I'm getting some really weird graphics problems. Junk appears on the screen, but only in certain areas and if I play with it enough it will go away but it always comes back. It looks like static on an old TV screen, screenshots are attached. Thanks for your help.

---

### Post by Leslie Viljoen on 2009-07-18
I have gotten that too, now and then - I assume these are bugs in the video driver that are being triggered. It happens far less in Gnome and Xfce.

---

### Post by reldruH on 2009-07-18
Is this something that will be fixed in Karmic? I'm willing to upgrade in a few days when alpha3 comes out if I can get rid of this problem.

---

### Post by HotShotDJ on 2009-07-18
See:  [HOWTO: Jaunty Intel Graphics Performance Guide]("http://ubuntuforums.org/showthread.php?t=1130582") conveniently located right here at ubuntuforums.org in the (wait for it...) [Multimedia and Video]("http://ubuntuforums.org/forumdisplay.php?f=334") discussion forum. ;)

---

### Post by QIII on 2009-07-18
You may be running into known performance regressions on some Intel graphics cards.


[http://www.ubuntu.com/getubuntu/releasenotes/904](http://www.ubuntu.com/getubuntu/releasenotes/904)

---

### Post by reldruH on 2009-07-18
> **HotShotDJ said:**
> See:  [HOWTO: Jaunty Intel Graphics Performance Guide]("http://ubuntuforums.org/showthread.php?t=1130582") conveniently located right here at ubuntuforums.org in the (wait for it...) [Multimedia and Video]("http://ubuntuforums.org/forumdisplay.php?f=334") discussion forum. ;)

Thank you very much, I should have looked there first. All of my problems were solved by that tutorial (even the blocked updates went away, it's wonderful).

Thanks again

---

### Post by HotShotDJ on 2009-07-19
> **reldruH said:**
> Thank you very much, I should have looked there first. All of my problems were solved by that tutorial (even the blocked updates went away, it's wonderful).You're quite welcome.  I installed Jaunty shortly after it was released and was bitten by that bug.  Thank goodness for psyke83's tutorial! (It also got Google Earth running properly with Compiz enabled -- something I could never accomplish, even with earlier versions of Ubuntu.)

Perhaps the moderators should consider linking to that tutorial in a sticky at the top of the "Absolute Beginner Talk" forum.

---

