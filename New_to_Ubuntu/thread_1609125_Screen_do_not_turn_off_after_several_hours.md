---
title: "Screen do not turn off after several hours?"
date: 2010-10-30
forum: New to Ubuntu
---

### Post by honeybear on 2010-10-30
Shall I use xset, for that (how is it the best choice)? 

I have fluxbox (no xscreensaver)

---

### Post by xjesse on 2010-10-30
Is there a reason why you don't want xscreensaver? The bare minimum would simply be a blank screen.

---

### Post by nlsthzn on 2010-10-30
> ** Will GNOME apps work in fluxbox**

 Yes. Do ./configure --enable-gnome. This enables GNOME  hints. You can also add "xscreensaver &" to your ~/.fluxbox/startup  file so you can lock the screen or use xscreensavers. 


[Source]("http://fluxbox-wiki.org/index.php?title=FAQ")

To just turn off what is displayed than I agree with xjesse...

As for Power Managers to switch off the screen etc. I suspect you can use gnome-power-manager, but have a read here [https://help.ubuntu.com/community/Fluxbox](https://help.ubuntu.com/community/Fluxbox) as there is a wealth of info on using Fluxbox :)

---

### Post by honeybear on 2010-10-30
> **nlsthzn said:**
> [Source]("http://fluxbox-wiki.org/index.php?title=FAQ")

To just turn off what is displayed than I agree with xjesse...

As for Power Managers to switch off the screen etc. I suspect you can use gnome-power-manager, but have a read here [https://help.ubuntu.com/community/Fluxbox](https://help.ubuntu.com/community/Fluxbox) as there is a wealth of info on using Fluxbox :)

I found this : 
> # turn off screen blanking and turn on energy star features
xset s off
xset dpms 600 60 60

but can I use the combination of xscreensaver (eventually turned to disabled) and xset?

---

### Post by nlsthzn on 2010-10-30
Pretty sure it will... install and test I say :)

---

