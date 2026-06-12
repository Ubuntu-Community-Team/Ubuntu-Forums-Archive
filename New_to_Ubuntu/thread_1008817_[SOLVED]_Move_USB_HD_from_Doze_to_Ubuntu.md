---
title: "[SOLVED] Move USB HD from Doze to Ubuntu"
date: 2008-12-11
forum: New to Ubuntu
---

### Post by Kellemora on 2008-12-11
Hi Gang

Two things, I have a 250 gig USB HD connected to a Doze XP machine and I want to move it to one of my Ubuntu machines.

Problem One, it won't let me unmount it from the Doze machine, says try again later.  Been doing that for two days now.

Problem Two, it's formatted NTFS, do I have to install (what) to use it directly with Ubuntu connected to this machine.  It works fine storing Ubuntu generated documents connected to the DOZE machine through the LAN to shared folders within.

I've heard if I just unplug it, it won't work.  The plug has been knocked out on occasion and plugged back in, but to the same machine.  I may try moving it to a different USB port to see if it will let me uninstall.  Or I could just switch it off, maybe that too will work, I don't know.  Haven't tried after reading the warnings here before.

Thanks

TTUL
Gary

---

### Post by aheckler on 2008-12-11
NTFS will work fine w/ Ubuntu, but you should probably find some way to disconnect it safely. My best guess would just to shut Windows down, unplug it, and see what happens.

---

### Post by Kellemora on 2008-12-12
Hi Heckler

I moved it to a different USB port, it autoloaded and then let me unmount it to disconnect it.

Don't I need a program like ntfs -3g or something like that before I connect it to my Ubuntu box?????

TTUL
Gary

---

### Post by Duck2006 on 2008-12-12
> **Kellemora said:**
> Hi Heckler

I moved it to a different USB port, it autoloaded and then let me unmount it to disconnect it.

Don't I need a program like ntfs -3g or something like that before I connect it to my Ubuntu box?????

TTUL
Gary

If ntfs-3g drivers are not loaded you can load it from your Synaptic Package Manager

---

### Post by az on 2008-12-12
> **Kellemora said:**
> 
Don't I need a program like ntfs -3g or something like that before I connect it to my Ubuntu box?????

TTUL
Gary

It's installed by default.  You have it already.  Just plug it in and watch the drive contents appear on your screen.

---

