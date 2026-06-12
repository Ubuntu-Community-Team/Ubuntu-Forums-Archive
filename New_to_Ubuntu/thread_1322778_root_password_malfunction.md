---
title: "root password malfunction"
date: 2009-11-11
forum: New to Ubuntu
---

### Post by Trevor Johnston on 2009-11-11
My root password for authentication is magically not working anymore... can I change this?

---

### Post by nothingspecial on 2009-11-11
Reboot and when you see the "grub loading" dialogue, press eascape.

Boot into recovery mode > root shell (or whatever it`s called at the moment)

Issue the command```
 adduser *[COLOR="Red"]your_username[/COLOR]* admin
```

and all should be fine.

---

### Post by Trevor Johnston on 2009-11-11
w00t thank you, it worked ^.^ .

---

### Post by nothingspecial on 2009-11-11
Nice one

:guitar:

---

