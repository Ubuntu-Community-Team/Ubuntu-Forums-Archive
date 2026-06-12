---
title: "Update Manager error"
date: 2009-09-28
forum: New to Ubuntu
---

### Post by davidsrsb on 2009-09-28
I am suddenly getting an error that stops me running Synaptic

'E:Unable to parse package file /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_jaunty-security_main_binary-i386_Packages (1), E:The package lists or status file could not be parsed or opened.'

A couple of times now Synaptic has frozen the PC and forced me to power off

---

### Post by mathay on 2009-09-28
What is your main server in Synaptic?

---

### Post by davidsrsb on 2009-09-28
I can't start synaptic to check
It says
"E:Unable to parse package file /var/lib/apt/lists
security.ubuntu.com_ubuntu_dists-jaunty-security_main_binary-
i386_packages (1)
E:The packages lists or status file could not be parsed or opened.
E:_cache->open() failed, please report.

---

### Post by davidsrsb on 2009-09-28
It was "Server for Malaysia"

---

### Post by drs305 on 2009-09-28
If hitting Reload and changing servers doesn't work, find the "security" repository in Synaptic or Software Sources Updates tab.  Untick them. This will remove the entry in the repository list, which is possibly corrupted. Wait a few seconds, retick the security repositories and press Reload in the main menu. See if it works now.

If not, change to a different server and repeat.

---

### Post by davidsrsb on 2009-09-29
Changing to "Main Server" and unticking 3rd parties, reloading and then reticking and reloading worked

---

