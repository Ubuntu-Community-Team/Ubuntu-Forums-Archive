---
title: "Software Center wont open"
date: 2010-11-12
forum: New to Ubuntu
---

### Post by hunter99507 on 2010-11-12
I was installing a package and something failed.  Now the update center, software center and synaptic center wont open.  How do i delete these files so i can make it work again.

I do sudo apt-get update, and this is what comes back

E: Type '&#8216;deb' is not known on line 59 in source list /etc/apt/sources.list
E: Type '&#8216;deb' is not known on line 1 in source list /etc/apt/sources.list.d/libreoffice.list
E: The list of sources could not be read.

How do i get rid of this?

---

### Post by hansdown on 2010-11-13
Hi hunter99507.

Your apt/sources.list needs to be updated.

Is this an upgrade?

I can't find a recent how-to, so someone should be able to help us both out here.

---

### Post by hunter99507 on 2010-11-13
I think in order to fix my issue i need to remove these. How do i go about removing these?

watts@Ubuntu:~$ sudo apt-get update
E: Type '‘deb' is not known on line 59 in source list /etc/apt/sources.list
E: Type '‘deb' is not known on line 1 in source list /etc/apt/sources.list.d/libreoffice.list
E: The list of sources could not be read.

---

### Post by hansdown on 2010-11-13
Can we take a look at your sources list?

If you are running 10.04, click

system> administration> software sources.

If you are running 10.10, you need to 

right click the applications, places, system menu and click edit menus.

In the left side column, scroll down to administration, and click on it.

In the right side column, see that the software sources is checked.

Now you can close that window, and click

system> administration> software sources> other software.

Could you post a screenshot?

---

### Post by oldos2er on 2010-11-13
> **hunter99507 said:**
> I think in order to fix my issue i need to remove these. How do i go about removing these?

watts@Ubuntu:~$ sudo apt-get update
E: Type '‘deb' is not known on line 59 in source list /etc/apt/sources.list
E: Type '‘deb' is not known on line 1 in source list /etc/apt/sources.list.d/libreoffice.list
E: The list of sources could not be read.

It looks like there's a spurious ` that shouldn't be there. Open a terminal (Applications, Accessories, Terminal) and run ```
gksu gedit /etc/apt/sources.list
``` to correct it.

---

### Post by hunter99507 on 2010-11-13
That fixed the issue oldos2er, thank you

---

