---
title: "PC will not boot from CD"
date: 2009-10-29
forum: New to Ubuntu
---

### Post by IamJohnHayes on 2009-10-29
I currently have 9.4 installed on my computer and just downloaded 9.10 and would like to install but I am having this issue:

I need to dual boot this PC due to training for work,  It is currently Ubuntu only.  The new Ubuntu disk will boot from CD but my windows disc (XP pro SP2, and a legit copy at that) will not boot it goes stright to the grub.  Its almost like a twisted joke. 

Does anyone else have this problem,  is there anyway I can make the Grub boot from a CD first?  I already have it set in the BIOS to boot cd's first.
This XP CD boots fine on other PC's

---

### Post by phillw on 2009-10-29
Try a cd-cleaner, check the cables etc.

Can you read a cd okay once the machine has started ?

A bit extreme, but, disconnect the hard-disk - see if the cd boots then.

Regards,

Phill.

---

### Post by coolbrook on 2009-10-29
Grub shouldn't have priority over your BIOS boot sequence.  That's very unusual.

Just so we're clear...

You have 9.04 installed, but you want to overwrite that with a dual boot of XP and 9.10?

---

### Post by bumanie on 2009-10-29
Does your computer have sata drives? If so, xp won't natively recognise them. You need to either go into bios and disable a hard drive setting or go to the drive manufacturers site and see if they have floppy or cd-rom download to install sata drivers. The bios options I have used only had two options so it's not hard to work out what to choose, nor hard to remember how to change it back if needed. i can't remember the exact name of the setting that needs to be changed, but each mobo manufacturer would possibly name it something different anyway.

---

