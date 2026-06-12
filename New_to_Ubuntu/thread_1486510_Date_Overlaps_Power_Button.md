---
title: "Date Overlaps Power Button"
date: 2010-05-17
forum: New to Ubuntu
---

### Post by walkerchuckwalker on 2010-05-17
[IMG]file:///home/corey/Desktop/Screenshot.png[/IMG]Can someone help with this display problem? There is a display issue with the date in the tool bar sometimes, where it will over lap the power button so I can't select that menu. Heres the screenshot:   (top right)                               [IMG]http://i903.photobucket.com/albums/ac233/walkerchuckwalker/Screenshot.png[/IMG]



If you could list some commands for terminal to use like:

reboot
poweroff

Things like that. How about the one for logoff? Lock Screen? Sleep?

---

### Post by Ozymandias_117 on 2010-05-17
> **walkerchuckwalker said:**
> [IMG]file:///home/corey/Desktop/Screenshot.png[/IMG]If you could list some commands for terminal to use like:

reboot
poweroff

Things like that. How about the one for logoff? Lock Screen? Sleep?

Have you tried unlocking and moving the time/date and stuff?

Reboot = sudo shutdown -r now

Poweroff = sudo shutdown -h now

Sleep = pm-suspend (Might need sudo)

Hibernate = pm-hibernate (Might need sudo)

The only way I know of to log out of the graphical login is to kill Xorg.

Edit: By the way, where'd you get that background?

Another edit: I just tested it for you... Don't kill Xorg unless you switch to a virtual terminal (ctrl + alt + f1). Your computer will freeze and you won't be able to do anything if you try to kill Xorg from a terminal emulator :):):)

---

### Post by walkerchuckwalker on 2010-05-18
I got the Background here
[http://www.hongkiat.com/blog/60-most-execellent-ubuntu-wallpapers/](http://www.hongkiat.com/blog/60-most-execellent-ubuntu-wallpapers/)

I think if you like that one, you will like about 80% of the others on this page.

---

### Post by Chesamo on 2010-05-18
Have you tried moving the power button over to the other side, or moving the date/time further away?

---

