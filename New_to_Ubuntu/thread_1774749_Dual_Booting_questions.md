---
title: "Dual Booting questions"
date: 2011-06-03
forum: New to Ubuntu
---

### Post by gantww on 2011-06-03
Greetings,
I'm working with a machine that has to have windows on it in case of emergency, but can get by just fine with Kubuntu for the rest of the time. Because I don't want to fart about with a VM and already have windows installed and configured as I need it, I'd like to dual boot with Kubuntu. I booted using an ubuntu disk and used GParted to shrink my windows partition.

However, now when I try to install Kubuntu, it doesn't have a real easy option for installing Kubuntu in the remaining space. Given 500 gigs of space to install in, what kind of partitions would you create and what size?

---

### Post by mikewhatever on 2011-06-03
You need to create two partitions, root and swap.
- root - about 500GB - swap
- swap - about the size of RAM.

You probably already have a couple of primary partitions, so I'd recommend making the Ubuntu partitions logical.

---

### Post by gantww on 2011-06-03
Should I put /home in its own partition? Is there any merit to doing that?

---

### Post by Rex Bouwense on 2011-06-03
Many people do just that which enables them to re-install without screwing up their settings.  Since I would always recommend backing up all of your data anyway, it is sort of like six of one and half a dozen of the other.

---

### Post by gantww on 2011-06-03
Excellent. Thank you. Looks like I'm ready to rock on this thing.

---

