---
title: "Laptop will not boot - beginner needs help please"
date: 2009-11-09
forum: New to Ubuntu
---

### Post by davidrc on 2009-11-09
Hi, I downloaded xubuntu 8.1 some time ago but have done little with it apart from sometimes running the live cd. Yesterday decided to instal it on my HP6720s laptop alongside Vista. Worked ok with a choice of booting into Xubuntu or Vista. There were 2 options for Vista, first one was ok but when I later tried it again i selected the second vista line and it booted to the HP recovery screen (there is a factory set recovery partition) now I can't get it to do anything other than go to this recovery screen. If I turn it off and then restart it goes straight to the recovery screen without showing a boot menu.
I don't want to run the recovery if I can avoid it - how do I get to the boot menu?
Any suggestions please.

---

### Post by MelDJ on 2009-11-09
try booting through a ubuntu live cd. then open gparted. right click the hp recovery partition and then press manage flags and uncheck everything then reboot. dont forget to press apply before exiting gparted

---

### Post by davidrc on 2009-11-09
Thanks but it will not now boot from the cd, still goes straight to HP recovery.

---

### Post by MelDJ on 2009-11-09
did you configure your BIOS to boot from cd?

---

### Post by davidrc on 2009-11-09
Yes, BIOS is set to boot from CD.
Before I installed xubuntu on the hd I did initially have a problem getting the live cd to run, I had to use option 3 on the cd for help.

---

### Post by MelDJ on 2009-11-09
strange. maybe there is a problem with your laptop

---

### Post by wyliecoyoteuk on 2009-11-09
Sounds like it is "remembering" that you were in the recovery mode. Can you exit that modegracefully? (i.e. without powering off).
If not,try switching off and removing the battery for a while.

---

### Post by sadaruwan12 on 2009-11-09
Remove the battery and also pull the power jack also after a minute put the battery and the power cord in and try to boot from the CD againe.

---

### Post by davidrc on 2009-11-09
Thanks for the suggestions. 
Have now tried removing battery and power cord but makes no difference still boots to the recovery screen whether or not the cd is in the drive.
There is a cancel option on the recovery but this just causes the machine to shut down and immediately restart back to the recovery screen, the only way I can turn it off is to use the power button as it is about to restart.
Looks as though I may have to go for the recovery option which will presumably put machine back to its factory state.

---

### Post by anewguy on 2009-11-09
I suppose it's possible that the recovery initially sets the mbr so that it will boot to recovery in case the power fails, etc..  I think I would double-check the BIOS to be sure the boot from CD option didn't get reset by the recovery option, and that the CD is the first device in the boot list, then try booting a livecd again.  If you can get the livecd to boot, you may still need to run grub to restore the mbr if it has changed.

Dave :)

---

### Post by davidrc on 2009-11-09
It gets worse!
Double checked that BIOS set to boot from cd first.
Still would not boot from livecd and went to recovery.
Decided to run recovery which seemed to be ok and reported successful recovery "Click finish to restart computer" - did this - straight back to recovery again, I seem to be stuck in a loop!
Don't know how to access MBR or what to alter if I did get there.
Perhaps this is not now a Ubuntu issue and I need to look for  HP recovery forum.
Thanks for trying to help.

---

### Post by davidrc on 2009-11-09
Hi MelDJ, 
managed to get it to boot from a different Ubuntu live cd and followed your suggestion to use gparted/manage flags. It worked, many thanks.

---

### Post by LewRockwell on 2009-11-09
> **davidrc said:**
> Hi MelDJ, 
managed to get it to boot from a different Ubuntu live cd and followed your suggestion to use gparted/manage flags. It worked, many thanks.

faulty Ubuntu disk then?

.

---

