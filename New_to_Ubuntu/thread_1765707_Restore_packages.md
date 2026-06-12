---
title: "Restore packages?"
date: 2011-05-23
forum: New to Ubuntu
---

### Post by holadebob on 2011-05-23
I made a mistake using bleachbit and removed all my packages from /var/cache/apt/archive.

I tried to reload package information in synaptic, but nothing changed.

So, does anyone know how to get synaptic to review the programs I have and then download all the packages needed for the programs I have?

:) I thought they were protected and bleachbit wouldn't touch them - never even thought of it really. I am humbled.

Thank you

---

### Post by oldfred on 2011-05-23
Why do you want to redownload the packages. You do not need them once installed.

You can get a list of installed packages.

from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
From old install
dpkg --get-selections > ~/my-packages
From New install
sudo dpkg --set-selections < my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade

But I do not think that redownloads packages, just lets you reinstall all the ones you have into a new install. If upgrading you should houseclean beforehand and edit out old packages.

---

### Post by holadebob on 2011-05-23
These methods all seem to install the program after the packages are downloaded. I just wanted to put the deleted packages back in /var/cache/apt/archive.

The reason for this to backup those packages for a quicker recovery in any future reinstall using aptoncd.

But, maybe it would be good to start over and build my install back up, with a chance of eliminating some programs I know I don't use anymore and forgot about. Some of the articles I've read suggest that. 

I think I'll do that tonight. Thanks for the way to make that list, that is handy.

I'll mark this one solved. 

Thank you from old Bob

---

