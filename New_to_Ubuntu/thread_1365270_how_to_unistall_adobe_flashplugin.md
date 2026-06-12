---
title: "how to unistall adobe flashplugin"
date: 2009-12-27
forum: New to Ubuntu
---

### Post by maligato on 2009-12-27
I need to un-install Adobe Flashplugin. Got advise of going to "Synaptic Package Manager" Once there, I receive this message
" E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report"
What are the steeps I need to do now? 
thank you
maligato
note: I am new with UBUNTU :(

---

### Post by kansasnoob on 2009-12-27
I thought that bug was supposed to be fixed in updates but:

[https://bugs.launchpad.net/ubuntu/+source/adobe-flashplugin/+bug/412944](https://bugs.launchpad.net/ubuntu/+source/adobe-flashplugin/+bug/412944)

The suggestion was to run:

```
sudo rm /var/lib/dpkg/info/adobe-flashplugin.prerm
```

---

### Post by mac9416 on 2010-01-24
The better way is to enable the partner repo by going to System>Administration > Software Sources > Other Software and enable 'http://archive.canonical.com/ karmic partner'.

---

