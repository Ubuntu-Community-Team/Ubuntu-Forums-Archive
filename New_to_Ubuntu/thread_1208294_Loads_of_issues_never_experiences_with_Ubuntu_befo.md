---
title: "Loads of issues never experiences with Ubuntu before"
date: 2009-07-09
forum: New to Ubuntu
---

### Post by haze. on 2009-07-09
I was updating from my LiveCD 7.10 to the newest version using the 'Update Manager' and while updating received countless errors regarding unmet dependencies...

I have tried installing amarok and assume I am running into the same errors.  Any idea how to fix these dependencies?  I have tried a few forum answers and nothing seems to fix the problems.  I really do not want to install back to 7.10.

Here is the error I get when runing 'sudo aptitude install amarok'

***************************************************

sudo aptitude install amarok
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages are BROKEN:
  amarok amarok-xine libopenexr2ldbl perl-suid x11-xserver-utils 
The following NEW packages will be automatically installed:
  iceauth kamera kdebase-bin kdebase-kio-plugins kdelibs-bin kdelibs-data 
  kdelibs4c2a kdemultimedia-kio-plugins kdesktop libarts1c2a libartsc0 
  libaudio2 libavahi-qt3-1 libdbus-1-2 libdbus-qt-1-1c2 libflac7 
  libgnutls12 libifp4 libjasper-1.701-1 libkcddb1 libkonq4 liblzo1 
  libmysqlclient15off libnjb5 libopenexr2c2a libpq4 libqt3-mt libruby1.8 
  libsasl2 libsasl2-modules-sql libtasn1-2 libtasn1-2-bin mysql-common 
  pmount ruby ruby1.8 
The following packages have been kept back:
  poppler-utils 
The following NEW packages will be installed:
  iceauth kamera kdebase-bin kdebase-kio-plugins kdelibs-bin kdelibs-data 
  kdelibs4c2a kdemultimedia-kio-plugins kdesktop libarts1c2a libartsc0 
  libaudio2 libavahi-qt3-1 libdbus-1-2 libdbus-qt-1-1c2 libflac7 
  libgnutls12 libifp4 libjasper-1.701-1 libkcddb1 libkonq4 liblzo1 
  libmysqlclient15off libnjb5 libopenexr2c2a libpq4 libqt3-mt libruby1.8 
  libsasl2 libsasl2-modules-sql libtasn1-2 libtasn1-2-bin mysql-common 
  pmount ruby ruby1.8 
0 packages upgraded, 39 newly installed, 0 to remove and 1 not upgraded.
Need to get 42.7MB of archives. After unpacking 126MB will be used.
The following packages have unmet dependencies:
  libopenexr2ldbl: Conflicts: libopenexr2c2a but 1.2.2-4ubuntu2 is to be installed.
  x11-xserver-utils: Conflicts: iceauth but 1:1.0.1-0ubuntu2 is to be installed.
  perl-suid: Depends: perl (= 5.8.7-10ubuntu1.2) but 5.8.8-12ubuntu0.4 is installed.
             Depends: libperl5.8 (= 5.8.7-10ubuntu1.2) but 5.8.8-12ubuntu0.4 is installed.
  amarok-xine: Depends: kdelibs4c2a (>= 4:3.5.8-1) but 4:3.5.2-0ubuntu18.6 is to be installed.
               Depends: libxine1 (>= 1.1.8) which is a virtual package.
  amarok: Depends: kdelibs4c2a (>= 4:3.5.8-1) but 4:3.5.2-0ubuntu18.6 is to be installed.
          Depends: libmp4v2-0 (>= 1:1.6dfsg) but it is not installable
          Depends: libmysqlclient15off (>= 5.0.27-1) but 5.0.22-0ubuntu6.06.11 is to be installed.
          Depends: libpq5 (>= 8.3~beta1) which is a virtual package.
          Depends: libqt3-mt (>= 3:3.3.8-b) but 3:3.3.6-1ubuntu6.4 is to be installed.
          Depends: libruby1.8 (>= 1.8.6.111) but 1.8.4-1ubuntu1.6 is to be installed.
          Depends: libtunepimp5 which is a virtual package.
Resolving dependencies...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
amarok [Not Installed]
amarok-xine [Not Installed]
iceauth [Not Installed]
kamera [Not Installed]
kdebase-bin [Not Installed]
kdebase-kio-plugins [Not Installed]
kdelibs-bin [Not Installed]
kdelibs4c2a [Not Installed]
kdemultimedia-kio-plugins [Not Installed]
kdesktop [Not Installed]
libarts1c2a [Not Installed]
libkcddb1 [Not Installed]
libkonq4 [Not Installed]
libopenexr2c2a [Not Installed]
perl-suid [Not Installed]

Score is -9755

Accept this solution? [Y/n/q/?] y
The following packages have been kept back:
  poppler-utils 
0 packages upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done   


***************************************************

Any ideas?  I need a fix.  Nothing is updating or installing.

Thanks!

---

### Post by Paqman on 2009-07-09
> **haze. said:**
> I was updating from my LiveCD 7.10 to the newest version using the 'Update Manager'


I've never tried that, but i'm not sure that it will work. The latest version of Ubuntu is 9.04. The upgrade path from 7.10 would go like:

7.10 > 8.04 > 8.10 > 9.04

So you'd have to upgrade three times (although you could stop at 8.04 since it's an LTS release) It would be a lot easier just to back up your data and reinstall with 9.04 than it would to do a whole chain of upgrades.

---

