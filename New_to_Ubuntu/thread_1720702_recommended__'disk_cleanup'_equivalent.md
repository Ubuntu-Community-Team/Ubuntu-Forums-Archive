---
title: "recommended  'disk cleanup' equivalent?"
date: 2011-04-03
forum: New to Ubuntu
---

### Post by Make Space for Science on 2011-04-03
Hi,

I have tried computer janitor but it either isn't work properly, or I am using is incorrectly.

Are there others out there that do a relatively good job of automatic cleaning for Ubuntu?

Appreciate any help.
MSFS

---

### Post by davidmohammed on 2011-04-03
I have used "[ubuntu tweak]("http://ubuntu-tweak.com/")" for doing just this.

---

### Post by arochester on 2011-04-03
Bleachbit? Tutorial here: [http://www.howtoforge.com/delete-unnecessary-files-from-your-desktop-with-bleachbit-on-ubuntu-9.04](http://www.howtoforge.com/delete-unnecessary-files-from-your-desktop-with-bleachbit-on-ubuntu-9.04)

---

### Post by I'mGeorge on 2011-04-03
sure there are
```
sudo apt-get clean
sudo apt-get autoclean
```

By the way when you uninstall a package you should consider using 
```
apt-get --purge remove package
``` this will also remove all its config files

you can install deborphan either(the equivalent of aptitude autoremove), but be careful, don't remove everything deborphan says you should. Some libraries even if they are not directly linked to any program they might be needed in certain circumstances and uninstalling them might cause loosing some programs functions

---

### Post by ajgreeny on 2011-04-03
You need to be a little careful with all these utilities, be it bleachbit, computer-janitor or even ubuntu-tweak to make sure that you check what it says you can and should remove.  They all have a tendency, in my experience, to mark anything you have installed manually which does not come from the repos of ubuntu itself.

---

### Post by Make Space for Science on 2011-04-04
Thanks all, will do some reading up on those suggested.

---

### Post by Q-ro on 2011-04-04
You could try "deborphan" be careful tho, some times it marks packages that have not been installed by synaptic (.deb you download from web pages).

Also it have a GUI,just install gtkorphan.

---

