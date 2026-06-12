---
title: "Tuning Utility"
date: 2011-08-03
forum: New to Ubuntu
---

### Post by sheshan123 on 2011-08-03
Isn't there a tuning utility for ubuntu? By tuning utility i mean the program which tunes up the pc, finds and deletes bloat files, cleans registry(well, an ubuntu alternative to it, is there?) etc. It would be good to find alternatives of Ccleaner, Glary Utilities or TuneUp utilities for ubuntu. Ty in advance. :popcorn:

---

### Post by Matt__ on 2011-08-03
not really needed :)
but if you want to tidy up a little, open a terminal
```
sudo apt-get clean && sudo apt-get autoremove
```you could also install [ubuntu-tweak]("http://ubuntu-tweak.com/") which has some useful tools.

---

### Post by sheshan123 on 2011-08-03
> **Matt__ said:**
> not really needed :)
but if you want to tidy up a little, open a terminal
```
sudo apt-get clean && sudo apt-get autoremove
```you could also install [ubuntu-tweak]("http://ubuntu-tweak.com/") which has some useful tools.
what does the code actually do?

---

### Post by Matt__ on 2011-08-03
removes install/update cache files and packages that are no longer needed/orphaned.

If you install Tweak it will do the same from a GUI and also clean up old kernel entries.

from```
man apt-get

```
> clean:
clean clears out the local repository of retrieved package files.
           It removes everything but the lock file from
           /var/cache/apt/archives/ and /var/cache/apt/archives/partial/. When
           APT is used as a dselect(1) method, clean is run automatically.
           Those who do not use dselect will likely want to run apt-get clean
           from time to time to free up disk space.>  autoremove:
           autoremove is used to remove packages that were automatically
           installed to satisfy dependencies for some package and that are no
             longer needed.


---

### Post by John-B on 2011-08-03
sheshan123, I found BleachBit is just like (Windows CCleaner) but even better.  It can be found in Ubuntu Software Center or Synaptic Package Manager

---

### Post by zeroseven0183 on 2011-08-03
Try Ubuntu Tweak. It's more than your needs. [http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

---

### Post by grahammechanical on 2011-08-03
There is also something called Computer Janitor that should already be installed. What it does and how good or safe it is I cannot tell you.

Regards.

---

### Post by Frogs Hair on 2011-08-03
Stay away from Computer Janitor unless you know exactly what your deleting. Ubuntu Tweak and Bleachbit run as administrator are better options if you want a GUI . The commands will serve just as well but is nice to see a list .

---

### Post by sheshan123 on 2011-08-04
Thanky You guys :) I'll give a try to all of em!

---

