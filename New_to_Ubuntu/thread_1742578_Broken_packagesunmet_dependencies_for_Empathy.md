---
title: "Broken packages/unmet dependencies for Empathy"
date: 2011-04-29
forum: New to Ubuntu
---

### Post by deludrien on 2011-04-29
Hi, I accidentally cleared out some packages that were required for Empathy with Computer Janitor, and had to uninstall it. When I try to install empathy from Ubuntu Software Center or synaptic package manager, I get told that "empathy" is a broken package, and I am unable to fix it. This is the message I receive when I try to fix the package:

> E: Unable to correct problems, you have held broken packages.
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies
If I try to install Empathy with apt-get, I get this:

>  sudo apt-get install empathy
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:

The following packages have unmet dependencies:
 empathy : Depends: libchamplain-0.10-0 (>= 0.9.0) but it is not installable
           Depends: libchamplain-gtk-0.10-0 (>= 0.9.0) but it is not installable
           Depends: libgck0 (>= 2.92.92.is.2.91.1) but it is not installable
           Depends: libgcr-3-0 (>= 2.92.92.is.2.91.4) but it is not installable
           Depends: libgnome-control-center1 (>= 1:2.91.2) but it is not installable
           Recommends: nautilus-sendto-empathy but it is not going to be installed
           Recommends: freedesktop-sound-theme but it is not installable
E: Broken packages
What can I do?

EDIT: I also just upgraded from Maverick to Natty, if that's of any importance.

---

### Post by mörgæs on 2011-04-29
I wouldn't spend long time on a system with trouble after an update. There can be lots of other problems hiding below the surface, so better to back up and reinstall.

[http://ubuntuforums.org/showthread.php?t=1580857](http://ubuntuforums.org/showthread.php?t=1580857)

---

### Post by deludrien on 2011-05-01
Okay, after reinstalling Natty, I have noticed a problem trying to update to Empathy 3 from the Telepathy PPA. When I try to install, I get these messages:

> empathy: Depends: libcamel1.2-19 (< 2.33) but 2.32.2-0ubuntu2 is to be installed
         Depends: libchamplain-0.10-0 (>= 0.9.0) but it is not going to be installed
         Depends: libchamplain-gtk-0.10-0 (>= 0.9.0) but it is not going to be installed
         Depends: libgck0 (>= 2.92.92.is.2.91.1) but it is not going to be installed
         Depends: libgcr-3-0 (>= 2.92.92.is.2.91.4) but it is not going to be installed
         Depends: libgnome-control-center1 (>= 1:2.91.2) but it is not going to be installed
         Depends: libgtk-3-0 (>= 3.0.2) but 3.0.8-0ubuntu1 is to be installed
         Depends: libnspr4 (>= 4.7.0~1.9b1) but 4.8.7-0ubuntu1 is to be installed
         Depends: libnss3 (>= 3.12.2~rc1) but 3.12.9+ckbi-1.82-0ubuntu2 is to be installed
         Depends: libsqlite3-0 (>= 3.7.3) but 3.7.4-2ubuntu5 is to be installed
         Depends: empathy-common (= 3.0.0-1~ppa11.04+1) but 3.0.0-1~ppa11.04+1 is to be installed
What does this mean, and how can I fix it?

---

### Post by mörgæs on 2011-05-01
Since the error is also in a fresh installation, I would open a bug report:

[https://launchpad.net/ubuntu](https://launchpad.net/ubuntu)

---

### Post by Benzoate on 2011-05-03
Not the best solution, but the missing packages are in the gnome ppa

```
sudo add-apt-repository ppa:gnome3-team/gnome3 
sudo apt-get update
```

Of-course, this will probably break everything, and the world will explode. Enjoy.

---

### Post by sathgarcia on 2011-06-29
hi everyone...

the following works for me... i thought these would help you too...

sudo add-apt-repository ppa:telepathy/ppa

sudo apt-get install gnome-common gettext libglib2.0-dev gtk-doc-tools libxml2-dev  libtelepathy-glib-dev libmissioncontrol-client-dev  libtelepathy-farsight-dev libx11-dev libgtk2.0-dev libcanberra-gtk-dev libgstreamer-plugins-base0.10-dev libebook1.2-dev libnotify-dev libunique-dev libgnome-keyring-dev

if libmissioncontrol-client-dev packages is not found just like what happened in mine, remove it and continue with the apt-get install on the rest of the packages.

then, look for this files, download & install... (unfortunately i forgot about which comes first, but surely you will figure it out) you may try the following order though...
1.) libtelepathy-dev_0.3.3-1_i386.deb
2.) libtelepathy2_0.3.3-1_i386.deb
3.) libmissioncontrol-client-dev_4.60-1_i386.deb
4.) libmissioncontrol-client0_4.60-1_i386.deb
5.) libcamel-1.2-23_3.0.0-1_i386.deb
6.) libebook1.2-10_3.0.2.1-0ubuntu1_i386.deb
7.) libedataserver1.2-14_3.0.2.1-0ubuntu1_i386.deb / 
8.) libgck0_3.0.3-2_i386.deb
9.) libgcr-3-0_3.0.3-2_i386.deb

finally, sudo apt-get install empathy

i have attached the files that i found and used... you may download it.
hope this would help... it works on mine (ubuntu 11.04)


God Bless.

---

### Post by donny.davis on 2011-06-29
i dont know whether this will work
but just try out

[http://www.mydigitallife.info/ubuntu-unmet-dependencies-not-going-to-be-installed-or-try-apt-get-f-install-error/](http://www.mydigitallife.info/ubuntu-unmet-dependencies-not-going-to-be-installed-or-try-apt-get-f-install-error/)

---

### Post by gesti on 2011-09-29
> **Benzoate said:**
> Not the best solution, but the missing packages are in the gnome ppa

```
sudo add-apt-repository ppa:gnome3-team/gnome3 
sudo apt-get update
```Of-course, this will probably break everything, and the world will explode. Enjoy.

 Thanks for this one. It helped and nothing exploded! :P
BTW why would anything have to explode because of this?

---

