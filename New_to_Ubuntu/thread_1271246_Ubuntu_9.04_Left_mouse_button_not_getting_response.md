---
title: "Ubuntu 9.04 Left mouse button not getting response"
date: 2009-09-20
forum: New to Ubuntu
---

### Post by B. Traven on 2009-09-20
Hi everyone,

I was wondering if I could get some help with Ubuntu 9.04.

I have recently upgraded to this version however I have immediately come across a major problem - a minute or so after starting up and logging in, the left/select button on the mouse cannot get a response, therefore I can't open or close anything or select anything. The middle and right mouse buttons are unaffected and work fine. I can still type in gedit for example.

I had no such problems with the earlier versions which I had for nearly a year.

Any help would be greatly appreciated. Is there any use in reinstalling?

Cheers,
Mike

---

### Post by majiciannz on 2009-09-21
> **B. Traven said:**
> Hi everyone,

I was wondering if I could get some help with Ubuntu 9.04.

I have recently upgraded to this version however I have immediately come across a major problem - a minute or so after starting up and logging in, the left/select button on the mouse cannot get a response, therefore I can't open or close anything or select anything. The middle and right mouse buttons are unaffected and work fine. I can still type in gedit for example.

I had no such problems with the earlier versions which I had for nearly a year.

Any help would be greatly appreciated. Is there any use in reinstalling?

Cheers,
Mike

This might sound like a stupid question but have you tried another mouse.
If you have ruled out a faulty mouse, can you try loading a live CD to see if you still have the problem.

If the problem has gone when running a live cd then perhaps you will have to re-install. Unless someone else can come up with a fix.

---

### Post by B. Traven on 2009-09-21
Hi majiciannz,
 
 
No a faulty mouse can definitely be ruled out - I have my Ubuntu dual-booted with Pista and it works ok there.

---

### Post by norm7446 on 2009-09-21
I would try and boot the Live CD, just to give it a try. 

Is the mouse a PS2 one or a USB one !!!!

---

### Post by B. Traven on 2009-09-26
Thanks for the advice

It no longer gives me any problem, possibly because I disabled the Touchpad within mouse preferences.

---

### Post by TimKraemer on 2009-11-11
It seems I have a very similar problem. 

The left mouse button stops responding in 9.04 and 9.10. I tried both on a live CD. However, on my laptop the touchpad as well as the USB mouse have the same problem.

If i change from left- to right-handed mouse, the right mouse button stop to work, and the left is fine.

I worked around that problem by using a different USB mouse, which worked fine for a while, but suddenly the problem appeared again on the USB mouse.

Any solutions?

Link to my thread: [http://ubuntuforums.org/showthread.php?t=1323171](http://ubuntuforums.org/showthread.php?t=1323171)

Would you mind posting the output of your  /var/log/Xorg.0.log
and "grep -B 5 mouse /proc/bus/input/devices" ?

---

### Post by itsbrad212 on 2009-11-11
sometimes ubuntu doesn't have the correct driver :D

---

### Post by TimKraemer on 2009-11-12
> **itsbrad212 said:**
> sometimes ubuntu doesn't have the correct driver :D

True.

Somehow there was a "Macintosh mouse emulation" device in my configuration that was mixed up with my touchpad oder USB mouse device. I don't understand why this is happening, or why it seems to happen only randomly, but I could fix my problem by telling HAL to ignore all Macintosh input devices.

@B. Traven:
Your problem my come back to hunt you with your USB mouse. If it does, check with "grep -B 5 mouse /proc/bus/input/devices" if you have a some kind of "Macintosh mouse emulation" in there. In case you have, look at my thread for the solution.

---

