---
title: "synaptic help"
date: 2009-08-06
forum: New to Ubuntu
---

### Post by dino1515 on 2009-08-06
Having a problem? Why is it that when I use synaptic to uninstall things such as cheese photo booth why does it say i need to uninstall gnome-desktop-environment???? Why would cheese photo booth make that be uninstalled also?????
This is not the only thing, there seems to be alot of things that require me to uninstall this or other important files, i just want to get rid of some things!

---

### Post by Sef on 2009-08-06
Ubuntu Desktop is a metapackage, thus if you try to remove on part of it, it all wants to be removed.

---

### Post by dino1515 on 2009-08-06
so how do i get rid of these things, it used to work fine but i recently reinstalled and now this is happening, even when i go to computer janitor which used to work great it wants to get rid of alot of things like the gnome desktop etc...

---

### Post by alexandari on 2009-08-06
That is weird. Just use **Add/Remove Programs** to uninstall. Btw,does **sudo apt-get install -f** give you anything about uninstalling gnome-desktop?

---

### Post by dino1515 on 2009-08-06
when i add/remove programs it tells me to use synaptic to uninstall the ones i want to get rid of. This is real annoying.

---

### Post by alexandari on 2009-08-06
how about using apt-get remove?

---

### Post by anaconda on 2009-08-06
> **Sef said:**
> Ubuntu Desktop is a metapackage, thus if you try to remove on part of it, it all wants to be removed.

And you dont have to worry about removing the meta-package!!

removing it WONT remove gnome.

---

### Post by dino1515 on 2009-08-06
I have attached a pic of my Janitor window, see how it wants to remove alot of important packages, there are 98 in total, i am afraid that if i hit cleanup then my system will break, why is it doing this, how do i fix it, maybe if someone told me what the absolute necessary files to keep my desktop and system running are then i could remove all but those or any help would be good?

---

### Post by 3rdalbum on 2009-08-06
If in doubt, don't remove anything.

If your package manager wants to remove a metapackage, then let it. It won't delete the packages that are referenced in the metapackage.

---

### Post by dino1515 on 2009-08-06
ended up just reinstalling ubuntu and starting again, it was annoying

---

### Post by LewRockwell on 2009-08-06
> **dino1515 said:**
> ended up just reinstalling ubuntu and starting again, it was annoying

honestly...

most of the people who pay-it-forward here and on other forums as well...

learned by trial, error, and dozens of re-installs...

.

---

