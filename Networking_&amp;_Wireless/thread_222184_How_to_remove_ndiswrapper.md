---
title: "How to remove ndiswrapper?"
date: 2006-07-24
forum: Networking &amp; Wireless
---

### Post by Gamebeavis on 2006-07-24
I have only ever installed/removed things using apt-get. But I recently had a problem with my wifi that required me to download/make/install it from source. But now I wish to remove it, but cant seem to figure it out. I removed the driver module from memory, then removed the driver from the hard disk, but now I am unable to actualy uninstall ndiswrapper, I think I have to make uninstall it, but i am not sure how.

---

### Post by Jagot on 2006-07-24
It should just be:

```
sudo make uninstall ndiswrapper
```

---

### Post by Gamebeavis on 2006-07-24
Ok, I tried that, but this is what I get. 

make: *** No rule to make target `uninstall'.  Stop.

---

### Post by orengolan on 2007-03-22
i am having the same problem, anything new?

---

### Post by Floppyjoe on 2007-03-22
If you installed a version of ndiswrapper not in the repositories you need to cd to the folder where you installed it from and then issue:
```
sudo make uninstall
``` a few times until it stops saying stuff about removing files.

---

### Post by orengolan on 2007-03-23
thanks, worked!

---

### Post by whitematter33 on 2007-12-13
I am still having problems with removing ndiswrapper. I have tried those methods, but it still gives the same error. Even when I am in the ndiswrapper directory.

Home/etc/ndiswrapper/

---

