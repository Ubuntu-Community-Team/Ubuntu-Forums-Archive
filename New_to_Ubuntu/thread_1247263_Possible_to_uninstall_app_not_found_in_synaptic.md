---
title: "Possible to uninstall app not found in synaptic?"
date: 2009-08-22
forum: New to Ubuntu
---

### Post by aharown07 on 2009-08-22
I was looking for a way to manage fonts and came across Font Manager here
[http://lazyubuntu.com/manage-fonts-in-ubuntu-with-font-manager.html](http://lazyubuntu.com/manage-fonts-in-ubuntu-with-font-manager.html)

So I installed following the directions there (didn't see Font Manager in the package mgrs)... using a dpkg command after a wget to download it.

However, after a few minutes it was clear to me that I wasn't going to figure out how to make it do what I wanted (browse a large collection of fonts on my usb hd and select ones to "install" (activate?)). 
So I went to Font Matrix, which is excellent. 

Anyway, now I can't figure out how to get rid of Font Manager and it's cluttering up a menu so... wd be nice. I'm assuming apt-get etc. won't work in this case since it doesn't show up in synaptic.

---

### Post by markharding557 on 2009-08-22
you will have to get rid of it manually that is hunt down the various bits and delete them

---

### Post by ks07 on 2009-08-22
He installed using dpkg, which implies he installed using a .deb file. Doesn't that mean he can go into synaptic, and font manager should be under the installed (local or obsolete) status section. At least that's what seems to happen on my ubuntu install after I installed gens.

---

### Post by aharown07 on 2009-08-22
Yep. That did it. Synaptic, then click **Origin** then **Local** (or something with "local" in it, as I recall), then it shows up and you can do the usual uninstall thing.
Thx

---

### Post by oldos2er on 2009-08-22
```
sudo dpkg -r <package name>
```

---

### Post by ks07 on 2009-08-22
> **aharown07 said:**
> Yep. That did it. Synaptic, then click **Origin** then **Local** (or something with "local" in it, as I recall), then it shows up and you can do the usual uninstall thing.
Thx
No problem glad to be of service for once :P

---

