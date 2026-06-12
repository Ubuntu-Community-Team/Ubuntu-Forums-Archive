---
title: "Dual booting ubuntu and vista with ubuntu installed first"
date: 2010-09-06
forum: New to Ubuntu
---

### Post by tacotime on 2010-09-06
Hey guys, 

As most of you know school started back not to long ago, and now I must go from my care free days of booting nothing but linux, to dual booting stinky old windows again.

My question is, how?

I mean I know how to partition my disk and install windows, but my concern is with GRUB, as most of you know when you install windows it wipes the mbr and puts the windows boot loader on it, so from there one couldn't boot in to ubuntu, unless you use EasyBCD which I don't want to.

I want to re-install grub, so if I boot from a Ubuntu Live CD and reinstall it would it detect my windows partition and automatically add it to the boot loader? Or would I have to edit GRUB?

---

### Post by Gone fishing on 2010-09-06
I think you will find what you need here:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by androiddev on 2010-09-06
Reinstall Windows on a seperate partition and then reinstall GRUB via the Live CD.

---

### Post by Mark Phelps on 2010-09-07
> **tacotime said:**
> I mean I know how to partition my disk and install windows, but my concern is with GRUB, as most of you know when you install windows it wipes the mbr and puts the windows boot loader on it 
No it does NOT replace GRUB with the Windows boot loader; instead; it overwrites the MBR.

[/QUOTE]I want to re-install grub, so if I boot from a Ubuntu Live CD and reinstall it would it detect my windows partition and automatically add it to the boot loader? Or would I have to edit GRUB?[/QUOTE]
Look in the link below about reinstalling GRUB from a LiveCD:

[https://help.ubuntu.com/community/Grub2]("https://help.ubuntu.com/community/Grub2")

---

### Post by migs73 on 2010-09-07
If you have plenty of RAM to support both your OS's try VirtualBox. Get the one from Oracle site not the one in the repos though. The Repo (OSE) version does not support USB.

---

