---
title: "Awk!  Screen gets all wobbly and/or magnified"
date: 2008-12-06
forum: New to Ubuntu
---

### Post by John Chambers on 2008-12-06
Recently with this Hardy Heron system, I've had a bizarre problem with the display:  Suddenly, for no reason that I can diagnose, the screen starts showing either or both of two extreme misbehaviors.  One is that everything on the screen starts moving around, seemingly as if it's trying to avoid the pointer.  It becomes difficult to point at something, because things move away (or to the side) when I try to move the pointer to them.

The other problem, which usually but not always happens with the first, is that some sort of screen zooming happens, and I can only see a part of the screen, magnified.  The bars at the top and bottom of the screen disappear, so I can't use anything there.  If I click on something, things happen, but not what I expect from where the pointer is.  It's as if the input is going to some window, but not the one that the pointer is in.  Moving the pointer around produces the usual changes of pointer icon, but the icon shown has no obvious relationship to where the pointer is.

So what sort of "feature" am I accidentally enabling?  Does it have a name, so I can look it up and find out how to either use it or disable it?

In particular, how might I be accidentally enabling it?  And is there a way to return to normal, stable screen behavior somehow?  So far, all I've found that works is a reboot, since nothing on the screen seems usable when it enters this mode.

---

### Post by Yuki_Nagato on 2008-12-06
Open up GNOME Terminal, and then enter this command:

```
metacity --replace
```

If that fails to fix your problems, go to the Applications menu and search around for any accessibility software that may be enabled. Systematically run through them and turn any magnifiers or such off.

---

