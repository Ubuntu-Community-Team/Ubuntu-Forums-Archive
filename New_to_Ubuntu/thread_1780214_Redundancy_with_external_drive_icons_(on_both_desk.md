---
title: "Redundancy with external drive icons (on both desktop and launcher)"
date: 2011-06-11
forum: New to Ubuntu
---

### Post by fillmont on 2011-06-11
So here's a minor issue that has been bugging me. I'm running Ubuntu 11.04 with Unity, and I use an external harddrive for all my media stuff. When it is mounted, I get an icon in two places - in the launcher and on the desktop. This seems to me to be redundant. Is there a way to change my settings so that the hard drive doesn't automatically appear on my desktop? I'm perfectly ok with it only appearing in the launcher.

---

### Post by VOT Productions on 2011-06-11
It's normal.

---

### Post by Morbius1 on 2011-06-11
Open a Terminal and type:
```
gconf-editor
```Then go to:
> /apps/nautilus/desktop/volumes_visibleAn uncheck it.

I'm assuming this still works with Unity.

---

### Post by Paqman on 2011-06-11
> **Morbius1 said:**
> 
I'm assuming this still works with Unity.

Sure does.

---

### Post by coffeecat on 2011-06-11
> **Morbius1 said:**
> I'm assuming this still works with Unity.

Yup! :)

---

### Post by fillmont on 2011-06-11
> **Morbius1 said:**
> Open a Terminal and type:
```
gconf-editor
```Then go to:
An uncheck it.

I'm assuming this still works with Unity.

Thank you kindly! Works like a charm.

---

