---
title: "Confused: changed user password on encrypted home, dialog box does not close"
date: 2011-01-29
forum: New to Ubuntu
---

### Post by sarc on 2011-01-29
I just changed my own login password using System/Administration/Users and Groups.  My /home was encrypted during installation.  When I clicked OK the dialog box grayed out and the 'hourglass' wheel appeared, like the system is waiting on the hard disk.  So I thing maybe the system is re-encrypting my home directory, but it's only a few GB and it's been like this for 20 minutes... is this normal?
Running 10.04 on an external USB drive

Thanks

---

### Post by [Snc] on 2011-01-29
> **sarc said:**
> I just changed my own login password using System/Administration/Users and Groups.  My /home was encrypted during installation.  When I clicked OK the dialog box grayed out and the 'hourglass' wheel appeared, like the system is waiting on the hard disk.  So I thing maybe the system is re-encrypting my home directory, but it's only a few GB and it's been like this for 20 minutes... is this normal?
Running 10.04 on an external USB drive

Thanks

External USB can be really snail slow, consider this, it has to read everything and decrypt it, encrypt it and write it back, that is a lot of traffic...

Anyway, the best thing is to let the comp do whatever it is doing, just give it time and be patient ;)

---

### Post by sarc on 2011-01-30
Ended up hard rebooting, then logging in as superuser, delete the user and recreate a new used with the new password.  Oh well..

---

