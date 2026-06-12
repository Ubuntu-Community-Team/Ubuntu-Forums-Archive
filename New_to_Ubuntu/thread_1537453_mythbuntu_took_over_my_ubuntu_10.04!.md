---
title: "mythbuntu took over my ubuntu 10.04!"
date: 2010-07-23
forum: New to Ubuntu
---

### Post by lonestarone on 2010-07-23
Hi-All,
  I did a stupid thing last week!  I installed mythbuntu from my repositories, (synaptic)  Now-I'm locked out of ubuntu 10.04??
  I'd like to just reinstall from my CD/ISO...I can't figure out cmds needed to recover my gnome desktop..
I'm concerned how to proceed.  From my CD - I can see via gparted the two HDs - one for windows and one for ubuntu.
  Do I simply delete/clear the ubuntu partition on its HD?  Will grub be reinstalled, since that controls the normal boots?
  I need to be totally clear on this procedure before I make things worse...I've always upgraded my ubuntu distros...never reinstalled.
Is it as simple as deleting the chosen partition and clicking on the install icon on the desktop from the live CD?   I hope so???
Thanks for help/suggestions.
John in Dallas.

---

### Post by matrixblue on 2010-07-23
Use a Live CD and backup your home directory to an external storage drive. Then install Ubuntu on the same partition.

A recommended practice is to create a partition and set the mount point to /. Make this partition 10 -15 GB. Then create another partition for /home. This way if something happens you can re-install Ubuntu without losing your files.

---

### Post by k3lt01 on 2010-07-23
If you installed it through the Repositories you will be able to select either at the GDM (Gnome Display Manager). I think what you have done is make Mythbuntu the default and that should be able to be easily changed without having to do a re-install, that way you can keep both.

---

### Post by lonestarone on 2010-07-23
Hi--k3lt01 and matrixblue,
  Appreciate your replies ...  Yes, I'd like to learn how to recover my gnome 10.04 since I can get into a cmd prompt using ctl+alt 1 or2..  How do I activate the GDM??
  Upon boot up, after login completes,  I get a black screen across the top a line with a 24hr. clock....cursor but no actions...ctrl alt 1 or2 gets me to cmd prompts...There I'm lost...
  Thanks for help.
  John in Dallas.

---

### Post by k3lt01 on 2010-07-23
The GDM is the Log in Screen, If you don;t already use it, it is optional so you might not be, you will have to enable it. I don't know the layout of Mythbuntu so I probably wont be accurate explaining this but it will give you something to look for.

The turn off button may have an option of "Guest Session" you could go there and it will come up with a log in screen of some sort (again I don;t now what Mythbuntu uses so be careful more reading may be required before you do this). There will be various options, you will need to look around, and you should be able to choose Mythbuntu or Ubuntu (it may even be Gnome or whatever Mythbuntu uses).

There is a way to hard set this but because my knowledge of the Mythbuntu graphical interface is limited I don't know how in it. Once you have Gnome up and running I can help more easily.

EDIT: Can you post screenshots of your System menu, if you can find one?

---

### Post by lonestarone on 2010-07-23
Hi -- k3lt01,
  That's the problem, I can't get into gnome desktop..myth has locked me out.
  Can I achieve GDM procedures from the live CD?  I assume it has to be installed first?  I found this during research?? Is this what your referring? 
Configuration
Configuration is done either by running gdmsetup or by editting the /etc/X11/gdm/gdm.conf (usually, could also be /etc/gdm/gdm.conf) file. The graphical tool does not support all the options possible so editting the configuration file is sometimes necessary. 
Options
gdm and thus also gdm-binary accept the following options:

-nodaemon
    Do not fork into the background 
--no-console
    No console (local) servers to be run 
--preserve-ld-vars
    Preserve LD_* variables 
--version
    Print the GDM version 
--help
    Print simple description of accepted options

gdmsetup accepts all standard GNOME options.

---

### Post by k3lt01 on 2010-07-23
Mythbuntu will have its own login manager, you need to find it and make it so you have to log in manually each time. Gnome has GDM, KDE has KDM I don't know what Mythbuntu has. MY advice is that you go to the Mythbuntu site and see what they say their login manager is and how to enable it.

---

### Post by lonestarone on 2010-07-24
Good Morning - k3lt01,
   YEAH, YEAH - SUCCESS!!!
Thanks k3 for leading me in the right direction...GDM...That solved my mess with mythtv!!!
   Sudo echo "usr/sbin/gdm"  That was the format that gave me the options of booting into gnome?? The rest of the format is >> /etc/x11/default-display-manager.
   Sure glad I asked on this forum...You guys ROCK!!!
My 10.04 is working great, updated OK, after I uninstalled everything """mythbuntu"""...It really messed up everything...My nvidia settings were broken - had HUGE icons and text...but a restart fixed that!??
  I now know how to fix things I break - instead of reinstalling...
Thanks for your help..
John in Dallas.

---

### Post by k3lt01 on 2010-07-24
That's very good news John :popcorn: Glad to have been of some very limited assistance. Have an excellent weekend.

---

