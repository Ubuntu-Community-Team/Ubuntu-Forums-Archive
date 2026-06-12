---
title: "help installing limewire pleae"
date: 2010-08-24
forum: New to Ubuntu
---

### Post by srChubs on 2010-08-24
i tried to install limewire and it said this....

Error: Dependency is not satisfiable: sun-java6-jre|icedtea-java7-jre|sun-java6-jdk|icedtea-java7-jdk
 
so i typed this in terminal...

sudo apt-get install sun-java6-jre

and then it said this....

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java6-jre is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-jre has no installation candidate

please help, thank you very much
                                                    -anthony

---

### Post by oldsoundguy on 2010-08-24
If you have the restricted extras repository installed, you can install Sun run time from Synaptic Package manager.

---

### Post by dtoronto on 2010-08-24
Sun Java was dropped from the ubuntu repositories

you can get it by adding a repo

```
sudo add-apt-repository "deb http://archive.canonical.com/ lucid partner"
sudo apt-get update
sudo apt-get install sun-java6-jre
```

---

### Post by dtoronto on 2010-08-24
On a side note, I may be wrong but I'm not sure that limewire comes packaged with a linux build, you may want to look at other options for bit-torrent.

---

### Post by srChubs on 2010-08-24
ok thanks everyone that worked, but now when i install it, it says that something is open like package manager, or sinaptic, but i go into system monitor and it says nothing is running except the system monitor. help? thanks

---

### Post by LiquidMeson on 2010-08-24
could also try [http://azureus.sourceforge.net/](http://azureus.sourceforge.net/) instead of limewire.

---

### Post by oldsoundguy on 2010-08-25
try re-setting (right alt/print screen/k (kill all processes) and then go back and try to install.

I haven't used limewire in years as when I was using Windows, it was so full of malware/virus files, that most downloads were useless in Windows.  Not sure how things are for Linux.

---

