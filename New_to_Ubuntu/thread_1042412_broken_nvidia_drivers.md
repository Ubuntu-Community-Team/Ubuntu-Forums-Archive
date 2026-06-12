---
title: "broken nvidia drivers"
date: 2009-01-17
forum: New to Ubuntu
---

### Post by gailin'tux on 2009-01-17
Hi.

I am new to Ubuntu and Linux in general. After being tired of my Windows viruses and the like I thought I would try something new so here I am. I have an issue though. I tried install Nvidia drivers from the "pop up" telling me that I should use drivers however an issue has occured:

> E: /var/cache/apt/archives/nvidia-177-kernel-source_177.82-0ubuntu0.1_i386.deb: corrupted filesystem tarfile - corrupted package archive

Now it won't let me install other packages because this package is broken. Not the mention that I am running in 800x600 and it is driving me crazy.

Help!

One more thing. When I did "nvidia-xconfig" to try to fix the issue I got this:

> Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Device section "Configured Video Device" must have a Driver
                  line.

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'


and when I try add/remove, I get this:

> Failed to check for installed and available applications

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

---

### Post by mikewhatever on 2009-01-17
Did you do what it told you to, namely **sudo apt-get update** and **sudo apt-get install -f**?

---

### Post by gailin'tux on 2009-01-17
Yes. I get this error at sudo apt-get install -f 

> Unpacking replacement openoffice.org-writer ...
lzma: Decoder error
dpkg-deb: subprocess <decompress> returned error exit status 1
dpkg: error processing /var/cache/apt/archives/openoffice.org-writer_1%3a2.4.1-11ubuntu2.1_i386.deb (--unpack):
 short read in buffer_copy (backend dpkg-deb during `./usr/lib/openoffice/program/libsw680li.so')
dpkg: regarding .../openoffice.org-core_1%3a2.4.1-11ubuntu2.1_i386.deb containing openoffice.org-core:
 openoffice.org-core conflicts with openoffice.org-writer (<< 1:2.4.1-11ubuntu2.1)
  openoffice.org-writer (version 1:2.4.1-11ubuntu2) is present and installed.
dpkg: error processing /var/cache/apt/archives/openoffice.org-core_1%3a2.4.1-11ubuntu2.1_i386.deb (--unpack):
 conflicting packages - not installing openoffice.org-core
Errors were encountered while processing:
 /var/cache/apt/archives/openoffice.org-writer_1%3a2.4.1-11ubuntu2.1_i386.deb
 /var/cache/apt/archives/openoffice.org-core_1%3a2.4.1-11ubuntu2.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


and when I do an update I now have 9 broken packages!

---

### Post by mikewhatever on 2009-01-17
Try **sudo dpkg --configure -a**.

---

### Post by akshay.bhardwaj on 2009-01-17
try using dpkg or package manager to install broken packages...
that would work

---

### Post by gailin'tux on 2009-01-17
when I did sudo dpkg --configure -a I get this:
> 
 sudo dpkg --configure -a
[sudo] password for galin: 
dpkg: dependency problems prevent configuration of openoffice.org-gnome:
 openoffice.org-gnome depends on openoffice.org-core (= 1:2.4.1-11ubuntu2.1); however:
  Version of openoffice.org-core on system is 1:2.4.1-11ubuntu2.
dpkg: error processing openoffice.org-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-impress:
 openoffice.org-impress depends on openoffice.org-core (= 1:2.4.1-11ubuntu2.1); however:
  Version of openoffice.org-core on system is 1:2.4.1-11ubuntu2.
dpkg: error processing openoffice.org-impress (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-math:
 openoffice.org-math depends on openoffice.org-core (= 1:2.4.1-11ubuntu2.1); however:
  Version of openoffice.org-core on system is 1:2.4.1-11ubuntu2.
dpkg: error processing openoffice.org-math (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-draw:
 openoffice.org-draw depends on openoffice.org-core (= 1:2.4.1-11ubuntu2.1); however:
  Version of openoffice.org-core on system is 1:2.4.1-11ubuntu2.
dpkg: error processing openoffice.org-draw (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-gtk:
 openoffice.org-gtk depends on openoffice.org-core (= 1:2.4.1-11ubuntu2.1); however:
  Version of openoffice.org-core on system is 1:2.4.1-11ubuntu2.
dpkg: error processing openoffice.org-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nvidia-glx-177:
 nvidia-glx-177 depends on nvidia-177-kernel-source (>= 177.82); however:
  Package nvidia-177-kernel-source is not installed.
dpkg: error processing nvidia-glx-177 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-calc:
 openoffice.org-calc depends on openoffice.org-core (= 1:2.4.1-11ubuntu2.1); however:
  Version of openoffice.org-core on system is 1:2.4.1-11ubuntu2.
dpkg: error processing openoffice.org-calc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xulrunner-1.9-gnome-support:
 xulrunner-1.9-gnome-support depends on xulrunner-1.9 (= 1.9.0.5+nobinonly-0ubuntu0.8.10.1); however:
  Version of xulrunner-1.9 on system is 1.9.0.3+nobinonly-0ubuntu1.
dpkg: error processing xulrunner-1.9-gnome-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-uno:
 python-uno depends on openoffice.org-core (= 1:2.4.1-11ubuntu2.1); however:
  Version of openoffice.org-core on system is 1:2.4.1-11ubuntu2.
dpkg: error processing python-uno (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-emailmerge:
 openoffice.org-emailmerge depends on python-uno; however:
  Package python-uno is not configured yet.
dpkg: error processing openoffice.org-emailmerge (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox-3.0-gnome-support:
 firefox-3.0-gnome-support depends on xulrunner-1.9-gnome-support (>= 1.9~b4~); however:
  Package xulrunner-1.9-gnome-support is not configured yet.
dpkg: error processing firefox-3.0-gnome-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox-gnome-support:
 firefox-gnome-support depends on firefox-3.0-gnome-support; however:
  Package firefox-3.0-gnome-support is not configured yet.
dpkg: error processing firefox-gnome-support (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 openoffice.org-gnome
 openoffice.org-impress
 openoffice.org-math
 openoffice.org-draw
 openoffice.org-gtk
 nvidia-glx-177
 openoffice.org-calc
 xulrunner-1.9-gnome-support
 python-uno
 openoffice.org-emailmerge
 firefox-3.0-gnome-support
 firefox-gnome-support


and I have tried the package manager more than once without success...

---

### Post by mikewhatever on 2009-01-18
Frankly, this looks a bit over my head. Have you tried fixing broken packages with Synaptic? It's under Edit->Fix Broken Packages.
Let me clarify, is this a regular Ubuntu desktop install and you are just updating?

---

