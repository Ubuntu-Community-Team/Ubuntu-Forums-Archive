---
title: "do not have permissions on pendrive"
date: 2010-12-12
forum: New to Ubuntu
---

### Post by spillage2 on 2010-12-12
Hi All,

Not really a big issue but every known and then when I pop in a pendrive I get a message "The folder "xxxxxxx" cannot be copied because you do not have permissions to create it in the destination.

If i format the drive its all good but would like to know why this is happening from time to time..

cheers,

Spill.

---

### Post by mapes12 on 2010-12-13
You should be able to overcome this by moving stuff from the pendrive with Nautilus launched with su privilages like this in Terminal ```
gksudo nautilus
```If you delete anything with Nautilus launched like this make sure you press and hold down the Shift key at the same time as hitting the Delete key otherwise you will end up clogging Root's Trash Can.

---

### Post by spillage2 on 2010-12-15
Of course nautilus...Thanks

---

