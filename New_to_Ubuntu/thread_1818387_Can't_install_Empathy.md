---
title: "Can't install Empathy"
date: 2011-08-04
forum: New to Ubuntu
---

### Post by lordievader on 2011-08-04
After an update the IM client Empathy was thrown of off my Ubuntu 11.04 install.
So I tried to reinstall it, but now it seems I cannot install it because of a few dependencies are not met. If I try to install one of the dependencies I get the error of no installation candidate.

When I try to install Empathy I get the following error:
```
The following packages have unmet dependencies:
 empathy : Depends: libcamel-1.2-23 (>= 3.0) but it is not installable
           Depends: libcamel-1.2-23 (< 3.1) but it is not installable
           Depends: libebook1.2-10 (>= 3.0.2.1) but 2.32.2-0ubuntu2 is to be installed
           Depends: libedataserver1.2-14 (>= 3.0.2.1) but 2.32.2-0ubuntu2 is to be installed
           Depends: libgck0 (>= 2.91.1) but it is not installable
           Depends: libgcr-3-0 (>= 2.91.4) but it is not installable
           Depends: libgnome-control-center1 (>= 1:2.91.2) but it is not installable
           Recommends: nautilus-sendto-empathy but it is not going to be installed
           Recommends: telepathy-indicator but it is not installable
E: Broken packages

```

It says something about broken packages, so I try to fix it with the command "sudo apt-get -f install"

This was the output:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

Hopefully someone knows how to install Empathy.

---

### Post by dniMretsaM on 2011-08-04
I don't know how to help, but you might try Pidgin (at least until you get Empathy back). I prefer it over Empathy myself.

---

### Post by lordievader on 2011-08-04
I guess I should indeed. I did prefer Empathy over Pidgin though...
Thank you for the hint.

---

### Post by Pazit on 2011-08-04
I had the same problem after upgrading to natty.

eventually I managed to download Empathy 2.34.0

try this link :

 [https://launchpad.net/ubuntu/natty/+source/empathy/2.34.0-0ubuntu3.1](https://launchpad.net/ubuntu/natty/+source/empathy/2.34.0-0ubuntu3.1)

Since you didn't mention the version you tried to install I hope it will 

help.

---

### Post by Rex Bouwense on 2011-08-04
Have you tried to install using the Synaptic Package Manager?  That is where I would go to try and re-install or if it is installed (by now) and not working use the broken package filter to install.

---

### Post by lordievader on 2011-08-04
It seems that package also needs something I do not have, I cannot find the package in Synaptic either...

I downloaded the 'original' package from your link, and running the autogen.sh gave the following error:
```
***Error***: You must have glib-gettext >= 2.2.0 installed
  to build Empathy.  Download the appropriate package for
  from your distribution or get the source tarball at
    ftp://ftp.gtk.org/pub/gtk/v2.2/glib-2.2.0.tar.gz

```

How can I install this glib-gettext?

Edit: I tried to install it through Synaptics (first try was through the terminal) and it wouldn't allow me to install, required me to fix broken packages.

---

### Post by lordievader on 2011-08-04
It seems I solved it. I tried deleting some repository's, one was called Telepathy, I guess that was the culprit. These sources where added through TweakUbunutu. It had updated the package empathy-common, and the package empathy wasn't updated, and couldn't handle the update it seems.

Well thank you for your help.

---

