---
title: "Reset Panel to initial default settings"
date: 2009-06-10
forum: New to Ubuntu
---

### Post by flyingsolo on 2009-06-10
I've reinstalled ubuntu on my laptop after a bit of a crash (long story) and installed 8.04 & upgraded to 8.10 (9.04 won't work with my video card).  After some fiddling with the panel, I'd like to reset it to the default install items/appearance.  Is there an easy way to do this?  (I could remove/reverse tweeks I've made but don't recall everything I did or just what the initial panel included so I'd like to just start fresh) 
Thanks.
(I'm referring to the top panel, btw.)

---

### Post by zvacet on 2009-06-11
You have to turn off gdm first with this command

```
sudo /etc/init.d/gdm stop
```
then type

```
rm -rf .gconf* .gnome* .nautilus*
```

```
sudo reboot
```

---

### Post by flyingsolo on 2009-06-11
Thanks, that did the trick.  I can now choose just a couple of the panel applets I really want.

---

### Post by 666f6f on 2010-04-02
> **zvacet said:**
> You have to turn off gdm first with this command

```
sudo /etc/init.d/gdm stop
```
then type

```
rm -rf .gconf* .gnome* .nautilus*
```

```
sudo reboot
```

hmm.. that seems a bit too much..

---

