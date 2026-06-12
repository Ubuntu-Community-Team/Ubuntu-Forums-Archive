---
title: "Virtual Machine w/o Hardware virtualization?"
date: 2011-01-25
forum: New to Ubuntu
---

### Post by Dwnshft on 2011-01-25
I'm wondering if there is a way to run a Virtual Machine with out having hardware virtualization? 
 
I have my OEM copy of 64bit Windows 7 that I neet to run in order to use certain peripherals (Iomega Sreenplay Director and Blackarmor Back up drive).
 
Does anyone know of how to do it or if they have another solution to not being able to mount my Screenplay? The blackarmor drive i've already established that its encrypted and has a launchable security app that is not linux friendly.

---

### Post by bodhi.zazen on 2011-01-25
Yes, it is called "dual booting".

By definition, a VM uses virtual hardware.

The closest thing you might get would be LXC or Openvz, but that technology does not support windows.

---

### Post by 1clue on 2011-01-25
+1.  You either need to dual boot or go buy an unencumbered Windows CD.

---

### Post by asmoore82 on 2011-01-25
I think the OP is asking about the need for the specific virtualization extensions in the hardware.

The answer is a wonderful NO!

VirtualBox provides it's own kernel module for psuedo-virtualization that works on any modern hardware
regardless of the hardware's support for true virtualization.
Obviously, performance isn't going to be as good as real hardware supported virutalization but it's still great.

Now as far as connecting devices to the virtualized OS, that's a whole other can of worms.

---

### Post by snowpine on 2011-01-25
It is true you can run VirtualBox on a computer that doesn't have hardware virtualization capabilities. However, I don't think you'll be able to get 64-bit running in that scenario; you'd need to purchase a 32-bit version of Windows.

The better solution is to dual-boot as has already been suggested by others.

---

### Post by 1clue on 2011-01-25
If you guys will re-read the original post, you'll see he wants to run his OEM Windows on a VM.  That does not work, because the VM is not emulating exactly that specific piece of hardware.

The OEM Windows CD will restrict itself to a handful of boxes.  We ran into that at work, where we bought a lot of 10 systems at one point, then years later had to get an installation CD.  It just so happened that even though the serial numbers on the boxes were consecutive, they spanned the manufacture lot number and so we needed 2 CDs instead of 1.

This OEM stuff, they're looking for specific computers to run on.  It has nothing to do with similar hardware, they're making sure that it only works directly on the hardware you bought from them, not on any other hardware that is technically identical.

---

### Post by bodhi.zazen on 2011-01-25
> **1clue said:**
> If you guys will re-read the original post, you'll see he wants to run his OEM Windows on a VM.  That does not work, because the VM is not emulating exactly that specific piece of hardware.

The OEM Windows CD will restrict itself to a handful of boxes.  We ran into that at work, where we bought a lot of 10 systems at one point, then years later had to get an installation CD.  It just so happened that even though the serial numbers on the boxes were consecutive, they spanned the manufacture lot number and so we needed 2 CDs instead of 1.

This OEM stuff, they're looking for specific computers to run on.  It has nothing to do with similar hardware, they're making sure that it only works directly on the hardware you bought from them, not on any other hardware that is technically identical.

Thank you for that information, but my guess would be that everyone who posted on this thread understood that.

---

