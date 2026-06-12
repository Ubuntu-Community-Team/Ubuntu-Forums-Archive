---
title: "Screen res. for game"
date: 2009-09-30
forum: New to Ubuntu
---

### Post by raceon4 on 2009-09-30
How would I do this?

To run Lincity-NG on a device which does not support 1024x768 (like some netbooks) you have to set the resolution manually until [bug:15192]("http://developer.berlios.de/bugs/?func=detailbug&group_id=2929&bug_id=15192") is fixed. To do so, you can start it once giving the right size as command line argument. It will be saved to userconfig.xml. 

thanks.

---

### Post by dearingj on 2009-09-30
open a terminal and type:
lincity-ng --size 800x600

Replace the 800x600 with whatever screen resolution your computer supports.

---

### Post by raceon4 on 2009-09-30
Perfect. Just what I was trying to figure out thanks.

---

