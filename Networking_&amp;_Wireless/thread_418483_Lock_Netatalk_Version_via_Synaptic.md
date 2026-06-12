---
title: "Lock Netatalk Version via Synaptic"
date: 2007-04-22
forum: Networking &amp; Wireless
---

### Post by bloodniece on 2007-04-22
I have netatalk version 2.0.3-4 installed from src and compiled using SSL.
However, Synaptic thinks I need to upgrade Netatalk to version 2.0.3-4.  I went into Synaptoc to 'lock' it to version 2.0.3-4 but netatalk keeps showing up in the upgradables.  How can I lock a version of an application if the repo version is the same version number.  If I install the repo verion then SSL is lost and netatalk stops working properly.

---

### Post by deelerious on 2007-05-06
This seems to be doing the job for now:

```
echo "netatalk hold" | sudo dpkg --set-selections
```

Courtesy of [Coderspiel]("http://technically.us/n8/articles/2006/11/16/a-year-of-plaintext-afp-passwords-is-enough")

---

