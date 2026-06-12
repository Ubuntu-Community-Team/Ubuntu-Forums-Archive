---
title: "packages kept back"
date: 2010-10-01
forum: New to Ubuntu
---

### Post by Hippytaff on 2010-10-01
Why when I apt-get upgrade are linux-generic linux-headers-generic linux-image-generic kept back?

---

### Post by andrewthomas on 2010-10-01
All the dependencies can not be satisfied.

---

### Post by Hippytaff on 2010-10-01
Tell me theres a quick fix :-)

---

### Post by CharlesA on 2010-10-01
> **andrewthomas said:**
> All the dependencies can not be satisfied.

Not exactly.

You'd need to do an **apt-get dist-upgrade** to get the new kernel.

---

### Post by Hippytaff on 2010-10-01
> You'd need to do an **apt-get dist-upgrade** to get the new kernel


Excellent...thanks

---

### Post by Hippytaff on 2010-10-01
is it now safe to remove these - linux-headers-2.6.32-24{u} linux-headers-2.6.32-24-generic{u} with aptitude remove?

---

### Post by Hippytaff on 2010-10-01
Yes it is - I just did it and it's still working :-D

---

