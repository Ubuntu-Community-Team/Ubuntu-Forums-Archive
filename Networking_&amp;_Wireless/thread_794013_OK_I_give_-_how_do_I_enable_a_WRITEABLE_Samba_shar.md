---
title: "OK I give - how do I enable a WRITEABLE Samba share?"
date: 2008-05-14
forum: Networking &amp; Wireless
---

### Post by keathmilligan on 2008-05-14
Hardy Heron - OK, I've gone through the work-arounds just to get Samba sharing working in the *first* place (grr) and I have managed to share a folder from my home directory, but it is read-only.

How do I make it read-write? (and no, not for everybody ala the "Allow other people to write option")

---

### Post by keathmilligan on 2008-05-14
I have a partial solution. If you're like me and you're coming from other Linux distros (like Fedora), you have certain expectations about how Samba should work. Ubuntu is more user-oriented. The right-click-and-share option from Nautilus is great if you just want to do something simple like share some pictures or music (read-only), but that's about it.

To share your entire home directory with read/write access or any other directory, you'll need to manually edit smb.conf. Install Samba, then edit smb.conf with:

sudo gedit /etc/smb.conf

(or whatever editor you prefer)

Look for the [homes] section. Uncomment and/or change the following lines:

[homes]
   comment = Home Directories
   browseable = no
   read only = no
   create mask = 0700
   directory mask = 0700
   valid users = %S

This will make all user home directories available via Samba with read/write access. The "valid users = %S" line insures that only the owner of a directory can access it.

---

