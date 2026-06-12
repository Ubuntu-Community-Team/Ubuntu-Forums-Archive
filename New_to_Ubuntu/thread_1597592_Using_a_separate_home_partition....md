---
title: "Using a separate /home partition..."
date: 2010-10-15
forum: New to Ubuntu
---

### Post by zer010 on 2010-10-15
What kind of things are saved? If I understand correctly, it saves my personal data(Pics, Docs, etc.), and settings. Does it also save apps? Will it also save my Compiz Cube setup?
I'm thinking of going to 10.10 via a fresh install and was wondering what I might have to reinstall.

---

### Post by Chesamo on 2010-10-15
It will save your configuration, but not the applications themselves. You might have some broken configs until you get the system back up to where it was, but you won't have to reconfigure the programs (since the configs are stored in your home dir).

---

### Post by zer010 on 2010-10-15
Thanks. I think I'll just do a total clean install and just reinstall the back ups of my data.

---

### Post by oldfred on 2010-10-15
You can export a list of installed apps and use that to reinstall the most current version of them.

 dpkg --get-selections > ubuntu-files

from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)

---

### Post by zer010 on 2010-10-16
Cool! That should be helpful. Thanks!

---

