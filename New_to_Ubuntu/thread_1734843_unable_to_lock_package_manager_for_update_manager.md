---
title: "unable to lock package manager for update manager"
date: 2011-04-20
forum: New to Ubuntu
---

### Post by ct2000 on 2011-04-20
hello I recently upgraded from 9.04 to 10.10 with a clean install but ever since I have not been able to upgrade through the update manager. Even if I restart the system it wont work and neither does software center I get the same error message The first pic is the error message i get then in the next pic is a new error I am getting about image upgredes failing. Eversince I did the install the system would intermittenly hang so I decided to check into it and found that the cpu was always at 100% something to do with root and apt-get I dont know if it is but figured it was worth adding thank you

---

### Post by jtarin on 2011-04-20
Try using Synaptic to update.Post results/messages.

or failing that you could use the command ```
dpkg-reconfigure -a
```  This will reconfigure all installed packages that use debconf. Warning: this may take a long time.

---

