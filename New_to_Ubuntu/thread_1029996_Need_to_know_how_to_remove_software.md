---
title: "Need to know how to remove software"
date: 2009-01-04
forum: New to Ubuntu
---

### Post by sadaruwan12 on 2009-01-04
Hi,
Guys do any one know how to completely remove an installed software on Ubuntu 'cos when I install I see so many dependences get installed but when I remove I see only that software getting removed all the other stuff stays in my hard disk can any one help me.

---

### Post by adult swim on 2009-01-04
```
sudo apt-get autoremove
``` will clean up left over dependencies that aren't being used by anything.

---

### Post by evilkastel on 2009-01-04
also, you might try to remove the sowftware with sudo apt-get purge

---

### Post by sadaruwan12 on 2009-01-04
Is there any GUI based software available for that purpose.

---

### Post by sadaruwan12 on 2009-01-04
> **evilkastel said:**
> also, you might try to remove the sowftware with sudo apt-get purge
What does purge do

---

### Post by baracuda68 on 2009-01-04
Also don't forget

sudo apt-get autoclean

cleans up partial packages that are unused...

:D

---

### Post by oneadvent on 2009-01-04
you can find it in synaptic and remove it there too.

---

### Post by semi_fiction on 2009-01-04
> **sadaruwan12 said:**
> Is there any GUI based software available for that purpose.
Go to System->Administration->Synaptic Package Manager. Search for the package you want to remove, then select "completely remove."
That should remove dependencies of that package that are not in use by other packages

---

### Post by baracuda68 on 2009-01-04
> **sadaruwan12 said:**
> What does purge do


Uninstalls the package _and_ deletes its configuration files along with it.
Normal "remove" command just uninstalls the package itself.

try 
apt-get --help

---

### Post by sadaruwan12 on 2009-01-04
> **semi_fiction said:**
> Go to System->Administration->Synaptic Package Manager. Search for the package you want to remove, then select "completely remove."
That should remove dependencies of that package that are not in use by other packages
No bro it doesn't remove the full package only the selected part of that package and that's my problem.

---

### Post by Sef on 2009-01-04
How did you install the software?

---

### Post by sadaruwan12 on 2009-01-04
> **Sef said:**
> How did you install the software?
Same way as every one using SPM (synaptic package manager)

---

### Post by bwang on 2009-01-04
Why don't you just use:
```
sudo apt-get autoremove
```
Open a Terminal and type the code in, then hit enter. Is there any particular reason why you need a GUI?

---

### Post by sadaruwan12 on 2009-01-04
> **bwang said:**
> Why don't you just use:
```
sudo apt-get autoremove
```
Open a Terminal and type the code in, then hit enter. Is there any particular reason why you need a GUI?
So that should clear up my unused dependxencies right

---

### Post by adult swim on 2009-01-04
> **sadaruwan12 said:**
> So that should clear up my unused dependxencies right

yes

---

