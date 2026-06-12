---
title: "can't get check mark to select option: time server"
date: 2009-11-11
forum: New to Ubuntu
---

### Post by phranku on 2009-11-11
using ubuntu 9.10.  want to select time server in System > Administration > Time and date.  i see the list of servers.  i point to a server and either click, press enter, or press space bar.  in any case, the little square to the left of the server's name changes from dark to light.  but no check mark appears.  am i doing it incorrectly?

---

### Post by 0cton on 2009-11-11
Idk in 9.10 but you should run it as root or seek a button called unlock.

---

### Post by phranku on 2009-11-11
I'm sorry, but I don't understand &quot;run it as root or seek a button called unlock.&quot;  Can you explain or direct me to a helpful link.

---

### Post by Tinker Dragoon on 2009-12-12
> **phranku said:**
> I'm sorry, but I don't understand &quot;run it as root or seek a button called unlock.&quot;  Can you explain or direct me to a helpful link.

Many (if not all) of the adminstration apps require root privileges, which are normally either asked for after clicking on a button marked "unlock," or which are granted automatically by typing the appropriate command in a shell (e.g. sudo time-admin). In the case of the Karmic Time and Date app, this is accomplished by clicking on the little button that says "click to make changes," which you should already have done to access the server list in the first place.

I'm not sure why the check mark isn't appearing in your case, unless perhaps you've changed your desktop appearance to a theme that doesn't use check marks, but I would think that the change of color in the check box means that the selection is still being ticked, regardless.

---

