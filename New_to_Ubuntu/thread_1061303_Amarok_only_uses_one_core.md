---
title: "Amarok only uses one core"
date: 2009-02-05
forum: New to Ubuntu
---

### Post by blairm on 2009-02-05
Hi,

Installed KDE 4.2 this morning and loving it, but noticed Amarok (the old one which is in the repositories, not Amarok2) appeared to use only one core of my E8400 (3ghz) processor.
CPU1 spent most of its time between 90% and 100%, while CPU2 was running between 2% and 10%.
Running htop showed three or four instances of amarokapp were consuming the vast majority of resources.
After uninstalling Amarok and using Rhythmbox, both cores are at similar levels, running between 3% and 22%.
Is this normal behaviour for Amarok? And if so is it anything to worry about? I do like Amarok more. 

Cheers,

Blair

---

### Post by stchman on 2009-02-05
> **blairm said:**
> Hi,

Installed KDE 4.2 this morning and loving it, but noticed Amarok (the old one which is in the repositories, not Amarok2) appeared to use only one core of my E8400 (3ghz) processor.
CPU1 spent most of its time between 90% and 100%, while CPU2 was running between 2% and 10%.
Running htop showed three or four instances of amarokapp were consuming the vast majority of resources.
After uninstalling Amarok and using Rhythmbox, both cores are at similar levels, running between 3% and 22%.
Is this normal behaviour for Amarok? And if so is it anything to worry about? I do like Amarok more. 

Cheers,

Blair

Maybe Rhythmbox has been coded to spawn additional threads if more than one core is in the system.

---

