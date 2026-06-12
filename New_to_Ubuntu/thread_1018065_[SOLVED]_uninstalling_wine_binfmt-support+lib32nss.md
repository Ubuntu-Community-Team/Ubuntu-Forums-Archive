---
title: "[SOLVED] uninstalling wine: binfmt-support+lib32nss-mdns"
date: 2008-12-21
forum: New to Ubuntu
---

### Post by frincha on 2008-12-21
After uninstalling wine I see that I could delete two more libraries than synaptic showed me (checked the dependencies then click on uninstall of those dependencies and there were no more dependencies), they are:

binfmt-support
lib32nss-mdns

I have Ubuntu 64,
are these files in a fresh install Ubuntu 64?

-If yes: If I install them again, will they be installed with the same configuration?

Tks in advance and Happy Christmas:)

---

### Post by ptn107 on 2008-12-22
*binfmt-support* is installed by default on a new system.  *lib32nss-mdns* was indeed pulled in by wine and does not have to be reinstalled.

---

### Post by frincha on 2008-12-23
> **ptn107 said:**
> *binfmt-support* is installed by default on a new system.  *lib32nss-mdns* was indeed pulled in by wine and does not have to be reinstalled.

Tks for the answer :) - I deduce that installing binfmt-support, it's configuration will be the same as before being uninstalled.

---

