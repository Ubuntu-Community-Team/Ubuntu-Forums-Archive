---
title: "Shift Lock (Caps Lock) does not impact top row (number keys)"
date: 2010-10-29
forum: New to Ubuntu
---

### Post by mbehe on 2010-10-29
Hi, 
Just installed 10.10 on a HP Compaq nc6400 laptop (including updates).
Keyboard is Belgian, and I selected it as such during install.
I noticed that after pressing 'Shift Lock' (Caps Lock on US kb) the number keys on the top row do not change their behaviour as I would expect.
Expected behaviour after pressing Shift Lock = behave as if Shift key is pressed (is behaviour on all previous OS's I've used (Dos, Windows, VMS, numerous Unix variants)
Actual behaviour: the bottom characters on the keys are shown, with the accented characters (é,è,à) capitalized. 
Any ideas on what settings I need to change to get the behaviour I expect?
Thanks

---

### Post by mbehe on 2010-10-29
Ok, to whom it may concern: found it in the BE-forums.
Need to modify the setting of the caps lock key under system->preferences->keyboard->layouts->options
Option to choose is 'CapsLock toggles Shift so all keys are affected'.

Just in case a developer reads this: Belgian keyboards have a _Shift_ Lock key and not a _Caps_ Lock key.
So this key's default behaviour should be locking the shift key and not locking capitalization of characters.

Anyway thanks to the guys of the BE forum

---

### Post by Omnomnom on 2010-10-29
Thanks for the info, my friend had a similar problem with tab, I'll be sure to point him here.

---

### Post by stephanvaningen on 2011-01-07
Please note that this results in a difference of behaviour with the arrow keys compared to windhoze: arrow keys then select text i.o. just moving the cursor. Or can this key behaviour also be disabled on top of the enablement of the number-keys on shift-lock?

> **mbehe said:**
> Ok, to whom it may concern: found it in the BE-forums.
Need to modify the setting of the caps lock key under system->preferences->keyboard->layouts->options
Option to choose is 'CapsLock toggles Shift so all keys are affected'.

Just in case a developer reads this: Belgian keyboards have a _Shift_ Lock key and not a _Caps_ Lock key.
So this key's default behaviour should be locking the shift key and not locking capitalization of characters.

Anyway thanks to the guys of the BE forum

---

