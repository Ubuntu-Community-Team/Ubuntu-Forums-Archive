---
title: "cannot add or remove ANY software"
date: 2010-12-04
forum: New to Ubuntu
---

### Post by noworldorder on 2010-12-04
Ununtu 10.04

I tried to install OpenbravoERP but it got hung up so I closed the installation.  Now I get this:

> The installation could have failed because of an error in the corresponding software package or it was cancelled in an unfriendly way. You have to repair this before you can install or remove any further software.

I am not able to remove Openbravo without getting this error.  Can't add any software...

Help please...

thx

---

### Post by wilee-nilee on 2010-12-04
Try these two commands separately in the terminal, also never shutdown a installation.
sudo dpkg --configure -a
sudo apt-get install -f

---

### Post by noworldorder on 2010-12-04
that worked!  thanks

so what should I have done if the installation process was hung up?

---

### Post by wilee-nilee on 2010-12-04
> **noworldorder said:**
> that worked!  thanks

so what should I have done if the installation process was hung up?

I missed the hung up part, and just posted the commands that are good for unlocking the system. I guess you did all that one can do. How were you installing that package?

---

### Post by noworldorder on 2010-12-04
> How were you installing that package?

Ubuntu Software Center

But with linux these problems are far and few between.

---

### Post by wilee-nilee on 2010-12-04
> **noworldorder said:**
> Ubuntu Software Center

But with linux these problems are far and few between.

Personally I would use synaptic it will show dependencies, that may be in a repo not open maybe. Glad it got back up a running though.

---

### Post by noworldorder on 2010-12-05
> Personally I would use synaptic 

I installed synaptic with Ubuntu Software Center but I cannot in applications.  Oh I such an absolute beginner....

---

### Post by Verbeck on 2010-12-05
> **noworldorder said:**
> I installed synaptic with Ubuntu Software  Center but I cannot in applications.  Oh I such an absolute  beginner....
its in system>administration>synaptic package manager

its installed by default

---

### Post by Penguin=) on 2010-12-05
Synaptic is already installed on your system =)

---

