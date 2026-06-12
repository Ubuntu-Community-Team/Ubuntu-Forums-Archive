---
title: "a problem in ubuntu 7.10"
date: 2008-03-31
forum: Networking &amp; Wireless
---

### Post by thiensa on 2008-03-31
hi when i run terminal, have a message show
thiensa@thiensa:~$ sudo apt-get install aircrack-ng
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using 
i don't repair that, help me

---

### Post by daengbo on 2008-03-31
You probably have another package manager running. Check for synaptic, Add/ Remove or the update manager. If you are SURE you don't have anything running, open a terminal and type
sudo rm /var/lib/dpkg/lock
That will get rid of the package system lock which you have on for some reason. It's possible you killed a process or rebooted during an installation.

Daeng

---

### Post by thiensa on 2008-03-31
i try same you talk but not complete, another reason

---

### Post by thiensa on 2008-03-31
thiensa@thiensa:/tmp$ sudo apt-get install aircrack-ng-0.9.0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package aircrack-ng-0.9.0
thiensa@thiensa:/tmp$ 
so, now its show same above, i don't know the line ": Couldn't find package aircrack-ng-0.9.0" meaning

---

### Post by mlentink on 2008-03-31
It means that this particular package is not in the repositories you have enabled in Ubuntu. You could try downloading and installing it from the site of its developer.

---

