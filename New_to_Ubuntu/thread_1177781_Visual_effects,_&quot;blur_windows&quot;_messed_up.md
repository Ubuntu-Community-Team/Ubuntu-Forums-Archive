---
title: "Visual effects, &quot;blur windows&quot; messed up desktop"
date: 2009-06-03
forum: New to Ubuntu
---

### Post by AdamLee on 2009-06-03
Hi

I was playing around with the (extras) visual effects, checked the "blur windows" option - now when I click on an icon, or drop down menu, the message box/menu list appears blacked out and I can't select any options.  Eventually the more applications I try to open, the more "black boxes" I get on my screen -until no desktop.  I've tried to open a terminal to try and reverse the problem (if I even knew how to do this!) but it's a matter of guessing where my terminal icon is in the toolbar at the top - and even if I get that right...the terminal window just appears as a black box.  

Unless there is some sort of keyboard shortcut that will disable the effect from my desktop - I think I might need a fix that I can do before I log in and get to my desktop.

Thanks - all help/suggestions welcomed!

---

### Post by mdawg414 on 2009-06-03
You could try Ctrl-Alt-Backspace to reboot X and see if the problem persists. Often times, if there is a problem, X will give you the option to enter low-graphics mode where the option can be disabled.

---

### Post by edthefox on 2009-06-10
i have the same problem.
 
anyone know of a way to disable desktop effects from the command line??

---

### Post by gcampbell86 on 2009-06-13
I tried using blur windows too and I have got the same problem, it really is a pain!! Does anyone have a solution to this?

---

### Post by gradinaruvasile on 2009-06-13
metacity --replace

in a terminal
Should disable compiz.

Also, install fusion-icon, put in autostart, u will have fast control (you have a tray icon which lets you to configure/disable/reload compiz on the fly. Very nice thing.

---

### Post by Aiffe on 2009-06-15
I had this same problem, and couldn't really get to Terminal what with everything being blacked out. Ctrl+alt+F6 metacity --replace returned "window manager error unable to open x display", so that was a bust.

I did fix it, though. I pressed alt+F2, and obviously the box that popped up was blacked out, but I just typed in "metacity --replace" blind and pressed enter, this did the trick. Then I unchecked "blur windows" and went back to emerald with "emerald --replace", everything's looking great and no more problems.

---

