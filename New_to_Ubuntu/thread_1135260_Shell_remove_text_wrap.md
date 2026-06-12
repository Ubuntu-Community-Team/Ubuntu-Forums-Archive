---
title: "Shell: remove text wrap"
date: 2009-04-24
forum: New to Ubuntu
---

### Post by deostroll on 2009-04-24
What is the terminal shell that get shipped with intrepid ibex? Plus how do I remove the text wrap feature (when I run Ternimal)?

---

### Post by cmnorton on 2009-04-24
Are you referring to the shell run by Terminal.app or the default shell of Linux?

The default shell of Ubuntu currently is dash, but bash is the shell when Terminal is run. 

As to wrapping, have a look at stty's man page. I looked through Terminal and could find no settings to change line wrapping.

---

### Post by kanikilu on 2009-04-24
The default terminal application in Ubuntu is **gnome-terminal**. Looking through the man page, I don't see an option to disable wrapping. 

You can do this with **xterm** using the **+aw** option, but I don't think the resulting behavior is what you are expecting...

---

