---
title: "KDE login Window???/"
date: 2009-10-13
forum: New to Ubuntu
---

### Post by baskar007 on 2009-10-13
I have KDE4.3 installed on my Ubuntu9.04.
I want to change my login window so i changed my login window in KDE's login manager.

But still same old login manger is in work. at the same time if i change login window from Gnome login manger it works. 

how do i get KDE login manager to work?

---

### Post by pythonscript on 2009-10-13
```
sudo apt-get gdm
```

followed by

```
sudo apt-get install kdm
```

This will remove the Gnome Display Manager and install the K Display Manager, which is what you're after.

---

### Post by baskar007 on 2009-10-13
> **pythonscript said:**
> ```
sudo apt-get gdm
```

followed by

```
sudo apt-get install kdm
```

This will remove the Gnome Display Manager and install the K Display Manager, which is what you're after.
/Documents$ sudo apt-get gdm
[sudo] password for baskar: 
E: Invalid operation gdm




IS apt-get remove gdm   ??

---

### Post by pythonscript on 2009-10-13
Whoops, I missed the remove argument, so yes, it should be 
```
sudo apt-get remove gdm
```

I'm not sure if you want to use 

```
sudo apt-get purge gdm
``` because that might remove too many gnome programs (especially if you run sudo apt-get autoremove) to clean up afterwards, so maybe just stick with remove unless someone with more experience in the community says otherwise. Sorry about the mix up!

---

### Post by sandyd on 2009-10-13
you can just do
```

sudo dpkg-reconfigure gdm

```
the installer will then give you a choice on disabling it instead of rmoving it....

---

### Post by baskar007 on 2009-10-14
Thank you.

---

