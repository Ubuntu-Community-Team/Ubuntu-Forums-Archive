---
title: "Errors while installing updates"
date: 2009-07-02
forum: New to Ubuntu
---

### Post by xshagy on 2009-07-02
When I try to install certain updates they fail and it gives me these errors.  Could someone help me understand what's going on.  I'm new to ubuntu so please be gentle. thanks.

E: gnome-applets-data: subprocess post-installation script returned error exit status 139
E: gnome-applets: dependency problems - leaving unconfigured
E: ubuntu-docs: subprocess post-installation script returned error exit status 139
E: synaptic: subprocess post-installation script returned error exit status 139
E: gnome-app-install: dependency problems - leaving unconfigured
E: apturl: dependency problems - leaving unconfigured
E: evince: subprocess post-installation script returned error exit status 139
E: evolution-common: subprocess post-installation script returned error exit status 139
E: evolution: dependency problems - leaving unconfigured
E: evolution-plugins: dependency problems - leaving unconfigured
E: gnome-desktop-data: subprocess post-installation script returned error exit status 139
E: gnome-about: dependency problems - leaving unconfigured
E: language-selector: dependency problems - leaving unconfigured
E: update-manager: dependency problems - leaving unconfigured
E: evolution-documentation-en: subprocess post-installation script returned error exit status 139
E: gnome-system-tools: subprocess post-installation script returned error exit status 139


E: gnome-applets-data: subprocess post-installation script returned error exit status 139
E: gnome-applets: dependency problems - leaving unconfigured
E: ubuntu-docs: subprocess post-installation script returned error exit status 139
E: synaptic: subprocess post-installation script returned error exit status 139
E: gnome-app-install: dependency problems - leaving unconfigured
E: apturl: dependency problems - leaving unconfigured
E: evince: subprocess post-installation script returned error exit status 139
E: evolution-common: subprocess post-installation script returned error exit status 139
E: evolution: dependency problems - leaving unconfigured
E: evolution-plugins: dependency problems - leaving unconfigured
E: gnome-desktop-data: subprocess post-installation script returned error exit status 139
E: gnome-about: dependency problems - leaving unconfigured
E: language-selector: dependency problems - leaving unconfigured
E: update-manager: dependency problems - leaving unconfigured
E: evolution-documentation-en: subprocess post-installation script returned error exit status 139
E: gnome-system-tools: subprocess post-installation script returned error exit status 139

---

### Post by quixote on 2009-07-03
"dependency problems" means that a program (or "package") that the one being installed depends on is not there or not functional.  There are a couple of general things that might be worth trying.

1) in Synaptic (System > Administration > Synaptic) under the "Edit" menu, there's an option to "Fix Broken Packages".

2) If that doesn't help, or doesn't help enough, the command line way is to open a terminal (main menu > Accessories > Terminal) and type ```
sudo dpkg --configure -a
```Be sure to close synaptic before you do that.  It's not good to have two package managers trying to work at once.  ("dpkg" stands for "debian package manager" and synaptic is the GUI front end for it.)

Hope this helps.

---

