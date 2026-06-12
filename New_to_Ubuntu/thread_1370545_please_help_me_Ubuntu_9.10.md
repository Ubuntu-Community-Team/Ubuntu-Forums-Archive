---
title: "please help me Ubuntu 9.10"
date: 2010-01-02
forum: New to Ubuntu
---

### Post by pleasehelpme90 on 2010-01-02
please help me how to uninstall vmware player 3.0 and i tried everything 

please see my screen shot

---

### Post by mjitkop on 2010-01-02
It looks like you need to have root privileges to do that. Type the word "sudo" first on the command line before typing the other commands. You will be prompted to enter your password before the uninstall proceeds.

```
sudo vmware-installer -u vmware-player
```

---

### Post by Cheesemill on 2010-01-02
You need to type 'sudo' before the command you ran. Try doing:
```
sudo vmware-installer -u vmware-player
```

---

### Post by kellemes on 2010-01-02
Try this..
```
sudo vmware-installer -u vmware-player
```
(and enter you're password when asked)

---

### Post by Ferretti on 2010-01-02
Just as Cheesemill said above, use "sudo vmware-installer -u vmware-player" (Without quotes).

---

### Post by YosefKaro on 2010-01-02
This thread may contain your answer: [http://ubuntuforums.org/showthread.php?t=1319101&page=2](http://ubuntuforums.org/showthread.php?t=1319101&page=2)

-Yos

P.S. WoW, talk about fast responses :D

---

### Post by pleasehelpme90 on 2010-01-02
thanks allllllllllll for the fast reply best os ever!!!

---

