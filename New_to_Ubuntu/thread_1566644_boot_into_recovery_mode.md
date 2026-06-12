---
title: "boot into recovery mode"
date: 2010-09-02
forum: New to Ubuntu
---

### Post by spillage2 on 2010-09-02
Hi,

I have a problem with broken packages and have read that these could be fixed by using to grub menu before gnome loads.

I have tried lots of thing to get this to boot but have failed very badly.

was setting up apache2 php5 mysql and phpmyadmin.

the last cause lots of probs so i tried to remove all of them and now it got messy.

cant install or remove any of them.

cheers

spill.

---

### Post by colobix on 2010-09-02
Go to synaptic and click edit > repair broken packages.
It's that simple actually.

---

### Post by spillage2 on 2010-09-02
thanks for your help. have run that but when i run the software centre it get this. i have tried installing apache2 and uninstalling but and banging my head against a wall.

installArchives() failed: W: Duplicate sources.list entry lucid/partner Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_lucid_partner_binary-i386_Packages) 
Selecting previously deselected package libmikmod2. 
(Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 158815 files and directories currently installed.) 
Unpacking libmikmod2 (from .../libmikmod2_3.1.11-a-6.1_i386.deb) ... 
Selecting previously deselected package libsmpeg0. 
Unpacking libsmpeg0 (from .../libsmpeg0_0.4.5+cvs20030824-2.2_i386.deb) ... 
Selecting previously deselected package libsdl-mixer1.2. 
Unpacking libsdl-mixer1.2 (from .../libsdl-mixer1.2_1.2.8-6build1_i386.deb) ... 
Selecting previously deselected package abe-data. 
Unpacking abe-data (from .../abe-data_1.1-3_all.deb) ... 
Selecting previously deselected package abe. 
Unpacking abe (from .../archives/abe_1.1-3_i386.deb) ... 
Processing triggers for man-db ... 
Processing triggers for desktop-file-utils ... 
Processing triggers for python-gmenu ... 
Rebuilding /usr/share/applications/desktop.en_GB.UTF8.cache... 
Processing triggers for python-support ... 
Setting up apache2.2-common (2.2.14-5ubuntu ... 
ERROR: Module reqtimeout does not exist! 
dpkg: error processing apache2.2-common (--configure): 
 subprocess installed post-installation script returned error exit status 1 
dpkg: dependency problems prevent configuration of apache2-mpm-itk: 
 apache2-mpm-itk depends on apache2.2-common (= 2.2.14-5ubuntu; however: 
  Package apache2.2-common is not configured yet. 
dpkg: error processing apache2-mpm-itk (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of apache2: 
 apache2 depends on apache2-mpm-worker (= 2.2.14-5ubuntu | apache2-mpm-prefork (= 2.2.14-5ubuntu | apache2-mpm-event (= 2.2.14-5ubuntu | apache2-mpm-itk (= 2.2.14-5ubuntu; however: 
  Package apache2-mpm-worker is not installed. 
  Package apache2-mpm-prefork is not installed. 
  Package apache2-mpm-event is not installed. 
  Package apache2-mpm-itk is not configured yet. 
 apache2 depends on apache2.2-common (= 2.2.14-5ubuntu; however: 
  Package apache2.2-common is not configNo apport report written because the error message indicates its a followup error from a previous failure.
No apport report written because the error message indicates its a followup error from a previous failure.
No apport report written because MaxReports is reached already
ured yet. 
dpkg: error processing apache2 (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libapache2-mod-php5: 
 libapache2-mod-php5 depends on apache2-mpm-prefork (>> 2.0.52) | apache2-mpm-itk; however: 
  Package apache2-mpm-prefork is not installed. 
  Package apache2-mpm-itk is not configured yet. 
 libapache2-mod-php5 depends on apache2.2-common; however: 
  Package apache2.2-common is not configured yet. 
dpkg: error processing libapache2-mod-php5 (--configure): 
 dependency problems - leaving unconfigured 
Setting up libmikmod2 (3.1.11-a-6.1) ... 
 
Setting up libsmpeg0 (0.4.5+cvs20030824-2.2) ... 
 
Setting up libsdl-mixer1.2 (1.2.8-6build1) ... 
 
Setting up abe-data (1.1-3) ... 
Setting up abe (1.1-3) ... 
 
Processing triggers for libc-bin ... 
ldconfig deferred processing now taking place 
Errors were encountered while processing: 
 apache2.2-common 
 apache2-mpm-itk 
 apache2 
 libapache2-mod-php5 
Setting up apache2.2-common (2.2.14-5ubuntu ... 
ERROR: Module reqtimeout does not exist! 
dpkg: error processing apache2.2-common (--configure): 
 subprocess installed post-installation script returned error exit status 1 
dpkg: dependency problems prevent configuration of libapache2-mod-php5: 
 libapache2-mod-php5 depends on apache2.2-common; however: 
  Package apache2.2-common is not configured yet. 
dpkg: error processing libapache2-mod-php5 (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of apache2-mpm-itk: 
 apache2-mpm-itk depends on apache2.2-common (= 2.2.14-5ubuntu; however: 
  Package apache2.2-common is not configured yet. 
dpkg: error processing apache2-mpm-itk (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of apache2: 
 apache2 depends on apache2-mpm-worker (= 2.2.14-5ubuntu | apache2-mpm-prefork (= 2.2.14-5ubuntu | apache2-mpm-event (= 2.2.14-5ubuntu | apache2-mpm-itk (= 2.2.14-5ubuntu; however: 
  Package apache2-mpm-worker is not installed. 
  Package apache2-mpm-prefork is not installed. 
  Package apache2-mpm-event is not installed. 
  Package apache2-mpm-itk is not configured yet. 
 apache2 depends on apache2.2-common (= 2.2.14-5ubuntu; however: 
  Package apache2.2-common is not configured yet. 
dpkg: error processing apache2 (--configure): 
 dependency problems - leaving unconfigured

---

