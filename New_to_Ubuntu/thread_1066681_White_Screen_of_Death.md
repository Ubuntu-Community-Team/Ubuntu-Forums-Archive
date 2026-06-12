---
title: "White Screen of Death"
date: 2009-02-11
forum: New to Ubuntu
---

### Post by gregbzh on 2009-02-11
I have suddenly started getting white screens for no apparent reason.  I have an NVidia GeForce 6200 with graphics driver version 177 installed.  CTRL+ALT+F1 will restore the screen, but it's bloody annoying.

Does anybody have suggestions?

[IMG]http://img410.imageshack.us/img410/5333/64858544cw4.png[/IMG]


Cheers.

---

### Post by meborc on 2009-02-11
what version of ubuntu are you running?

you might want to try a newer version of nvidia drivers... 

is compiz running when this happens? does it happen without compiz as well?

---

### Post by waspbr on 2009-02-11
it's a compiz problem, to get back to your desktop,there are two ways I can think off:

[LIST=1]
[*]at you login screen, choose the sessions option and there choose failsafe gnome, login
[*]this is a little more tricky, as you login into your white screen press alt + F2 , then without actually seeing anything type carefully "metacity --replace" (no speech marks), this shoudl bring you out of compiz
[/LIST]

/a way of solving this would be to install a different version of the display drivers, either through the regular hardware drivers meny or through a program called envyng.Pick your poison.

---

### Post by gregbzh on 2009-02-11
> **meborc said:**
> what version of ubuntu are you running?

you might want to try a newer version of nvidia drivers... 

is compiz running when this happens? does it happen without compiz as well?

I'm using 8.10 and yes Compiz is running when this happens.  Strange as I've been using Ubuntu on this machine since Dapper.  It just started for no apparent reason. 

Thanks for your help.

---

### Post by gregbzh on 2009-02-11
> **waspbr said:**
> it's a compiz problem, to get back to your desktop,there are two ways I can think off:

[LIST=1]
[*]at you login screen, choose the sessions option and there choose failsafe gnome, login
[*]this is a little more tricky, as you login into your white screen press alt + F2 , then without actually seeing anything type carefully "metacity --replace" (no speech marks), this shoudl bring you out of compiz
[/LIST]

/a way of solving this would be to install a different version of the display drivers, either through the regular hardware drivers meny or through a program called envyng.Pick your poison.

Thanks for the suggestions.  For the most part my system runs without a hitch.  The white screen only appears every so often.  I've just tried envyng but it found the same driver currently installed (177).  I might roll back and see what happens.

I'll keep trying.  Cheers.

---

### Post by gregbzh on 2009-02-11
In developing news... My dual boot of Vista is crashing too (ie. completely freezing).  It could well be time for a new graphics card.  Must be that if Ubuntu is packing a sad when it never has since I've been using it (Dapper).

Great, something else to buy in the middle of a financial crisis!

---

