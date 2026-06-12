---
title: "fglrx nightmare"
date: 2010-10-11
forum: New to Ubuntu
---

### Post by costalot on 2010-10-11
i have an ATi X1650 pro grafics card and i can't load any drivers for it at all, im told i need FGLRX, but cant load this file no matter how hard i try, iv looked in hardware drivers and it tell me there are "no proprietary drivers are in use on this system". i have trid in vain to follow the ati install instructions for the catalyst but it easer to just reinstall windows and be done with it. i had 3d grafics on Friday and it was great, then i woke did an update and now nothing. i followed every instruction i could find and found that all the instuction dont work for me. someone please help im ready to put my foot theogh this machine

---

### Post by Mark Phelps on 2010-10-12
There are no fglrx drivers that will work with your card and Ubuntu versions newer than 8.10. AMD (formerly, ATI) dropped fglrx support for your card over a year ago.  The only drivers that will work now are the open-source drivers and those are installed by default during initial setup.

Don't download any fglrx drivers or try to force their installation.  They will not work, they will trash your display, and you will then have to go to a lot of trouble to boot into a console -- only to have to remove them and replace them with the same drivers you already have now.

---

### Post by fatality_uk on 2010-10-12
The work around for my update to Meerkat and having an ATI driver issue was to delete my xorg.conf file, restart my machine and when either prompted or by selecting system->administration->hardware drivers and letting the ATI drivers from the repository be installed.

You might need a livecd to do this do you have one to hand?

---

