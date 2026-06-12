---
title: "new user account"
date: 2009-05-28
forum: New to Ubuntu
---

### Post by natman on 2009-05-28
Hi,
I am thinking about playing around with my ubuntu by testing some new driver repos ( [[COLOR="Blue"]here[/COLOR]]("https://launchpad.net/~ubuntu-x-swat/+archive/x-updates"))
My question if i do all this in a new user account and then screw up and make mistakes, will my other user account still be safe?

Thanks:

---

### Post by whoop on 2009-05-28
No, updates/upgrade/installations are nearly always system wide, not account wide (is that even a word "wide" ?).

---

### Post by Kobalt on 2009-05-28
Yes, changing drivers and so on affects your system, not only user settings.

---

### Post by philinux on 2009-05-28
> **natman said:**
> Hi,
I am thinking about playing around with my ubuntu by testing some new driver repos ( [[COLOR="Blue"]here[/COLOR]]("https://launchpad.net/~ubuntu-x-swat/+archive/x-updates"))
My question if i do all this in a new user account and then screw up and make mistakes, will my other user account still be safe?

Thanks:

Best way to test is to set up another install on it's own partition, or use virtualbox to install then test.

---

### Post by whoop on 2009-05-28
> **Kobalt said:**
> Yes, changing drivers and so on affects your system, not only user settings.

That's funny, a "No" and a "Yes" and if I am not mistaken we are both correct ;)

---

### Post by CatKiller on 2009-05-28
A good rule-of-thumb is that anything that requires sudo, and so asks you to enter a password, is system-wide. Anything that doesn't need sudo only affects one user.

---

