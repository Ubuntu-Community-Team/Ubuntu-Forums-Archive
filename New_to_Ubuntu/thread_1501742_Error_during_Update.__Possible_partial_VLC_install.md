---
title: "Error during Update.  Possible partial VLC install problem."
date: 2010-06-04
forum: New to Ubuntu
---

### Post by StuM on 2010-06-04
Hi all,

I've recently had an error message come up when updating via the update manager.  This is the error that occurred. 

[IMG]http://i.imgur.com/dmdXO.png[/IMG]

One thing which may or may not be connected is that a short while ago I tried to install VLC via the software centre. For some reason it failed mid install, with some packages being installed, but others not.  It wouldn't let me resume, or delete the ones I'd already installed.

Even if this problem isn't connected, some help with how to reverse this bad install would be appreciated.

**Edit:** I've just noticed the vlc letters in the error messages, so it definitely looks like the failed VLC install is causing the problem.

---

### Post by Riaku on 2010-06-04
try a sudo apt-get remove purge vlc then try.

---

### Post by StuM on 2010-06-04
> **Riaku said:**
> try a sudo apt-get remove purge vlc then try.

I tried that.  Unfortunately I just get the following message:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package purge
```

Although the Update Manager is empty now.  I'm a bit worried it did a partial upgrade of some sort before now.  I didn't get a choice it just came up with more error messages at the end.

---

### Post by Riaku on 2010-06-04
```
 sudo apt-get remove vlc && sudo apt-get update 
``` then

---

### Post by StuM on 2010-06-04
> **Riaku said:**
> ```
 sudo apt-get remove vlc && sudo apt-get update 
``` then

That seemed to be more successful.  Except when I tried to reinstall VLC I got the error messages below. Which makes me think there is still some problem hanging around:

```
installArchives() failed: Selecting previously deselected package vlc.
(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 160598 files and directories currently installed.)
Unpacking vlc (from .../vlc_1.0.6-1ubuntu1.1_i386.deb) ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_GB.UTF8.cache...
Processing triggers for man-db ...
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
Setting up libupnp3 (1:1.6.6-4) ...
No apport report written because the error message indicates its a followup error from a previous failure.
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libupnp3 (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of vlc-nox:
 vlc-nox depends on libupnp3 (>= 1.4.3); however:
  Package libupnp3 is not configured yet.
 vlc-nox depends on libvlc2 (>= 1.0.0~rc); however:
  Package libvlc2 is not configured yet.
 vlc-nox depends on libvlccore2 (>= 1.0.2); however:
  Package libvlccore2 is not configured yet.
dpkg: error processing vlc-nox (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of vlc-plugin-pulse:
 vlc-plugin-pulse depends on vlc-nox (= 1.0.6-1ubuntu1.1); however:
  Package vlc-nox is not configured yet.
 vlc-plugin-pulse depends on libvlccore2 (>= 1.0.0~rc1); however:
  Package libvlccore2 is not configured yet.
dpkg: error processing vlc-plugin-pulse (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of vlc:
 vlc depends on vlc-nox (= 1.0.6-1ubuntu1.1); however:
  Package vlc-nox is not configured yet.
 vlc depends on libvlccore2 (>= No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
1.0.0~rc1); however:
  Package libvlccore2 is not configured yet.
dpkg: error processing vlc (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libvlccore2
 libvlc2
 libupnp3
 vlc-nox
 vlc-plugin-pulse
 vlc
Setting up libupnp3 (1:1.6.6-4) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libupnp3 (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of vlc-nox:
 vlc-nox depends on libupnp3 (>= 1.4.3); however:
  Package libupnp3 is not configured yet.
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

---

### Post by Riaku on 2010-06-04
search for those libs in the synaptic package manager and remove them one by one then install vlc

---

### Post by StuM on 2010-06-04
> **Riaku said:**
> search for those libs in the synaptic package manager and remove them one by one then install vlc

Tried that but still the same problem... grrrr.

It's getting late here, and my head is tired so will have to take a fresh look at this tomorrow.  Thanks for your efforts Riaku.

---

### Post by Riaku on 2010-06-04
> **StuM said:**
> Tried that but still the same problem... grrrr.

It's getting late here, and my head is tired so will have to take a fresh look at this tomorrow.  Thanks for your efforts Riaku.
we'll figure it out :) no worries

---

