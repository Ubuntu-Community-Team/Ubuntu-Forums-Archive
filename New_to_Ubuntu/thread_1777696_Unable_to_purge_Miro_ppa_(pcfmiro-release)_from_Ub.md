---
title: "Unable to purge Miro ppa (pcf/miro-release) from Ubuntu Natty Narwhal"
date: 2011-06-08
forum: New to Ubuntu
---

### Post by mtotowajirani on 2011-06-08
I've tried to purge the Miro ppa after I uninstalled it. I've tried using Ubuntu Tweak, Synaptic package manager and the terminal to remove it. I'm removing it because its giving me a 404 error when I try to update it.

Here is the terminal code and response when I try to purge it:

> 
admin@mothership:~$ sudo ppa-purge: pcf/miro-release
[sudo] password for admin: 
sudo: ppa-purge:: command not found
admin@mothership:~$ sudo ppa-purge pcf/miro-release
Updating packages lists
W: Failed to fetch [http://ppa.launchpad.net/pcf/miro-release/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/pcf/miro-release/ubuntu/dists/natty/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/pcf/miro-release/ubuntu/dists/natty/main/binary-i386/Packages](http://ppa.launchpad.net/pcf/miro-release/ubuntu/dists/natty/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
Warning:  apt-get update failed for some reason
PPA to be removed: pcf/miro-release ppa
Warning:  Could not find package list for PPA: pcf/miro-release ppa
admin@mothership:~$
Please help me completely remove this ppa. I need this fix urgently!

**UPDATE: **I'm using Ubuntu 11.04 Natty Narwhal

---

### Post by jtarin on 2011-06-08
You didn't say what version of Ubuntu but for maverick [ppa-purge]("https://launchpad.net/ubuntu/maverick/i386/ppa-purge/0.2.7.1+bzr53"). You might find it in the repositories for your version.

---

### Post by mtotowajirani on 2011-06-08
> **jtarin said:**
> You didn't say what version of Ubuntu but for maverick [ppa-purge]("https://launchpad.net/ubuntu/maverick/i386/ppa-purge/0.2.7.1+bzr53"). You might find it in the repositories for your version.
I mentioned it in the title. I'm using Ubuntu 11.04 Natty Narwhal

---

