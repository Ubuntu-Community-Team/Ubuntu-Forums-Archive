---
title: "How do I change root password via users and groups?"
date: 2011-03-09
forum: New to Ubuntu
---

### Post by Lucradia on 2011-03-09
Root no longer shows up in the gnome users and groups control panel. It seems over-simplified. Only my user shows up, and I can only create users. It allows me to change who is in the root usergroup (root doesn't show up sadly) but not change root, the user.

VirtualBox Guest Additions requires the administrative password, not my own password (putting my own in says it's wrong); and I'd rather not use sudo on the run files, and would rather have it more user-friendly by just running the autostart.

---

### Post by vanadium on 2011-03-09
The root account on an Ubuntu system is disabled. There is therefore no good reason to set or change the root password.

To work on a prompt with root permissions, you can use "sudo -i"

Virtual box guest editions also can work with a user account with root permissions. You must be missing something there.

---

### Post by Lucradia on 2011-03-09
> **vanadium said:**
> Virtual box guest editions also can work with a user account with root permissions. You must be missing something there.

Nope, I'm running VBGA as if it were a normal CD, autostarting within ubuntu, it asks for the root password.

so what's the command for the users and groups dialog so I can sudo -i it?

---

