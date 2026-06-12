---
title: "Google Earth"
date: 2009-07-07
forum: New to Ubuntu
---

### Post by ncc1701e on 2009-07-07
I accidently installed google earth as root and now I wish to uninstall it and re-install correctly. When I click its uninstall script using sudo nautilus it says:

** (nautilus:5112): WARNING **: Unable to add monitor: Operation not supported
Could not find a usable uninstall program. Aborting.

does this mean i need to get some sort of un-installer program?

---

### Post by cariboo on 2009-07-07
All programs are installed as root, or else the only place you can install the is in your home directory. If you installed Google Earth from the Medibuntu repositories, then use:

```
sudo apt-get purge googleearth
```

If you installed from a binary, just start nautilus as root, press Alt-F2 and type:

```
gksu nautilus
```

Navigate to the directory Google Earth is installed in a delete it.

---

