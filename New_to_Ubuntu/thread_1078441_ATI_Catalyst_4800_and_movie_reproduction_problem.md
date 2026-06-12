---
title: "ATI Catalyst 4800 and movie reproduction problem"
date: 2009-02-23
forum: New to Ubuntu
---

### Post by Harisz750 on 2009-02-23
Hi...   I 've recently installed Ubuntu 8.10  64bit on a friendly P.C.  and it has an ATI catalyst 4800 graphic card on it.. i have the hardware drivers enabled and also tried to enable the extra visual effects to make it more eye-candy..  the problem is that when i enable the effects.. either extra or normal..  i have problems with movies' playback...  it flicks.. and the movie can't be seen clearly..     i tried many programs such as VLC   MPlayer Totem .. the problem remains..  the thing is that when i disable the effects.. everything plays normally and without problems.  i also tried envy-ng and the recent ati drivers from their site but still no luck!   Is there any solution to make extra effects work without causing problems in movie playback?

---

### Post by Harisz750 on 2009-02-23
i said that i have already tried that.. didn't work.. thanks anyway..   other suggestions?

---

### Post by sydbat on 2009-02-23
You have to have Desktop Effects disabled to view movies (or play games) smoothly. It is a known bug.

---

### Post by zika on 2009-02-23
System->Preferences->MultimediaSystemsSelector->Video->X11(no Xv) and You can keep compiz ...:)

---

### Post by hobo89 on 2009-02-23
> **zika said:**
> System->Preferences->MultimediaSystemsSelector->Video->X11(no Xv) and You can keep compiz ...:)
I'd love it if that worked, but I don't have MultimediaSystemsSelector in the Preferences menu.

---

### Post by zika on 2009-02-23
> **hobo89 said:**
> I'd love it if that worked, but I don't have MultimediaSystemsSelector in the Preferences menu.
System->Preferences->"Main Menu"->Preferences->check"Multimedia Systems Selector"
or
Alt-F2:gstreamer-properties

---

### Post by hobo89 on 2009-02-23
> **zika said:**
> System->Preferences->"Main Menu"->Preferences->check"Multimedia Systems Selector"
or
Alt-F2:gstreamer-properties

Ah looks a little more promising. I assume I want the 'Default Output' section. But the options are 'X Windows System (No Xv)' or 'X Window System (X11/XShm/Xv)' or 'Custom'. Which do I want?
Thanks. I love you if this works! (In a totally straight way of course)

Edit: Nevermind, the 'Test' button answers my questions.
Thanks!

Edit 2: For video to play properly in VLC you also need to go to Tools > Preferences... and set output to X11. Totem worked straight away though.

---

### Post by zika on 2009-02-23
enjoy!

---

