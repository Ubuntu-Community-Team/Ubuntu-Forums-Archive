---
title: "any one know what is this ???"
date: 2010-06-19
forum: New to Ubuntu
---

### Post by jabor ihab on 2010-06-19
Hello every one please with all regards 
I am used Ubuntu 10.4 but there is problem 
after update , uncompleted update and this is my out put 
 
E: korganizer: subprocess installed post-installation script returned error exit status 2
E: libvncserver0: subprocess installed post-installation script returned error exit status 2
E: krdc: dependency problems - leaving unconfigured
E: krfb: dependency problems - leaving unconfigured

if any one could solve it please 
what is should be done to let update install with out an error

---

### Post by philinux on 2010-06-19
Open a terminal, apps>access>terminal.

```
sudo dpkg --configure -a
```

---

### Post by shardvexspangler on 2010-06-19
Those are probably debian files.  You are using Kubuntu aren't you?  Those are KDE thingies.
 
Open the terminal.
To fix the first error "sudo apt-get install korganizer"

---

### Post by Chame_Wizard on 2010-06-19
Seems like the necessary package is missing.
```
sudo aptitude kdelibs kde-base
```

---

### Post by jabor ihab on 2010-06-19
Dear all thanks a lot for your replay 
but I do all the steps which recommended me with it ,still the error thank you again

---

### Post by lkjoel on 2010-06-19
Go to the terminal, then type this:
```
gksu synaptic
```Do you receive a pop-up saying something like "You have X broken packages"?

---

