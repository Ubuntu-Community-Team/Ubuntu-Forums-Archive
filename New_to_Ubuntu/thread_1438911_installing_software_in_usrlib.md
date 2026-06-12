---
title: "installing software in usr/lib"
date: 2010-03-25
forum: New to Ubuntu
---

### Post by javafiend on 2010-03-25
Is there any benefit to attempting to install software, such a s tar.gz package, into usr/lib as opposed to your home folder?

---

### Post by cogier on 2010-03-25
I can't see why as that's where a lot of the programs will go when installed and to save space you might like to delete the taz.gz file once the installation is complete.

---

### Post by wojox on 2010-03-25
Anything you install outside of the repo's should go in /opt

---

### Post by javafiend on 2010-04-06
So if I already have something installed in my home folder I should just be able to move it to /opt and change shortcut links right?

---

### Post by philinux on 2010-04-06
> **javafiend said:**
> So if I already have something installed in my home folder I should just be able to move it to /opt and change shortcut links right?

There's nothing wrong with it being in your home folder. If it aint broke etc...

---

### Post by mcduck on 2010-04-06
> **javafiend said:**
> Is there any benefit to attempting to install software, such a s tar.gz package, into usr/lib as opposed to your home folder?

If you are the only user on the machine (or you only want the apps/libraries to be available to your own user, not others), then installing things into your home directory is absolutely fine.

If you want the app/library to be available to all users of the machine, then you of course need to install it into some location accessible to anybody. Either the default system directories, or /opt if you like to keep stuff coming from outside of Ubuntu's package management separated from the default stuff (like I do).

---

### Post by KdotJ on 2010-04-06
> **mcduck said:**
> /opt if you like to keep stuff coming from outside of Ubuntu's package management separated from the default stuff (like I do).

Me too, all my extra non-ubuntu stuff gets installed into here, including my own projects which I have packaged. I dont like having programs installed to my home directory, (except for the folders i dont see eg. the ones with a prefix of a dot). The same as back when I used windows I didnt insall programs into "My Documents".

---

