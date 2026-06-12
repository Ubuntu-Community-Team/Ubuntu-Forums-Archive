---
title: "Removing Virtualbox"
date: 2009-02-26
forum: New to Ubuntu
---

### Post by L Campbell on 2009-02-26
I'm using a PC with 8.04.

I recently installed Virtualbox using this:-

sudo apt-get install virtualbox-ose-guest-modules-server

Now I'm having a problem with my computer and want to remove this.  Would this be the correct code to use to remove it?

sudo apt-get remove virtualbox-ose-guest-modules-server

TIA.

---

### Post by NikoC on 2009-02-26
That ought to do the trick!
If you add --purge after 'install' configuration files will be removed as well!

---

### Post by tarps87 on 2009-02-26
> **NikoC said:**
> That ought to do the trick!
If you add --purge after 'install' configuration files will be removed as well!

or

```
sudo apt-get purge virtualbox-ose-guest-modules-server
```
:)

---

### Post by L Campbell on 2009-02-26
> **tarps87 said:**
> or

```
sudo apt-get purge virtualbox-ose-guest-modules-server
```
:)

Thanks, that seemed to do the trick.

Kind regards.

---

