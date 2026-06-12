---
title: "Synaptic/dpkg is messup up. What now?"
date: 2009-02-19
forum: New to Ubuntu
---

### Post by mac9416 on 2009-02-19
OK, so when trying to install debs (no internet conn.) I (like a fool) used "sudo dpkg --force-depends" on one too many files and now "apt-get install -f" wants to uninstall CRITICAL software to fix it. What now?
Thanks!

---

### Post by bapoumba on 2009-02-19
Hmm, this is probably due to a version package that is not right according to the dependency tree. Maybe uninstall said package and grab the correct version one (from a CD for ex)?

Without more infos, it is hard to guess :)

---

### Post by mac9416 on 2009-02-19
Unfortunately, it was quite a few packs. Do you think maybe upgrading all would work? Difficult to do, but may work. Thanks!

---

### Post by bapoumba on 2009-02-20
May be, depend on what you did. If you used "n+1" packages version on "n" installation, it should work. Make sure the important packages (ubuntu-minimal, ubuntu-standard, ubuntu-desktop, I might miss some) are installed and you use dist-upgrade.

If apt-get complains, and if you have never been using aptitude, maybe aptitude can do it (aptitude full-upgrade), they do not share log files.
If dpkg complains and the dependency tree is too borked, it might be better to perform a full reinstall. I'm sure debian has tools to fix that (I searched and found equivs, it's in the repos) but I have never used them, so I cannot really help you, sorry.
Here for ex: [http://linux.derkeiler.com/Mailing-Lists/Debian/2006-08/msg01885.html](http://linux.derkeiler.com/Mailing-Lists/Debian/2006-08/msg01885.html)

---

