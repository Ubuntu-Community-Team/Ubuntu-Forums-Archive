---
title: "Grub and multiple operating systems"
date: 2009-11-29
forum: New to Ubuntu
---

### Post by Space-Wolf on 2009-11-29
If I create a third partition and install another Linux based OS like Fedora, will the grub that came with Ubuntu just add it to the list, or will it be more complicated?

---

### Post by k3nz13 on 2009-11-29
Especially if you're installing another OS that includes GRUB itself, it will just add the new entry to the bootloader.

---

### Post by ranch hand on 2009-11-29
If you install Fedora it will take over the boot duties.  It should pick up everything on your drive.

Be very careful installing Fedora, it has a tendency to over write partitions that are other Linux OS' (does not play nice with others).  Just make sure you check the status of every partition when installing and you should be fine.

---

### Post by pi.boy.travis on 2009-11-29
You may be better off choosing not to install GRUB in the Fedora installer, and then adding Fedora to Ubuntu's GRUb with the update-grub command. . .

---

### Post by coffeecat on 2009-11-29
The bad news is that Fedora doesn't bother to detect other Linux distros for the grub menu. It will only give you a Windows/Fedora dual-boot menu - and a hidden one at that to make booting into Windows difficult for newbies! It will ignore anything else on the HD. Believe me, I installed F12 only the other day.

The good news is that the latest Fedora 12 still uses grub 1. I found this out the hard way by trying to edit the grub menu as though it was grub 2 - and then I noticed menu.lst. :rolleyes: Silly me! So, if you are familiar with grub 1, editing menu.lst is all you need do. But as you're posting in the Beginner's Forum, that may be complicated for you.

If you want to try other distros and avoid configuring grub, I suggest you install Ubuntu, Suse or Mandriva **after** Fedora. Those three are more sociable than Fedora.

---

### Post by Space-Wolf on 2009-11-29
Thanks for the responses all.  After looking into it a bit, I might just hold off on Fedora or any other distros until I get more familiar with Ubuntu, it seems like a good place to start.  This is a little offtopic, but if I want to download music and get limewire, will it slowdown Ubuntu at all?

---

### Post by pi.boy.travis on 2009-11-29
> **Space-Wolf said:**
> Thanks for the responses all.  After looking into it a bit, I might just hold off on Fedora or any other distros until I get more familiar with Ubuntu, it seems like a good place to start.  This is a little offtopic, but if I want to download music and get limewire, will it slowdown Ubuntu at all?

Ubuntu is naturally more resistant to malicious software, so you should be ok.  I have been using limewire for years with no issues.  The only penalty is disk space. . .

---

### Post by Space-Wolf on 2009-11-29
Awesome, thanks guys.

---

