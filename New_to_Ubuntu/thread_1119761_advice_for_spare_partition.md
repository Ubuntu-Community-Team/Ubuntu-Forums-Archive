---
title: "advice for spare partition"
date: 2009-04-08
forum: New to Ubuntu
---

### Post by nml on 2009-04-08
Currently have a duel boot Ubuntu 8.10 and XPpro set up on an old IBM T42 (1.7ghz pentium M with 1.5 gig Ram) that's currently got an 'unused' 12.5 gig partition (presently formatted with ext3)..

I recently had to reinstall XPpro due to my partitioning efforts.......finding the drivers wasn't to bad (I had them basically saved for rainy days such as these), but updating the blasted system with all the 'security' updates was a real pain.....I do not want to do that again anytime soon!!!

I want to have the freedom to play around with new distros, but I don't want to mess up my current usable Ubuntu/XPpro set up.....so before I go playing around with my unused partition, what's the best/safest way to use it with new installs/uninstalls?

I have Virtual box on my Ubuntu partition, but I'm not sure if my machine is sufficient to run in a Virtual Environment (I'm not really a big fan of using Parallels on my Mac...kind of limiting with some stuff but I keep it for one program I need to run)..

All suggestions/opinions appreciated on how and what to play with/experiment with, on my unused 12 gig ext3 partition...

TIA,

Mick

---

### Post by NESFreak on 2009-04-08
well if you're installing ONLY to that separate partition,than the only thing you could screw up would be grub. You could search the forums and/or wiki on how to restore/repair grub. Also please remember not to 'move' partitions in such a way that sda3 becomes for instance sda7. This includes especially the windows partition.

---

### Post by kiridude on 2009-04-08
I don't see why you would have any problems installing another os on your free partition. I currently run ubuntu, redhat, and xp and have no probs. I use redhat cuz of database work I do but wouldn't recommend it for home use. Try Fedora, I hear its really improved lately. For fun, why not have a look at puppylinux - its so small and really fast, in fact it runs in RAM. 

I must point out, though, that Ubuntu is really the superior OS right now, so it looks like you got it right from the beginning :-)

If you're using an external for things like movies, pics, music, etc, 12 gigs is more than enough for another os. I use about 4 gigs for Ubuntu.

---

### Post by nml on 2009-04-08
> Try Fedora, I hear its really improved lately. For fun, why not have a look at puppylinux - its so small and really fast, in fact it runs in RAM.

OK, lets say I want to try one of the above.....do I download, then burn the .iso, burn a CD, then boot and install.  Once it's installed (hopefully on the free partition) how do I go about fixing or adding to the Grub bootloader?  I assume it's adding something to the end of menu.lst.

Next question, if I decide to rid of that install, whats the easiest/safest way to delete it...

thanks,

Mick

---

### Post by CLomax on 2009-04-08
> **nml said:**
> OK, lets say I want to try one of the above.....do I download, then burn the .iso, burn a CD, then boot and install.

No need to burn anything to a CD, you can use this instead:
**Unetbootin**
[http://sourceforge.net/project/downloading.php?groupname=unetbootin&filename=unetbootin-linux-319&use_mirror=heanet](http://sourceforge.net/project/downloading.php?groupname=unetbootin&filename=unetbootin-linux-319&use_mirror=heanet)

It downloads the .iso image and installs it directly. No fumbling around with CDs.

**NB:** If you select the wrong partition you'll overwrite it. Be cautious with this.

:KS

---

### Post by NESFreak on 2009-04-08
grub: [https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

As far as removing the other os goes, just format it's partition. Be sure that if the other os installed its own bootloader, it might need files stored on the just deleted partition. Just reinstall grub from the ubuntu live cd.

I don't know what bootloader comes with your other bootloader, but you can alway manually install grub again from the livecd (again as explained in the link).

Learn how menu.lst works before installing a second distribution, since than you could just add ubuntu to it (or the other distribution if you choose to leave your already installed grub intact. Ubuntus menu.lst is stored in /boot/grub/menu.lst
If the other has its own menu.lst, you could just add the entries of the on not being loaded at boot to the one that does get loaded).

Btw if you feel like trying out a specific second OS try searching the forums for other peoples dualboot experiences.

---

