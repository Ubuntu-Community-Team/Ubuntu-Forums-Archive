---
title: "stuck in grub-rescue - grub-xputs not found."
date: 2010-11-10
forum: New to Ubuntu
---

### Post by otveit on 2010-11-10
hello,
during upgrade from 10.04 to 10.10 my computer (asus ul30vt) froze completely. The upgrade seemed to be almost finished, so i rebooted. Since that i have only seen the grub-rescue prompt with the error message: "The symbol "grub_xputs" not found."

I have tried the potential workarounds i have found, but with no success. Trying to load modules in the rescue prompt result in the same error message. 

I get no result from trying to boot the liveUsb (have no dvd/cd-rom) or changing around on the boot order.  

The only option left that i can think of is bringing the computer to a friends house and mounting the hardrive in her desktop computer and trying to fix grub from her ubuntu installation.

anyone have any tips on alternatives to this(!), or any tip on how to proceed if i hook the drive up to another machine physically?

---

### Post by Hippytaff on 2010-11-10
Can you boot from a liveUSB and then post the result of this script
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by Quackers on 2010-11-10
Have a look at this thread.
[http://ubuntuforums.org/showthread.php?t=1580752](http://ubuntuforums.org/showthread.php?t=1580752)

The commands in post #2 did not work for me, but the commands in post #4 after the "[COLOR="DarkRed"]Added[/COLOR]" [COLOR="Black"]did work. [/COLOR]

---

### Post by otveit on 2010-11-11
thanks for replys, but i am not able to boot liveUSB. Thats my problem, i am stuck in grub-rescue.

---

### Post by Quackers on 2010-11-11
Turn the machine off and start from usb.

---

