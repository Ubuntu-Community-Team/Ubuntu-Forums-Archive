---
title: "help updating to gnome 2.32"
date: 2010-09-15
forum: New to Ubuntu
---

### Post by cadogan281 on 2010-09-15
i was reading that gnome 2.32 release canidate just came out today.i have been trying to find a tutorial on here and on the web for upgrading to it.does anyone know how to update to the beta release?thanks

---

### Post by lkjoel on 2010-09-15
Try:
```
sudo add-apt-repository ppa:wrinkliez/ppasearch
sudo apt-get update
sudo apt-get install ppasearch
ppasearch gnome
```
Then find an entry that is similar to "Gnome Daily", "Gnome Testing", "Gnome Unstable" or "Gnome Beta"
Then enter the number.

---

### Post by andrewthomas on 2010-09-15
> **lkjoel said:**
> Try:
```
sudo add-apt-repository ppa:wrinkliez/ppasearch
sudo apt-get update
sudo apt-get install ppasearch
ppasearch gnome
```
Then find an entry that is similar to "Gnome Daily", "Gnome Testing", "Gnome Unstable" or "Gnome Beta"
Then enter the number.
 I don't believe that this will work.

---

### Post by cadogan281 on 2010-09-16
i did gnome experimental (36) and tried to update in update manager but nothing showed up.was i missing something?

---

### Post by lkjoel on 2010-09-16
> **cadogan281 said:**
> i did gnome experimental (36) and tried to update in update manager but nothing showed up.was i missing something?
Check on the Synaptic Package Manager.
Press Reload.
Click on Mark all Updates.
Search for gnome.
You should see either yellow packages, or other packages with newer versions.

---

### Post by cadogan281 on 2010-09-16
allright that worked.thank u.

---

### Post by lkjoel on 2010-09-16
> **cadogan281 said:**
> allright that worked.thank u.
Do you want to mark this as solved?

---

### Post by cadogan281 on 2010-09-16
do i just write that in the title,or was there a different thing for that?

---

### Post by lkjoel on 2010-09-16
Click on Thread Tools->Mark this thread as solved.

---

