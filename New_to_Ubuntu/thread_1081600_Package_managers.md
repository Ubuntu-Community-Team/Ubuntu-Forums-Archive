---
title: "Package managers"
date: 2009-02-26
forum: New to Ubuntu
---

### Post by DarkSaga70 on 2009-02-26
I am getting this msg when trying to use a package manager and I even rebooted.....
betty@betty-desktop:~$ sudo apt-get install ubuntu-restricted-extras
[sudo] password for betty:
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
betty@betty-desktop:~$ sudo apt-get install ubuntu-restricted-extras
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
betty@betty-desktop:~$

PLease help.

---

### Post by howefield on 2009-02-26
Close all running package managers and try again.

---

### Post by avtolle on 2009-02-26
Do you have any of the above open: Synaptic Package Manager, Add/Remove Programs. If so, close it and retry.

If you have earlier received a message advising you to run "dpkg --configure -a", dpkg is open; run```
sudo dpkg --configure -a
```(dpkg is another way to manage packages).

---

### Post by DarkSaga70 on 2009-02-26
> **howefield said:**
> Close all running package managers and try again.

I rebooted the computer and nothing is running but i still get this msg.

---

### Post by DarkSaga70 on 2009-02-26
fixed thanks bunches

---

