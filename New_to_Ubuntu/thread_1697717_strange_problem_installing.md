---
title: "strange problem installing"
date: 2011-03-01
forum: New to Ubuntu
---

### Post by vivek.pandey on 2011-03-01
hi everyone
it seems i have a lot of troubles installing anything
i tried to install nasm in my lapi through terminal and got following error report

root@NEO:/home/vivek# sudo apt-get install nasm

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  nasm
0 upgraded, 1 newly installed, 0 to remove and 14 not upgraded.
Need to get 0B/1031kB of archives.
After this operation, 2863kB of additional disk space will be used.
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = "en_US:en",
	LC_ALL = (unset),
	LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
Selecting previously deselected package nasm.
(Reading database ... 307689 files and directories currently installed.)
Unpacking nasm (from .../nasm_2.08.01-1_i386.deb) ...
Processing triggers for man-db ...
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = "en_US:en",
	LC_ALL = (unset),
	LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = "en_US:en",
	LC_ALL = (unset),
	LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
/usr/bin/mandb: can't set the locale; make sure $LC_* and $LANG are correct
Processing triggers for doc-base ...
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = "en_US:en",
	LC_ALL = (unset),
	LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
Processing 1 added doc-base file(s)...
Registering documents with scrollkeeper...
Processing triggers for install-info ...
Setting up nasm (2.08.01-1) ...


does anybody know what is it?

thanx in advance

---

### Post by Hippytaff on 2011-03-01
Try doing ```
sudo apt-get update && sudo apt-get upgrade
``` if no luck try
```
sudo apt-get install -f
``` If still no luck try```
sudo dpkg --configure -a
```
 
If this doesn't sort it you may need to reinstal perl

---

### Post by Verbeck on 2011-03-01
try the solution here >> [http://ubuntuforums.org/showthread.php?t=1346581](http://ubuntuforums.org/showthread.php?t=1346581)

```

sudo locale-gen en_US.UTF-8
sudo dpkg-reconfigure locales

```

---

### Post by Hippytaff on 2011-03-01
> **Verbeck said:**
> try the solution here >> [http://ubuntuforums.org/showthread.php?t=1346581](http://ubuntuforums.org/showthread.php?t=1346581)
 
```

sudo locale-gen en_US.UTF-8
sudo dpkg-reconfigure locales

```
 
Actually that would make more sense

---

### Post by vivek.pandey on 2011-03-01
> **Verbeck said:**
> try the solution here >> [http://ubuntuforums.org/showthread.php?t=1346581](http://ubuntuforums.org/showthread.php?t=1346581)

```

sudo locale-gen en_US.UTF-8
sudo dpkg-reconfigure locales

```

i tried this and then tried to install but i am getting this error

E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

i know this means somewhere a process which requires authentication is running but mystery is i cant locate it right now only google chrome is running no other process

---

### Post by Verbeck on 2011-03-01
run* ps aux  | egrep -i 'apt|dpkg' * to see which processes might be using it and kill them.
then run[I] sudo rm -f /var/lib/dpkg/lock

[/I]edit: OR*; *just reboot the system and try again

---

