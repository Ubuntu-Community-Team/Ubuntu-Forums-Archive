---
title: "Laptop fan Running"
date: 2009-02-22
forum: New to Ubuntu
---

### Post by Martin Marshalek on 2009-02-22
I know that this issue has come up many times before with laptop fans running constantly but I noticed something odd. When my fan runs constantly, the computer is actually cold there. What does this mean. 

Also, I found I could solve the problem by using the ubuntu-laptop-mode package but it then removes ubuntu-desktop, which means I won't get updates for Ubuntu core packages anymore. How can I use ubuntu-laptop-mode and keep ubuntu-desktop?

---

### Post by ibuclaw on 2009-02-22
> **Martin Marshalek said:**
> I know that this issue has come up many times before with laptop fans running constantly but I noticed something odd. When my fan runs constantly, the computer is actually cold there. What does this mean.

It means that the fans are working, and keeping your CPU cold. (Heat == bad) :)
> **Martin Marshalek said:**
> 
Also, I found I could solve the problem by using the ubuntu-laptop-mode package but it then removes ubuntu-desktop, which means I won't get updates for Ubuntu core packages anymore. How can I use ubuntu-laptop-mode and keep ubuntu-desktop?
That is complete blasphemy, ubuntu-desktop is a **meta-package**, it's only job is to install the packages it has dependencies on.
Removing it will do nothing. All installed packages will still be upgraded.

Regards
Iain

---

### Post by Martin Marshalek on 2009-02-22
Thanks, I thought meta-packages pointed to updates. I'll install the package to fix this then.

---

