---
title: "On a defualt install why do all of the system files/folders have read and execute"
date: 2011-06-15
forum: New to Ubuntu
---

### Post by venom104 on 2011-06-15
On a default install why do all of the system files/folders have read and execute permissions by default? Isn't this a security risk (The fact that the other group is given read and execute permissions)? 

Are there installs that restrict all the system folders (/etc,/bin,/boot,ect) to the root user only, or is there a way to do this?

I'm asking because it seems kind of funny to allow any user on the machine to VIEW any file or folder on the machine by default.

---

### Post by lykwydchykyn on 2011-06-15
> **venom104 said:**
> On a default install why do all of the system files/folders have read and execute permissions by default? Isn't this a security risk (The fact that the other group is given read and execute permissions)? 

Are there installs that restrict all the system folders (/etc,/bin,/boot,ect) to the root user only, or is there a way to do this?

I'm asking because it seems kind of funny to allow any user on the machine to VIEW any file or folder on the machine by default.

If you restricted system folders to root only, you wouldn't be able to run any software.

"execute" on a folder gives you permission to browse to the folder.

On my install, only the executable files have execute permissions, at least from the directories I looked at.

Actually, not every file is viewable by every user.  Try viewing /var/log/syslog as a non-admin user, for instance -- can't do it.  Files that contain sensitive information (passwords, etc) are generally only readable by root or the owner.  But locking down executables, libraries, and config files would be pointless -- you'd just not be able to use them.

---

### Post by venom104 on 2011-06-16
> **lykwydchykyn said:**
> If you restricted system folders to root only, you wouldn't be able to run any software.

"execute" on a folder gives you permission to browse to the folder.

On my install, only the executable files have execute permissions, at least from the directories I looked at.

Actually, not every file is viewable by every user.  Try viewing /var/log/syslog as a non-admin user, for instance -- can't do it.  Files that contain sensitive information (passwords, etc) are generally only readable by root or the owner.  But locking down executables, libraries, and config files would be pointless -- you'd just not be able to use them.

Thank you for your speedy reply! This one is closed.

---

### Post by dFlyer on 2011-06-16
Please change the title of the thread to solved.

---

