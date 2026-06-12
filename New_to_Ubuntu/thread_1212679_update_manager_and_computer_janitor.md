---
title: "update manager and computer janitor"
date: 2009-07-14
forum: New to Ubuntu
---

### Post by 289531.EXE on 2009-07-14
is it safe to download everything in the update manager and how do i know weather to delete  or keep  things that come up in the computer janitor?

---

### Post by Finalfantasykid on 2009-07-14
I've always just downloaded everything in update manager with no problems.  

And I don't like computer janitor much, it tends to make some programs not work anymore.

To clean up I prefer to do...

```
sudo apt-get autoclean
```

```
sudo apt-get clean
```

```
sudo apt-get autoremove
```

You can also go to synaptic package manager, and delete all residual packages(usually the last option on the left side.

---

### Post by steveneddy on 2009-07-14
> **Finalfantasykid said:**
> I've always just downloaded everything in update manager with no problems.  

And I don't like computer janitor much, it tends to make some programs not work anymore.

To clean up I prefer to do...

```
sudo apt-get autoclean
``````
sudo apt-get clean
``````
sudo apt-get autoremove
```You can also go to synaptic package manager, and delete all residual packages(usually the last option on the left side.

Agree here, autoclean and autoremove are better ways of keeping your Ubuntu PC tidy.

This is what all the cool kids do.

---

### Post by 289531.EXE on 2009-07-14
thanks alot guys!

---

