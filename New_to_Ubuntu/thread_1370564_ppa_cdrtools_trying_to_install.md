---
title: "ppa cdrtools trying to install"
date: 2010-01-02
forum: New to Ubuntu
---

### Post by klein de usa on 2010-01-02
hi 
i'm trying to install cdrtools from ([https://launchpad.net/~ubuntu-burning/+archive/ppa](https://launchpad.net/~ubuntu-burning/+archive/ppa)) i think i did everything right added the repositories and the server key, then i went to Synaptic Package Manager and searched for cdrtools and it came up blank, no package ????????????   i also searched out smake and it did come up and i installed it. so how do i install cdrtools from the ppa????? 


2.6.24-26-generic #1 SMP Tue Dec 1 17:55:03 UTC 2009 x86_64 GNU/Linux

---

### Post by spcwingo on 2010-01-02
Have you updated the package lists since you added the ppa?  Just to be sure run this command in a terminal:

```
sudo apt-get update
```

To see if that fixed it, while in the terminal, run this command:

```
apt-cache search cdrtools
```

---

### Post by klein de usa on 2010-01-04
hi 
thank you spcwingo, but for some reason that didn't work either. i did find the answer in link [http://ubuntuforums.org/showthread.php?t=851707]("http://ubuntuforums.org/showthread.php?t=851707") post #5 . this worked like a charm !!! so this can be marked solved

---

