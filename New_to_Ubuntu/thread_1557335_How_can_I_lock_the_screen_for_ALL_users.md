---
title: "How can I lock the screen for ALL users?"
date: 2010-08-20
forum: New to Ubuntu
---

### Post by hodad on 2010-08-20
I would like to be able to disable all other users when I lock the screen on my (emphasis on MY) pc.  Right now, I can lock the screen, but others can still log in under their (subordinate)logons.   Anyone know how I can lock out ALL users when I choose "Lock Screen"?

Thanks

---

### Post by zeroseven0183 on 2010-08-20
To disable the user switching, do it in Configuration Editor.
1. Open it in the terminal: **gconf-editor**
2. Navigate to **desktop**  > **gnome** > l**ockdown**
3. check **disable_user_switching**

You'll see that the button to Switch User is now hidden/disabled when you lock your screen.
Hope that helps.

---

### Post by hodad on 2010-08-22
Thanks for your suggestion - it worked only too well!

It indeed disabled user switching, but, unfortunately, also disabled my own shutdown and my own lock screen.  After doing the disable, the kids can openly use my session (since I can no longer lock the screen).

Was interesting finding the gconf screen, tho!

---

