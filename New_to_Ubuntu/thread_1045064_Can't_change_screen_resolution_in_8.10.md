---
title: "Can't change screen resolution in 8.10"
date: 2009-01-20
forum: New to Ubuntu
---

### Post by snowbalance on 2009-01-20
Hi again :oops:

I just did a clean install of 8.10 from 7.04, only now I can't change the screen resolution.  I have tried what I used in 7.04, that is: ```
sudo dpkg-reconfigure -phigh xserver-xorg
```, but instead of getting VESA and the resolutions, I get this:
```
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
```
There are no Update managers open, Synaptic isn't open... help? :(

---

### Post by cmnorton on 2009-01-20
There is a probably a lock file lying around somewhere, and you'll have to look for a file that ends in .lock file and delete it.

---

### Post by snowbalance on 2009-01-20
> **cmnorton said:**
> There is a probably a lock file lying around somewhere, and you'll have to look for a file that ends in .lock file and delete it.
I'm really, really, really brand new at this... would you or someone mind explaining what this means and how to do it? :)

---

### Post by zebanon on 2009-01-20
If u hav done default installation then there is an option in system>Preferences>screen resolution
i can change resolution using default installation but if i install the nvidia driver then there are no options of mine screen reso...

---

### Post by snowbalance on 2009-01-20
> **zebanon said:**
> If u hav done default installation then there is an option in system>Preferences>screen resolution
i can change resolution using default installation but if i install the nvidia driver then there are no options of mine screen reso...
Yes they are there, but they only go up to 800x600 :( Blargh.

---

### Post by zebanon on 2009-01-20
> **snowbalance said:**
> Yes they are there, but they only go up to 800x600 :( Blargh.

yes buddy i have installed the recommended drivers then also i havnt got the required reso which is 1280*1024

---

### Post by TunaCanTommy on 2009-01-20
Have you tried:

Applications -> System Tools -> nVidia Xserver Settings

---

### Post by snowbalance on 2009-01-20
> **TunaCanTommy said:**
> Have you tried:

Applications -> System Tools -> nVidia Xserver Settings
I don't have a System Tools tab under Applications :(

---

### Post by cmnorton on 2009-01-20
Try under System --> Administration and look for restricted drivers.

---

