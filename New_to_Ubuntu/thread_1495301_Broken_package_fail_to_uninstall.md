---
title: "Broken package fail to uninstall"
date: 2010-05-27
forum: New to Ubuntu
---

### Post by frozenflames on 2010-05-27
**Broken package fail to uninstall** 			
 			 			 		   		 		 		[SIZE=2][B]i  am Ubuntu rookie i installed the following package onboard (Simple  On-screen Keyboard with macros and easy layout creation) when i try to  uninstall it using Synaptic Package manger i get the following error
[/B][/SIZE][SIZE=2][B]
dpkg: parse error, in file '/var/lib/dpkg/status' near  line 26430:
 invalid package name (character `|' not allowed (only letters, digits   and characters `-+._'))
  [/B][/SIZE]
[SIZE=2][B]:confused:and when i try to  configure it get the same error any help :confused:
msi@msi-desktop:~$ sudo dpkg --configure[/B] -a

[B]dpkg: parse error, in file '/var/lib/dpkg/status' near line 26430:
 invalid package name (character `|' not allowed (only letters, digits  and characters `-+._'))
[/B][/SIZE]using Ubuntu 10.4

---

### Post by Ozymandias_117 on 2010-05-27
Can you post the output of ```
head -26430 /var/lib/dpkg/status | tail
```

---

### Post by frozenflames on 2010-05-27
Version: 1.1.4-1ubuntu1
Depends: python (>= 2.4), python-support (>= 0.90.0), python-lazr.uri
Description: Python library for navigating WADL files
 The Web Application Description Language (WADL) is an XML vocabulary for
 describing the capabilities of HTTP resources. wadllib can be used in
 conjunction with an HTTP library to navigate and manipulate those resources.
Original-Maintainer: Debian Python Modules Team <python-modules-team@lists.alioth.debian.org>
Homepage: [https://launchpad.net/wadllib](https://launchpad.net/wadllib)

Package: python-vir|key

---

### Post by Ozymandias_117 on 2010-05-27
Try this...
```
sudo cp /var/lib/dpkg/status /var/lib/dpkg/status.bak
gksu gedit /var/lib/dpkg/status
``` then click "Search -> Go to Line" and enter 26430 then change ```
python-vir|key
``` to ```
python-virtkey
```
Save and exit.

Afterwards try ```
sudo aptitude update
``` then try to remove your program.


If something breaks you can just use ```
sudo cp /var/lib/dpkg/status.bak /var/lib/dpkg/status
```

There may be an easier way to do this... But this should work.

---

### Post by frozenflames on 2010-05-27
it worked sort of but still 

msi@msi-desktop:~$ sudo dpkg --configure -a

dpkg: parse error, in file '/var/lib/dpkg/available' near line 27363:
 invalid package name (character `|' not allowed (only letters, digits and characters `-+._'))

i want to remove onboard it wont install and when i try to uninstall same thing but with one less error :)

---

### Post by Ozymandias_117 on 2010-05-27
> **frozenflames said:**
> 
dpkg: parse error, in file '/var/lib/dpkg/available' near line 27363:
 invalid package name (character `|' not allowed (only letters, digits and characters `-+._'))

Ok, now ```
head -27363 /var/lib/dpkg/available | tail
```

---

### Post by frozenflames on 2010-05-27
msi@msi-desktop:~$ head -27363 /var/lib/dpkg/available | tail
  - google-account-setup
  - sa-junk-plugin
  - bogo-junk-plugin
  - exchange-operations
  - mono
  - webdav-account-setup
Homepage: [http://www.gnome.org/projects/evolution/](http://www.gnome.org/projects/evolution/)
Original-Maintainer: Debian Evolution Maintainers <pkg-evolution-maintainers@lists.alioth.debian.org>

---

### Post by frozenflames on 2010-05-27
msi@msi-desktop:~$ head -27363 /var/lib/dpkg/available | tail
  - google-account-setup
  - sa-junk-plugin
  - bogo-junk-plugin
  - exchange-operations
  - mono
  - webdav-account-setup
Homepage: [http://www.gnome.org/projects/evolution/](http://www.gnome.org/projects/evolution/)
Original-Maintainer: Debian Evolution Maintainers <pkg-evolution-maintainers@lists.alioth.debian.org>

Package: python-vir|key

---

### Post by Ozymandias_117 on 2010-05-27
```
sudo cp /var/lib/dpkg/available /var/lib/dpkg/available.bak
gksu gedit /var/lib/dpkg/available
``` then click "Search -> Go to Line" and enter 27363 then change ```
python-vir|key
``` to ```
python-virtkey
```
Save and exit.

Try ```
sudo aptitude update
``` then try to remove your program again.

---

### Post by frozenflames on 2010-05-27
:KSIt worked finally it worked thank You so much:KS

:):):):):)

---

### Post by Ozymandias_117 on 2010-05-27
No problem :)

Please remember to go to Thread Tools at the top of the thread and hit "Mark as Solved" when your problems have been resolved.

---

### Post by hectoralex on 2010-05-28
Hello, new user here with a similar problem... I don't mean to HIJACK this thread but I figured it is similar.  I am running 10.04 LTR and encountered this problem during upgrade to 10.04...

"@ASUS-AMD64:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up python-lazr.uri (1.0.2-1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing python-lazr.uri (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 python-lazr.uri
E: Sub-process /usr/bin/dpkg returned an error code (1)"

Your help is appreciated!


> **Ozymandias_117 said:**
> No problem :)

Please remember to go to Thread Tools at the top of the thread and hit "Mark as Solved" when your problems have been resolved.

---

