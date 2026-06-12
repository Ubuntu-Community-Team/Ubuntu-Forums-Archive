---
title: "Incorrect Screen Resolution in Jaunty"
date: 2009-06-07
forum: New to Ubuntu
---

### Post by signonmail on 2009-06-07
Greetings,

Sorry if this has been answered a thousand times but I can't seem to find an answer to my particular goof.

I changed my screen refresh rate from 60Hz to 75Hz.  When I rebooted a get a screen that is a rainbow of colors.

I am using a Dell C610 laptop with an ATI video card and a Gateway FPD1530 display.

Can anyone tell me how boot to a terminal session and change the resolution back to 60Hz?

Thanks

---

### Post by Mark Phelps on 2009-06-08
Do Ctrl-Alt-F1 to get to a console and run xrandr.  Do a "man" on xrandr and you will see thet "--rate" parameter which is used to set the refresh rate.

---

### Post by reeseslover531 on 2009-06-08
Also you can try the ubuntu recovery mode from the grub boot menu.

---

### Post by NightwishFan on 2009-06-08
I would try the Ubuntu Recovery Mode. Just press escape during the GRUB countdown and choose recovery. Then repair your graphics automatically from there. Good luck!

---

### Post by signonmail on 2009-06-08
> **NightwishFan said:**
> I would try the Ubuntu Recovery Mode. Just press escape during the GRUB countdown and choose recovery. Then repair your graphics automatically from there. Good luck!
 
Unfortunately, I tried that and it didn't work.  I think I'm stuck attempting a fix with terminal.  
 
Thanks for the suggestion

---

### Post by signonmail on 2009-06-08
> **Mark Phelps said:**
> Do Ctrl-Alt-F1 to get to a console and run xrandr. Do a "man" on xrandr and you will see thet "--rate" parameter which is used to set the refresh rate.
 
Attempted xrandr and sudo xrandr from the terminal. Both commands yield "Can't open display".

---

### Post by reeseslover531 on 2009-06-09
that is weird, what does ```
xrandr -q
``` say?

---

### Post by signonmail on 2009-06-09
> **reeseslover531 said:**
> that is weird, what does ```
xrandr -q
``` say?

xrandr -q yields the same message "Can't open display".

---

### Post by signonmail on 2009-06-09
Solution.  Reinstall OS.  Learn valuable lesson to not mess with the screen resolution when you are just learning Linux..  This is NOT Windows.

---

### Post by wpshooter on 2009-06-09
> **signonmail said:**
> Solution.  Reinstall OS.  Learn valuable lesson to not mess with the screen resolution when you are just learning Linux..  This is NOT Windows.

So you are not supposed to be able to change the screen display attributes in Ubuntu ?

---

### Post by reeseslover531 on 2009-06-10
You can generally do them from the display control panel.  I am not sure why this one just epically failed.

---

### Post by NightwishFan on 2009-06-10
There might be some other issue. The repair X server option should restore it to its original configuration when you installed. It even returns me to using the NV driver.

---

