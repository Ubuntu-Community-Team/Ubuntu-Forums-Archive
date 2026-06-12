---
title: "How to completely uninstall Firefox?"
date: 2009-01-23
forum: New to Ubuntu
---

### Post by tahitiwibble on 2009-01-23
I would like to install a virgin copy of Firefox. Can someone tell me how to **completely** remove it along with **all** the add-ins, extensions, flash players etc etc.

Many thanks.

---

### Post by SunnyRabbiera on 2009-01-23
well step 1 is to remove firefox via the package manager, I am sure you know how to do this if you removed packages before.
step 2 is a bit more tricky, open your home directory and hit control-h to unhide hidden folders.
find the .mozilla folder and just send it to your trash bin, then delete it.
reinstall firefox
done :D

---

### Post by tahitiwibble on 2009-01-23
Thanks SunnyR, will this procedure get rid of everything related to Firefox? Java, for example. I'd really like to start with a Firefox as if I'd just replaced the whole OS.

---

### Post by Bios Element on 2009-01-23
Open up your terminal and type the following.

```

sudo apt-get purge firefox
sudo apt-get install firefox

```

That should do ya.

---

### Post by SunnyRabbiera on 2009-01-23
> **tahitiwibble said:**
> Thanks SunnyR, will this procedure get rid of everything related to Firefox? Java, for example. I'd really like to start with a Firefox as if I'd just replaced the whole OS.

No, for flash and java you will have to remove them separately.
But again its easy to do with the package manager.

---

### Post by tahitiwibble on 2009-01-23
Thanks to both you guys ..... here goes. :)

---

