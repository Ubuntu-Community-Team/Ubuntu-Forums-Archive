---
title: "[SOLVED] How do I force firefox to close please?"
date: 2009-01-12
forum: New to Ubuntu
---

### Post by scotttie on 2009-01-12
Hi Everyone,
I have a popup that wont go away on firefox it keeps reproducing it's self and asking me to download a virus scanner (as if!!)How do I for this to close please?
Thanks
 Scottie

---

### Post by jimmy the saint on 2009-01-12
system>administration>system monitor

Go to processes tab

Right click on Firefox process

select "end process"
if it doesn't end after a few seconds
right-click again and select "kill process"

---

### Post by scotttie on 2009-01-12
Thanks jimmy the saint, worked a treat!

---

### Post by cb34 on 2009-01-12
or you can open a terminal and type:
killall -9 -r firefox

sometimes you have more than 1 firefox process open, and closing it in system monitor, you can have some firefox file left open.. so the above command will kill any and all processes with the word firefox in it.

just another option for you to know about. :)

---

### Post by stefangr1 on 2009-01-12
You can also push Alt+F2 (or a terminal) and then type the command xkill. Then you will get a little cross that will close the window you click on.

---

### Post by cb34 on 2009-01-12
hehe, just dont click it on the main desktop..:p

i did that once..hehehe

---

