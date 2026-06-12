---
title: "Remove Purge does not remove my files"
date: 2009-04-02
forum: New to Ubuntu
---

### Post by gackt on 2009-04-02
Hi all, 

I'm trying to remove gambas2 (it failed to launch after i update it), when i enter remove with purge it only remove single file with small size. How do i clean remove this gambas2 (i'm trying to reinstall it).
Thanks

---

### Post by |Mitch| on 2009-04-02
you can remove it from Synaptic Package Manager

---

### Post by gackt on 2009-04-02
> **|Mitch| said:**
> you can remove it from Synaptic Package Manager

I did but it did not remove all the file ( i marked the remove all ).

---

### Post by Kevbert on 2009-04-02
Have you tried
```
sudo apt-get remove --purge gambas2
sudo apt-get autoremove
sudo apt-get clean
sudo apt-get autoclean
``` ?

---

### Post by gackt on 2009-04-02
> **Kevbert said:**
> Have you tried
```
sudo apt-get remove --purge gambas2
sudo apt-get autoremove
sudo apt-get clean
sudo apt-get autoclean
``` ?

sudo apt-get autoremove will remove 1286mb =  waks...i'm affraid that others software might error if i do this...gambas is only 22mb as i recall. Thanks

---

### Post by Kevbert on 2009-04-03
If autoremove gets rid of all that information then it looks like you may have found a new bug. It may be worth raising a bug report on [[COLOR="Red"]Launchpad[/COLOR]]("https://launchpad.net/") for this. Please include as much info as possible.  It may be that you have some other redundant software and that is one reason why the remove amount is so high. A small amount of this may be due to the package gambas2. If you do decide to try this command you could always fall back to using
```
sudo apt-get install -f
```
to repair any damaged packages.

---

