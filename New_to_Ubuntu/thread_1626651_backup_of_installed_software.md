---
title: "backup of installed software"
date: 2010-11-20
forum: New to Ubuntu
---

### Post by kiraku on 2010-11-20
hi:

I want to do a formatting to my pc, so I would like to know if there is a way to backup the programs, or at least the list of them that i have installed on it, so i can reinstall them after the formatting??

cya

---

### Post by bkratz on 2010-11-20
You might be interested in this thread this morning

[http://ubuntuforums.org/showthread.php?t=1626102](http://ubuntuforums.org/showthread.php?t=1626102)

---

### Post by sikander3786 on 2010-11-20
You can use APTonCD for that.

[http://aptoncd.sourceforge.net](http://aptoncd.sourceforge.net)

---

### Post by kiraku on 2010-11-22
ok, thanxz for the answers!!

---

### Post by oldfred on 2010-11-22
If you just want a list of installed apps (good for new install as it will reinstall with the newest version).

from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)

and using synaptic
[http://ubuntuforums.org/showthread.php?t=1057608](http://ubuntuforums.org/showthread.php?t=1057608)

 dpkg --get-selections | grep -v deinstall > ubuntu-files
or
 dpkg --get-selections > ubuntu-files

---

