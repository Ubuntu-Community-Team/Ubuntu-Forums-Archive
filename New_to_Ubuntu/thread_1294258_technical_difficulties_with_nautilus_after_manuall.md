---
title: "technical difficulties with nautilus after manually upgrading it"
date: 2009-10-18
forum: New to Ubuntu
---

### Post by klemperal on 2009-10-18
I wanted to try the latest version of nautilus, so I downloaded, compiled and installed it via sudo checkinstall.  Afterwards, certain right click extensions such as 'open terminal here,' 'set as wallpaper,' or archiving no longer appeared.  I figured that the latest version I was using was what was causing the problems, so I uninstalled it and reinstalled the original version from the repos.  However, the above extensions are still not working for me after reverting the the older version.  Anyone know what I should do to fully restore nautilus's functionality?

---

### Post by Paqman on 2009-10-18
Have you tried reinstalling all the plugins?

---

### Post by desmane on 2009-10-18
do *sudo apt-get autoremove --purge nautilus* and maybe removing the config files in home (~/home/username/.nautilus) any good?

---

