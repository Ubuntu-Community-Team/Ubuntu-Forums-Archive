---
title: "Compiz slows down computer"
date: 2010-01-05
forum: New to Ubuntu
---

### Post by John.b.Goode on 2010-01-05
Hello,
I am running a Lenovo T400 with discrete graphics, and proprietary driver installed.  I would love to use Compiz animation, but when I have effects turned on, if I click on, say, my 'Home Folder' icon (or any other application, minimized window, etc.), I experience a very perceptible delay before it actually pops up.  Everything is relatively instant with eye candy turned off.  Is this common?  Is there a way to mitigate this problem?  Thank you in advance for your help.

---

### Post by thatguruguy on 2010-01-05
it sounds like you have a driver problem.  Do you have the ATI graphics card?

---

### Post by alphacrucis2 on 2010-01-05
> **thatguruguy said:**
> it sounds like you have a driver problem.  Do you have the ATI graphics card?


It's a well known problem with fglrx and/or X. There was a backfill patch that fixed the issue but messed up users with other hardware such as nvidia and intel so it was withdrawn but it can still be installed from a ppa. See the following launchpad thread.

[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/351186?comments=all]("https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/351186?comments=all")

I don't know if there is a proper fix but the ppa mentioned in launchpad may provide a workaround for fglrx users.

---

### Post by John.b.Goode on 2010-01-05
It appears so.  When I go to System> Administration> Hardware drivers I am told that ATI/AMD proprietary FGLRX graphics driver is in use.

---

### Post by John.b.Goode on 2010-01-05
Brilliant!!!! alphacrucis2, thanks so much, everything is resolved.

---

