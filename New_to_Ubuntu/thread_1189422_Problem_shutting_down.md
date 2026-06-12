---
title: "Problem shutting down"
date: 2009-06-16
forum: New to Ubuntu
---

### Post by darkfeline on 2009-06-16
I'm running Ubuntu Intrepid, and recently, I've been having trouble shutting down or restarting my computer.  I don't remember doing anything out of the ordinary when the problem emerged.  Basically, what happens is that the computer shuts down/reboots as it normally would, but when it's supposed to turn off, the screen just becomes all messed up.  At this point, I just manually turn off the computer via the power button.  It appears to be no more than an annoyance, since I can still turn off my PC, but I don't know if it's a symptom to a more serious problem, and even if it isn't a big problem, it's still annoying.  All help appreciated, since I have no idea where to even start to fix this.

---

### Post by swisstone198 on 2009-06-16
How far through shutdown does it get before you have to turn it off?

---

### Post by abhiroopb on 2009-06-16
Similar type of things happens to me.

At random times when I shutdown it gets to a black screen with a blinking cursor and stays there.

---

### Post by 4Orbs on 2009-06-16
This works for some people, myself included. Open the /etc/modules file in a text editor as root:
```
gksudo gedit /etc/modules
```
and add this as the last line of the file
```
apm power_off=1
```
Save and close the file.
Reboot.
Shutdown should work after that.

---

### Post by darkfeline on 2009-06-16
Well, after rebooting a few times, the problem seems to have resolved itself... Some sort of temporary xorg glitch, perhaps?  At any rate, if it comes back, I'll probably try your suggestion, 4Orbs.  
What had happened before was that everything went as expected, but at the point where my computer shuts off normally, it would show a weird fuzzy screen.
@abhiroopb: You seem to have another problem entirely, though I'm just guessing, really.  Sometimes, when I start my computer, it freezes at BIOS with a blank screen and blinking cursor.  Unplugging any USB devices solves this.  Not sure if it'll help your situation, though, sorry.

---

