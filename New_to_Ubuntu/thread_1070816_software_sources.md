---
title: "software sources"
date: 2009-02-15
forum: New to Ubuntu
---

### Post by 16sinker on 2009-02-15
In Software Sources/update tab I can't tick the option Recommended updates/intrepid updates. Why? I'm able to check my other options.

---

### Post by Partyboi2 on 2009-02-16
Try enabling it in your sources.list file. If unsure how to make the changes to your /etc/apt/sources.list file then open a terminal (Applications>Accessories>Terminal) and post the output to
```
cat /etc/apt/sources.list
```

---

### Post by 16sinker on 2009-03-01
Here is the output of the sources.list.bofus66@ubuntudell:~$ cat /etc/apt/sources.list
  
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid restricted universe multiverse main
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-backports restricted universe multiverse main
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-proposed restricted universe multiverse main
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-security restricted universe multiverse main
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-updates restricted main multiverse intrepid universe
deb-src [http://ppa.launchpad.net/tualatrix/ubuntu](http://ppa.launchpad.net/tualatrix/ubuntu) intrepid main
deb [http://ppa.launchpad.net/tualatrix/ubuntu](http://ppa.launchpad.net/tualatrix/ubuntu) intrepid main

deb [http://ppa.launchpad.net/ubuntu-tweak-testing/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-tweak-testing/ppa/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/ubuntu-tweak-testing/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-tweak-testing/ppa/ubuntu) intrepid main
bofus66@ubuntudell:~$ 
Sorry to be so slow to reply.

---

### Post by 16sinker on 2009-03-01
This problem was solved with an /etc/apt/sources.list edit and apt-get update on another thread in General Help. Thanks again Forger.

---

