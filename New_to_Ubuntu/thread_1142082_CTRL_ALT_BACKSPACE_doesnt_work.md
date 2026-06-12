---
title: "CTRL ALT BACKSPACE doesnt work"
date: 2009-04-28
forum: New to Ubuntu
---

### Post by asuastrophysics on 2009-04-28
whose idea was it to take out CTRL ALT BACKSPACE? 

how do i put this back?

---

### Post by mikewhatever on 2009-04-28
Ubuntu release notes:
[http://www.ubuntu.com/getubuntu/releasenotes/904#Ctrl-Alt-Backspace%20disabled%20by%20default%20in%20Xorg](http://www.ubuntu.com/getubuntu/releasenotes/904#Ctrl-Alt-Backspace%20disabled%20by%20default%20in%20Xorg)

---

### Post by phantom3113 on 2009-04-28
As the release notes say, this was disabled to prevent people from accidentally restarting X. To switch it back, run "dontzap --disable"

---

### Post by x33a on 2009-04-28
please search the forums or google, before posting new threads. this key-combo disable has been discussed many times before.

install dontzap
```
sudo aptitude install dontzap
```then do as phantom instructed

---

### Post by mc4100 on 2009-04-28
You can still achieve the same thing, without installing anything more.
Switch to tty with, for example, Ctrl+Alt+F1 and run:
```
sudo service gdm restart
```

---

### Post by x33a on 2009-04-28
> **mc4100 said:**
> You can still achieve the same thing, without installing anything more.
Switch to tty with, for example, Ctrl+Alt+F1 and run:
```
sudo service gdm restart
```

this seems easier to you instead of pressing ctrl+alt+backspace?

and if you don't want to install anything, you can directly modify xorg.conf

[https://wiki.ubuntu.com/X/Config/DontZap](https://wiki.ubuntu.com/X/Config/DontZap)

---

### Post by asuastrophysics on 2009-04-29
thanks for the how-to, guys. i probably should've checked the forums first. 

i've been using sudo /etc/init.d/gdm restart. it's kind of a pain in the a** when compared to CTRL ALT BACKSPACE.

that's weird that they thought people were accidentally pressing it. i never once accidentally hit all those three together. the backspace key is far enough away from DELETE for it to not be a problem. :)

---

### Post by mikewhatever on 2009-04-29
> **asuastrophysics said:**
> 

that's weird that they thought people were accidentally pressing it. i never once accidentally hit all those three together. the backspace key is far enough away from DELETE for it to not be a problem. :)

The backspace and del keys are right next to each other on many notebooks.

---

### Post by Wiebelhaus on 2009-04-29
In all the years of Linux computing I have never once inadvertently hit that specific key combination. Nor can I see how anyone could , seriously.

---

### Post by brunogirin on 2009-04-29
> **asuastrophysics said:**
> that's weird that they thought people were accidentally pressing it. i never once accidentally hit all those three together. the backspace key is far enough away from DELETE for it to not be a problem. :)

Well, it all depends on your keyboard I suppose. On the ThinkPad T42 I am typing this on, there is about 2mm of space between the Delete and the Backspace keys. Considering my sausage fingers and the fact that the Backspace key is significantly larger, it would be very easy to press it rather than delete.

So, I sort of understand the logic behind it: disable a key sequence that a lot of people don't use (well, I've never used it, obviously my own experience is not representative but I believe the concept of restarting X is alien to most newbies) while giving the option to re-enable this behaviour for people who use and want it.

---

### Post by Wiebelhaus on 2009-04-29
> **brunogirin said:**
> Well, it all depends on your keyboard I suppose. On the ThinkPad T42 I am typing this on, there is about 2mm of space between the Delete and the Backspace keys. Considering my sausage fingers and the fact that the Backspace key is significantly larger, it would be very easy to press it rather than delete.

So, I sort of understand the logic behind it: disable a key sequence that a lot of people don't use (well, I've never used it, obviously my own experience is not representative but I believe the concept of restarting X is alien to most newbies) while giving the option to re-enable this behaviour for people who use and want it.

I've explained it to noobs as an emergency exit , if something freezes or stops responding hit eject and log back in.

---

### Post by Sukarn on 2009-04-29
The new default key combination for this is **[Right Alt]+[SysRq]+[k]**

---

### Post by adam_kimber on 2009-04-29
I find the CTRL-ALT-BACKSPACE combo really useful. Use it to get my X back if a fullscreen App won't die from the KILL -KILL option. Usually happens when messing about with Wine though... 

As for CTRL-ALT-DELETE that does nothing in ubuntu anyway? So why would people be pressing that combination and then accidently nuking X? Seems to me that there must be a really small minority of cases where this has actually happened. Oh well. At least it can be turned back on!

---

### Post by Paqman on 2009-04-29
> **sx66gns said:**
> In all the years of Linux computing I have never once inadvertently hit that specific key combination. Nor can I see how anyone could , seriously.

Me neither. I've used it a lot on purpose though. My machine sometimes fails to resume from suspend properly. Enabling it is now on my shortlist of things to do on a fresh install.

---

