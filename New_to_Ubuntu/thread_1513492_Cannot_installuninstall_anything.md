---
title: "Cannot install/uninstall anything"
date: 2010-06-19
forum: New to Ubuntu
---

### Post by Jawwwwsh on 2010-06-19
Hey guys I'm new to Ubuntu but loving it so far!

I cannot install/uninstall any programs correctly at the moment, this is a fresh install from the ISO downloaded from the website only a few days ago but I get these errors when trying to install programs (so far tryed to install 7zip, Rar and VirtualBox)

```
installArchives() failed: Selecting previously deselected package dkms. 
(Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 149243 files and directories currently installed.) 
Unpacking dkms (from .../dkms_2.1.1.2-2fakesync1_all.deb) ... 
Selecting previously deselected package fakeroot. 
Unpacking fakeroot (from .../fakeroot_1.14.4-1ubuntu1_i386.deb) ... 
Selecting previously deselected package libqt4-network. 
Unpacking libqt4-network (from .../libqt4-network_4%3a4.6.2-0ubuntu5_i386.deb) ... 
Selecting previously deselected package libqt4-opengl. 
Unpacking libqt4-opengl (from .../libqt4-opengl_4%3a4.6.2-0ubuntu5_i386.deb) ... 
Selecting previously deselected package patch. 
Unpacking patch (from .../patch_2.6-2ubuntu1_i386.deb) ... 
Selecting previously deselected package virtualbox-ose. 
Unpacking virtualbox-ose (from .../virtualbox-ose_3.1.6-dfsg-2ubuntu2_i386.deb) ... 
Selecting previously deselected package virtualbox-ose-dkms. 
Unpacking virtualbox-ose-dkms (from .../virtualbox-ose-dkms_3.1.6-dfsg-2ubuntu2_all.deb) ... 
Selecting previously deselected package virtualbox-ose-qt. 
Unpacking virtualbox-ose-qt (from .../virtualbox-ose-qt_3.1.6-dfsg-2ubuntu2_i386.deb) ... 
Processing triggers for man-db ... 
Processing triggers for ureadahead ... 
ureadahead will be reprofiled on next reboot 
Processing triggers for desktop-file-utils ... 
Processing triggers for python-gmenu ... 
Rebuilding /usr/share/applications/desktop.en_GB.UTF8.cache... 
Processing triggers for python-support ... 
Setting up libvlccore2 (1.0.6-1ubuntu1.1) ... 
dpkg (subprocess): unable to execute installed post-installation script: Exec format error 
dpkg: error processing libvlccore2 (--configure): 
 subprocess installed post-installation script returned error exit status 2 
dpkg: dependency problems prevent configuration of libvlc2: 
 libvlc2 depends on libvlccore2 (>= 1.0.0~rc1); however: 
  Package libvlccore2 is not configured yet. 
dpkg: error processing libvlc2 (--configure): 
 dependency problems - leaving unconfigured 
Setting up libass4 (0.9.9-0ubuntu1) ... 
No apport report written because the error message indicates its a followup error from a previous failure.
dpkg (subprocess): unable to execute installed post-installation script: Exec format error 
dpkg: error processing libass4 (--configure): 
 subprocess installed post-installation script returned error exit status 2 
Setting up libdca0 (0.0.5-3) ... 
dpkg (subprocess): unable to execute installed post-installation script: Exec format error 
dpkg: error processing libdca0 (--configure): 
 subprocess installed post-installation script returned error exit status 2 
Setting up libupnp3 (1:1.6.6-4) ... 
No apport report written because MaxReports is reached already
dpkg (subprocess): unable to execute installed post-installation script: Exec format error 
dpkg: error processing libupnp3 (--configure): 
 subprocess installed post-installation script returned error exit status 2 
Setting up libx264-85 (2:0.85.1448+git1a6d32-4) ... 
No apport report written because MaxReports is reached already
dpkg (subprocess): unable to execute installed post-installation script: Exec format error 
dpkg: error processing libx264-85 (--configure): 
 subprocess installed post-installation script returned error exit status 2 
No apport report written because MaxReports is reached already
dpkg: dependency problems prevent configuration of vlc-nox: 
 vlc-nox depends on libass4 (>= 0.9.7); however: 
  Package libass4 is not configured yet. 
 vlc-nox depends on libdca0; however: 
  Package libdca0 is not configured yet. 
 vlc-nox depends on libupnp3 (>= 1.4.3); however: 
  Package libupnp3 is not configured yet. 
 vlc-nox depends on libvlc2 (>= 1.0.0~rc); however: 
  Package libvlc2 is not configured yet. 
 vlc-nox depends on libvlccore2 (>= 1.0.2); however: 
  Package libvlccore2 is not configured yet. 
 vlc-nox depends on libx264-85; however: 
  Package libx264-85 is not configured yet. 
dpkg: error processing vlc-nox (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of vlc: 
 vlc depends on vlc-nox (= 1.0.6-1ubuntu1.1); however: 
  Package vlc-nox is not configured yet. 
 vlc depends on libvlccore2 (>= 1.0.0~rc1); however: 
  Package libvlccore2 is not configured yet. 
dpkg: error processing vlc (--configure): 
 dependency problems - lNo apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
eaving unconfigured 
dpkg: dependency problems prevent configuration of vlc-plugin-pulse: 
 vlc-plugin-pulse depends on vlc-nox (= 1.0.6-1ubuntu1.1); however: 
  Package vlc-nox is not configured yet. 
 vlc-plugin-pulse depends on libvlccore2 (>= 1.0.0~rc1); however: 
  Package libvlccore2 is not configured yet. 
dpkg: error processing vlc-plugin-pulse (--configure): 
 dependency problems - leaving unconfigured 
Setting up dkms (2.1.1.2-2fakesync1) ... 
 
Setting up fakeroot (1.14.4-1ubuntu1) ... 
update-alternatives: using /usr/bin/fakeroot-sysv to provide /usr/bin/fakeroot (fakeroot) in auto mode. 
 
Setting up libqt4-network (4:4.6.2-0ubuntu5) ... 
 
Setting up libqt4-opengl (4:4.6.2-0ubuntu5) ... 
 
Setting up patch (2.6-2ubuntu1) ... 
Setting up virtualbox-ose (3.1.6-dfsg-2ubuntu2) ... 
 * Stopping VirtualBox kernel modules 
   ...done. 
 * Starting VirtualBox kernel modules 
 * No suitable module for running kernel found 
   ...fail! 
invoke-rc.d: initscript virtualbox-ose, action "restart" failed. 
 
Setting up virtualbox-ose-dkms (3.1.6-dfsg-2ubuntu2) ... 
Loading new virtualbox-ose-3.1.6 DKMS files... 
First Installation: checking all kernels... 
Building only for 2.6.32-22-generic 
Building for architecture i686 
Building initial module for 2.6.32-22-generic 
Done. 
 
vboxdrv.ko: 
Running module version sanity check. 
 - Original module 
   - No original module exists within this kernel 
 - Installation 
   - Installing to /lib/modules/2.6.32-22-generic/updates/dkms/ 
 
vboxnetadp.ko: 
Running module version sanity check. 
 - Original module 
   - No original module exists within this kernel 
 - Installation 
   - Installing to /lib/modules/2.6.32-22-generic/updates/dkms/ 
 
vboxnetflt.ko: 
Running module version sanity check. 
 - Original module 
   - No original module exists within this kernel 
 - Installation 
   - Installing to /lib/modules/2.6.32-22-generic/updates/dkms/ 
 
depmod................. 
 
DKMS: install Completed. 
 * Stopping VirtualBox kernel modules 
   ...done. 
 * Starting VirtualBox kernel modules 
   ...done. 
 
Processing triggers for python-central ... 
Setting up virtualbox-ose-qt (3.1.6-dfsg-2ubuntu2) ... 
 
Processing triggers for libc-bin ... 
ldconfig deferred processing now taking place 
Errors were encountered while processing: 
 libvlccore2 
 libvlc2 
 libass4 
 libdca0 
 libupnp3 
 libx264-85 
 vlc-nox 
 vlc 
 vlc-plugin-pulse 
Setting up libupnp3 (1:1.6.6-4) ... 
dpkg (subprocess): unable to execute installed post-installation script: Exec format error 
dpkg: error processing libupnp3 (--configure): 
 subprocess installed post-installation script returned error exit status 2 
Setting up libdca0 (0.0.5-3) ... 
dpkg (subprocess): unable to execute installed post-installation script: Exec format error 
dpkg: error processing libdca0 (--configure): 
 subprocess installed post-installation script returned error exit status 2 
Setting up libass4 (0.9.9-0ubuntu1) ... 
dpkg (subprocess): unable to execute installed post-installation script: Exec format error 
dpkg: error processing libass4 (--configure): 
 subprocess installed post-installation script returned error exit status 2 
Setting up libx264-85 (2:0.85.1448+git1a6d32-4) ... 
dpkg (subprocess): unable to execute installed post-installation script: Exec format error 
dpkg: error processing libx264-85 (--configure): 
 subprocess installed post-installation script returned error exit status 2 
dpkg: dependency problems prevent configuration of vlc-nox: 
 vlc-nox depends on libass4 (>= 0.9.7); however: 
  Package libass4 is not configured yet. 
 vlc-nox depends on libdca0; however: 
  Package libdca0 is not configured yet. 
 vlc-nox depends on libupnp3 (>= 1.4.3); however: 
  Package libupnp3 is not configured yet. 
 vlc-nox depends on libx264-85; however: 
  Package libx264-85 is not configured yet. 
dpkg: error processing vlc-nox (--configure): 
 dependency problems - leaving unconfigured 
Setting up libvlccore2 (1.0.6-1ubuntu1.1) ... 
dpkg (subprocess): unable to execute installed post-installation script: Exec format error 
dpkg: error processing libvlccore2 (--configure): 
 subprocess installed post-installation script returned error exit status 2 
dpkg: dependency problems prevent configuration of vlc: 
 vlc depends on vlc-nox (= 1.0.6-1ubuntu1.1); however: 
  Package vlc-nox is not configured yet. 
 vlc depends on libvlccore2 (>= 1.0.0~rc1); however: 
  Package libvlccore2 is not configured yet. 
dpkg: error processing vlc (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libvlc2: 
 libvlc2 depends on libvlccore2 (>= 1.0.0~rc1); however: 
  Package libvlccore2 is not configured yet. 
dpkg: error processing libvlc2 (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of vlc-plugin-pulse: 
 vlc-plugin-pulse depends on vlc-nox (= 1.0.6-1ubuntu1.1); however: 
  Package vlc-nox is not configured yet. 
 vlc-plugin-pulse depends on libvlccore2 (>= 1.0.0~rc1); however: 
  Package libvlccore2 is not configured yet. 
dpkg: error processing vlc-plugin-pulse (--configure): 
 dependency problems - leaving unconfigured
```Anyone able to help??

