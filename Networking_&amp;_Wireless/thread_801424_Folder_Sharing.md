---
title: "Folder Sharing"
date: 2008-05-20
forum: Networking &amp; Wireless
---

### Post by CollisionInc on 2008-05-20
I am trying to share a folder that can be accessed from windows systems on my network. When i share the foler i get the following error message:

'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error Permission denied
You do not have permission to create a usershare. Ask your administrator to grant you permissions to create a share.

Any Advice?

---

### Post by danwizard208 on 2008-05-20
I have this same problem when using a right click context menu...
A workaround i found is to open a terminal and run shares-admin, which asks you for your password, and then lets you edit shares globally.

---

### Post by bluefrog on 2008-05-20
you must be a member of the group sambashare. Use the syst/admin/users tool to add your user then log out / log in.

---

### Post by CollisionInc on 2008-05-20
> **danwizard208 said:**
> I have this same problem when using a right click context menu...
A workaround i found is to open a terminal and run shares-admin, which asks you for your password, and then lets you edit shares globally.

Tried that - but get the same error as before when i try sharing again!

---

### Post by CollisionInc on 2008-05-20
> **bluefrog said:**
> you must be a member of the group sambashare. Use the syst/admin/users tool to add your user then log out / log in.

Ive checked and I am a member of the SAMBASHARE group

---

### Post by jetsam on 2008-05-20
This is a known bug.  See post #4 of this thread for the work-around: [http://ubuntuforums.org/showthread.php?t=772706]("http://ubuntuforums.org/showthread.php?t=772706")

---

