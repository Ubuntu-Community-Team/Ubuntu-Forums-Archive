---
title: "another update manager error message"
date: 2009-01-15
forum: New to Ubuntu
---

### Post by rburkartjo on 2009-01-15
when i click on the update manager i get this error message

E: Archive directory /var/cache/apt/archives/partial is missing.

how can i fix/tks cheesemaker

---

### Post by Crafty Kisses on 2009-01-15
Try the following:
```
cd /var/cache/apt
```
Type the following to make sure the archive folders are displayed:
```
ls
```
Then if you don't see archives, you can make the directory:
```
sudo mkdir archives
```
Navigate to the archives directory:
```
cd archives
```
Then you need to create the partial folder by running the following:
```
sudo mkdir partial
```
Then make sure you clean up the package manager to make sure everything is up and running:
```
sudo apt-get autoclean
```

---

### Post by rburkartjo on 2009-01-15
code what did i do wrong

ray@ray-desktop:~$ sudo mkdir archives
ray@ray-desktop:~$ cd archives
ray@ray-desktop:~/archives$ sudo mkdir partial
ray@ray-desktop:~/archives$ sudo apt-get autoclean
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to read /var/cache/apt/archives/partial/ - opendir (2 No such file or directory)
ray@ray-desktop:~/archives$ 
/tks cheesemaker

---

### Post by rburkartjo on 2009-01-15
code got it working been a long day must be tired tks for your help/cheesemaker

---

