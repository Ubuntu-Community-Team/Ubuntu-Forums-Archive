---
title: "No xorg.conf file (HP2133)"
date: 2009-09-03
forum: New to Ubuntu
---

### Post by Chalfont on 2009-09-03
Hi
In trying to fix an ongoing display issue in my HP2133 netbook, using 9.04, the solution advanced is very simple, just to add a line in the xorg.conf file.

Someone was extremely nice and told me the exact detail as to how to open said file and do this.

Unfortunately, when I open the file it is blank and when I try to save it, it tells me the file doesn't exist.

I am editing the file using these commands:
Open Terminal (Applications > Accessories > Terminal)
- In the Terminal window, type in 'gksu gedit /etc/X11/xorg.conf' (no quotes)

As I say, when I click on save, it comes back with a "no entry sign" graphic and the text "Could not find file /etc/x11/xorg.conf."

So where will it be?
How can i create a new one?  Should I?

---

### Post by bodhi.zazen on 2009-09-03
from > "Could not find file /etc/x11/xorg.conf." it appears you have a typo

it is X11 not x11

/etc/X11/xorg.conf (big X), your error message has a small x

---

### Post by Sealbhach on 2009-09-03
Let's see what's in your X11 folder.

Use the cd (change directory) command:

```
cd /etc/X11
```The list the contents in there:

```
ls
```Copy and paste what you get back here.


EDIT: Good eyesight!

.

---

### Post by kevinatkins on 2009-09-03
Hi,

Make sure you get the case of the filename an path correct - it's /etc/X11/xorg.conf. The X in X11 is upper-case (yep, GNU / Linux is sensitive to case, unlike Windows)

---

### Post by Chalfont on 2009-09-03
> **kevinatkins said:**
> Hi,

Make sure you get the case of the filename an path correct - it's /etc/X11/xorg.conf. The X in X11 is upper-case (yep, GNU / Linux is sensitive to case, unlike Windows)


Aha!
Case sensitive, never thought about that.... Thanks

FOLLOW UP - YES! IT WORKS. Thanks

---

