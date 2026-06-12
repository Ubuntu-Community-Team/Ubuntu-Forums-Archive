---
title: "Error while updating"
date: 2010-04-26
forum: New to Ubuntu
---

### Post by Kosimo on 2010-04-26
Hello Guys, 

I am using Lucid Lynx, and after a normal update this is what the system says...

> sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up mfc9880lpr (1.1.2-1) ...
/var/lib/dpkg/info/mfc9880lpr.postinst: 4: /etc/init.d/lpd: not found
dpkg: error processing mfc9880lpr (--configure):
 subprocess installed post-installation script returned error exit status 127
Errors were encountered while processing:
 mfc9880lpr
E: Sub-process /usr/bin/dpkg returned an error code (1)



Any idea about how to fix this?  I've already tried sudo apt-get -f install or sudo dpkg --configure  But nothing works.

Thank you!

---

### Post by Kosimo on 2010-04-26
mfc9880lpr was a brother driver I was trying to install last week, now I can't remove it, either by using sudo apt-get remove mfc9880lpr or in synaptic... This is the output
> 
E: mfc9880lpr: subprocess installed post-removal script returned error exit status 127


---

### Post by Kosimo on 2010-04-26
Still trying to remove the broken package....  But nothing:

>  sudo dpkg --configure -a
cosimo@cosimo-laptop:~$ >sudo apt-get install -f
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
cosimo@cosimo-laptop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  mfc9880lpr
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 146285 files and directories currently installed.)
Removing mfc9880lpr ...
/var/lib/dpkg/info/mfc9880lpr.postrm: 3: /etc/init.d/lpd: not found
dpkg: error processing mfc9880lpr (--remove):
 subprocess installed post-removal script returned error exit status 127
Errors were encountered while processing:
 mfc9880lpr
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Kosimo on 2010-04-26
Please helpp... :( I am in the office and can't install anything...

---

### Post by Soul-Sing on 2010-04-26
please close all -apt/synaptic/add-remove/dpkg
```
gksudo nautilus
```
navigate via nautilus to: var/lib/dpkg/info
use: search option: find mfc9880lpr and remove it. close nautilus

```
sudo apt-get update
```

---

### Post by Kosimo on 2010-04-26
> **leoquant said:**
> please close all -apt/synaptic/add-remove/dpkg
```
gksudo nautilus
```
navigate via nautilus to: var/lib/dpkg/info
use: search option: find mfc9880lpr and remove it. close nautilus

```
sudo apt-get update
```


Absolutely amazing.  It worked.   Thank you so much. ;)

---

