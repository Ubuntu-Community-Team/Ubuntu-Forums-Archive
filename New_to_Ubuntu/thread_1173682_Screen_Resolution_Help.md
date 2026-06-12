---
title: "Screen Resolution Help"
date: 2009-05-30
forum: New to Ubuntu
---

### Post by monchedeng on 2009-05-30
Hi, I mistakenly changed my resolution to the lowest setting, now I cannot revert back using the Appearance settings function since the apply button cannot be seen anymore.

How can I change my resolution manually?

---

### Post by keplerspeed on 2009-05-30
Have a look here: [http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

You can just reconfigure X by entering this command:

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by CatKiller on 2009-05-30
> **monchedeng said:**
> Hi, I mistakenly changed my resolution to the lowest setting, now I cannot revert back using the Appearance settings function since the apply button cannot be seen anymore.

Alt-A will do the same as pressing the _A_pply button. Alt-C will do the same as pressing the _C_lose button.

---

