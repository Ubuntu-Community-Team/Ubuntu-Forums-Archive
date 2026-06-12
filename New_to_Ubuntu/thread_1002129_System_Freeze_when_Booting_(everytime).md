---
title: "System Freeze when Booting (everytime)"
date: 2008-12-04
forum: New to Ubuntu
---

### Post by beastrace91 on 2008-12-04
Just when I had everything working...

So I just installed Steam/Counter Strike:Source via wine, I had my gfx drivers all installed using envyng. Upon loading CSS I see the game screen with the words "loading" for a few moments and then the screen goes black just showing a cursor. Upon tapping ctrl+esc it tabs out of the game window for a second and then back into it... Not a big deal, I tap the power button and everything shuts down just fine.

How ever now when I boot my laptop after logging in, it gets to the desktop screen, the screen flashes white for a moment and then goes back to normal, how ever when it goes back, the mouse still moves but I cannot click anything and it does not finish booting.

Did installing CSS and attempting to run it do this or is it coming from somewhere else? In any case any input on how to resolve the issue at hand? I removed vista when I had Kubuntu working so at the moment I am CPUless :( posting this from a school computer.

HALP!
~Jeff

---

### Post by beastrace91 on 2008-12-04
*bump* 

Even the slightest idea, anyone? I just really need it to boot so I can use it... I really do not want to have to reformat and possibly have this happen again :/

~Jeff

---

### Post by beastrace91 on 2008-12-04
*nudge*

Going back to vista is going to kill part of my soul...

~Jeff

---

### Post by handydan918 on 2008-12-04
IF you can get to a console...(via ctrl+alt+f1 maybe) you might try ```
sudo dpkg-reconfigure --phigh xserver-xorg
```

Luck!

---

### Post by handydan918 on 2008-12-04
> **beastrace91 said:**
> *nudge*

Going back to vista is going to kill part of my soul...

~Jeff

Hang tough! Don't give the b4rst4rds the satisfaction!



:p

---

### Post by beastrace91 on 2008-12-05
Thanks for the response... I will try this as soon as I can. If that does not fix it I think I am just going to install Ubuntu and then manually install KDE3 and all the KDE apps I like on it, most of the issues I've had so far have been from KDE 4 it seems :/

Either way I will let u know if that command line works.

~Jeff

---

### Post by beastrace91 on 2008-12-05
> **handydan918 said:**
> IF you can get to a console...(via ctrl+alt+f1 maybe) you might try ```
sudo dpkg-reconfigure --phigh xserver-xorg
```

Luck!

That did nothing useful :/

Ahh well formatting to Ubuntu 8.10 and then just going to install KDE3 once that is done... I don't get why they had to upgrade with KDE4 still so buggy.

~Jeff

---

