---
title: "synaptip package manager error after installing Flash"
date: 2009-11-27
forum: New to Ubuntu
---

### Post by panupat on 2009-11-27
I downloaded .deb from adobe website. The first time I downloaded it GDebi seemed to go through the installation till the end.

Then firefox still couldn't play flash contents. So I re-downloaded the .deb again. This time, every time I try, GDebi is giving me error.

> Could not open 'install_flash_player_10_linux.deb'

The package might be corrupted or you are not allowed to open the file. Check the permissions of the file.

The file went to my user-name/download directory. I tried deleting it, give it read-write-execute permission for everyone, still getting the same error.

Also now my Synaptic Package Manager will not start :/ giving me error

> E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

Can anyone help me solve this problem?

---

### Post by Soul-Sing on 2009-11-27
```
sudo gedit /var/lib/dpkg/status
```

remove the flashplugin nonfree content=>save

---

