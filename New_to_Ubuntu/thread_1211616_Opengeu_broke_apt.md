---
title: "Opengeu broke apt"
date: 2009-07-12
forum: New to Ubuntu
---

### Post by Warpnow on 2009-07-12
So, I added the opengeu PPA and tried to install enlightenment from it, but one of the necessary deb files isn't on their server, an error other people are experiencing, too.

Now, I can't remove or purge the half-way done enlightenment install...

chase@chase-laptop:~$ sudo apt-get purge opengeu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package opengeu-e17-luna-crescente-themes needs to be reinstalled, but I can't find an archive for it.
chase@chase-laptop:~$ sudo apt-get remove opengeu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package opengeu-e17-luna-crescente-themes needs to be reinstalled, but I can't find an archive for it.
chase@chase-laptop:~$ 


How can I force apt to remove the components of opengeu-desktop it downloaded/installed?

---

