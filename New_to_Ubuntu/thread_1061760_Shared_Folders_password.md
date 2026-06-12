---
title: "Shared Folders password?"
date: 2009-02-06
forum: New to Ubuntu
---

### Post by fraser_m on 2009-02-06
I've used the Shared Folders setup in Nautilus to set my "Public" folder to share, but when I try to access it from any computer, Ubuntu or Windows, it asks for a password. I've tried using my username and password from Ubuntu, but it keeps rejecting it.

Any ideas?

---

### Post by fraser_m on 2009-02-06
If I enable Guest Access, it works fine, but I want some security, and I want a password for it...

---

### Post by fraser_m on 2009-02-06
Sorted. I tried using:
```
sudo smbpasswd -a family
```but this didn't work. I tried to use it on my own username, and it did. I then tried to access the share using this password, and it worked. I then created a new user "family" on my system, and did *smbpasswd* again. It all works now. Yay!

Where's the SOLVED button?

---

### Post by superprash2003 on 2009-02-06
SOLVED feature temporarily suspended..

---

