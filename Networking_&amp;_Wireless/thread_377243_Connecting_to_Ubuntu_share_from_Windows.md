---
title: "Connecting to Ubuntu share from Windows?"
date: 2007-03-05
forum: Networking &amp; Wireless
---

### Post by NeilBlanchard on 2007-03-05
Greetings,

I've shared a folder in Ubuntu, and from a Windows computer, I can see the Ubuntu machine, but when I try to explore it, it asks for a user name and password.  I enter the Ubuntu user name and password, but that doesn't work.

What user name and password is it asking for, and do I have to set this up in Ubuntu?  (This is harking back to Win2K, it seems?)

---

### Post by va1ha11a on 2007-03-06
You need to set up the samba users, there is some info here:

[https://help.ubuntu.com/6.10/ubuntu/serverguide/C/windows-networking.html]("https://help.ubuntu.com/6.10/ubuntu/serverguide/C/windows-networking.html")

---

### Post by NeilBlanchard on 2007-03-06
Hello,

Thanks you very much!  BTW, I had to add the sudo:

sudo smbpasswd -a: <username>

...and I had to use the current Ubuntu user name.

**Wish list item: give this a GUI control panel in the Networking settings!**  8-)

---

### Post by NeilBlanchard on 2007-07-06
Hello,

> **NeilBlanchard said:**
> Thanks you very much!  BTW, I had to add the sudo:

sudo smbpasswd -a: <username>

...and I had to use the current Ubuntu user name.

Why won't this work for any other username, other than the currently logged on user?  This is awkward, to say the least.

Also, how can I conneect to an SMB (Samba) share form another Ubuntu machine?  It never asks for a name, but then it never can open the share, either.  What other networking protocol is used (native?) to Ubuntu/Linux?

---

