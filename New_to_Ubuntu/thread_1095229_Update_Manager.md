---
title: "Update Manager"
date: 2009-03-13
forum: New to Ubuntu
---

### Post by mayagrafix on 2009-03-13
I am having a small problem with the update manger on a P2 laptop. I get the following:


> 
The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Failed to fetch [http://mx.archive.ubuntu.com/ubuntu/dists/feisty-backports/main/binary-i386/Packages.gz](http://mx.archive.ubuntu.com/ubuntu/dists/feisty-backports/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://mx.archive.ubuntu.com/ubuntu/dists/feisty-backports/restricted/binary-i386/Packages.gz](http://mx.archive.ubuntu.com/ubuntu/dists/feisty-backports/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://mx.archive.ubuntu.com/ubuntu/dists/feisty-backports/universe/binary-i386/Packages.gz](http://mx.archive.ubuntu.com/ubuntu/dists/feisty-backports/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://mx.archive.ubuntu.com/ubuntu/dists/feisty-backports/multiverse/binary-i386/Packages.gz](http://mx.archive.ubuntu.com/ubuntu/dists/feisty-backports/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]
Some index files failed to download, they have been ignored, or old ones used instead.

I already ran "apt get purge" and dpkg as per error message request but now I still get the above message and notice from the update manager that my sistem is up to date, last checked 33 days ago (??).

Otherwise the Update Manger works fine and my "Net connection is up and running 100%. 

Thanks in advance for all of your great work.:D:D

---

### Post by drs305 on 2009-03-13
Those links are to a feisty repository that no longer exists on the server. You can edit sources.list manually or via synaptic to eliminate those references. If you are still running fiesty you can still find links to these repositories although I would recommend installing a newer version.

Here is a link to the older repositories:
[http://old-releases.ubuntu.com/ubuntu/dists/]("http://old-releases.ubuntu.com/ubuntu/dists/")

---

### Post by taurus on 2009-03-13
Feisty has been expired and no longer support.  The repos have moved to.

Therefore, you need to edit /etc/apt/sources.list

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/apt/sources.list
```
and replace all the **[http://mx.archive.ubuntu.com/](http://mx.archive.ubuntu.com/)** with **[http://old-releases.ubuntu.com/](http://old-releases.ubuntu.com/)**.  Save it and then run

```
sudo apt-get update
sudo apt-get upgrade
```

Otherwise, just post your /etc/apt/sources.list.

```
cat /etc/apt/sources.list
```

---

### Post by mayagrafix on 2009-03-13
Great. Thanks for the prompt reply. However, I checked the version of Ubuntu I'm running and it is not Feisty, but release 8.10 (intrepid) with Gnome 2.24.1 which, as I understand it, is the latest and greatest from Canonical.:KS

Do the same instructions apply just the same?

---

### Post by avtolle on 2009-03-13
You should edit the/etc/apt/sources.list and either delete the lines referring to the Feisty repos or comment them out (using a # before each such line).

---

### Post by mayagrafix on 2009-03-13
Thanks very much. Will edit as recommended.

---

