---
title: "Single Click is recognized as Double Click"
date: 2009-08-05
forum: New to Ubuntu
---

### Post by yangt299 on 2009-08-05
Hi all,

I am currently running Ubuntu 8.0.4 and I've been having this problem ever since I downloaded Ubuntu. Sometimes, when I am on my computer, the computer recognizes my mouse single clicking as double clicking. This caused caused a lot of trouble, especially when checking emails. Has anyone else ever had this problem? Is it a bug in the code? Also, it is not the mouse itself's problem; I tried with a different mouse but the problem did not go away.

Please help!! Thanks

---

### Post by wojox on 2009-08-05
Go into System > Preferences > Mouse > Accessibility and make sure Dwell Click is not enabled.

---

### Post by yangt299 on 2009-08-05
Thanks for the fast reply!!

Dwell click was not enabled, nor was the software installed to make it enabled. Could there be another problem?

Thanks!!

---

### Post by sydbat on 2009-08-05
What, specifically, are you doing when you get the 'single' click? Are you in Firefox checking your email? Are you simply wanting to open an icon on your desktop? Is it while you are using Open Office?

Knowing what you are specifically doing when you single click on something (and expect it to be a double click) will help us determine what the problem is.

---

### Post by Marlonsm on 2009-08-05
I have seen a computer (running Win XP, not Ubuntu) that from time to time breaks the mouse, and it starts having the same problem you're having.
And the weird part is, even if I use that mouse in other computer, it keeps double clicking. So maybe the problem is your mouse, not the computer.

Have you tried that mouse in other computer?

---

### Post by AVHATION on 2009-08-08
I have similar symtoms - one mouse click acts as two. It affects Evolution (e.g. when delting one message, two get deleted).  It affects word processing (e.g.if highlighting one or two letters to edit, the whole word or one sentence or one para gets highlighted,  It affects web browsing too.  I am using Ubuntu 8.04 with latest updates. I also use Virtuasl box (for Windows XP; the mouse works OK there I think but very slowly).  I have not added any programmes recently.

---

### Post by AVHATION on 2009-08-08
P.S The drop down menus of Ubuntu and Firefox also do not stay selected when trying to choose an item If I press and hold I can get to the item I want. Also, the Ubuntu tool bar sometimes gets dragged by accident from the top to another side position.
Looking at th esystem log I found 2 mouse entries - could they be relvant?

Aug  9 10:47:23 henry-desktop kernel: [   21.477783] input: Macintosh mouse button emulation as /devices/virtual/input/input0

Aug  9 10:47:23 henry-desktop kernel: [   21.485198] mice: PS/2 mouse device common for all mice

---

### Post by AVHATION on 2009-08-08
P.P.S.  Mousetweaks  Assistive Technologies is not enabled.

---

### Post by AVHATION on 2009-08-23
After reading elsewhere about "random" clicks" and keyboard keys sometimes producing double letters, I seem to have suppressed my symptom by rapidly pressing the left mouse button (at max rate) for several seconds. The advice was to do this for at leaast a minute, but for me it seems to have done the trick after just a few tens of seconds. Hooray!

---

### Post by jbsongaku on 2009-09-06
I've been having the same issue. Seems to be hardware related for me. Clicking in a more gentler way seems to do the trick. When I do a soft click or drag, it works properly. When I click the mouse button all the way down, I get this erratic behavior...

Might be something to try, I've heard many people solved their "issue" by buying a new mouse, so this kind of fits the situation ;)

---

### Post by FreewheelinFrank on 2009-09-06
Run this command in a terminal:

```
xev
```

A little widow appear plus a slightly larger window.

Mouse click in the small window; the big window will show you the output.

If there are two outputs per click, your mouse is FUBAR'ed.

---

