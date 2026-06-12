---
title: "My Home folder is also my desktop, how do I change that?"
date: 2009-02-04
forum: New to Ubuntu
---

### Post by klwinters on 2009-02-04
I just installed eeebuntu 2 on my EeePC 900 and it had my home folder set as also my desktop. How do I make them separate folders again? Thanks for the help!

---

### Post by handydan918 on 2009-02-04
> **klwinters said:**
> I just installed eeebuntu 2 on my EeePC 900 and it had my home folder set as also my desktop. How do I make them separate folders again? Thanks for the help!

huh? Not sure what this means.
Open a terminal and do ```
cd
``` and enter, then post the output of ls -a

---

### Post by glotz on 2009-02-04
Fire up **gconf-editor** and point it to /apps/nautilus/preferences/desktop_is_home_dir and uncheck the box.

---

