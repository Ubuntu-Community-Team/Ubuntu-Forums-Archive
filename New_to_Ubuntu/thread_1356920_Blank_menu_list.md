---
title: "Blank menu list?"
date: 2009-12-16
forum: New to Ubuntu
---

### Post by jrenaldy on 2009-12-16
I installed Ubnuntu recently as a secondary OS to Vista.  For the life of me I can't figure out how to make Vista my default OS.  I've tried to edit the menu list but there doesn't seem to be anything to edit.  I just see a blank text edit screen.  I think I know what to do once I have something there but right now nothing.  Any suggestions?

---

### Post by howefield on 2009-12-16
Is it grub2 ? If so, see this thread that drs305 was kind enough to write.

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

You could also install startupmanager with Synaptic Package Manager if you prefer a gui.

---

### Post by sisco311 on 2009-12-16
> **jrenaldy said:**
> I installed Ubnuntu recently as a secondary OS to Vista.  For the life of me I can't figure out how to make Vista my default OS.  I've tried to edit the menu list but there doesn't seem to be anything to edit.  I just see a blank text edit screen.  I think I know what to do once I have something there but right now nothing.  Any suggestions?

[thread=1302743]Grub 2 - 5 Common Tasks[/thread] ~ *2 Menu Default Entry*

[uhelp]community/Grub2[/uhelp]
[thread=1195275]The Grub 2 Guide[/thread]
[thread=1287602]Grub 2 Title Tweaks[/thread]

---

### Post by jrenaldy on 2009-12-16
Thanks!  I got it to work through the startup package manager.  I really appreciate your help!  

Any suggestions on how to delete stuff through that GUI?  For some reason I have an "old" version of the OS in the menu: Ubuntu, Linux 2.6.31-**15**-generic-pae with a recovery mode as well.  Currently I've been using Ubuntu, Linux 2.6.31-**16**-generic-pae.

---

### Post by howefield on 2009-12-16
As explained in the above mentioned link, startupmanager is not fully functional with grub2, but have a look in the advanced tab for an option "Limit the number of kernels in the boot menu"

The old kernels can be removed with Synaptic Package Manger, but unless they are causing you grief, might be best to leave them.

---

### Post by jrenaldy on 2009-12-16
Thanks again!  I think I'll just leave well enough alone!

---

### Post by jrenaldy on 2010-01-12
Thanks again for your help!

---

### Post by jrenaldy on 2010-01-12
Does anyone know the easiest way to remove old Kernels? Right now after a few Ubuntu updates, I have two old kernels that seem to be effecting my OS boot order.  Any suggestions on how to get rid of them?

---

### Post by sisco311 on 2010-01-12
> **jrenaldy said:**
> Does anyone know the easiest way to remove old Kernels? Right now after a few Ubuntu updates, I have two old kernels that seem to be effecting my OS boot order.  Any suggestions on how to get rid of them?

Use Synaptic package manager to uninstall the the old kernels:
[thread=1195275]The Grub 2 Guide[/thread] *-> 7. Removing Entries from Grub 2*

---

