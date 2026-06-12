---
title: "Permissions issue notification at startup"
date: 2009-11-05
forum: New to Ubuntu
---

### Post by GGreen on 2009-11-05
I have a message popping up when I start up my Ubuntu laptop.  It says "User's $HOME/.dmrc file is being ignored.  This prevents the default session and language from being saved.  File should be owned by user and have 644 permissions.  user's $HOME directory must be owned by user and not writable by other users."

I had this come up before but when I reinstalled Ubuntu, it went away.  I was looking at permissions for my /home folder yesterday but I don't think I changed anything.

Any idea why this happened and how to remedy?

---

### Post by philinux on 2009-11-05
You must have changed something ;).

[https://help.ubuntu.com/community/dmrcErrors](https://help.ubuntu.com/community/dmrcErrors)

---

### Post by mcduck on 2009-11-05
One possible reason for that happening is running graphical applications with "sudo" instead of "gksudo", or starting a root session in terminal with "sudo su" or "sudo -s" instead of "sudo -i".

Sudo doesn't load root user's environment correctly for graphical applications, meaning that you end running the program with root permisssions but using your normal user's settings and configuration files. In some cases this isn't a problem, but in other is will result in your user's files becoming owned by root user. It's pretty much the same issue with "sudo su" versus "sudo -i".

---

### Post by philinux on 2009-11-05
> **mcduck said:**
> one possible reason for that happening is running graphical applications with "sudo" instead of "gksudo", or starting a root session in terminal with "sudo su" or "sudo -s" instead of "sudo -i".

Sudo doesn't load root user's environment correctly for graphical applications, meaning that you end running the program with root permisssions but using your normal user's settings and configuration files. In some cases this isn't a problem, but in other is will result in your user's files becoming owned by root user. It's pretty much the same issue with "sudo su" versus "sudo -i".

+1

---

### Post by GGreen on 2009-11-08
Thanks Philinux!  The link to you gave led me to the solution.  Problem solved!

---

