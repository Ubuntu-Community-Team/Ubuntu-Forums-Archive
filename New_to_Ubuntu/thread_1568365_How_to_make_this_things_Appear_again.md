---
title: "How to make this things Appear again"
date: 2010-09-05
forum: New to Ubuntu
---

### Post by suseno on 2010-09-05
[IMG]http://i9.photobucket.com/albums/a62/oogenesis/Nautilus.png[/IMG]

[SIZE="4"][FONT="Arial Black"]Need help to make that on the bottom-right corner appear again. So I can find a file quickly just by typing it's name.[/FONT][/SIZE]

---

### Post by Christian Knudsen on 2010-09-05
Seems similar to the problem described here:

[http://ubuntuforums.org/showthread.php?t=1161629](http://ubuntuforums.org/showthread.php?t=1161629)

That other thread talks about installing GCIM.

---

### Post by inameiname on 2010-09-05
I take it you cant get it to work with just typing something while you are in Nautilus, as it's a default thing in Ubuntu now?

---

### Post by suseno on 2010-09-05
I use 9.04 and never upgrade. Previously it works.

_[COLOR="Red"]It also works normally in another user session such as Guest session[/COLOR]_. The screenshot there is captured from the same machine using Guest session.

Anyone have step by step idea on how to solve this??

---

### Post by Christian Knudsen on 2010-09-05
Would reinstalling Nautilus fix this?

---

### Post by suseno on 2010-09-05
Now it is **SOLVED**

SCIM (Smart Common Input Method) a tools to write Chinese character is the Culprit

---

### Post by suseno on 2010-09-05
The real Culprit is Actually **[COLOR="Red"]scim-bridge-client-gtk[/COLOR]** package

No more problem after I uninstall it.

> **IME server of scim-bridge communicate with SCIM**

scim-bridge is a wrapper libray for SCIM, writen in C.

SCIM (Smart Common Input Method) is an input method (IM) platform.

Scim-bridge-client-gtk is the gtk client of scim-bridge, it provide
another gtk-immodule for SCIM.


---

