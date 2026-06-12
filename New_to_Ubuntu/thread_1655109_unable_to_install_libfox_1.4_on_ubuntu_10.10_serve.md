---
title: "unable to install libfox 1.4 on ubuntu 10.10 server"
date: 2010-12-29
forum: New to Ubuntu
---

### Post by nelthatec on 2010-12-29
I am installing Cafecon Leche on ubuntu 10.10 and this is the message I am getting while installing Libfox 1.4:

nelthatec3@nelthatec3:~$ sudo apt-get install libfox1.4 libfox1.4-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package libfox1.4
E: Couldn't find any package by regex 'libfox1.4'
E: Unable to locate package libfox1.4-dev
E: Couldn't find any package by regex 'libfox1.4-dev'
nelthatec3@nelthatec3:~$ 

I have updated the software, and installed Java runtime.

Please help.

---

### Post by qamelian on 2010-12-29
Ubuntu 10.10 doesn't include libfox 1.4. Only libfox 1.6 is in the repos. the package name is libfox-1.6-0. You can find this info from the cli by typing:

```
apt-cache search libfox
```

---

### Post by nelthatec on 2010-12-29
> **qamelian said:**
> Ubuntu 10.10 doesn't include libfox 1.4. Only libfox 1.6 is in the repos. the package name is libfox-1.6-0. You can find this info from the cli by typing:

```
apt-cache search libfox
```
Thanks, will try libfox 1.6. hope it will work on cafe con leche.

---

