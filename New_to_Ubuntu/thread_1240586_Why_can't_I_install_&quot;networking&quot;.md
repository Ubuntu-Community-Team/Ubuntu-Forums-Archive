---
title: "Why can't I install &quot;networking&quot;?"
date: 2009-08-14
forum: New to Ubuntu
---

### Post by tahitiwibble on 2009-08-14
Can someone please help me with this;

```
dad@dad-desktop:~$ network-admin
The program 'network-admin' is currently not installed.  You can install it by typing:
sudo apt-get install gnome-network-admin
bash: network-admin: command not found
dad@dad-desktop:~$ sudo apt-get install gnome-network-admin
[sudo] password for dad: 
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
dad@dad-desktop:~$ sudo apt-get install gnome-network-admin
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
dad@dad-desktop:~$
```

---

### Post by tahitiwibble on 2009-08-14
SOLVED - Synaptic did it OK .......... strange.

---

### Post by HotShotDJ on 2009-08-14
Just for future reference... the error you had in the terminal means that you had a software installer (Synaptic Package Manager, Add/Remove Software, Update Manager, gDebi) running.  You cannot use more than one deb installer at a time.

---

