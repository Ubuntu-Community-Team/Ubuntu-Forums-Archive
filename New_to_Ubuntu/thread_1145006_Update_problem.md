---
title: "Update problem"
date: 2009-05-01
forum: New to Ubuntu
---

### Post by Celectt on 2009-05-01
Release8.10
Keep on getting same message when I update .
Not all updates can be installed
Run a partial upgrade ,to install as many updates as possible.

This can be caused by:
A previous upgrade which didn't complete
Problems with some...etc
...
...

When I choose partial upgrade,it start doing something for a few seconds then it disappear.I tried many times,I cannot even upgrade to 9.04

---

### Post by taurus on 2009-05-01
Close the update manager.  Then, open a terminal and run

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get dist-upgrade
```
That would update your system with the new kernel.

---

### Post by Celectt on 2009-05-01
Not working.Must I do a fresh install from CD?
.
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7D2C7A23BF810CD5

W: Failed to fetch [http://ppa.launchpad.net/awn-testing/ubuntu/dists/jaunty/deb-src/binary-i386/Packages.gz](http://ppa.launchpad.net/awn-testing/ubuntu/dists/jaunty/deb-src/binary-i386/Packages.gz)  404 Not Found



W: Failed to fetch [http://ppa.launchpad.net/awn-testing/ubuntu/dists/jaunty/http://ppa.launchpad.net/awn-testing/ubuntu/binary-i386/Packages.gz](http://ppa.launchpad.net/awn-testing/ubuntu/dists/jaunty/http://ppa.launchpad.net/awn-testing/ubuntu/binary-i386/Packages.gz)  404 Not Found



W: Failed to fetch [http://ppa.launchpad.net/awn-testing/ubuntu/dists/jaunty/jaunty/binary-i386/Packages.gz](http://ppa.launchpad.net/awn-testing/ubuntu/dists/jaunty/jaunty/binary-i386/Packages.gz)  404 Not Found



E: Some index files failed to download, they have been ignored, or old ones used instead.

henk@henk-desktop:~$ sudo apt-get dist-upgrade

---

### Post by nandemonai on 2009-05-01
If that doesn't do it you can mark all upgrades in Synaptic and try that way. I've had the same issue in Intrepid before.

---

### Post by Niniel on 2009-05-01
I ran into this issue myself, but I found it relatively easy to troubleshoot: I had one program on my system that I had compiled myself, and then also installed a newer version via Synaptic later - the KGrubEditor. I got rid of both versions - which included some K-libraries that were a bit tricky because they wouldn't uninstall unless I uninstalled a certain one first - and after that it worked.
I looked at the programs/libraries my update manager was unable to update - they were listed in the update window but greyed out - and then checked them out in Synaptic.
After the upgrade to 9.04 I re-installed KGrubEditor and all is well. 
Maybe a similar approach will work for you, too.

---

### Post by nandemonai on 2009-05-01
> **Celectt said:**
> Not working.Must I do a fresh install from CD?
.
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7D2C7A23BF810CD5

W: Failed to fetch [http://ppa.launchpad.net/awn-testing/ubuntu/dists/jaunty/deb-src/binary-i386/Packages.gz](http://ppa.launchpad.net/awn-testing/ubuntu/dists/jaunty/deb-src/binary-i386/Packages.gz)  404 Not Found



W: Failed to fetch [http://ppa.launchpad.net/awn-testing/ubuntu/dists/jaunty/http://ppa.launchpad.net/awn-testing/ubuntu/binary-i386/Packages.gz](http://ppa.launchpad.net/awn-testing/ubuntu/dists/jaunty/http://ppa.launchpad.net/awn-testing/ubuntu/binary-i386/Packages.gz)  404 Not Found



W: Failed to fetch [http://ppa.launchpad.net/awn-testing/ubuntu/dists/jaunty/jaunty/binary-i386/Packages.gz](http://ppa.launchpad.net/awn-testing/ubuntu/dists/jaunty/jaunty/binary-i386/Packages.gz)  404 Not Found



E: Some index files failed to download, they have been ignored, or old ones used instead.

henk@henk-desktop:~$ sudo apt-get dist-upgrade

You have a problem with a 3rd party repository. 1. You have no key for said repository and 2. There is no jaunty/jaunty directory in that repo.

Either a problem with your sources file or the repository itself it seems.

---

### Post by tarps87 on 2009-05-01
Try commenting out the awn entire in the sources list
```
sudo gedit /etc/apt/sources.list
```
Find the line(s) that have awn in them and put a # at the start of that line.

---

### Post by Celectt on 2009-05-01
{mark all upgrades in Synaptic} Worked Thank you.
How do I get this tread as solved ?

---

### Post by MeanStreak on 2009-05-03
Was having the same problem in Jaunty. The following worked for me. Thanks! :)

> **taurus said:**
> Close the update manager.  Then, open a terminal and run

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get dist-upgrade
```
That would update your system with the new kernel.

---

