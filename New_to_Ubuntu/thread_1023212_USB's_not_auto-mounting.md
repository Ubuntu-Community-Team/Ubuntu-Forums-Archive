---
title: "USB's not auto-mounting"
date: 2008-12-27
forum: New to Ubuntu
---

### Post by Hopalong on 2008-12-27
USB sticks don't always get mounted immediately and automatically. I had a lot of trouble over this (and if I can find the thread I added to. I'll mark it solved!) One crucial point is this: Ubuntu can't talk to memory sticks formatted with you know who's *exFAT* format. If yours won't mount, try going to a Windows installation, and format it in FAT.
  It got mine working.

---

### Post by atngplusultra on 2008-12-27
A simpler, perhaps non-windows way, would be to simply edit fstab and set the USB device lines such that they will mount? if I recall, this is what was necessary on my machine.

---

### Post by mkvnmtr on 2008-12-27
I have been working today to get my external hard drives and sticks working to pas between my Ubuntu and my mac os. I got it all figured out by the command line but the guy typing kept making typing errors. The terminal kept me straight. Luckily I made notes so I can do it again in less than 3 hours.

---

### Post by dwilson89 on 2008-12-28
> **mkvnmtr said:**
> I have been working today to get my external hard drives and sticks working to pas between my Ubuntu and my mac os. I got it all figured out by the command line but the guy typing kept making typing errors. The terminal kept me straight. Luckily I made notes so I can do it again in less than 3 hours.

What is  the command line.

---

