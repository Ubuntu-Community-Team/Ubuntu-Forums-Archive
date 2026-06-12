---
title: "Is there a way i can install steam for ubuntu?"
date: 2011-04-20
forum: New to Ubuntu
---

### Post by Bunny12391 on 2011-04-20
I want to play left4dead but the install file isn't an .exe so i cant run it on wine

---

### Post by ibznorange on 2011-04-20
Certainly viable

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=14592](http://appdb.winehq.org/objectManager.php?sClass=version&iId=14592)

Can i ask what format the steam installer for windows is?

---

### Post by Bunny12391 on 2011-04-20
its steaminstall.msi

---

### Post by ibznorange on 2011-04-20
Hrm. My only nixbox right now is running headless, so i cant really test which of these is correct, but check here.

[http://wiki.jswindle.com/index.php/Wine_MSI](http://wiki.jswindle.com/index.php/Wine_MSI)

Like i said, i cant check for sure, but im inclined to take first stab at 
```
wine start steaminstall.msi
```

If that doesnt work, try the others. 
Im assuming youre running Maverick or Lucid, which should leave you with pretty solid functionality. Its been getting mostly gold and platinums on various distros since 1.2 release candidates, so Id assume you have pretty good luck, provided you dont end up with any oddball video card issues.

---

