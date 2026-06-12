---
title: "Can't install package (disabled button, no status given)."
date: 2009-07-09
forum: New to Ubuntu
---

### Post by MaximeDebosschere on 2009-07-09
Hello to everyone,
 
I'm trying to install the python-gnome2-extras package in Ubuntu 9.04 (Jaunty Jackalope).
 
As the screenshot underneath shows, the install button is disabled while no status is being given. 
 
There is no internet access, I wonder if this has anything to do with it? Where do I go from here?
 
Thanks in advance,
Maxime.
 
 
[IMG]http://img140.imageshack.us/img140/9058/screenshotcgk.jpg[/IMG]

---

### Post by random turnip on 2009-07-09
Are you sure it's not already installed?

Is this in Add/Remove?

---

### Post by MaximeDebosschere on 2009-07-09
> **random turnip said:**
> Are you sure it's not already installed?
 
Is this in Add/Remove?
I forgot to mention: it's not.
 
_Edit_: I definitely know that python-gnome2-extras is not installed: when trying to install a package which depends on it, a 'Dependency is not satisfiable' error is being displayed.

---

### Post by MaximeDebosschere on 2009-07-10
Anyone? I still haven't found the cause of this problem.

---

### Post by SaaTeeVaaGreen on 2009-07-10
i dunno why the install button is disabled, but have you tried to install it with the terminal using the apt-get command?

---

### Post by oldos2er on 2009-07-10
> **MaximeDebosschere said:**
> 
There is no internet access, I wonder if this has anything to do with it? 

 All the package manager front-ends (e.g. Add/Remove, Synaptic, apt-get, etc.) expect a working internet connection. If you have access to another computer, you can use either Keryx ([http://keryxproject.org/](http://keryxproject.org/)) or AptonCD ([http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)) to download packages.

---

