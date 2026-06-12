---
title: "touchpad problem in gnome3"
date: 2011-06-27
forum: New to Ubuntu
---

### Post by deep.3997 on 2011-06-27
Hey guys,
I have just installed gnome3 and everything is working fine except that when i tap on my touchpad it doesnt respond. I am able move the cursor from the touchpad but for left and right click i need to press the buttons.I cant do it by tapping on the touchad.
I have ubuntu 11.04 installed.

Please help.

---

### Post by mkornig on 2011-06-27
I can activate/deactivate clicks as follows:

Système > Préférences > Souris > Pavé tactile.

I use French on my system. In English you probably have to replace "Souris" by "Mouse" and "Pavé tactile" by "Touchpad"?

---

### Post by mkornig on 2011-06-27
I've just checked: I use Gnome 2.30.2. But there should be something similar in Gnome 3, I guess. Let me know if the system settings thing works for you.

---

### Post by deep.3997 on 2011-06-27
The "Enable mouse click with touchpad" option is checked but still its not working.It was working fine before installing gnome3.

---

### Post by mkornig on 2011-06-27
> **deep.3997 said:**
> The "Enable mouse click with touchpad" option is checked but still its not working.It was working fine before installing gnome3.

Oh, it's checked? Sorry, then I can't help you.

It might be a bug?

---

### Post by deep.3997 on 2011-06-27
yeah i fixed it.
by typing   
 synclient TouchButton1=1
in terminal and now its working

---

### Post by Zapata1879 on 2011-07-26
had the same issue, in my case it has been TapButton1=1 (instead of "TouchButton"). Still missing the two fingers tap as middle click... haven't found the solution yet (--> this refers to AsusA52 only!)

---

