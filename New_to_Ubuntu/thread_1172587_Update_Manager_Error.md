---
title: "Update Manager Error"
date: 2009-05-28
forum: New to Ubuntu
---

### Post by Peter J Cooke on 2009-05-28
I am new to this I am getting this error message when I try to update what do I do to get it sorted?

E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_jaunty-updates_restricted_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

---

### Post by skymera on 2009-05-28
try ```
 sudo aptitude update 
```

---

### Post by raymondh on 2009-05-28
Hello Peter J Cooke

Have a look at your /etc/apt/sources.list with your favorite editing editor and make sure your uncommented sources are Jaunty related and not intrepid. Then save and exit the editor and open a terminal and type/enter (one at a time):

```
sudo apt-get update
sudo apt-get upgrade
```

and see what happens.

If you still receive those errors, you may try this fix suggested by a forum member Leoquant:

[http://ubuntuforums.org/showthread.php?p=7350314](http://ubuntuforums.org/showthread.php?p=7350314)

Regards,

---

