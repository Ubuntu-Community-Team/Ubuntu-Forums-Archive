---
title: "desktop displays"
date: 2010-01-31
forum: New to Ubuntu
---

### Post by squrl on 2010-01-31
I have two network drives that mount through fstab. They work fine. My question is... Is there a way to get rid of the icon and display on the desktop but not disturb the mounting?

Thanks

---

### Post by cenzorrll on 2010-01-31
i believe if you mount them through /mnt instead of /media they will not show on the desktop (although i also don't think they'll "show" anywhere else either)

---

### Post by tom.swartz07 on 2010-01-31
> **cenzorrll said:**
> i believe if you mount them through /mnt instead of /media they will not show on the desktop (although i also don't think they'll "show" anywhere else either)

[http://www.howtogeek.com/howto/ubuntu/hide-removable-drive-icons-from-your-ubuntu-desktop/](http://www.howtogeek.com/howto/ubuntu/hide-removable-drive-icons-from-your-ubuntu-desktop/)


Best and easiest method ever.


Hope this helps!

---

### Post by dolphinaura on 2010-01-31
run gconf-editor
then go to apps -> naitulus -> desktop
its rigght i there (i think)

---

### Post by tom.swartz07 on 2010-01-31
> **dolphinaura said:**
> run gconf-editor
then go to apps -> naitulus -> desktop
its rigght i there (i think)

Yep! Just like in my post-

Its titled 'volumes visible', just un-check it

---

### Post by cenzorrll on 2010-02-02
> **tom.swartz07 said:**
> [http://www.howtogeek.com/howto/ubuntu/hide-removable-drive-icons-from-your-ubuntu-desktop/](http://www.howtogeek.com/howto/ubuntu/hide-removable-drive-icons-from-your-ubuntu-desktop/)


Best and easiest method ever.


Hope this helps!

hmm, never even thought to look there.  badass.

---

