---
title: "Sony Vaio PCG-TR5AP"
date: 2010-05-29
forum: New to Ubuntu
---

### Post by CBR_Rob on 2010-05-29
I picked up a Sony Vaio that was no longer being used at work. When I try to load Ubuntu to it, I get the live cd booting screen then everything stops and I get a black screen. This system meets the minimum requirements (although I don't know how to find out if it is an x86 processor). I've attached a print screen of the system properties from Windows.

---

### Post by CBR_Rob on 2010-06-04
Figured out the problem it is not a x86 processor. Apparently the Pentium processors with i686 architecture is not supported by the kernel. Found that out by trying to install 9.10 that I was planning to upgrade from.

---

### Post by WanderingAlbatross on 2010-07-29
Hmmm...  I have the same laptop, and just installed 9.10 recently.  It does run, though I am working through various issues.  I don't think your problem is the kernal.  Mine has a Pentium as well.

---

### Post by brainstuff on 2010-11-04
Know it's an old post but did you solve it? I got mine working by hitting "e" to edit the Grub line, remove quiet splash and add forcexvesa

This puts it in crappy resolution, but I've only just started tinkering with it.

---

### Post by WanderingAlbatross on 2010-12-16
The modeset=i915 setting worked for me after hitting 'e'.

---

