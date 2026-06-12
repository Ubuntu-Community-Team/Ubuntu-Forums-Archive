---
title: "Some sort of Boot Scan"
date: 2010-02-08
forum: New to Ubuntu
---

### Post by jkb609gi8 on 2010-02-08
Periodically on boot up Ubuntu automatically does a disc or hard-drive scan. If one is paying attention, you can skip this process. I would like to know if there is any way to disable this feature?

---

### Post by pizza-is-good on 2010-02-08
Sorry, I don't know how to disable it, but I don't know why you'd want to do that tho. It is only once in a while, and it doesn't take that long.
It is good to have a routine check, it might detect problems and fix itself without having you go through any or much trouble.

If you don't have time for it one of the times that it pops up, just skip it, and let it run the next time you boot.

~pizza

---

### Post by nwadams on 2010-02-08
I'm not sure if you can disable the feature. I know there used to be a way to change the number of boots between occurrences. I'm wondering though, why would you want to disable this feature? It makes sure your disk is healthy and not dying.

---

### Post by ssulaco on 2010-02-08
I would highly recommend letting the FSCK run.
[http://en.wikipedia.org/wiki/Fsck](http://en.wikipedia.org/wiki/Fsck)

---

### Post by jkb609gi8 on 2010-02-08
The reason I want to disable the boot scan is because my hard-drive is on its way out, and the scan repetitively hangs up at the defective point. By chance I was able to re-install ubuntu, however I am quite sure if I allow it to scan it will hang again. I am just trying to by some time before replacing the hard-drive. I could not run e2fsck  manually. The automatic version doesn't seem to repair bad sectors. (If that is the correct term?)

---

### Post by jken146 on 2010-02-08
Back up! It will stop working altogether at some point.

I'd suggest running fsck manually (maybe in verbose mode) and letting it run until it's finished, even though that may take a long time.

---

### Post by tad1073 on 2010-02-08
put 0 0 at the end of you fstab entry, like so:
```
#Entry for /your/device :
UUID=yourUUID    /    ext4    errors=remount-ro    0    0
```

open a terminal and type:
```
sudo cp /etc/fstab /etc/fstab.backup
```
```
sudo gedit /etc/fstab
```

---

