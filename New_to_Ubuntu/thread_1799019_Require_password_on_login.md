---
title: "Require password on login"
date: 2011-07-07
forum: New to Ubuntu
---

### Post by PrettyFlower on 2011-07-07
Ok now before I get redirected to 30 different places where this has already been posted and solved, let me explain the problem.  I'm running Ubuntu 11.04 and want to require a password on login. I turned it off at some point so it would auto-login but now I want to go back to the original behavior.  Most threads say to do this using System > Administration > Login Window > Security Tab but this is impossible since this menu doesn't actually exist, and has instead been replaced with something called Login Screen that doesn't seem to contain an option to require a password.  I have also tried editing /etc/gdm/config.conf but there doesn't seem to be a way to require a password from there either.  Sorry if this is a really nooby question, but I've been completely unable to solve this myself.

---

### Post by SteveDee on 2011-07-07
The System > Administration > Login Screen should look like the attached...

...select the "show the screen..." radio button.

---

### Post by sleepy3103 on 2011-07-07
Try the power button in the top panel to the right, then system settings.

---

### Post by grahammechanical on 2011-07-07
If you load that Login Screen utility you will see a little box called Login Screen Settings. Unlock it to edit it and tick the box marked Show the screen for choosing who will log in. This will uncheck the box Log in as named user automatically.

Regards.

---

### Post by dcsoldschool53 on 2011-07-07
Check login utility for natty. If it is not in there, try looking in users and groups. It is in one or the other, not sure which one.

---

