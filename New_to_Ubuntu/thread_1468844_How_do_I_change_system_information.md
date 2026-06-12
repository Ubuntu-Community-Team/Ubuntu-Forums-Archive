---
title: "How do I change system information?"
date: 2010-05-01
forum: New to Ubuntu
---

### Post by crjackson on 2010-05-01
My desktop says the system name is charles-laptop, how do I changes this to charles-desktop ?

---

### Post by wojox on 2010-05-01
You need to change them in hosts and hostname:

```
gksudo gedit /etc/hosts
```

```
gksudo gedit /etc/hostname
```

---

### Post by crjackson on 2010-05-01
> **wojox said:**
> You need to change them in hosts and hostname:

```
gksudo gedit /etc/hosts
```

```
gksudo gedit /etc/hostname
```

Thanks, it's not changed yet.  Does it take affect after a reboot?

---

### Post by wojox on 2010-05-01
> **crjackson said:**
> Thanks, it's not changed yet.  Does it take affect after a reboot?

You got it.

---

### Post by crjackson on 2010-05-01
> **wojox said:**
> You got it.

Thanks for your help. I won't if a UPS being connected caused the install to think it was a laptop.

Thanks again.

Reboot did the trick!

---

