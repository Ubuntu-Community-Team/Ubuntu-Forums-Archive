---
title: "Attempted to use Synaptic, mangled something"
date: 2010-11-29
forum: New to Ubuntu
---

### Post by zipteye on 2010-11-29
I had multiple entries in the boot menu 2.6.35-23-generic, and 2.6.35-22.
Well, i wanted to get rid of the other entries so I tried to use Synaptic to remove all the 2.6.35-22 stuff I could find.

System still works but it boot s slower and something flashes across the screen ... I cant read the first thing fast enough but the second entry is "Too many connections".

Thats me... poke at stuff until it either works or until It's reduced to an irreparable state.  :D

---

### Post by bioterror on 2010-11-29
> **zipteye said:**
> I had multiple entries in the boot menu 2.6.35-23-generic, and 2.6.35-22.
Well, i wanted to get rid of the other entries so I tried to use Synaptic to remove all the 2.6.35-22 stuff I could find.

System still works but it boot s slower and something flashes across the screen ... I cant read the first thing fast enough but the second entry is "Too many connections".

Thats me... poke at stuff until it either works or until It's reduced to an irreparable state.  :D

You should keep few kernels in GRUB list for the case of bad day.
Usually you can remove the kernel with a command "sudo apt-get remove linux-image-2.6.35-22-generic".

but removing that kernel image should not affect at all in boot times.

What else did you remove?

---

### Post by amjjawad on 2010-11-29
Hope [this]("http://ubuntuforums.org/showthread.php?t=1586923") will help!

---

