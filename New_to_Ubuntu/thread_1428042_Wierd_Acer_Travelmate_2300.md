---
title: "Wierd Acer Travelmate 2300"
date: 2010-03-12
forum: New to Ubuntu
---

### Post by Phil Hansen on 2010-03-12
My sister had the above laptop which was giving problems.
I have installed 9.04 onto a new box and everything works fine and she is very happy.
Easiest widowz to linux conversion ever.
I took over the old laptop to play with and the fun starts.
9.04 starts to boot and hangs
9.10 gets a bit further and then hangs
7.04 starts to boot and hangs
Puppy runs fine.
It is one of those OEM machines with a hidden install drive.
I want to clean the whole drive but cannot as I cannot get a "try ubuntu" running to use gparted to clean up the XP mess.
Any ideas!
Thanks

---

### Post by ikt on 2010-03-12
> **Phil Hansen said:**
> I took over the old laptop to play with and the fun starts.
9.04 starts to boot and hangs
9.10 gets a bit further and then hangs
7.04 starts to boot and hangs
Puppy runs fine.


You are trying to boot into a *livecd* and it is hanging?

Does it hang at the same part every time?

---

### Post by Phil Hansen on 2010-03-12
> **ikt said:**
> You are trying to boot into a *livecd* and it is hanging?

Does it hang at the same part every time?

All livecd's and all never hang in the same place.
As I said weird.
Maybe it is throwaway time - unless I can completely reformat the drive.
How without something like gparted?
[edit]
But then again booting from a live CD should have no influence on the hard drive.

---

### Post by ikt on 2010-03-13
> **Phil Hansen said:**
> 
But then again booting from a live CD should have no influence on the hard drive.

Indeed, if the live cd isn't booting sounds like a hardware incompatibility issue :(

---

### Post by RT236 on 2010-03-13
Just thinking here...  might want to be sure your main memory is OK.  I just went through this here with one my custom desktops I built up.  Passed mem tests OK, but one mem module was still bad, did not show bad during mem testing.  I had noticed mem test and System Monitor were only showing 512mb than 1gb mem.  System only hung on reboot and during install from live disk at reboot. ...did mem module swaps and then one at a time, isolated bad mem module.  All works OK now for 9.04 and 9.10.

I have no idea if this is of help to you, but was just thinking of this when I saw your problem.

---

