---
title: "Control key not working"
date: 2010-01-11
forum: New to Ubuntu
---

### Post by unknown user on 2010-01-11
Recently my left hand control key ahs stopped working for things like Control + C/V. The smaller one on the right had side works all OK though. I can however, press control (left side) at the top of my address book contacts and click half way down to highlight all the email addresses, in Thunderbirds. So I do not think it is a hardware issue.

Is there anything that I can do to reset the keyboard, check if the Control key is working or generally get it working again?

---

### Post by ibninja on 2010-01-11
enter
```
xev
```
in terminal, and press the ctrl key.
it should return something similar to
```
KeyRelease event, serial 35, synthetic NO, window 0x4000001,
    root 0x118, subw 0x0, time 133090149, (238,-437), root:(1045,281),
    state 0x0, keycode 151 (keysym 0x1008ff2b, XF86WakeUp), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False
```
every time you press the key. This will prove whether it is a hardware issue or not. If it is not hardware (and that message comes up everytime you press the ctrl key) moving the ~/.gconf folder to a backup location (i.e. anywhere else on the hard drive) might fix the problem, but it might also alter other settings.

---

### Post by unknown user on 2010-01-12
Thanks for this, it looks like it is a hardware issue as nothing comes up

---

