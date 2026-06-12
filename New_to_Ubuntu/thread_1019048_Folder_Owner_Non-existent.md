---
title: "Folder Owner Non-existent"
date: 2008-12-22
forum: New to Ubuntu
---

### Post by The Middle Gear on 2008-12-22
All of the important folders on my sister's computer are locked. The important folders being the only ones she wants to access, like her documents and her pictures. Neither of us have any idea how they became locked, and the owner is set to "1001," which apparently does not exist. I couldn't change the permissions as root, and nothing I found on this site or with Google were of any use.

We're both Windows users(the Linux user who set up her machine is... absent...), and I want to fix this for her so she can actually use her computer.

So my question is, with the owner set to a non-existent user, how do I change the permissions of her folders, or do whatever, so that she can access them(preferably to back them up)?

---

### Post by taurus on 2008-12-22
Are those directories in your $HOME?  You can user chown to change the ownership of those directories/files from 1001 back to your username, 1000.  Assuming her login name is sister, you could do something like

```
sudo chown -R sister:sister /home/sister
ls -la /home/sister
```

---

### Post by The Middle Gear on 2008-12-22
I don't know. They're on the desktop.

---

### Post by drs305 on 2008-12-22
> **The Middle Gear said:**
> I don't know. They're on the desktop.

Taurus' example for folders/files on the Desktop will still work.
To view the file listings, the second command would now be:
```

ls -la /home/sister/Desktop

```

or you can open Nautilus with the command:
```

nautilus ~/Desktop

```

---

### Post by The Middle Gear on 2008-12-22
It appears to be fixed. Thanks a lot guys. I may not be too impressed with Linux(too complicated for me >.>) but the community is definitely the most impressive I've seen.

---

