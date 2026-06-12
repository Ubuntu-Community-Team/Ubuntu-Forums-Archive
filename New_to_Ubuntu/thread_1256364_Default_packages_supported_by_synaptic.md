---
title: "Default packages supported by synaptic"
date: 2009-09-02
forum: New to Ubuntu
---

### Post by Macinbomzh on 2009-09-02
Could someone please list all the packages that come by default with ubuntu which require synaptic?

I accidently removed synaptic and now add/remove and language support are gone.

Thank you for your patience.

---

### Post by CatKiller on 2009-09-02
If you've gone too far down the rabbit hole and removed the APT backends, you're in trouble. If it's just that you've removed the graphical tools, but package management works otherwise, you can use ```
sudo apt-get install ubuntu-desktop
``` to re-install all the packages that are included by default with Ubuntu. That's probably your best bet to get things back to how they were. Unless I'm misinterpreting what you've said, and you *don't* want things back the way they were, you just want language support back.

---

### Post by egalvan on 2009-09-02
> **Macinbomzh said:**
> 
I accidently removed synaptic and now add/remove and language support are gone.


if you just removed Synaptic, you can try:

```
sudo apt-get install synaptic
```

before installing the complete desktop.

---

### Post by Macinbomzh on 2009-09-02
I only need graphical tools; I've managed to find add/remove but cannot find language support.

I don't want to have my ubuntu re-installed; Just language support.

---

### Post by halitech on 2009-09-02
if you run the above command it will simply compare the list of files that are installed to what should be installed and install whatever is missing.

---

### Post by Macinbomzh on 2009-09-02
Working.

Would be alot easier if someone would just add a "repair" button somewhere; well added it myself, now all is fine. 

Thank you. :D

---

