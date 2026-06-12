---
title: "Dual Boot lost XP in Grub2"
date: 2010-02-27
forum: New to Ubuntu
---

### Post by Brutus2006 on 2010-02-27
I hope someone can help me,

I have 2 hard disks one with Ubuntu the other XP. Recently I got a upgrade to new Kernal, after that my XP drive went missing cant access it thru Grub.

My Kernal is 2.6.31-20-generic-pae, Thats another question is why do I have pae my friends have legacy. 


Thanks in advance

---

### Post by Sef on 2010-02-27
>  My Kernal is 2.6.31-20-generic-pae, Thats another question is why do I  have pae my friends have legacy. 

If you have 4 gb ram on a 32-bit system, then you will need pae to be able to use all of the ram.

---

### Post by ercferret18 on 2010-02-27
type in "sudo update-grub"

---

### Post by garvinrick4 on 2010-02-28
Do you mean it just boots straight to Ubuntu with out showing a Grub?

---

### Post by -kg- on 2010-02-28
> **ercferret18 said:**
> type in "sudo update-grub"

In a terminal window, of course! :p

A bit confusing.  You should not have lost your XP selection under GRUB with a kernel upgrade.  You *did* have GRUB as your bootloader, right?  This wasn't a WUBI installation or anything?

Also, if GRUB is your bootloader, do you have any other Linux installations?  If another Linux installation "owns" GRUB in the MBR, you will have to update GRUB from *that* installation.

---

### Post by kansasnoob on 2010-02-28
My best guess is that you've built up a very long list of kernels and Windows is simply "pushed" off the bottom of the list. If that's correct then just keep on the down arrow and it should show up.

Regardless it would eliminate a lot of guess work to see the output of the Boot Info Script:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

