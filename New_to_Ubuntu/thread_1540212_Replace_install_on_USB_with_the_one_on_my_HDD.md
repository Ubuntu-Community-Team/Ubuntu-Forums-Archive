---
title: "Replace install on USB with the one on my HDD?"
date: 2010-07-27
forum: New to Ubuntu
---

### Post by grief -l on 2010-07-27
Made a portable USB stick with vanilla 10.04. Is there any way to &quot;inoculate&quot; it with the 10.04 install that's on my hard drive? The one on my hard drive has ubuntu, xubuntu, lyx, lynx, GIMP and a few other odds and ends like FF plug ins.    I assume it would take a lot more than just replacing the /Home directory with the one on the hard drive, but I really need to hear what exactly it would entail - or is it easier to just apt-get install everything by hand?   Thanks in advance!  Gabe

---

### Post by grief -l on 2010-07-27
bumpity

---

### Post by oldfred on 2010-07-27
Your /home has all your user settings and for most users all their data.

You can export a list of all installed programs:

from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)

and using synaptic
[http://ubuntuforums.org/showthread.php?t=1057608](http://ubuntuforums.org/showthread.php?t=1057608)

sudo cp /etc/apt/sources.list ~/sources.list.backup
Otherwise if you have added any PPAs or other sources, the tip will only reinstall Ubuntu files,

If you did any manual system configurations, you may want to also look in /etc for those files.

---

### Post by grief -l on 2010-07-27
Thanks a bunch oldfred. Exactly what I was looking for!  Gabe

---

