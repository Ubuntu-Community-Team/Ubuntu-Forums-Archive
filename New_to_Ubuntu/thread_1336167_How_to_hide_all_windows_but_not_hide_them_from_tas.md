---
title: "How to hide all windows but not hide them from taskbar?"
date: 2009-11-24
forum: New to Ubuntu
---

### Post by karatedog on 2009-11-24
I'd like to get that "windows"-ish effect where I can hide all the windows (Ctlr+Alt+D) but they are not hidden from the taskbar.
Simple workflow:
- I write an email, and want to include a screenshot
- I take the screenshot (copy&paste from clipboard is not working :-(
- I save the screenshot. To save time I select the deafult folder, which is Desktop
- now I have to hide all windows, grab the saved file's icon, pull it to the taskbar, wait a little until the window pops up, bring the icon into the window and drop.

Now the problem is, if I hide all windows, they are gone from the taskbar, too. So there is no place to pull the dragged icon back.

Changing viewport is a solution (if the other viewport is not full of windows either) but I consider it a workaround, I truly believe there is some configuration to do this ;)

---

### Post by qwerty2009 on 2009-11-24
Thats strange when i push (ctrl>alt>d) my windows minimises and they still remain on the panel

try adding the "show desktop" applet to your panel

---

### Post by philinux on 2009-11-24
> **qwerty2009 said:**
> add the "show desktop" applet to your panel

Should be there, bottom left by default unless it was removed by the OP.

---

### Post by drs305 on 2009-11-24
As stated, the "show desktop" feature is what you want. In the left corner of the bottom panel do you have a monitor-looking icon? That is the "show desktop" icon and if you click it all your windows will be minimized.  It should be there by default.


*Please mark the thread solved via the Thread Tools link near the upper right of the original post when you no longer need assistance.*

---

### Post by karatedog on 2009-11-24
Sorry for your time #-o
The culprit is Compiz's Show Desktop. If I turn it off, the Show desktop button and Ctrl+Alt+D works as it should.
When turned on, it behaves differently. Hides every window from screen, plus hides every unhidden window from taskbar. Strangely, every window that was hidden by the user, stays on the taskbar even pressing Ctrl+Alt+D.

---

