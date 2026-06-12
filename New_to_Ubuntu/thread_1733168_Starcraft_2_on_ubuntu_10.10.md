---
title: "Starcraft 2 on ubuntu 10.10"
date: 2011-04-18
forum: New to Ubuntu
---

### Post by haggardtechno on 2011-04-18
Hey everyone, pretty stumped here :/. I recently switched to Ubuntu, and I tried to install Starcraft 2 earlier. I installed it through wine, and all went well, but everytime i try to start the game, it goes to the first load screen, then crashes and gives me the crash report window. Any Ideas ? :s

---

### Post by sandyd on 2011-04-18
> **haggardtechno said:**
> Hey everyone, pretty stumped here :/. I recently switched to Ubuntu, and I tried to install Starcraft 2 earlier. I installed it through wine, and all went well, but everytime i try to start the game, it goes to the first load screen, then crashes and gives me the crash report window. Any Ideas ? :s
Follow instructions at
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=20882](http://appdb.winehq.org/objectManager.php?sClass=version&iId=20882)

might also want to add the [WINE PPA]("https://launchpad.net/%7Eubuntu-wine/+archive/ppa") to update to the latest version of WINE.

You can add it (and upgrade WINE) by running
```

sudo add-apt-repository ppa:ubuntu-wine/ppa
sudo apt-get update
sudo apt-get install   wine1.3 wine1.3-gecko
```

---

### Post by pi3.1415926535... on 2011-04-18
It would be helpful to know what this crash error was. Also see [WINE's page on Starcraft II compatibility]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=20882").

---