I first tryed to install 7zip so I could open a Rar file, it seemed to install correctly but the rar file still did not open (rar file is not corrupt or malicious) so tryed uninstalling + reinstalling and started getting errors, does anyone know whats going on?

---

### Post by nick_goodfate on 2010-06-19
> **Jawwwwsh said:**
> Hey guys I'm new to Ubuntu but loving it so far!

I cannot install/uninstall any programs correctly at the moment, this is a fresh install from the ISO downloaded from the website only a few days ago but I get these errors when trying to install programs (so far tryed to install 7zip, Rar and VirtualBox)

```
installArchives() failed: Selecting previously deselected package dkms. 
(Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 149243 files and directories currently installed.) 
Unpacking dkms (from .../dkms_2.1.1.2-2fakesync1_all.deb) ... 
Selecting previously deselected package fakeroot. 
Unpacking fakeroot (from .../fakeroot_1.14.4-1ubuntu1_i386.deb) ... 
Selecting previously deselected package libqt4-network. 
Unpacking libqt4-network (from .../libqt4-network_4%3a4.6.2-0ubuntu5_i386.deb) ... 
Selecting previously deselected package libqt4-opengl. 
Unpacking libqt4-opengl (from .../libqt4-opengl_4%3a4.6.2-0ubuntu5_i386.deb) ... 
Selecting previously deselected package patch. 
Unpacking patch (from .../patch_2.6-2ubuntu1_i386.deb) ... 
Selecting previously deselected package virtualbox-ose. 
Unpacking virtualbox-ose (from .../virtualbox-ose_3.1.6-dfsg-2ubuntu2_i386.deb) ... 
Selecting previously deselected package virtualbox-ose-dkms. 
Unpacking virtualbox-ose-dkms (from .../virtualbox-ose-dkms_3.1.6-dfsg-2ubuntu2_all.deb) ... 
Selecting previously deselected package virtualbox-ose-qt. 
Unpacking virtualbox-ose-qt (from .../virtualbox-ose-qt_3.1.6-dfsg-2ubuntu2_i386.deb) ... 
Processing triggers for man-db ... 
Processing triggers for ureadahead ... 
ureadahead will be reprofiled on next reboot 
Processing triggers for desktop-file-utils ... 
Processing triggers for python-gmenu ... 
Rebuilding /usr/share/applications/desktop.en_GB.UTF8.cache... 
Processing triggers for python-support ... 
Setting up libvlccore2 (1.0.6-1ubuntu1.1) ... 
dpkg (subprocess): unable to execute installed post-installation script: Exec format error 
dpkg: error processing libvlccore2 (--configure): 
 subprocess installed post-installation script returned error exit status 2 
dpkg: dependency problems prevent configuration of libvlc2: 
 libvlc2 depends on libvlccore2 (>= 1.0.0~rc1); however: 
  Package libvlccore2 is not configured yet. 
dpkg: error processing libvlc2 (--configure): 
 dependency problems - leaving unconfigured 
Setting up libass4 (0.9.9-0ubuntu1) ... 
No apport report written because the error message indicates its a followup error from a previous failure.
dpkg (subprocess): unable to execute installed post-installation script: Exec format error 
dpkg: error processing libass4 (--configure): 
 subprocess installed post-installation script returned error exit status 2 
Setting up libdca0 (0.0.5-3) ... 
dpkg (subprocess): unable to execute installed post-installation script: Exec format error 
dpkg: error processing libdca0 (--configure): 
 subprocess installed post-installation script returned error exit status 2 
Setting up libupnp3 (1:1.6.6-4) ... 
No apport report written because MaxReports is reached already
dpkg (subprocess): unable to execute installed post-installation script: Exec format error 
dpkg: error processing libupnp3 (--configure): 
 subprocess installed post-installation script returned error exit status 2 
Setting up libx264-85 (2:0.85.1448+git1a6d32-4) ... 
No apport report written because MaxReports is reached already
dpkg (subprocess): unable to execute installed post-installation script: Exec format error 
dpkg: error processing libx264-85 (--configure): 
 subprocess installed post-installation script returned error exit status 2 
No apport report written because MaxReports is reached already
dpkg: dependency problems prevent configuration of vlc-nox: 
 vlc-nox depends on libass4 (>= 0.9.7); however: 
  Package libass4 is not configured yet. 
 vlc-nox depends on libdca0; however: 
  Package libdca0 is not configured yet. 
 vlc-nox depends on libupnp3 (>= 1.4.3); however: 
  Package libupnp3 is not configured yet. 
 vlc-nox depends on libvlc2 (>= 1.0.0~rc); however: 
  Package libvlc2 is not configured yet. 
 vlc-nox depends on libvlccore2 (>= 1.0.2); however: 
  Package libvlccore2 is not configured yet. 
 vlc-nox depends on libx264-85; however: 
  Package libx264-85 is not configured yet. 
dpkg: error processing vlc-nox (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of vlc: 
 vlc depends on vlc-nox (= 1.0.6-1ubuntu1.1); however: 
  Package vlc-nox is not configured yet. 
 vlc depends on libvlccore2 (>= 1.0.0~rc1); however: 
  Package libvlccore2 is not configured yet. 
dpkg: error processing vlc (--configure): 
 dependency problems - lNo apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
eaving unconfigured 
dpkg: dependency problems prevent configuration of vlc-plugin-pulse: 
 vlc-plugin-pulse depends on vlc-nox (= 1.0.6-1ubuntu1.1); however: 
  Package vlc-nox is not configured yet. 
 vlc-plugin-pulse depends on libvlccore2 (>= 1.0.0~rc1); however: 
  Package libvlccore2 is not configured yet. 
dpkg: error processing vlc-plugin-pulse (--configure): 
 dependency problems - leaving unconfigured 
Setting up dkms (2.1.1.2-2fakesync1) ... 
 
Setting up fakeroot (1.14.4-1ubuntu1) ... 
update-alternatives: using /usr/bin/fakeroot-sysv to provide /usr/bin/fakeroot (fakeroot) in auto mode. 
 
Setting up libqt4-network (4:4.6.2-0ubuntu5) ... 
 
Setting up libqt4-opengl (4:4.6.2-0ubuntu5) ... 
 
Setting up patch (2.6-2ubuntu1) ... 
Setting up virtualbox-ose (3.1.6-dfsg-2ubuntu2) ... 
 * Stopping VirtualBox kernel modules 
   ...done. 
 * Starting VirtualBox kernel modules 
 * No suitable module for running kernel found 
   ...fail! 
invoke-rc.d: initscript virtualbox-ose, action "restart" failed. 
 
Setting up virtualbox-ose-dkms (3.1.6-dfsg-2ubuntu2) ... 
Loading new virtualbox-ose-3.1.6 DKMS files... 
First Installation: checking all kernels... 
Building only for 2.6.32-22-generic 
Building for architecture i686 
Building initial module for 2.6.32-22-generic 
Done. 
 
vboxdrv.ko: 
Running module version sanity check. 
 - Original module 
   - No original module exists within this kernel 
 - Installation 
   - Installing to /lib/modules/2.6.32-22-generic/updates/dkms/ 
 
vboxnetadp.ko: 
Running module version sanity check. 
 - Original module 
   - No original module exists within this kernel 
 - Installation 
   - Installing to /lib/modules/2.6.32-22-generic/updates/dkms/ 
 
vboxnetflt.ko: 
Running module version sanity check. 
 - Original module 
   - No original module exists within this kernel 
 - Installation 
   - Installing to /lib/modules/2.6.32-22-generic/updates/dkms/ 
 
depmod................. 
 
DKMS: install Completed. 
 * Stopping VirtualBox kernel modules 
   ...done. 
 * Starting VirtualBox kernel modules 
   ...done. 
 
Processing triggers for python-central ... 
Setting up virtualbox-ose-qt (3.1.6-dfsg-2ubuntu2) ... 
 
Processing triggers for libc-bin ... 
ldconfig deferred processing now taking place 
Errors were encountered while processing: 
 libvlccore2 
 libvlc2 
 libass4 
 libdca0 
 libupnp3 
 libx264-85 
 vlc-nox 
 vlc 
 vlc-plugin-pulse 
Setting up libupnp3 (1:1.6.6-4) ... 
dpkg (subprocess): unable to execute installed post-installation script: Exec format error 
dpkg: error processing libupnp3 (--configure): 
 subprocess installed post-installation script returned error exit status 2 
Setting up libdca0 (0.0.5-3) ... 
dpkg (subprocess): unable to execute installed post-installation script: Exec format error 
dpkg: error processing libdca0 (--configure): 
 subprocess installed post-installation script returned error exit status 2 
Setting up libass4 (0.9.9-0ubuntu1) ... 
dpkg (subprocess): unable to execute installed post-installation script: Exec format error 
dpkg: error processing libass4 (--configure): 
 subprocess installed post-installation script returned error exit status 2 
Setting up libx264-85 (2:0.85.1448+git1a6d32-4) ... 
dpkg (subprocess): unable to execute installed post-installation script: Exec format error 
dpkg: error processing libx264-85 (--configure): 
 subprocess installed post-installation script returned error exit status 2 
dpkg: dependency problems prevent configuration of vlc-nox: 
 vlc-nox depends on libass4 (>= 0.9.7); however: 
  Package libass4 is not configured yet. 
 vlc-nox depends on libdca0; however: 
  Package libdca0 is not configured yet. 
 vlc-nox depends on libupnp3 (>= 1.4.3); however: 
  Package libupnp3 is not configured yet. 
 vlc-nox depends on libx264-85; however: 
  Package libx264-85 is not configured yet. 
dpkg: error processing vlc-nox (--configure): 
 dependency problems - leaving unconfigured 
Setting up libvlccore2 (1.0.6-1ubuntu1.1) ... 
dpkg (subprocess): unable to execute installed post-installation script: Exec format error 
dpkg: error processing libvlccore2 (--configure): 
 subprocess installed post-installation script returned error exit status 2 
dpkg: dependency problems prevent configuration of vlc: 
 vlc depends on vlc-nox (= 1.0.6-1ubuntu1.1); however: 
  Package vlc-nox is not configured yet. 
 vlc depends on libvlccore2 (>= 1.0.0~rc1); however: 
  Package libvlccore2 is not configured yet. 
dpkg: error processing vlc (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libvlc2: 
 libvlc2 depends on libvlccore2 (>= 1.0.0~rc1); however: 
  Package libvlccore2 is not configured yet. 
dpkg: error processing libvlc2 (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of vlc-plugin-pulse: 
 vlc-plugin-pulse depends on vlc-nox (= 1.0.6-1ubuntu1.1); however: 
  Package vlc-nox is not configured yet. 
 vlc-plugin-pulse depends on libvlccore2 (>= 1.0.0~rc1); however: 
  Package libvlccore2 is not configured yet. 
dpkg: error processing vlc-plugin-pulse (--configure): 
 dependency problems - leaving unconfigured
```Anyone able to help??

