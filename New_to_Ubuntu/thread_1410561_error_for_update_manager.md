---
title: "error for update manager"
date: 2010-02-18
forum: New to Ubuntu
---

### Post by ub newb on 2010-02-18
the package manager kept saying I had broken dependencies when I have tried to do updates for the last couple months, and then doesn't do the installing.  I was going to try to upgrade Hardy to 8.10 to see if that would fix it. I started the process but then chickened out when I read of all the problems people ran into doing this from the update manager and cancelled the upgrade. I also figured I'd better fix the broken dependencies before I attempted the upgrade. Now the update manager has quit working entirely and I get this error message: 

Could not initialize the package information



A unresolvable problem occurred while initializing the package information.



Please report this bug against the 'update-manager' package and include the following error message:



'E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.'

Is there any help for this? Should I be asking this somewhere else? 

Thanks:?

---

### Post by zvacet on 2010-02-19
```
sudo apt-get dist-upgrade
```

---

### Post by ub newb on 2010-02-19
thank you for your reply. Would you please clarify what this code is for? Is it to fix the update manager problem, or is it to access the upgrade to 8.10 or both?

---

### Post by zvacet on 2010-02-19
> 'E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

Command I posted should install held packages.That maybe fix your problem.

---

### Post by ub newb on 2010-02-20
I have tried as you suggested and got this result: 

XXXXXXXx@MDdesktop:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  cpp-4.2: Depends: gcc-4.2-base (= 4.2.4-1ubuntu3) but 4.2.4-1ubuntu4 is installed
  gcc-4.2: Depends: gcc-4.2-base (= 4.2.4-1ubuntu3) but 4.2.4-1ubuntu4 is installed
  libffi4: Depends: gcc-4.2-base (= 4.2.4-1ubuntu3) but 4.2.4-1ubuntu4 is installed
  libnss3-dev: Depends: libnspr4-dev but it is not installable
E: Unmet dependencies. Try using -f.
XXXXXXXXX@MDdesktop:~$ -f
bash: -f: command not found
XXXXXXXXX@MDdesktop:~$ apt-get -f install
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

Do I have to continue this as root, start over as root user? My knowledge base regarding linux is about non-existent

---

### Post by prismpirate on 2010-02-20
Try 

```
sudo apt-get -f install
```

You should be required to run in root.

---

### Post by ub newb on 2010-02-20
XXXXXXX@MDdesktop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... failed.
The following packages have unmet dependencies:
  cpp-4.2: Depends: gcc-4.2-base (= 4.2.4-1ubuntu3) but 4.2.4-1ubuntu4 is installed
  gcc-4.2: Depends: gcc-4.2-base (= 4.2.4-1ubuntu3) but 4.2.4-1ubuntu4 is installed
  libffi4: Depends: gcc-4.2-base (= 4.2.4-1ubuntu3) but 4.2.4-1ubuntu4 is installed
  libnss3-dev: Depends: libnspr4-dev but it is not installable
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies


yuk, any more ideas?

---

### Post by ub newb on 2010-02-21
broken dependencies as listed in Synaptic Package Manager: 

cpp-4.2      installed 4.2.4-1ubuntu 
gcc-4.2                  "
libffi4                  "
libnss3-dev           3.12.3.1 0ubuntu

latest version listed is the same as that installed

The only options that aren't greyed out for these items are "mark for complete removal" or "unmark." Clicking either unmark or mark for complete removal brings up a message with a list of at least 50-60  things that will also be removed! I don't know what they are, things like gnome keyring, gnome terminal? This sounds like I am killing my machine. 

Any help? :confused:

---

### Post by ub newb on 2010-02-28
bumped up, is there someplace else I should go to get assistance with this? 

thanks

---

### Post by sandyd on 2010-02-28
> **ub newb said:**
> broken dependencies as listed in Synaptic Package Manager: 

cpp-4.2      installed 4.2.4-1ubuntu 
gcc-4.2                  "
libffi4                  "
libnss3-dev           3.12.3.1 0ubuntu

latest version listed is the same as that installed

The only options that aren't greyed out for these items are "mark for complete removal" or "unmark." Clicking either unmark or mark for complete removal brings up a message with a list of at least 50-60  things that will also be removed! I don't know what they are, things like gnome keyring, gnome terminal? This sounds like I am killing my machine. 

Any help? :confused:
```

sudo dpkg --force all --purge cpp-4.2 gcc-4.2 libffi4 libnss3-dev
sudo apt-get install cpp-4.2 gcc-4.2 libffi4 libnss3-dev
```
this might be becasue you stopped the upgrade in the middle... so you now have a half-upgraded system...

---

### Post by ub newb on 2010-03-03
did as you suggested with poor results. 

 sudo dpkg --force all --purge cpp-4.2 gcc-4.2 libffi4 libnss3-dev 
[sudo] password for XXXXX: 
(Reading database ... 168648 files and directories currently installed.) 
Removing libnss3-dev ... 
dpkg: gcc-4.2: dependency problems, but removing anyway as you request: 
 gcc depends on gcc-4.2 (>= 4.2.3-1). 
Removing gcc-4.2 ... 
dpkg: libffi4: dependency problems, but removing anyway as you request: 
 python-notify depends on libffi4 (>= 4.2.1). 
 python-gobject depends on libffi4 (>= 4.1.1-21). 
 python-gtksourceview2 depends on libffi4. 
 deskbar-applet depends on libffi4. 
 python-vte depends on libffi4. 
 python-gnome2-desktop depends on libffi4. 
 totem-gstreamer depends on libffi4. 
 rhythmbox depends on libffi4. 
 python-launchpad-integration depends on libffi4. 
Removing libffi4 ... 
Purging configuration files for libffi4 ... 
dpkg: cpp-4.2: dependency problems, but removing anyway as you request: 
 cpp depends on cpp-4.2 (>= 4.2.3-1). 
Removing cpp-4.2 ... 
Processing triggers for libc6 ... 
ldconfig deferred processing now taking place 
XXXXX@MDdesktop:~$ sudo apt-get install cpp-4.2 gcc-4.2 libffi4 libnss3-dev 
Reading package lists... Done 
Building dependency tree       
Reading state information... Done 
Package cpp-4.2 is not available, but is referred to by another package. 
This may mean that the package is missing, has been obsoleted, or 
is only available from another source 
E: Package cpp-4.2 has no installation candidate 


Now opening synaptic package manager, nothing will upgrade because I still have broken dependencies. The message says fix those first, so I am right back where I started. :popcorn:

---

### Post by ub newb on 2010-03-07
giving this a bump. I haven't a resolution yet. Thanks.

---

### Post by ub newb on 2010-03-12
Can I ask a mod to move this request over to the thread about updating Ubuntu? It's been 3 weeks, and I'm still not able to fix this. 

Thanks

---

