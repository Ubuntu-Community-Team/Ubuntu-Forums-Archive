---
title: "Residual Menu images after 10.10 upgrade"
date: 2010-10-15
forum: New to Ubuntu
---

### Post by dude-buntu on 2010-10-15
Hello - new here!

I had a successful upgrade from 10.04 to 10.10 but noticed the menu options are exceptionally jumpy and many times leaves residual pieces of the drop down menus when I scroll through....also sometimes I have to click on the option multiple times to activate the drop down menu.

The only way to clear it off the screen is to right click and choose edit menus

I have Maverick Meerkat on:

Compaq Presario
2ghz Sempron processor
1024mb ram
inboard video

I believe the system requirements are ok for Meerkat - not sure if this is video driver related - no other indicators of incompatibility. There were no problems with this in 10.04 

Other than this, great job to the Ubuntu team!

---

### Post by mutt850 on 2010-10-19
Ditto, having the same problem on an HP DV7 only I cannot get the after image to clear at all without a reboot. Thankfully it does not happen every time I use a menu.

---

### Post by sandyd on 2010-10-19
> **dude-buntu said:**
> Hello - new here!

I had a successful upgrade from 10.04 to 10.10 but noticed the menu options are exceptionally jumpy and many times leaves residual pieces of the drop down menus when I scroll through....also sometimes I have to click on the option multiple times to activate the drop down menu.

The only way to clear it off the screen is to right click and choose edit menus

I have Maverick Meerkat on:

Compaq Presario
2ghz Sempron processor
1024mb ram
inboard video

I believe the system requirements are ok for Meerkat - not sure if this is video driver related - no other indicators of incompatibility. There were no problems with this in 10.04 

Other than this, great job to the Ubuntu team!
seems like a problem with video card.
its called ghosting.

post output of
```

lspci
```

---

### Post by mutt850 on 2010-10-21
On the HP DV7 the problem seems to have gone away after I disabled the ATI/AMD proprietary FGLRX graphics driver.

---

### Post by daviesk24 on 2011-02-05
I'm having this trouble too.  I have a Lenovo 3000 N200 with a nVIDIA GeForce Go 7300 graphics card running Ubuntu 10.10 with metacity.  The problem seems to happen about every day now.  

I've also noticed that a very light blue and mostly translucent circle appears on the screen from time to time.

I downloaded the latest nVidia driver, version 260.19.36, but that didn't seem to help.  The only way I can clean up the screen is to run a "metacity --replace" command.   Does anyone have suggestions?  Thanks.

---

