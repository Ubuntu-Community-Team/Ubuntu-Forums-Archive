---
title: "uninstall wine"
date: 2009-04-23
forum: New to Ubuntu
---

### Post by Stuntman Mike on 2009-04-23
i cant remove "wine-1.0.1" directory from home folder tried entering in it and run sudo make uninstall and sudo rm -r wine-1.0.1 from home dir. and it says permission denied

i run sudo apt-get remove wine && aptitude remove wine and i just want to remove that directory cause its all it left to remove and to reinstall again pls help

---

### Post by ugriffin on 2009-04-23
```
sudo apt-get purge wine
sudo rm -rf /home/yourusername/.wine
```

---

### Post by Stuntman Mike on 2009-04-23
rm-rf command not found

---

### Post by Stuntman Mike on 2009-04-23
k need space :D

---

