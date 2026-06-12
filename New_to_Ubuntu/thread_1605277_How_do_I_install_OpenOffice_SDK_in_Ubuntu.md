---
title: "How do I install OpenOffice SDK in Ubuntu"
date: 2010-10-25
forum: New to Ubuntu
---

### Post by achab on 2010-10-25
I have used Fedora and OpenSuse for years (in my spare time), but this is my first day of Ubuntu. I downloaded the .deb package of OpenOffice SDK, and tried the dpkg command on it. I got an error message saying:

dpkg: dependency problems prevent configuration of ooobasis3.2-sdk:
 ooobasis3.2-sdk depends on ooobasis3.2-core01; however:
  Package ooobasis3.2-core01 is not installed.
dpkg: error processing ooobasis3.2-sdk (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ooobasis3.2-sdk

I believe ooobasis3.2-core01 HAS been installed. It just has not been installed as a .deb package, but instead during the installation of Ubuntu 10.10. Here is the basis for my belief:

root@ZT:/usr/lib/openoffice/basis3.2# pwd
/usr/lib/openoffice/basis3.2
root@ZT:/usr/lib/openoffice/basis3.2# ls
help  presets  program  registered-components  share  ure-link


I would rather not have to reinstall it a second time as a .deb package. Even though I would eventually be willing to do it if I have no other choice.


What are my options for installing OpenOffice SDK. Please give me an answer in the form of a step by step, not a one liner.

Thanks,

Abdenour

---

### Post by john77eipe on 2010-10-25
The easiest way to do it would be to use Ubuntu Software Center. (USC)

In USC, search for openoffice.

---

### Post by AngusH on 2010-10-25
Hey just so you know, in Ubuntu these are the ways to install packages (in order of ease):
1)Synaptic/software-center/apt-get, all the same tool with different front ends, automatic dependency resolution.
2) .deb files, double click to install, will try and resolve dependencies using the above method.
3) PPAs (could go second, there isn't much difference) are repositories run for apt, but not by canonical, just random users.
4) .tar.gz and other installer files.

---

### Post by migs73 on 2010-10-25
Welcome to Ubuntu. They don't use the tag line 'Linux for Human Beings' for nothing!

+1 on Synaptic/USC/apt-get

Made easy for all us non-IT people. ;)

EDIT; couldn't find it in USC but could in synaptic.

---

