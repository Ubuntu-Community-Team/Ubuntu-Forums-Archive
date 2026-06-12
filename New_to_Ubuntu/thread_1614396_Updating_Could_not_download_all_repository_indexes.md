---
title: "Updating: Could not download all repository indexes"
date: 2010-11-05
forum: New to Ubuntu
---

### Post by LEP-Recon on 2010-11-05
This is my first time posting on here, and wasn't sure what threat to post in, so the absolute beginner thread seemed like a safe bet.

Anyways, when I run the update manager, upon attempting to retrieve the final update, I get this message:

[INDENT]Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Failed to fetch cdrom://Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release i386 (20100816.1)/dists/lucid/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom://Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release i386 (20100816.1)/dists/lucid/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.[/INDENT]

I'm not entirely sure what it's asking me to do.  At first I thought it was asking for the CD, but that didn't seem to do anything.

Any suggestions?
Thanks!

---

### Post by CharlesA on 2010-11-05
You probably need to deselect the CD in software sources.

---

### Post by AngusH on 2010-11-05
Hey, you seem to have cd repos enabled. Go to System> Administration >Software Sources. Then make sure the box that says something about cdroms (it's near the bottom) is unchecked.
Regards
Angus

---

### Post by LEP-Recon on 2010-11-06
Ah, thank you so much!  That fixed it alright!

---

