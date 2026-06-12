---
title: "Power Manager not responding on boot"
date: 2010-05-02
forum: New to Ubuntu
---

### Post by Ahunt on 2010-05-02
I just installed Lucid on my 1.8 Ghz AMD CPU desktop and also on an Intel desktop too. Both installations went fine, but the AMD PC is suffering from an odd boot-up problem. Boot takes 3-4 minutes and results in a "Power Manager is not responding" error half way though the boot.

Any ideas how to fix this? The other PC, installed from the same CD is working fine.

---

### Post by Ahunt on 2010-05-03
Well this looks like a bad time to post questions - everyone seems to be hopping trying to solve Lucid issues.

Lacking a response here and not being able to fix the problem, I decided to reformat and do a reinstall from the CD again in the hopes that it would fix the error, but it didn't. The exact same error was duplicated.

I tried doing an update and the Update Manager downloaded two lib files. After that the problem seems to have resolved itself. Boot time is now about 60 seconds and it doesn't hang up on the power manager error. 

I would suggest anyone else who has this error try the update manager and see if that helps.

---

### Post by mynameisnick on 2010-05-05
That's humorous in a way. I didn't have the problem until I ran update manager.

---

### Post by joham34 on 2010-05-07
I had the same problem although after a few secs the boot continued normally. From the Ubuntu Software centre, I uninstalled Gnome Power Management and got rid of the problem. It is not a critical feature of gnome anyway

---

### Post by DarinB on 2010-06-13
how to uninstall gnome power manager

---

### Post by syn4k on 2010-07-24
System -> Administration -> Synaptic Package Manager -> search for gnome-power-manager. Uninstalling this also removes ubuntu-desktop. I don't know how joham34's computer is still working without this.

---

### Post by drewster1829 on 2010-08-03
syn4k, I read somewhere that ubuntu-desktop is just a package that has every default Ubuntu package (in the desktop install) as a dependency, and isn't actually required.  

That way, if you've fiddled with your system and removed some default packages, installing ubuntu-desktop restores them. I used to think it was important, too, but I guess not. :p

---

### Post by joham34 on 2010-08-08
Well, gnome power management installed itself again somehow in my PC, this time not only appearing on boot the message "power manager not responding" etc but sometimes my pc wouldnt boot at all and had to reboot . I again uninstalled it from the synaptic and so far everything works fine (at least on my pc) I have Ubuntu 10.04 (Lucid Lynx, upgraded from Karmic Coala)

---

