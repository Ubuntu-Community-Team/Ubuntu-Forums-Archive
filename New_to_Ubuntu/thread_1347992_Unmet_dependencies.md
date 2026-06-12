---
title: "Unmet dependencies"
date: 2009-12-06
forum: New to Ubuntu
---

### Post by dendan on 2009-12-06
I tried installing mysql and netbeans on ubuntu9.10 but got this error message. Please help. tried 'apt-get -f install', how do i get rid of this message forever? and download netbeans and mysql.
```

dedan01@dedan01-laptop:~$ sudo apt-get install mysql-server
[sudo] password for dedan01: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
  mysql-server: Depends: mysql-server-5.1 but it is not going to be installed
  sun-java6-jre: Depends: sun-java6-bin (= 6-15-1) but it is not going to be installed or
                          ia32-sun-java6-bin (= 6-15-1) but it is not installable
                 Recommends: gsfonts-x11 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
dedan01@dedan01-laptop:~$ 


```

---

### Post by llamabr on 2009-12-06
did you run:

```
sudo apt-get -f install
```

---

### Post by dendan on 2009-12-06
yes tried it got
```

dedan01@dedan01-laptop:~$ apt-get -f install
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
dedan01@dedan01-laptop:~$

```

---