I first tryed to install 7zip so I could open a Rar file, it seemed to install correctly but the rar file still did not open (rar file is not corrupt or malicious) so tryed uninstalling + reinstalling and started getting errors, does anyone know whats going on?

what command you type in terminal to get this ? (i mean sudo apt-get inst... )

---

### Post by nick_goodfate on 2010-06-19
also, if you could open this file > /etc/apt/sources.list and paste here its contents , it would be helpful .

---

### Post by Jawwwwsh on 2010-06-19
I am not using terminal, I was installing with the GUI software centre thing :)

```
#deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://gb.archive.ubuntu.com/ubuntu/ lucid main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ lucid-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ lucid universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ lucid universe
deb http://gb.archive.ubuntu.com/ubuntu/ lucid-updates universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ lucid multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ lucid multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ lucid-updates multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu lucid partner
# deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://security.ubuntu.com/ubuntu lucid-security main restricted
deb-src http://security.ubuntu.com/ubuntu lucid-security main restricted
deb http://security.ubuntu.com/ubuntu lucid-security universe
deb-src http://security.ubuntu.com/ubuntu lucid-security universe
deb http://security.ubuntu.com/ubuntu lucid-security multiverse
deb-src http://security.ubuntu.com/ubuntu lucid-security multiverse
```

