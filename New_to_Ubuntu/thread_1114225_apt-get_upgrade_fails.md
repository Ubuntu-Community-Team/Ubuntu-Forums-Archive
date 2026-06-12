---
title: "apt-get upgrade fails"
date: 2009-04-02
forum: New to Ubuntu
---

### Post by edpatterson on 2009-04-02
I am having problems with rsync so I went to samba.org/rsync to look for help. I saw that version 3.0.5 had been released and figured maybe my problems would go away if I upgraded.

I tried 
apt-get upgrade rsync
and saw it was going to upgrade a plethora of stuff. I say Y :-)
It displayed an error about being unable to fetch some archives. rsync --version still shows the old version.

Is apt-get upgrade a wise thing to do?

Trying to get rsync to sync a directory to numerous machines via cron.

Ed

---

### Post by Anthon on 2009-04-02
Maybe your internet connection was temporarily down and caused the fetch to fail.
Normally apt-get upgrade should not give you any problems. I would just retry the upgrade and see if all the stuff comes at second try.

---

### Post by Therion on 2009-04-02
Usually you can resolve this by simply switching servers and using apt-get again.

---

### Post by mister_pink on 2009-04-02
Firstly, apt-get upgrade doesn't take a package name as you've given it, its just "sudo apt-get upgrade". This is the same as applying the updates that should appear in the notification area. 

Any upgrade will only take you to the newest version that is in the repositories which is unlikely to be the absolutely newest version.

Finally, its unlikely that you actually need to upgrade rsync. Its quite a mature bit of software and I doubt that much gets changed to it. Its more likely that the rsync commands aren't correct. Try asking for help with that instead.

---

### Post by sheshbesh on 2009-04-02
Don't forget to run "sudo apt-get update" before you run "sudo apt-get upgrade"

I guess the package in the repositories is not the most up-to-date (it takes a bit of time until the ubuntu developers check the new releases). If you insist on installing the latest, you can download a .deb file and then use "dpkg -i" to install it. or you could compile the source...

cheers

---

