---
title: "update manager. greyed out adobe-flashplugin?"
date: 2009-12-09
forum: New to Ubuntu
---

### Post by jmcgovern on 2009-12-09
I've done an update today, and everything appeared to go just fine, as usual, except  I now have an entry for adobe-flashplugin in Update Manager, but it's greyed out.  It was also present in the list of updates, but it was unchecked and i could not select it.  Anyone know why. I have the proper repository enabled.

---

### Post by zvacet on 2009-12-13
```
sudo apt-get update && sudo apt-get upgrade

sudo apt-get dist-upgrade
```

---

