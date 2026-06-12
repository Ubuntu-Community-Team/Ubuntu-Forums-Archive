---
title: "Install has no launcher bar"
date: 2011-08-08
forum: New to Ubuntu
---

### Post by pgagy on 2011-08-08
I'm not really a newbie, but this is a silly newbie question, so I figured I'd post here! :)  I've been using Kubuntu since about 9.10.  I put the live CD on my work laptop this weekend, and I really liked the Ubuntu launcher bar.  I figured I'd try it on my home computer (which is much slower/older than laptop), so I loaded the live CD and the interface was not the same. There was no fancy launcher bar, and there was a a bar at the bottom.  Is there a reason why the launcher bar didn't install?  I figured that Ubuntu realized how crappy this computer is and decided to not install it, in order to give a better user experience.  But that's just a guess.

---

### Post by dwasifar on 2011-08-08
That is exactly right.

Unity needs screen compositing.  If the hardware's not up to it, it can't do compositing, falls back to a different operating mode, and you don't get the dock.

---

