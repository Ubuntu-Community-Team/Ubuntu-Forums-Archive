---
title: "Compiz Help!"
date: 2011-08-29
forum: New to Ubuntu
---

### Post by leskylar on 2011-08-29
Hey guys,  new to linux here.  Seems that the learning curve is steep and the best way is to dive in!  unfortunately, I've messed things up and it's probably a simple fix that I just don't know.

I installed 11.04 a few days ago and just tonight got around to playing with the compiz settings.  Long story short, when booted in "normal" mode I can only see my desktop image.  No menus, no shortcuts work (except ctrl+alt+del, and ctrl+alt+f4.)  In all other modes things seem normal (ubuntu classic, classic no effects, safe mode.)  I've tried running [COLOR=Blue]unity --replace[/COLOR] [COLOR=Black]to no avail.  I've also tried reseting the default settings within compiz from safemode, but also to no avail.  What do you suggest?

-Sky

EDIT:  and yes I have been reading other threads on this same subject, though they aren't working out for me...
[/COLOR]

---

### Post by zirch on 2011-08-29
Try resetting compiz. Copy paste in the terminal one line at a time.

```
gconftool-2 --recursive-unset /apps/compiz
gconftool-2 --recursive-unset /apps/compiz-1
gconftool-2 --recursive-unset /apps/compizconfig-1
```

After that, reset unity or reboot.

---

