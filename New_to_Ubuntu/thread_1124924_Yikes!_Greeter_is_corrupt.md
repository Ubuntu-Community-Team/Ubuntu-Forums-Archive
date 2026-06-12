---
title: "Yikes! Greeter is corrupt?"
date: 2009-04-13
forum: New to Ubuntu
---

### Post by ayastona on 2009-04-13
hi.. i installed conky according to the howto on this site...

then i realized that i didnt want it and removed the .conkyrc and .conkyrc~ files... then i removed the .sh file that i created so that it would run on startup... then i removed the entry for conky to start in system>preferences>sessions...

conky was still running on mydesktop...

i logged out and i got an error message saying that my greeter is corrupt and that it will try to revert to the other one or something...

when i got the chance to log in, i noticed that it was the same background and stuff that i set for remote logins a while back... 

how to fix?

---

### Post by Sorivenul on 2009-04-15
Did you try and actually *uninstall* conky, not just remove its configuration files?

Try:
```
sudo apt-get remove --purge conky
```

---

### Post by ayastona on 2009-04-17
that fixed it! thanks

---

