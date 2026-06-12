---
title: "How do I change my password?"
date: 2010-01-04
forum: New to Ubuntu
---

### Post by greenleaves123 on 2010-01-04
OK, this is a really stupid question lol, but I can't seem to figure out how to change my password.

---

### Post by drs305 on 2010-01-04
Well, it depends. Have you forgotten it or just want to change it. 

To change it, System, Administration, Users & Groups. Unlock it, highlight your username, select Properties, and there is an option to change the password.

*Please mark the thread solved via the Thread Tools link near the upper right of the original post when you no longer need assistance.*

---

### Post by sisco311 on 2010-01-04
Go to System -> Preferences -> About Me and click the Change Password button

or

Go to System -> Administration -> Users and Groups -> select your user -> Properties -> Account tab -> Set password by hand.

or

Open a terminal (Applications -> Accessories -> Terminal) 
and run:
```
passwd
```
NOTE: In the terminal there is no visual feedback when you enter your password.

---

### Post by greenleaves123 on 2010-01-04
Thanks for that!

---

### Post by sisco311 on 2010-01-04
> **drs305 said:**
> 
To change it, System, Administration, Users & Groups. Unlock it, highlight your username, select Properties, and there is an option to change the password.



Users are allowed to change they own password. So there is no need to click the unlock button (run the application as root).

---

