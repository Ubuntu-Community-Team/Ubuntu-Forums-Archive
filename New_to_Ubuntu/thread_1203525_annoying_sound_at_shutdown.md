---
title: "annoying sound at shutdown"
date: 2009-07-03
forum: New to Ubuntu
---

### Post by orky7 on 2009-07-03
hey there is an annoying "system" (beep) sound in 9.04 twice or thrice when i shutdown my computer i checked the sound settings and disabled almost every thing but the sound is still there what to do to disable the system sound,by the way there was no such sound while using 8.04....

---

### Post by ubudog on 2009-07-03
To turn it off go to [http://ubuntuforums.org/showthread.php?t=126746](http://ubuntuforums.org/showthread.php?t=126746) That should show you how.

---

### Post by orky7 on 2009-07-03
the thing is there is no system sound problem on application like terminal,vim or in keys like backspace i disabled the system sound totally but still there is that sound(system beep) when i shutdown my system  why?

---

### Post by ubudog on 2009-07-03
It just does that.  I don't think there is a way to disable it.  Sorry.

---

### Post by Celauran on 2009-07-03
Blacklist the module. Edit /etc/modprobe.d/blacklist (blacklist.conf in Jaunty) and add the following line:

```
blacklist pcspkr
```

Requires a reboot to take effect.

---

### Post by ubudog on 2009-07-03
I totally forgot about that.

---

### Post by arjuntank on 2009-07-03
check /etc/rc0.d

---

### Post by orky7 on 2009-07-03
check for what in /etc/rc0.d, as i am relatively new in this field.

---

### Post by arjuntank on 2009-07-03
blacklist pcspkr

didnt solved your problem?
if not try System \ Preferences \ Sound and turn off the system beep..
simple!
or
open /etc/inputrc
uncomment the following line or just place it in the file
set bell-style none
means do not bell on tab-completion

Edit:
/etc/rc0.d contains scripts that executes during runlevel 0 that is during shutdown
some of the applications might have caused the beep. I am not pretty sure about this.

---

### Post by imbjr on 2009-07-03
> **ubudog said:**
> It just does that.  I don't think there is a way to disable it.  Sorry.

My PC has just started doing this.

I think I'm going to have to blacklist a driver ...

---

### Post by raymondh on 2009-07-03
[http://ubuntuforums.org/archive/index.php/t-1021542.html](http://ubuntuforums.org/archive/index.php/t-1021542.html)
[http://www.debuntu.org/how-to-turn-off-virtual-console-beep](http://www.debuntu.org/how-to-turn-off-virtual-console-beep)

---

### Post by ubudog on 2009-07-03
Just go to System>Preferences>Sound and then go to the tab named Sounds and uncheck the one that says "Play alert sound".  See if that works.

---

