---
title: "Extremely terrible problem (     :( :(       )"
date: 2009-06-10
forum: New to Ubuntu
---

### Post by mj1001 on 2009-06-10
I have been ubuntu for some time (still a beginner ) so i tryed to install compizfusion and it worked great and when playing with the compizfusion manager i click on something and then the screen started to become black and everytime i click on the shutdown button on my keyboard it restart and the login works that start up works the chime song works and then after 2 seconds , the screen becomes black again.

Please help on what to do because may things have been stored on my ubuntu.
Please show me in steps how to fix everything since i am just a beginner 

(Feeling really depressed)


Thank you

---

### Post by hellocatfood on 2009-06-10
I had a similar problem. My screen went white when I tried to start compiz.

For me this was fixed by installing the proprietary graphics driver. You can do this by going to System > Administration > Drivers. If there are any drivers available you can install them from that menu.

I'm  a newbie too, but this worked for me

---

### Post by mj1001 on 2009-06-10
> **hellocatfood said:**
> I had a similar problem. My screen went white when I tried to start compiz.

For me this was fixed by installing the proprietary graphics driver. You can do this by going to System > Administration > Drivers. If there are any drivers available you can install them from that menu.

I'm  a newbie too, but this worked for me

I got a black screen i don't know which to click and even if I do it sometimes gets stuck... :(
Isn't there any shortcut to open the terminal and type a code that will fix my graphics...

---

### Post by hellocatfood on 2009-06-10
You can set a keyboard shortcut to open the terminal: System > Preferences > Keyboard Shortcuts I use F4 but choose whatever you want. I don't know the code to kill an application, but a quick google search could sort that out :-)

---

### Post by VCoolio on 2009-06-10
This command [seems to reset]("http://www.linuxforums.org/forum/ubuntu-help/116239-how-earth-do-you-reset-compiz-defaults-command-line.html") your compiz settings to default, so if the problem is a compiz setting (and from your post I assume that's it) this may fix it:
```
gconftool-2 --recursive-unset /apps/compiz
```

edit: forgot to say that ctrl+alt+F1 (or F2-6, try some) will give you a terminal; ctrl+alt+F7 will get you back to x.

---

### Post by mj1001 on 2009-06-11
> **VCoolio said:**
> This command [seems to reset]("http://www.linuxforums.org/forum/ubuntu-help/116239-how-earth-do-you-reset-compiz-defaults-command-line.html") your compiz settings to default, so if the problem is a compiz setting (and from your post I assume that's it) this may fix it:
```
gconftool-2 --recursive-unset /apps/compiz
```edit: forgot to say that ctrl+alt+F1 (or F2-6, try some) will give you a terminal; ctrl+alt+F7 will get you back to x.



Thank you and thanks alot guys for your help :)

really appreciate it :D

---

