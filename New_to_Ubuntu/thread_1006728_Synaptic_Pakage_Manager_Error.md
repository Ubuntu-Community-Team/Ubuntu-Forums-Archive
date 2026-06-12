---
title: "Synaptic Pakage Manager Error"
date: 2008-12-09
forum: New to Ubuntu
---

### Post by lambert128 on 2008-12-09
Help needed please

I'm running Ubuntu 8.10, when I open Synaptic Package Manager I get the following error:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E:_cache->open() failed, please report.

I've tried running 'sudo dpkg --configure -a', but I get the following errors

invoke-rc.d: initscript system-tools-backends, action "start" failed.
dpkg:error processing system-tools-backends (--configure):
subprocess post-installation script returned error exit status 1
dpkg: ../../scr/packages.c:221: process_queue: Assertion 'dependtry <=4' failed. Aborted

Any ideas?

---

### Post by DougieFresh4U on 2008-12-09
Try
```
sudo apt-get -f install
sudo dpkg --configure -a
```

---

### Post by porchrat on 2008-12-09
> **lambert128 said:**
> Help needed please

I'm running Ubuntu 8.10, when I open Synaptic Package Manager I get the following error:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E:_cache->open() failed, please report.

I've tried running 'sudo dpkg --configure -a', but I get the following errors

invoke-rc.d: initscript system-tools-backends, action "start" failed.
dpkg:error processing system-tools-backends (--configure):
subprocess post-installation script returned error exit status 1
dpkg: ../../scr/packages.c:221: process_queue: Assertion 'dependtry <=4' failed. Aborted

Any ideas?

Wow this has been happening a lot lately

---

### Post by lambert128 on 2008-12-12
I tried sudo apt-get -f install with no luck I get the following msg

E: dpkg was interrupted, you must manually run 'dpkg -- configure -a' to correct the problem

and sudo dpkg --configure -a, gives:

invoke-rc.d:iniscript system-tools backends, action start failed. 
dpkg: error processing system-tools-backends (-- configure):
subprocess post-installation script returned error exit status 1
dpkg: ../../src/packages.c:221: pocess_queue: Assertion 'dependtry <= 4' failed. 

anyone any more ideas.

ps thanks for the help so far

---

### Post by gb5757870 on 2008-12-17
I am getting the same errors and driving me nuts. Any solutions?

---

### Post by gb5757870 on 2008-12-17
Solution found at:
[http://ubuntuforums.org/showthread.php?t=994334&highlight=process_queue%3A+Assertion+%60dependtry+%26lt%3B%3D+4%27+failed](http://ubuntuforums.org/showthread.php?t=994334&highlight=process_queue%3A+Assertion+%60dependtry+%26lt%3B%3D+4%27+failed)

In my case, it was a program called unison-desktop which crippled me.

---

