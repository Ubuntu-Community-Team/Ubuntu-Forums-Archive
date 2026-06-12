---
title: "Disappearing Background."
date: 2010-12-03
forum: New to Ubuntu
---

### Post by bvpainter on 2010-12-03
If I set a background it disappears after a few minutes and I just get a plain black screen, with all my usual icons.

Can anyone explain what is happening and how I can get my background back.

I have an ATI RV516 Graphics Card in a Dell Dimension C521 machine. It has worked perfectly up to now.

---

### Post by Daveth on 2010-12-03
does this still apply if you use the system default desktop background images? I'm guessing you are using your own.

---

### Post by bvpainter on 2010-12-04
Yes it does, but I think I may have cured the problem.

---

### Post by bvpainter on 2010-12-04
> **bvpainter said:**
> Yes it does, but I think I may have cured the problem.
I was wrong, when i rebooted this morning, my background was there.but after about 10 minutes it disappeared again.

---

### Post by uriel1998 on 2010-12-04
First try using one of the default images, as Daveth suggested.  That would point toward different problems.

It sounds like you've got more than one thing trying to draw on the desktop (that is, more than one thing drawing the desktop).  You can make sure that Nautilus is rendering your desktop (the default behavior in Ubuntu) by running [FONT=Courier New][SIZE=3]gconf-editor[/SIZE][/FONT] from the terminal.  You'll see a two paned window (illustrated below).  Go to [FONT=Courier New][SIZE=3]/apps/nautilus/preferences[/SIZE][/FONT] and scroll until you see [FONT=Courier New][SIZE=3]background_set[/SIZE][/FONT].  If that's not checked, check it.

[ATTACH]177359[/ATTACH]

If that's checked, see if running a particular program is causing the program.  (In other words, can you force the problem to occur?  If so, what does it?)   What are you running as your window manager?

---

### Post by bvpainter on 2010-12-04
Very strange. I got a system update notice, it re-installed all my themes and things seem to have gone back to normal.

Thanks for the help though. I'll keep it in case the same thing happens again.

---

