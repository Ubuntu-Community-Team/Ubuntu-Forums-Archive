---
title: "Error messages when using Synaptic"
date: 2010-03-08
forum: New to Ubuntu
---

### Post by sunwatcher on 2010-03-08
I have a new install of 9.04, and I'm adding my usual apps with Synaptic.  Unfortunately, I'm also getting some error messages, and a few apps are not installing correctly.  Here are the messages I've gotten:

[INDENT]E: /var/cache/apt/archives/kdelibs5_4%3a4.2.2-0ubuntu5.4_i386.deb: short read in buffer_copy (backend dpkg-deb during `./usr/lib/libkio.so.5.2.0')

E: /var/cache/apt/archives/openoffice.org-core_1%3a3.0.1-9ubuntu3.2_i386.deb: short read in buffer_copy (backend dpkg-deb during `./usr/lib/openoffice/basis3.0/program/libooxli.so')[/INDENT]

This may have begun after an update (not sure), but Openoffice was removed from my system altogether and things that rely on KDE (like Amarok) are not installing.

Synaptic shows broken packages for certain apps, and then shows the above errors.

What can I do?

---

### Post by Temposs on 2010-03-08
I would manually go and delete those .deb files. Then uninstall the openoffice.org-core and kdelibs packages, and install them again.

---

### Post by Temposs on 2010-03-08
Actually, you might have to reverse the order of that. Uninstall those packages first and then delete the .deb files.

---

### Post by sunwatcher on 2010-03-08
I manually deleted the debs with thunar running as root, and uninstalled openoffice.org-core through Synaptic.  kdelibs5 did not show as installed.  I then tried reinstalling both, but I get the same error and kdelibs-bin now shows as broken.

What else can I try?

---

### Post by sunwatcher on 2010-03-08
The reverse process worked -- problem solved.  Thanks Temposs!  Do you know why the problem happened in the first place?

---

### Post by Temposs on 2010-03-08
Seems like you had corrupted .deb files. That was the assumption I was working under. I'm glad you fixed your problem :-)

---