Thats the info you requested, thank you in advance for any help!! :)

---

### Post by ronnielsen1 on 2010-06-19
You should be able to install unrar or p7zip available in synaptic or sudo apt-get install unrar p7zip in terminal

---

### Post by nick_goodfate on 2010-06-19
open a terminal and try to install 7zip for example from there. it throws errors again ?
> sudo apt-get install p7zip
while you type your password , it wont appear to screen, its normal .

---

### Post by Jawwwwsh on 2010-06-19
> **ronnielsen1 said:**
> You should be able to install unrar or p7zip available in synaptic or sudo apt-get install unrar p7zip in terminal
Heres an attempt to install unrar
```
installArchives() failed: Selecting previously deselected package unrar-free. 
(Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 149727 files and directories currently installed.) 
Unpacking unrar-free (from .../unrar-free_1%3a0.0.1+cvs20071127-1_i386.deb) ... 
Processing triggers for man-db ... 
Setting up libvlccore2 (1.0.6-1ubuntu1.1) ... 
dpkg (subprocess): unable to execute installed post-installation script: Exec format error 
dpkg: error processing libvlccore2 (--configure): 
 subprocess installed post-installation script returned error exit status 2 
dpkg: dependency problems prevent configuration of libvlc2: 
 libvlc2 depends on libvlccore2 (>= 1.0.0~rc1); however: 
  Package libvlccore2 is not configured yet. 
dpkg: error processing libvlc2 (--configure): 
 dependency problems - leaving unconfigured 
Setting up libass4 (0.9.9-0ubuntu1) ... 
No apport report written because the error message indicates its a followup error from a previous failure.
dpkg (subprocess): unable to execute installed post-installation script: Exec format error 
dpkg: error processing libass4 (--configure): 
 subprocess installed post-installation script returned error exit status 2 
Setting up libdca0 (0.0.5-3) ... 
dpkg (subprocess): unable to execute installed post-installation script: Exec format error 
dpkg: error processing libdca0 (--configure): 
 subprocess installed post-installation script returned error exit status 2 
No apport report written because MaxReports is reached already
Setting up libupnp3 (1:1.6.6-4) ... 
dpkg (subprocess): unable to execute installed post-installation script: Exec format error 
dpkg: error processing libupnp3 (--configure): 
 subprocess installed post-installation script returned error exit status 2 
No apport report written because MaxReports is reached already
Setting up libx264-85 (2:0.85.1448+git1a6d32-4) ... 
dpkg (subprocess): unable to execute installed post-installation script: Exec format error 
dpkg: error processing libx264-85 (--configure): 
 subprocess installed post-installation script returned error exit status 2 
No apport report written because MaxReports is reached already
dpkg: dependency problems prevent configuration of vlc-nox: 
 vlc-nox depends on libass4 (>= 0.9.7); however: 
  Package libass4 is not configured yet. 
 vlc-nox depends on libdca0; however: 
  Package libdca0 is not configured yet. 
 vlc-nox depends on libupnp3 (>= 1.4.3); however: 
  Package libupnp3 is not configured yet. 
 vlc-nox depends on libvlc2 (>= 1.0.0~rc); however: 
  Package libvlc2 is not configured yet. 
 vlc-nox depends on libvlccore2 (>= 1.0.2); however: 
  Package libvlccore2 is not configured yet. 
 vlc-nox depends on libx264-85; however: 
  Package libx264-85 is not configured yet. 
dpkg: error processing vlc-nox (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of vlc: 
 vlc depends on vlc-nox (= 1.0.6-1ubuntu1.1); however: 
  Package vlc-nox is not configured yet. 
 vlc depends on libvlccore2 (>= 1.0.0~rc1); however: 
  Package libvlccore2 is not configured yet. 
dpkg: error processing vlc (--configure): 
 dependency problems - lNo apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
eaving unconfigured 
dpkg: dependency problems prevent configuration of vlc-plugin-pulse: 
 vlc-plugin-pulse depends on vlc-nox (= 1.0.6-1ubuntu1.1); however: 
  Package vlc-nox is not configured yet. 
 vlc-plugin-pulse depends on libvlccore2 (>= 1.0.0~rc1); however: 
  Package libvlccore2 is not configured yet. 
dpkg: error processing vlc-plugin-pulse (--configure): 
 dependency problems - leaving unconfigured 
Setting up unrar-free (1:0.0.1+cvs20071127-1) ... 
update-alternatives: using /usr/bin/unrar-free to provide /usr/bin/unrar (unrar) in auto mode. 
 
Errors were encountered while processing: 
 libvlccore2 
 libvlc2 
 libass4 
 libdca0 
 libupnp3 
 libx264-85 
 vlc-nox 
 vlc 
 vlc-plugin-pulse 
Setting up libupnp3 (1:1.6.6-4) ... 
dpkg (subprocess): unable to execute installed post-installation script: Exec format error 
dpkg: error processing libupnp3 (--configure): 
 subprocess installed post-installation script returned error exit status 2 
Setting up libdca0 (0.0.5-3) ... 
dpkg (subprocess): unable to execute installed post-installation script: Exec format error 
dpkg: error processing libdca0 (--configure): 
 subprocess installed post-installation script returned error exit status 2 
Setting up libass4 (0.9.9-0ubuntu1) ... 
dpkg (subprocess): unable to execute installed post-installation script: Exec format error 
dpkg: error processing libass4 (--configure): 
 subprocess installed post-installation script returned error exit status 2 
Setting up libx264-85 (2:0.85.1448+git1a6d32-4) ... 
dpkg (subprocess): unable to execute installed post-installation script: Exec format error 
dpkg: error processing libx264-85 (--configure): 
 subprocess installed post-installation script returned error exit status 2 
dpkg: dependency problems prevent configuration of vlc-nox: 
 vlc-nox depends on libass4 (>= 0.9.7); however: 
  Package libass4 is not configured yet. 
 vlc-nox depends on libdca0; however: 
  Package libdca0 is not configured yet. 
 vlc-nox depends on libupnp3 (>= 1.4.3); however: 
  Package libupnp3 is not configured yet. 
 vlc-nox depends on libx264-85; however: 
  Package libx264-85 is not configured yet. 
dpkg: error processing vlc-nox (--configure): 
 dependency problems - leaving unconfigured 
Setting up libvlccore2 (1.0.6-1ubuntu1.1) ... 
dpkg (subprocess): unable to execute installed post-installation script: Exec format error 
dpkg: error processing libvlccore2 (--configure): 
 subprocess installed post-installation script returned error exit status 2 
dpkg: dependency problems prevent configuration of vlc: 
 vlc depends on vlc-nox (= 1.0.6-1ubuntu1.1); however: 
  Package vlc-nox is not configured yet. 
 vlc depends on libvlccore2 (>= 1.0.0~rc1); however: 
  Package libvlccore2 is not configured yet. 
dpkg: error processing vlc (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libvlc2: 
 libvlc2 depends on libvlccore2 (>= 1.0.0~rc1); however: 
  Package libvlccore2 is not configured yet. 
dpkg: error processing libvlc2 (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of vlc-plugin-pulse: 
 vlc-plugin-pulse depends on vlc-nox (= 1.0.6-1ubuntu1.1); however: 
  Package vlc-nox is not configured yet. 
 vlc-plugin-pulse depends on libvlccore2 (>= 1.0.0~rc1); however: 
  Package libvlccore2 is not configured yet. 
dpkg: error processing vlc-plugin-pulse (--configure): 
 dependency problems - leaving unconfigured 

```
click install in the software centre and that is the error that is returned.

