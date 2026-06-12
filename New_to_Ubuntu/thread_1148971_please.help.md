---
title: "please.help"
date: 2009-05-04
forum: New to Ubuntu
---

### Post by mamamia88 on 2009-05-04
ever.since.i.installed.jaunty.my.spacebar.has.stopped.working.at.random.times.restarting.x.fixes.it.sometimes.it.just.starts.working.randomly.i.know.it's.not.hardware.becaue.i.tried.a.usb.keyboard.same.problem.and.when.this.occurs.for.some.reason.gnome-do.still.works.please.help.me.fix.this.it's.rather.annoying

---

### Post by mamamia88 on 2009-05-04
please help can't take this much longer

---

### Post by blueridgedog on 2009-05-04
Do you have another keyboard to try just to rule out a conflict with the one you are using?

---

### Post by hansdown on 2009-05-04
There was another thread with the exact problem.

I'll try looking.

---

### Post by mamamia88 on 2009-05-04
yeah that was me too didn't help last time

---

### Post by hansdown on 2009-05-04
Sorry mamamia88.I saw your posts.

There are some bug reports. Almost the same as 8.10 had.

---

### Post by hansdown on 2009-05-04
I just had a crazy idea.

Since the problem in 8.10 seemed to be fixed with an update,maybe try 

Manually running the update manager.System> administration> update manager.

If it tells you your system is up to date, click check anyway.

---

### Post by mamamia88 on 2009-05-04
thats one of the first things i tried if it happens again ill be back here this is just unacceptable

---

### Post by arashiko28 on 2009-05-04
Have you tried to see your xorg configuration?

Looks like there's some sort of conflict and will be helpful to check it while your keyboard works well, because it is not graphical mode. Try typing
> sudo nano /etc/X11/xorg.conf

Check your keyboard settings, I highly recommend that if something is working, don't touch it!!! by own experience.

---

