---
title: "Ubuntu 11.04 doesn't shut down or restart"
date: 2011-08-03
forum: New to Ubuntu
---

### Post by al.adab on 2011-08-03
apologies if a solution to this has been posted - couldn't find it through google

have installed Ubuntu 11.04 on an Asus EEE PC 904HD - it works perfectly, except that occasionally I can't shut it down or restart it (in which case I resort to *sudo halt*)

without really knowing if it's the right thing to do, I tried to apply 
[http://jechem.blogspot.com/2011/04/fix-plymouth-splash-screen-in-ubuntu-on.html](http://jechem.blogspot.com/2011/04/fix-plymouth-splash-screen-in-ubuntu-on.html) 

the problem hasn't been solved, though. I'm not sure this has to do with the fact that I can't update the grub (though changes appear to have been saved): [I]

~$ sudo update-grub
/etc/default/grub: 35: Syntax error: EOF in backquote substitution[/I]

I also tried [http://www.omgubuntu.co.uk/2011/05/how-to-fix-the-plymouth-boot-screen-when-using-proprietary-graphics-drivers/](http://www.omgubuntu.co.uk/2011/05/how-to-fix-the-plymouth-boot-screen-when-using-proprietary-graphics-drivers/) 

it's still occasionally impossible to shut down Ubuntu, though some of the graphics upon booting seem to have improved...any idea?

---

### Post by skatinjj on 2011-08-03
[http://www.linuxquestions.org/questions/linux-newbie-8/ubuntu-10-04-lts-not-closing-down-827685/]("http://www.linuxquestions.org/questions/linux-newbie-8/ubuntu-10-04-lts-not-closing-down-827685/")

Apparently for those people using 10.04, they just had to remove the shutdown button from the panel and add it back.  One person had to remove it, add it back, use the shutdown command from terminal before the fix worked.

---

### Post by skatinjj on 2011-08-03
Also curious, can you shutdown the computer from the terminal with this:

```
sudo shutdown now
```

---

### Post by al.adab on 2011-08-03
thanks both - haven't tried the 10.04 fix yet.

yes, *sudo shutdown now*  seems to initially shut down the system except that it then leads to a scroll-down menu. The option on the top (if I remember correctly) is about restarting the system in safe/normal mode. If I click that, the system does not restart: it gets kind of stuck at the battery check. Ctrl-Alt-F1 + *sudo halt* is the only solution at that point...

---

### Post by amjjawad on 2011-08-03
> **al.adab said:**
> apologies if a solution to this has been posted - couldn't find it through google


[www.googlubuntu.com](www.googlubuntu.com)

;)

---

### Post by al.adab on 2011-08-06
all of a sudden I can shut down normally - don't know why...

---

### Post by fonsi2099 on 2011-08-10
I resolved the problem disabling the "quickstarter" by Libreoffice.
I notice that after I've activated the systray quickstarter my UBU-11.04 doesn't shutdown or restart anymore.

as follow: 
Open your Libreoffcie go to:  Tool/Options/Libreoffice/Memory/ Enable systray Quickstarter (let it disabled)

:popcorn:

---

### Post by al.adab on 2011-08-16
quickstarter was indeed the reason. 
great, thanks for your help

---

