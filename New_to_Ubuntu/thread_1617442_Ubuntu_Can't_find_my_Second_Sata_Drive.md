---
title: "Ubuntu Can't find my Second Sata Drive"
date: 2010-11-09
forum: New to Ubuntu
---

### Post by Shoei on 2010-11-09
Hello All

I'm new to Ubuntu, fairly new to the Linux world... But have to say... LOVE IT!...

got one real issue...

When My desktop was a windows pc... I had two Sata drives running on it...
Killed the windows... because it was slow and sucked... install Unbuntu... very nice!

But I can't see my second drive... this has all the family pics and every thing important to me on it.

I tried  mount dev/sdb1 it fails...
I did the fdisk-l and it dose not come up in the list.  I have just noticed that my sata dvd rw drive is not available either

Searched through the threads... seems to be many... some please help clarify, how to resolve this issue?

Thanks
Shoei

:guitar:

---

### Post by Hippytaff on 2010-11-09
What does
```

df -h

```
return?

---

### Post by Shoei on 2010-11-09
I solved this... it was I BIOS thing... update the BIOS... Add the Sata Drive Ubuntu wins again!

---

