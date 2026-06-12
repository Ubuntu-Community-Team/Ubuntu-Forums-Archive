---
title: "Ubuntu Software Centre (install/remove problems)"
date: 2011-08-21
forum: New to Ubuntu
---

### Post by tolf242 on 2011-08-21
Hi,

I seem to be having problems installing and removing from the "Ubuntu Software Centre", It returns "Package operation failed" when I install and/or remove.

Has anyone had or having the same problem? It was working fine earlier today, then all of a sudden, threw this problem up.

These are the details it gave out...

------------------------

Package operation failed

The installation or removal of a software package failed.

-> Details

installArchives() failed: Selecting previously deselected package python-farsight.
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
(Reading database ... 245237 files and directories currently installed.)
Unpacking python-farsight (from .../python-farsight_0.0.26-1ubuntu1_i386.deb) ...
Selecting previously deselected package python-papyon.
Unpacking python-papyon (from .../python-papyon_0.5.5-1ubuntu1.2_all.deb) ...
Selecting previously deselected package emesene.
Unpacking emesene (from .../emesene_2.11.4+dfsg-0ubuntu1_all.deb) ...
Selecting previously deselected package python-dnspython.
Unpacking python-dnspython (from .../python-dnspython_1.9.4-0ubuntu1_all.deb) ...
Selecting previously deselected package python-xmpp.
Unpacking python-xmpp (from .../python-xmpp_0.4.1-cvs20080505.2_all.deb) ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_GB.UTF8.cache...
Processing triggers for man-db ...
Processing triggers for python-support ...
Setting up g15daemon (1.9.5.3-8.1ubuntu2) ...
Starting g15daemon: .../dev/input/uinput not found ...invoke-rc.d: initscript g15daemon, action "start" failed.
dpkg: error processing g15daemon (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of g15stats:
 g15stats depends on g15daemon; however:
  Package g15daemon is not configured yet.
dpkg: error processing g15stats (--configure):
 dependency problems - leaving unconfigured
Setting up python-farsight (0.0.26-1ubuntu1) ...
No apport report written because the error message indicates its a followup error from a previous failure.
Setting up python-papyon (0.5.5-1ubuntu1.2) ...
Setting up emesene (2.11.4+dfsg-0ubuntu1) ...
Setting up python-dnspython (1.9.4-0ubuntu1) ...
Setting up python-xmpp (0.4.1-cvs20080505.2) ...
Processing triggers for python-support ...
Processing triggers for python-central ...
Errors were encountered while processing:
 g15daemon
 g15stats
Setting up g15daemon (1.9.5.3-8.1ubuntu2) ...
Starting g15daemon: .../dev/input/uinput not found ...invoke-rc.d: initscript g15daemon, action "start" failed.
dpkg: error processing g15daemon (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of g15stats:
 g15stats depends on g15daemon; however:
  Package g15daemon is not configured yet.
dpkg: error processing g15stats (--configure):
 dependency problems - leaving unconfigured

-------------------------------------------------

Any thoughts on this will be gratefully received.

Many thanks in advance, tolf.

---

### Post by blazemore on 2011-08-22
Does it do this for everything?

Have you added any additional repositories?

Try running
```
sudo rm -f /var/cache/apt/archives/*; sudo apt-get update; sudo dpkg --configure -a; sudo apt-get -f install ; sudo apt-get upgrade -y
```

This will:
Remove any cached packages which may be a problem
Update the repository
Try to reinstall any pending installations
Force install pending installations
Upgrade the system

---

### Post by tolf242 on 2011-08-22
Thank you blazemore, 

that code seems to have cleared, what looked like a blockage. Yes it did fail for everything and no additional repositories were installed. It just went funky while installing Python.

Many thanks, tolf.

---