---

### Post by ronnielsen1 on 2010-06-19
Try this. In Accessories > Terminal

sudo aptitude update
sudo aptitude -f install

---

### Post by nick_goodfate on 2010-06-19
> **Jawwwwsh said:**
> Heres an attempt to install unrar
```
installArchives() failed: Selecting previously deselected package unrar-free. 
(Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 149727 files and directories currently installed.) 
Unpacking unrar-free (from .../unrar-free_1%3a0.0.1+cvs20071127-1_i386.deb) ... 
Processing triggers for man-db ... 
Setting up libvlccore2 (1.0.6-1ubuntu1.1) ... 
dpkg (subprocess): unable to execute installed post-installation script: Exec format error 
dpkg: error processing libvlccore2 (--configure): 
 subprocess installed post-installation script returned error exit status 2 
dpkg: dependency problems prevent configuration of libvlc2: 
 libvlc2 depends on libvlccore2 (>= 1.0.0~rc1); however: 
  Package libvlccore2 is not configured yet. 
dpkg: error processing libvlc2 (--configure): 
 dependency problems - leaving unconfigured 
Setting up libass4 (0.9.9-0ubuntu1) ... 
No apport report written because the error message indicates its a followup error from a previous failure.
dpkg (subprocess): unable to execute installed post-installation script: Exec format error 
dpkg: error processing libass4 (--configure): 
 subprocess installed post-installation script returned error exit status 2 
Setting up libdca0 (0.0.5-3) ... 
dpkg (subprocess): unable to execute installed post-installation script: Exec format error 
dpkg: error processing libdca0 (--configure): 
 subprocess installed post-installation script returned error exit status 2 
No apport report written because MaxReports is reached already
Setting up libupnp3 (1:1.6.6-4) ... 
dpkg (subprocess): unable to execute installed post-installation script: Exec format error 
dpkg: error processing libupnp3 (--configure): 
 subprocess installed post-installation script returned error exit status 2 
No apport report written because MaxReports is reached already
Setting up libx264-85 (2:0.85.1448+git1a6d32-4) ... 
dpkg (subprocess): unable to execute installed post-installation script: Exec format error 
dpkg: error processing libx264-85 (--configure): 
 subprocess installed post-installation script returned error exit status 2 
No apport report written because MaxReports is reached already
dpkg: dependency problems prevent configuration of vlc-nox: 
 vlc-nox depends on libass4 (>= 0.9.7); however: 
  Package libass4 is not configured yet. 
 vlc-nox depends on libdca0; however: 
  Package libdca0 is not configured yet. 
 vlc-nox depends on libupnp3 (>= 1.4.3); however: 
  Package libupnp3 is not configured yet. 
 vlc-nox depends on libvlc2 (>= 1.0.0~rc); however: 
  Package libvlc2 is not configured yet. 
 vlc-nox depends on libvlccore2 (>= 1.0.2); however: 
  Package libvlccore2 is not configured yet. 
 vlc-nox depends on libx264-85; however: 
  Package libx264-85 is not configured yet. 
dpkg: error processing vlc-nox (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of vlc: 
 vlc depends on vlc-nox (= 1.0.6-1ubuntu1.1); however: 
  Package vlc-nox is not configured yet. 
 vlc depends on libvlccore2 (>= 1.0.0~rc1); however: 
  Package libvlccore2 is not configured yet. 
dpkg: error processing vlc (--configure): 
 dependency problems - lNo apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
eaving unconfigured 
dpkg: dependency problems prevent configuration of vlc-plugin-pulse: 
 vlc-plugin-pulse depends on vlc-nox (= 1.0.6-1ubuntu1.1); however: 
  Package vlc-nox is not configured yet. 
 vlc-plugin-pulse depends on libvlccore2 (>= 1.0.0~rc1); however: 
  Package libvlccore2 is not configured yet. 
dpkg: error processing vlc-plugin-pulse (--configure): 
 dependency problems - leaving unconfigured 
Setting up unrar-free (1:0.0.1+cvs20071127-1) ... 
update-alternatives: using /usr/bin/unrar-free to provide /usr/bin/unrar (unrar) in auto mode. 
 
Errors were encountered while processing: 
 libvlccore2 
 libvlc2 
 libass4 
 libdca0 
 libupnp3 
 libx264-85 
 vlc-nox 
 vlc 
 vlc-plugin-pulse 
Setting up libupnp3 (1:1.6.6-4) ... 
dpkg (subprocess): unable to execute installed post-installation script: Exec format error 
dpkg: error processing libupnp3 (--configure): 
 subprocess installed post-installation script returned error exit status 2 
Setting up libdca0 (0.0.5-3) ... 
dpkg (subprocess): unable to execute installed post-installation script: Exec format error 
dpkg: error processing libdca0 (--configure): 
 subprocess installed post-installation script returned error exit status 2 
Setting up libass4 (0.9.9-0ubuntu1) ... 
dpkg (subprocess): unable to execute installed post-installation script: Exec format error 
dpkg: error processing libass4 (--configure): 
 subprocess installed post-installation script returned error exit status 2 
Setting up libx264-85 (2:0.85.1448+git1a6d32-4) ... 
dpkg (subprocess): unable to execute installed post-installation script: Exec format error 
dpkg: error processing libx264-85 (--configure): 
 subprocess installed post-installation script returned error exit status 2 
dpkg: dependency problems prevent configuration of vlc-nox: 
 vlc-nox depends on libass4 (>= 0.9.7); however: 
  Package libass4 is not configured yet. 
 vlc-nox depends on libdca0; however: 
  Package libdca0 is not configured yet. 
 vlc-nox depends on libupnp3 (>= 1.4.3); however: 
  Package libupnp3 is not configured yet. 
 vlc-nox depends on libx264-85; however: 
  Package libx264-85 is not configured yet. 
dpkg: error processing vlc-nox (--configure): 
 dependency problems - leaving unconfigured 
Setting up libvlccore2 (1.0.6-1ubuntu1.1) ... 
dpkg (subprocess): unable to execute installed post-installation script: Exec format error 
dpkg: error processing libvlccore2 (--configure): 
 subprocess installed post-installation script returned error exit status 2 
dpkg: dependency problems prevent configuration of vlc: 
 vlc depends on vlc-nox (= 1.0.6-1ubuntu1.1); however: 
  Package vlc-nox is not configured yet. 
 vlc depends on libvlccore2 (>= 1.0.0~rc1); however: 
  Package libvlccore2 is not configured yet. 
dpkg: error processing vlc (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libvlc2: 
 libvlc2 depends on libvlccore2 (>= 1.0.0~rc1); however: 
  Package libvlccore2 is not configured yet. 
dpkg: error processing libvlc2 (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of vlc-plugin-pulse: 
 vlc-plugin-pulse depends on vlc-nox (= 1.0.6-1ubuntu1.1); however: 
  Package vlc-nox is not configured yet. 
 vlc-plugin-pulse depends on libvlccore2 (>= 1.0.0~rc1); however: 
  Package libvlccore2 is not configured yet. 
dpkg: error processing vlc-plugin-pulse (--configure): 
 dependency problems - leaving unconfigured 

```
click install in the software centre and that is the error that is returned.

