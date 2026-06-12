---
title: "E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a soluti"
date: 2010-02-13
forum: New to Ubuntu
---

### Post by ksmyself on 2010-02-13
i was installing java runtime environment with following command

sudo apt-get install sun-java6-jre sun-java6-plugin equivs

and after it was downloaded i closed the terminal.

I tried to install it again but i get this :


root@ubuntu:~# sudo apt-get install sun-java6-jre sun-java6-plugin equivs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  sun-java6-jre: Depends: sun-java6-bin (= 6-15-1) but it is not going to be installed or
                          ia32-sun-java6-bin (= 6-15-1) but it is not installable
                 Recommends: gsfonts-x11 but it is not going to be installed
  sun-java6-plugin: Depends: sun-java6-bin (= 6-15-1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).




if i try to download something i get the the same error
please help me out of this 
thanks in advance

---

### Post by nothingspecial on 2010-02-13
Type

```
sudo apt-get -f install
```

---

