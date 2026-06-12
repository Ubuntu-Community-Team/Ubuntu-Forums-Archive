---
title: "default keyring"
date: 2008-12-05
forum: New to Ubuntu
---

### Post by sameer.india on 2008-12-05
when I try to connect to a wireless network a message comes asking for a password for the nm-applet to access the default keyring in which neither my root password nor my sudo password work.
So I deny and things are fine.
But I want to know what it is about.

---

### Post by mazapoint.com on 2008-12-05
> **sameer.india said:**
> when I try to connect to a wireless network a message comes asking for a password for the nm-applet to access the default keyring in which neither my root password nor my sudo password work.
So I deny and things are fine.
But I want to know what it is about.

to reset the default keyring password, open system->keyring manager select view->keyrings and delete the default keyring, the next time u start a session, u will be prompted for a new password. note … this deletes all your keys on the keyring

---

### Post by flanagan on 2008-12-05
I had the same problem in Hardy 8.04 as did many others. Seems it was a problem in Network Manager. I solved it by replacing Network Manager with Wicd according to [http://www.akyl.net/Network+Manager+problem+in+Ubuntu+8.04]("http://www.akyl.net/Network+Manager+problem+in+Ubuntu+8.04").

That said, I have done a clean install of Intrepid 8.10 on a separate machine and have no problem with Network Manager.

---