try this in terminal :
> sudo apt-get --fix-broken install p7zip
(i think thats the correct syntax, but if it isnt it just wont run , no worry )

---

### Post by Jawwwwsh on 2010-06-19
> **ronnielsen1 said:**
> Try this. In Accessories > Terminal
 
 sudo aptitude update
 sudo aptitude -f install
 Did this, seemed to work correctly, could I ask what it did though? :P
> **nick_goodfate said:**
> try this in terminal :
 
 (i think thats the correct syntax, but if it isnt it just wont run , no  worry )
 ```
joshua@joshua-desktop:~$ sudo apt-get --fix-broken install p7zip
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  p7zip-full
The following NEW packages will be installed
  p7zip
0 upgraded, 1 newly installed, 0 to remove and 5 not upgraded.
9 not fully installed or removed.
Need to get 359kB of archives.
After this operation, 1,024kB of additional disk space will be used.
Get: 1 http://gb.archive.ubuntu.com/ubuntu/ lucid/universe p7zip 9.04~dfsg.1-1 [359kB]
Fetched 359kB in 5s (64.0kB/s)                           
Selecting previously deselected package p7zip.
(Reading database ... 149736 files and directories currently installed.)
Unpacking p7zip (from .../p7zip_9.04~dfsg.1-1_i386.deb) ...
Processing triggers for man-db ...
Setting up libvlccore2 (1.0.6-1ubuntu1.1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libvlccore2 (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of libvlc2:
 libvlc2 depends on libvlccore2 (>= 1.0.0~rc1); however:
  Package libvlccore2 is not configured yet.
dpkg: error processing libvlc2 (--configure):
 dependency problems - leaving unconfigured
Setting up libass4 (0.9.9-0ubuntu1) ...
No apport report written because the error message indicates it's a follow-up error from a previous failure.
                            dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libass4 (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libdca0 (0.0.5-3) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libdca0 (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports has already been reached
                                                                    Setting up libupnp3 (1:1.6.6-4) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libupnp3 (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libx264-85 (2:0.85.1448+git1a6d32-4) ...
No apport report written because MaxReports has already been reached
                                                                    dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libx264-85 (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of vlc-nox:
 vlc-nox depends on libass4 (>= 0.9.7); however:
  Package libass4 is not configured yet.
 vlc-nox depends on libdca0; however:
  Package libdca0 is not configured yet.
 vlc-nox depends on libupnp3 (>= 1.4.3); however:
  Package libupnp3 is not configured yet.
 vlc-nox depends on libvlc2 (>= 1.0.0~rc); however:
  Package libvlc2 is not configured yet.
 vlc-nox depends on libvlccore2 (>= 1.0.2); however:
  Package libvlccore2 is not configured yet.
 vlc-nox depends on libx264-85; however:
  Package libx264-85 is not configured yet.
dpkg: error processing vlc-nox (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of vlc:
 vlc depends on vlc-nox (= 1.0.6-1ubuntu1.1); however:
  Package vlc-nox is not configured yet.
 vlc depends on libvlccore2 (>= 1.0.0~rc1); however:
  Package libvlccore2 is not configured yet.
dpkg: error processing vlc (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of vlc-plugin-pulse:
 vlc-plugin-pulse depends on vlc-nox (= 1.0.6-1ubuntu1.1); however:
  Package vlc-nox is not configured yet.
 vlc-plugin-pulse depends on libvlccore2 (>= 1.0.0~rc1); however:
  Package libvlccore2 is not configured yet.
dpkg: error processing vlc-plugin-pulse (--configure):
 dependency problems - leaving unconfigured
Setting up p7zip (9.04~dfsg.1-1) ...
No apport report written because MaxReports has already been reached
                                                                    Errors were encountered while processing:
 libvlccore2
 libvlc2
 libass4
 libdca0
 libupnp3
 libx264-85
 vlc-nox
 vlc
 vlc-plugin-pulse
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

:confused:

---

### Post by Jawwwwsh on 2010-06-19
a little bit more info, everytime I try and install something through the software centre and get one of these error messages it still thinks the program is installed (but the program doesnt seem to work [using 7zip and unrar as examples, still cannot access my .rar file]) and then when you go to uninstall the program you get another error, possibly the same one I think!

---

### Post by nick_goodfate on 2010-06-19
> **Jawwwwsh said:**
> Did this, seemed to work correctly, could I ask what it did though? :P

:confused:

xaxa ! why are you confused ?:p i m just stupid ....:D good to know that you solved your problem ! mark this thread as SOLVED from thread tools !

---

### Post by ronnielsen1 on 2010-06-19
sudo apt-get update
sudo apt-get -f install

Type in these from a terminal and if you have broken packages, it should fix them.

---

### Post by Jawwwwsh on 2010-06-19
guys, still getting the same problems after doing everything you have all suggested.

Could it be to do with small space left on primary HDD? only 250 Mb left as its a tiny HDD as a last resort (there is an external HDD connected though)

Is there any way to just revert Ubuntu to how it was when it was first installed? I havent got any data on here its just a web browsing PC and when I first installed it about a week ago I was able to install Gmount ISO fine!!

---

### Post by ronnielsen1 on 2010-06-19
> Did this, seemed to work correctly, could I ask what it did though?

> Run apt-get -f install or apt-get -f remove  without specifying a package, to force completion of package  installations. If you are attempting a system upgrade, then use apt-get  upgrade -f dist-upgrade. You might want to add the --no-download  switch, so that you are working only with packages already on your  system, rather than downloading other ones and possibly compounding your  problems.
  
[http://www.linux.com/archive/feed/48910](http://www.linux.com/archive/feed/48910)

>  		a little bit more info, everytime I try and install something through  the software centre and get one of these error messages it still thinks  the program is installed (but the program doesnt seem to work
I don't know on that one. Logout or reboot needed to clear the cache? You might try Synaptic to see if you still have issues

---

### Post by slooksterpsv on 2010-06-19
sudo apt-get update - updates the local cache of what the repositories contain on your computer so that when you try to install a program it knows where it install it from.

sudo apt-get -f install - forces installation of previous packages that weren't installed, that way if there was a package hanging in the background that needed to install first, it does so with the -f flag.

Another command I would try is:
sudo apt-get autoremove - to remove packages that are broken, out of date or aren't necessary for the system anymore.

---

