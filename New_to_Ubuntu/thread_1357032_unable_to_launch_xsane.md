---
title: "unable to launch xsane"
date: 2009-12-16
forum: New to Ubuntu
---

### Post by donkyhotay on 2009-12-16
I'm unable to launch xsane, I can scan using the CLI so I know the problem isn't with the scanner itself but with the xsane GUI interface. When I launch xsane through the CLI I get error:

(xsane:4850): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated
Segmentation fault

I'm running karmic 64bit, I was able to scan just fine with previous versions of ubuntu (up through jaunty). This is a clean install (not an upgrade). I do not have compiz (desktop effects) running. I've also tried performing a google search and have found [this post](https://blueprints.launchpad.net/ubuntu/+spec/spinbutton-adjustment-warnings) and [this post](https://bugs.launchpad.net/ubuntu/+source/xsane/+bug/341874) but neither give a solution.

---

### Post by donkyhotay on 2009-12-18
nobody?

---

### Post by kansasnoob on 2009-12-18
Not what you're really looking for but I always use the flegita front-end:

```
sudo apt-get install flegita
```

> Flegita intend to be a simple but powerful standalone utility based
on Gnome Scan Infrastructure. It allow to select scanner, select
document sources, preview, rotate and save to various format
(including PDF). Further functionnalities are planned such as mass
acquisition, multipage PDF, etc.

Regarding Xsane you might go to Synaptic and see if Xsane shows up broken, or just maybe try marking it for re-installation. Or maybe try running the command:

```
sudo apt-get -f install
```

To try and resolve any unmet dependencies.

---

