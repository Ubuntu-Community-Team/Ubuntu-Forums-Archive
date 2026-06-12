---
title: "Login to a windows account"
date: 2009-11-15
forum: New to Ubuntu
---

### Post by WitchCraft on 2009-11-15
Is it possible to login into a windows account using Linux?
(=will I have permission to access the windows shares for this account with samba?)

The authorization server runs windows with active-directory in a domain.

---

### Post by The Cog on 2009-11-15
Yes. Using nautilus, enter an address like this into the address bar:
**smb://MYDOMAIN;administrator@1.2.3.4/C$**
or pull own the nautilus menu and choose File->Connect to server, and choose a type of Windows Share.

---

