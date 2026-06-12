---
title: "Update Manager problems"
date: 2009-01-17
forum: New to Ubuntu
---

### Post by CBJFanGirl on 2009-01-17
OK, I've gone and done something sorta stupid and now I need some help.

One morning I was in the process of doing updates for Intrepid via the update manager while I was a cafe waiting to go for time to clock into work (across the street).  The updates were taking a while, but it was nearly done.  I thought I may have time on my battery power to unplug, run across the street and plug it in at work.  But unfortunately I did not.  The battery died while in still installing updates.

Now, when I go to update manager, it gives me two warnings:
[INDENT]E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.[/INDENT]

I tried to do the first thing in the terminal, but it tells me that it requires "superuser privilege."  What is that and how do I get it? (mind you, I have nearly zero previous Linux experience, so please dumb it down as much as possible :)).

---

### Post by Sef on 2009-01-17
> [INDENT]E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.[/INDENT]I tried to do the first thing in the terminal, but it tells me that it requires "superuser privilege." What is that and how do I get it? (mind you, I have nearly zero previous Linux experience, so please dumb it down as much as possible :smile:).Run sudo before dpkg:

```
sudo dpkg --configure -a
```

---

### Post by perlluver on 2009-01-17
> **CBJFanGirl said:**
> OK, I've gone and done something sorta stupid and now I need some help.

One morning I was in the process of doing updates for Intrepid via the update manager while I was a cafe waiting to go for time to clock into work (across the street).  The updates were taking a while, but it was nearly done.  I thought I may have time on my battery power to unplug, run across the street and plug it in at work.  But unfortunately I did not.  The battery died while in still installing updates.

Now, when I go to update manager, it gives me two warnings:
[INDENT]E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.[/INDENT]

I tried to do the first thing in the terminal, but it tells me that it requires "superuser privilege."  What is that and how do I get it? (mind you, I have nearly zero previous Linux experience, so please dumb it down as much as possible :)).

Open the terminal, Applications>Accessories>Terminal then run sudo dpkg --configure -a

---

### Post by CBJFanGirl on 2009-01-17
Oh! :P Thank you!!  Now I'm starting to learn what sudo is all about :)

---

