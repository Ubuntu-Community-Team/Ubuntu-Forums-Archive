---
title: "pixleated screen after playing with multiple monitors on Jaunty"
date: 2009-04-26
forum: New to Ubuntu
---

### Post by hendo2515 on 2009-04-26
Hi,

I upgraded to Jaunty today from Hardy on my T60 Lenovo laptop. Everything installed fine but went back to the default screen drivers. I installed the ATI drivers with package manager but couldnt find how to use them. I next went to the "Multiple Monitors" applet and tried to set the multiple monitors section. The screen didnt look right so i decided to reboot. Now I get the boot up screen ok, but the log in screen is full of rubbish, pixelated, and unreadable. 

I have tried to go into recovery mode and try and fix by adjusting xorg.conf manually, with the fix module in the recovery mode screen, xfix, dpkg-reconfigure and event by removing it completely. Nothing!!! The screen boots up exactly the same every time. :(. Could someone help me out please?

---

### Post by anim on 2009-04-26
You've tried:
sudo dpkg-reconfigure xserver-xorg

from the recovery console?

---

### Post by hendo2515 on 2009-04-26
Sure did. Nothing changed.

---

### Post by hendo2515 on 2009-04-26
I should add it didnt prompt for any screen settings in the process only keyboard. But i think read somewhere that the screen/monitor setting have been moved.

---

### Post by hendo2515 on 2009-04-27
Ok. i removed the fglrx packages and the system booted up.

---

