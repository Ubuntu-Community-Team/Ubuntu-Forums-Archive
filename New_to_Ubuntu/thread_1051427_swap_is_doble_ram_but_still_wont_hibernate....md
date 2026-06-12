---
title: "swap is doble ram but still wont hibernate..."
date: 2009-01-26
forum: New to Ubuntu
---

### Post by libihero on 2009-01-26
my swap is double my ram right now, and when i try to hibernate, all i get is a blank screen with a flashing text prompt.  i wait for two minutes and it still does not hibernate.

---

### Post by mrbiggbrain on 2009-01-26
DId u install from disk or via WUBI (from windows)

---

### Post by libihero on 2009-01-26
i only have ubuntu on my harddrive

---

### Post by drs305 on 2009-01-26
Is your swap working correctly? You can check with:
```
free -m
```

If not:
```

sudo swapon -a
*then check*
free -m
*if not:*
sudo blkid -c /dev/null | grep swap && cat /etc/fstab | grep swap  # Compare UUIDs

```

---

### Post by libihero on 2009-01-26
i get:
   total       used       free     shared    buffers     cached
Mem:          1895        966        929          0         64        274
-/+ buffers/cache:        627       1268
Swap:         3906          0       3906
it looks like it's workin fine right?

---

### Post by drs305 on 2009-01-26
> **libihero said:**
> 
it looks like it's workin fine right?

Yes it does. In answer to post #7, I'll look around - you might try searching with some of your machine's specifics.

---

### Post by libihero on 2009-01-26
then is there any reason why my computer isn't hibernating?

---

### Post by anewguy on 2009-01-26
Try making swap 2xmemory size PLUS about 200k for overhead and see if that works - may need more, but start at 200k.  If not, I suspect something else is running which stops hibernation.

Dave :)

---

### Post by libihero on 2009-01-26
k i'll just put 500k just in case....

---

### Post by libihero on 2009-01-27
ok now my swap is more than double my ram, and hibernate still doesnt work... :(

---

### Post by Locutus_of_Borg on 2009-01-27
try the tuxonice kernel patch
[http://www.tuxonice.net/](http://www.tuxonice.net/)

be sure to set your swap partition device in the kernel

and i'd suggest not checking replace swsusp in the kernel as well

---

### Post by libihero on 2009-01-27
lol can u explain that in lamen terms?

---

### Post by libihero on 2009-02-09
i still need help with this.... :(

---

