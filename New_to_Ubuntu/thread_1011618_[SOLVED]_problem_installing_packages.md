---
title: "[SOLVED] problem installing packages"
date: 2008-12-14
forum: New to Ubuntu
---

### Post by anirup on 2008-12-14
sudo dpkg -i bsc.deb
(Reading database ... dpkg: error processing bsc_2.27-2_i386.deb (--install):
 files list file for package `umbrello' is missing final newline
Errors were encountered while processing:
 bsc_2.27-2_i386.deb
Processing was halted because there were too many errors.

sudo dpkg -i install_flash_player_10_linux.deb 
(Reading database ... dpkg: error processing install_flash_player_10_linux.deb (--install):
 files list file for package `umbrello' is missing final newline
Errors were encountered while processing:
 install_flash_player_10_linux.deb
Processing was halted because there were too many errors.

**[B]whenever i try to install a package i get the above error.umbrello is working fine.i installed it long time back.and i had installed many packages after that but why this problem.the problem started after i tried to reinstall adobe flashplayer.**[/B]

---

### Post by dwasifar on 2008-12-15
I don't know what umbrello is, but the first step I would try would be to remove (or purge) it and reinstall it, preferably from the repos and not from a .deb.

---

### Post by anirup on 2008-12-15
**i not able to remove also.same message is displayed.**

---

### Post by dwasifar on 2008-12-15
> **anirup said:**
> **i not able to remove also.same message is displayed.**

Try reinstalling umbrello in Synaptic then.

---

### Post by anirup on 2008-12-15
**[B]i am not able to do any installation,uninstallation or reinstallation**[/B]

---

### Post by dwasifar on 2008-12-15
The only other things I can recommend you try are these:

```
sudo dpkg --configure -a
sudo apt-get install -f
```

Beyond that, I don't have a ready answer.  I'll look around though.

---

### Post by anirup on 2008-12-15
**[B]i tried all of them.**[/B]

---

### Post by Ender41 on 2008-12-15
> **anirup said:**
> **[B]i tried all of them.**[/B]


 Have you tried adding a newline to the end of the umbrello.list file ?
You will find it in /var/lib/dpkg/info

Ender

---

### Post by anirup on 2008-12-15
**[B]u are great**[/B]

---

