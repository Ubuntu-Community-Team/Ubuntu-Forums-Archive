---
title: "Hibernate/Standby Question"
date: 2009-02-11
forum: New to Ubuntu
---

### Post by wheeeeee on 2009-02-11
I'm not really sure if this is me not knowing WHAT Hibernate/Standby mean in windows vs ubuntu, or whether or not this is an actual problem.  I've seen lots of posts RE:Hibernate/standby not working, but I'm not sure whether or they they apply to me.

MY QUESTION:
When I hibernate my computer, it seems like the the computer just locks the screen (leave msg, type password, etc), but doesn't really HIBERNATE, as in go into low battery mode, so that you have to jiggle the mouse button or push the laptop on button to get to that screen.  So, is it that I have to configure something, or is this how it's supposed to happen?

Running Toshiba Satellite A135, if that makes a dif.

---

### Post by jemate18 on 2009-02-11
> **wheeeeee said:**
> I'm not really sure if this is me not knowing WHAT Hibernate/Standby mean in windows vs ubuntu, or whether or not this is an actual problem.  I've seen lots of posts RE:Hibernate/standby not working, but I'm not sure whether or they they apply to me.

MY QUESTION:
When I hibernate my computer, it seems like the the computer just locks the screen (leave msg, type password, etc), but doesn't really HIBERNATE, as in go into low battery mode, so that you have to jiggle the mouse button or push the laptop on button to get to that screen.  So, is it that I have to configure something, or is this how it's supposed to happen?

Running Toshiba Satellite A135, if that makes a dif.

You may want to find out acpi or /usr/bin/apmd

---

### Post by camper365 on 2009-02-11
When you hibernate, you are completely turning the computer off and copying the RAM to the hard drive so that when you unhibernate you have all your windows open from last time. When you standby, you go into low battery mode.

If your computer is old, that may be the problem. When you standby, you have to close the laptop lid before it truly goes into standby, and when you open it again, you resume from standby. I think that is a nice feature of Ubuntu vs. Windows, but some people may find it annoying.

---

### Post by wheeeeee on 2009-02-12
Thanks for the explanation of the difference.

I think I am having trouble with these functions on my laptop.  When I hit hibernate, the screen still has leave message/password on it, even after leaving it alone for half an hour.  So battery is still being used.

I'll search and post if I've found the answer, but any links would be appreciated.  THANKS!

---

