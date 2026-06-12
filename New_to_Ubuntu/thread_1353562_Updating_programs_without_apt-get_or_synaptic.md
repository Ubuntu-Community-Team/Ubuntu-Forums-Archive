---
title: "Updating programs without apt-get or synaptic"
date: 2009-12-12
forum: New to Ubuntu
---

### Post by ancau on 2009-12-12
Hi there,

I was wondering how to update programs without synaptic or apt-get? I installed qbittorrent with the "add/remove applications" and it installed fine, but when i started it i realised it was and old version (v2 has been released, and i have installed v1.3.3). Both synaptic and apt-get say that i have the latest version.

So... to install using the tarball, or using the instructions at 

[http://qbittorrent.sourceforge.net/download.php](http://qbittorrent.sourceforge.net/download.php) 

do i first need to uninstall the version i have installed? or install the version differently? Or just install it as said? Would I not have to bother with all the instructions on the website since I've already had a previous version installed? 

Thanks!

ancau :)

---

### Post by QIII on 2009-12-12
What you will have to do depends entirely on the instructions from the source of the package.

The probable reason you are being told that you have the most recent version is that you have the most recent version available in the repos.

The repos sometimes do not have the very most recent versions of some software because the developers and MOTUs need some time to be sure that the packages are stable and will work well with your version of Ubuntu.  This, unfortunately, leads to a lag between when the software provider releases a new version and when you can get it through a version of APT (apt-get, Synaptic, Software Center) from the repos.

---

### Post by 3rdalbum on 2009-12-12
You don't necessarily have to remove the old version first. It might actually help to keep the old version.

Qbittorrent might be available in a PPA (Personal Package Archive repository). Try doing a Google search for "Qbittorrent PPA" and see if it comes up. If there is one, then you can add it to your system and it will keep this program up-to-date for you (and you won't have to compile it from source).

---

