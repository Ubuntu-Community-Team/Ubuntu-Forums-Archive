---
title: "Package Dependencies cannot be resolved"
date: 2010-06-10
forum: New to Ubuntu
---

### Post by LinuxLewis on 2010-06-10
I think I messed something up when trying to install/uninstall pidgin. I keep getting the message "Package Dependencies cannot be resolved" when trying to install pidgin. I just installed this today. Please help!

---

### Post by SlidingHorn on 2010-06-10
```
sudo apt-get -f install pidgin
```

---

### Post by LinuxLewis on 2010-06-10
The following packages have unmet dependencies:
  pidgin: Depends: pidgin-data (< 1:2.6.6-z) but 1:2.7.1-1ubuntu1~pidgin1.10.04 is to be installed
E: Broken packages

---

### Post by oliver369 on 2010-06-14
Hi LinuxLewis,

I just stumbled over the same issue as you, eventually I tried the following:
sudo apt-get remove pidgin*

Hope this helps.

---

### Post by day7 on 2011-01-07
Oliver369 thanks, your:

[COLOR="Green"]sudo apt-get remove pidgin* [/COLOR]

worked.  Immediately after I did:

[COLOR="Green"]sudo apt-get install pidgin[/COLOR]

and it installed fine.

---

