---
title: "Saving my data"
date: 2009-11-14
forum: New to Ubuntu
---

### Post by bj218 on 2009-11-14
I would like to set up Ubuntu 9.04 so that each time I upgrade I would not loose all the things that I have installed on 9.04. If this possible I would need to get a very detailed set of instructions on how to do it as I am not very computer literate. I don´t understand why this is not built in as part of the update process!!

---

### Post by BarfBag on 2009-11-14
Are you talking about a clean reinstall, or a dist-upgrade?

---

### Post by Old *ix Geek on 2009-11-14
It's very easy. The reason it's not built in as part of the update process is simple: Linux is about CHOICE.  It's up to YOU to decide what YOU want. :)

When you're doing a fresh install, you need to choose 'manual editing' (or whatever it's called!) at the point where you're presented with formatting/partitioning options.  If you don't manually select your own choices, but instead accept the default, I think you'll end up with the entire disk used as one partition (someone correct me if I'm wrong on that--I NEVER go that route).

Okay, once in the manual editing place, you need to decide how to split up your hard drive, which depends on its size and how you want to use it.  This is the scheme I always use:

/
/home
/data
swap

On / I install the OS; this is the smallest partition.  On /home, as you might expect!, go user accounts; this is a large partition.  I use /data for storing things like photos, videos, mail, and so on; this is the biggest partition.  I allocate a smallish amount of space for swap.

If you follow this basic idea, you'll never lose your data--as long as you're NOT storing it on the root partition.  You can safely do a fresh install later on, i.e., format the / partition and do a clean install, without affecting your other partitions.

Usual disclaimer: You're always safest having a current backup before upgrading...but we all have current backups anyway, right? :D

---

### Post by bj218 on 2009-11-16
> **BarfBag said:**
> Are you talking about a clean reinstall, or a dist-upgrade?

A clean install. My main concern is I do not want to lose the things that are in bill my home like Bookmarks my Pass Words Screensaver etc. So far
I have been unable to copy bill to a new partition that I made for this purpose.

---

