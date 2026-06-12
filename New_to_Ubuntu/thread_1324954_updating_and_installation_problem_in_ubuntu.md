---
title: "updating and installation problem in ubuntu"
date: 2009-11-13
forum: New to Ubuntu
---

### Post by zainflameworker7 on 2009-11-13
i just installed ubuntu 9.10 removing vista completely as i didn't wanted a dual boot but after a week i'm having a lot of problem first is the update manager does not update although it was updating befpre but now whenever i try to update i get the following message:

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

plus i cannot install the deb packages Ubuntu was installing them before but now i cannot install them i get the following message:

only one software management tool is allowed to run at same time
please close the other application e.g.'Update Manager','aptitude, or ' Synaptic' first

please help i'm new to Ubuntu and Linux so i don't have knowledge about its command line or any programming language

---

### Post by coldReactive on 2009-11-13
System > Administration > System Monitor > Processes Tab

Are synaptic, update-manager, aptitude, apt, etc. running? If so, right-click them and kill them.

---

### Post by jimmy the saint on 2009-11-13
> i just installed ubuntu 9.10 removing vista completely as i didn't wanted a dual boot but after a week i'm having a lot of problem first is the update manager does not update although it was updating befpre but now whenever i try to update i get the following message:

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.
E: _cache->open() failed, please report.

Open a terminal Applications>accessories>terminal, and type in 
```
sudo dpkg --configure -a
```

to correct the problem.

---

### Post by zainflameworker7 on 2009-11-13
thanks for the help my problem is solved

---

### Post by coldReactive on 2009-11-13
> **zainflameworker7 said:**
> thanks for the help my problem is solved

How did you solve it?

---

### Post by zainflameworker7 on 2009-11-13
i tried it [coldReactive]("http://ubuntuforums.org/member.php?u=813221") method but couldnt find anything but then i tried [jimmy the saint]("http://ubuntuforums.org/member.php?u=375437") method and it worked so now everything is working normally

---

