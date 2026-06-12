---
title: "uninstalling a tar ball"
date: 2009-01-25
forum: New to Ubuntu
---

### Post by DarinB on 2009-01-25
thank you to all on installing tar ball
i did install gnormalize some of the dependants were not available and i can't find documentation on to find out what i am missing i will have to stick to deb and ubuntu packages this has been more than i bargained for.
SO HOW DO I UNINSTALL THIS PUPPY AND ALL THE REST OF THE STUFF IT ADDED
this has been a learning experience as long as it doesn't break anything else...please give me advise maybe i should just leave it and pretend it is not there... i have tons of HD space and everything is working except gnormalize of course!!!!!! 
any ideas...but i still would like to know you to uninstall any tar ball for future use.

---

### Post by xikarrousx on 2009-01-25
you should be able to just:

make uninstall

have you tried this command yet?

---

### Post by Mud.Knee.Havoc on 2009-01-25
> **DarinB said:**
> 
any ideas...but i still would like to know you to uninstall any tar ball for future use.

You should be using checkinstall (it's available in the repos if you don't already have it installed).  When you build a program from source, substitute 'sudo checkinstall' for 'sudo make install'.

Here's some [info to read]("https://help.ubuntu.com/community/CheckInstall").

EDIT: Forgot to mention *why* you should be doing this.  It basically creates a .deb from the source, so it can be removed easily (ie. via Synaptic).

---

### Post by oldos2er on 2009-01-25
If you weren't able to compile it, there's nothing to uninstall; just delete the source code folder.

---

