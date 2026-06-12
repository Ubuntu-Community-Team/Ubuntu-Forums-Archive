---
title: "A few errors in Jaunty..."
date: 2009-06-10
forum: New to Ubuntu
---

### Post by melrokz on 2009-06-10
1. How to install a new DVDROM driver for 8.10? My DVD, when ejected, comes out and immediately goes in! How to solve this?

2. Sometimes, when I click 'computer' in Nautilus, an error pops up saying "Nautilus cannot handle computer locations" Plz advice.

---

### Post by 4Orbs on 2009-06-10
1. When I was using Intrepid the cd eject/retract race was fixed with one of the updates. Don't remember which update, maybe the big Python transition.

2. Nautilus occasionally becomes rebellious.

---

### Post by melrokz on 2009-06-11
Anyone out there knows about the specific update to fix the DVDROM driver?
The nautilus problem too... I've installed nautilus-actions recently, could it be bcoz of that?

---

### Post by melrokz on 2009-06-12
1. How to install a new DVDROM driver for 8.10? My DVD, when ejected, comes out and immediately goes in! How to solve this?

2. Sometimes, when I click 'computer' in Nautilus, an error pops up saying "Nautilus cannot handle computer locations" Plz advice.

---

### Post by melrokz on 2009-06-12
1. How to install a new DVDROM driver for 8.10? My DVD, when ejected, comes out and immediately goes in! How to solve this?

2. Sometimes, when I click 'computer' in Nautilus, an error pops up saying "Nautilus cannot handle computer locations" Plz advice.

---

### Post by s.fox on 2009-06-12
Hi,

1-  I did a little reading through some old threads and found [this]("http://ubuntuforums.org/showthread.php?p=5005773#post5005773") one.  People have posted all the way upto May this year describing your problem. Unfortunately nobody there seems to have found a solution :(


2-  If you open terminal and type this command,  what happens?:
```
eject
```Does your cd tray stay open?

If so use this command to close it:

```
eject -t 
```

My post concerning #2 isn't a permanent solution.  Its just something that may work if you need to do something right now.   Hopefully others will have a better idea and post soon.

-Ash R

---

### Post by 3rdalbum on 2009-06-12
Run Update Manager (System > Administration > Update Manager) and apply all the updates. I think it was a HAL update that fixed the problem, but you should apply all updates - that way you'll get all the bug fixes and security patches from the last 8 months, including a new point release of Gnome that might fix your second problem, and a number of fixes for problems that you haven't noticed yet.

---

### Post by 3rdalbum on 2009-06-12
A moderator will probably merge these threads. I posted in the other one. You need to go System > Administration > Update Manager, click Check, and then apply all the updates. This will definitely fix the first problem, definitely fix some problems that you haven't encountered, and might possibly fix the second problem.

---

### Post by frodon on 2009-06-12
Duplicate threads merged.

---

