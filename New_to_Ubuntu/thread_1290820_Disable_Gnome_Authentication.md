---
title: "Disable Gnome Authentication?"
date: 2009-10-13
forum: New to Ubuntu
---

### Post by Odd_sam on 2009-10-13
I don't like having to "authenticate" myself every time I want to do simple stuff like mounting a file system or changing the CPU scale. How would I disable this?

---

### Post by Faolan84 on 2009-10-13
System > Administration > Authorizations

Go down the list and change the permissions regarding what you want to be able too access as a user and what requires root.

JUST BE REALLY CAREFUL!

Okay I found the entries you are looking for should be under:
hal > storage
  and the other one is
hal > power management > Configure CPU scaling frequency

---

### Post by coldReactive on 2009-10-13
> **Faolan Devyn Aodfin said:**
> System > Administration > Authorizations

Go down the list and change the permissions regarding what you want to be able too access as a user and what requires root.

JUST BE REALLY CAREFUL!

Adding yourself to "able to perform administrative tasks" when you normally can't will not allow you to change the root password (even though it should.)

He also wants to disable sudo/gksudo completely, which is not something that normally is allowed to be discussed, as it is equivalent to gaining or logging into root.

---

### Post by Odd_sam on 2009-10-14
That's where I went in 9.04 but I wasn't exactly thinking straight when I posted this and forgot to add that I'm on the karmic beta release.The Authorizations menu is not listed or hidden. And I already ran the visudo command and added myself as a user who does not have to use a password to use sudo/gksudo

---

### Post by Odd_sam on 2009-10-14
Turns out you have to install it from the repositories.
```

sudo apt-get install policykit-gnome

```

---

