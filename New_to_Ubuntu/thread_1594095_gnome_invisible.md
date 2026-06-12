---
title: "gnome invisible"
date: 2010-10-12
forum: New to Ubuntu
---

### Post by SpockPrime on 2010-10-12
i was messing around in ccsm (opacity, brightness and saturation) and now everything is invisible, is there anyway to fix this without reinstalling Ubuntu

---

### Post by sikander3786 on 2010-10-12
At the login screen, press Ctrl + Alt + F1, it will take you to a console. Login using your credentials. The better option will be to remove compiz with all its configuration and reinstall it later.

```
sudo apt-get remove --purge compiz
```

```
sudo apt-get install compiz
```

After completion, press Ctrl + Alt + F7, you will see the login screen, login and see if it helped.

---

### Post by SpockPrime on 2010-10-12
I have Ubuntu set to auto login so no login screen but when i was on my desktop i was able to ctrl-alt-f1 and remove compiz but it didn't help.

---

### Post by sikander3786 on 2010-10-12
Remove the compiz config file from .config and restart.

```
rm -R /home/***username***/.config/compiz
```

---

### Post by SpockPrime on 2010-10-12
unfortunately that didn't work either, i appreciate you time and help but i think i will just reinstall. thanks again

---

### Post by ft-Orchard on 2010-10-12
Deleting **~/.gnome **should work. 
The factory settings will be restored.

(restart after.)

---

### Post by SpockPrime on 2010-10-12
would i do it like this?

rm -R /home/username/.gnome


if so it said no such folder.

---

### Post by lkjoel on 2010-10-12
> **SpockPrime said:**
> would i do it like this?

rm -R /home/username/.gnome


if so it said no such folder.
Try:
```
rm -rf ~/.gnome
rm -rf ~/.gnome2

```
I think they mean .gnome2.

---

