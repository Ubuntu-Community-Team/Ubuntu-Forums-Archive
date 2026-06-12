---
title: "Ubuntu 11.04 - Firefox 4 - Can't get the new bookmarks button to display"
date: 2011-05-03
forum: New to Ubuntu
---

### Post by NonStop on 2011-05-03
I've just upgraded to Ubuntu 11.04, and in the new firefox 4 I can't get the new bookmarks button to display.

If I go into customise, then I can see it displayed on the right-hand side, but if I come out of customise it dissapears.

How do I solve this?

---

### Post by NonStop on 2011-05-03
Anyone?

---

### Post by Dave K on 2011-05-03
Same here, but I am also missing the stop/reload buttons. If I add turn the text labels on I get those 2 back but not bookmarks.

If I find a solution I will post back.

---

### Post by Dave K on 2011-05-03
Use "view"/"Toolbars"/"Custom" to remove the broken buttons and add them back and it works.

Seams like some sort of a corruption issue.

EDIT: Just realized I also switched from the bookmark menu icon with a down arrow on the right to the simple button.

---

### Post by chromatica86 on 2011-05-05
I'm having the same problem. The above solution didn't work.

---

### Post by dwhite on 2011-05-05
also same problem, when i try to add button to the menu 

view-->toolbars-->customize

i cannot get the button to show up,

---

### Post by dwhite on 2011-05-05
appears to be a bug, if i disable the "Global menu bar integration" extension everything works fine.

here is screenshot once that extension is disabled, compare to screenshot above things ok now, and i can add buttons (for example i've added the fullscreen button as you can see in this screenshot.

 if i wanted to purge firefox completley and reinstall how would i do that? is this a bug for anyone else?

---

### Post by chromatica86 on 2011-05-06
> **dwhite said:**
> appears to be a bug, if i disable the "Global menu bar integration" extension everything works fine.

here is screenshot once that extension is disabled, compare to screenshot above things ok now, and i can add buttons (for example i've added the fullscreen button as you can see in this screenshot.

 if i wanted to purge firefox completley and reinstall how would i do that? is this a bug for anyone else?

Success!!
Thank you sir. This is much better now.:guitar:

---

### Post by dwhite on 2011-05-06
glad it worked for you

actually it's not a bug, that's the way the programmer made the extension, i posed the question on launchpad last night and i got an answer from the programmer...kind of cool, here is his answer (glad i posted it as a question and not a bug report :))

> Chris Coulson proposed the following answer:
That is because the menubar is rendered by Unity rather than Firefox,
and applications can't just drop random widgets or applets in there
(note, that only Firefox ever supported this anyway). The items on the
panel are meant to behave consistently (like a menu), and dropping
random widgets on there would break that, just like the mess of random
applets in gnome-panel. In addition to that, supporting this at the menu
protocol level would add an additional layer of complexity that we just
don't want to maintain.

---

### Post by andygait on 2011-05-07
> **dwhite said:**
> appears to be a bug, if i disable the "Global menu bar integration" extension everything works fine.

here is screenshot once that extension is disabled, compare to screenshot above things ok now, and i can add buttons (for example i've added the fullscreen button as you can see in this screenshot.

 if i wanted to purge firefox completley and reinstall how would i do that? is this a bug for anyone else?


Worked a treat. Many thanks. 

:D

---

