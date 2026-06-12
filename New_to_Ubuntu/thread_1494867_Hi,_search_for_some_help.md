---
title: "Hi, search for some help"
date: 2010-05-27
forum: New to Ubuntu
---

### Post by xiangzi on 2010-05-27
I am a new comer for ubuntu, and have a problem .
I used the dpkg -l in the terminal,and the result was too many.
I can't see the abcd```` ones, the first one can be shown in my terminal is the l***s
and I don't how to get the whole thing.
thx.

---

### Post by chickencaesar on 2010-05-27
You could use less:

dpkg -l | less

This shows the list a page at a time. Hit the space bar to see the next page.

---

### Post by jvector on 2010-05-27
Also in a terminal, you can use <Shift>-<PageUp> to see text that has scrolled out of sight. (You may also have a scroll bar at the side of the terminal).

---

