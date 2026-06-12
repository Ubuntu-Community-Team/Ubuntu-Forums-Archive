---
title: "invisisble add-on on panel cannot remove them"
date: 2009-11-26
forum: New to Ubuntu
---

### Post by civillianslave on 2009-11-26
i tried to add to my top panel something which would monitor my system for overheating.
It seems to have put several on the bar but i cannot see them and right clicking on a large section of the bar produces nothing like the normal "Add to panel- properties" options.

Can anyone help?

(i know i have put up a few posts here but these are pains in my laptop, i LOVE the new Ubuntu so if i can work these niggles out......heaven)

---

### Post by stoogiebuncho on 2009-11-26
Which panel applet are you trying to use?

---

### Post by 73ckn797 on 2009-11-26
You can get the panels back up to the OEM state just after installation by running the following command using terminal.
 

 Go to Applications/Accessories/Terminal
 

 Paste this command in:
 ```
gconftool-2 --recursive-unset /apps/panel
```
 

 Restart the computer and all will be back to normal.


At least this will get you back to the beginning then you can modify again.

---

