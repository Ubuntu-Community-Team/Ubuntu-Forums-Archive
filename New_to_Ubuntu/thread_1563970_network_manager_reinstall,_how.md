---
title: "network manager reinstall, how?"
date: 2010-08-29
forum: New to Ubuntu
---

### Post by squishy003 on 2010-08-29
[SIZE=3]Hello,

I accidentally uninstalled by networkManager and now I have no wireless connection.  I tried to download from synpactic, but no.  I tried to add it from the software center, but no.  Apparently both require internet connection. 

I am in hell trying to figure this out.  Is there anyway that I could networkManager back and working.  Please somebody help me.
[/SIZE]

---

### Post by zeroseven0183 on 2010-08-29
You can download the .DEB package of network-manager from here [http://packages.ubuntu.com/lucid/net/](http://packages.ubuntu.com/lucid/net/)

That link is for Lucid Lynx assuming that you installed 10.04.

---

### Post by jimrz on 2010-08-29
you should be able to install it from the same media (cd or usb) you used for your ubuntu install.

---

### Post by zeroseven0183 on 2010-08-30
> **jimrz said:**
> you should be able to install it from the same media (cd or usb) you used for your ubuntu install.

Yup. You can do```
 sudo aptitude reinstall network-manager network-manager-gnome
```

---

### Post by dineshs on 2010-08-30
Can you try 
[http://ubuntuforums.org/showpost.php?p=9702097&postcount=17](http://ubuntuforums.org/showpost.php?p=9702097&postcount=17)

---

