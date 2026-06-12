---
title: "LibreOffice - should I uninstall OO first?"
date: 2011-02-24
forum: New to Ubuntu
---

### Post by cwmoser on 2011-02-24
Wanting to install LibreOffice v3.3.
Should I uninstall Open Office first?
I'm currently using OO v3.2

Is LibreOffice better than Open Office - or just more Open Source?

Carl

---

### Post by rburkartjo on 2011-02-24
cw you can keep both libre will work fine with oo still installed. your choice

---

### Post by gyussz on 2011-02-24
The LibreOffice installer should automatically remove any OpenOffice versions. I had some bad experiences with earlier development versions, but nothing bad can happen. If the installer fails you can always remove OO manually and start the installer again. Should be fine.

LibreOffice seems better for me in functionality, compatibility and provides a bit more seamless usability. I also prefer the name :)

---

### Post by Hedgehog1 on 2011-02-24
The guide to get the correct version of LibreOffice is:

[https://wiki.ubuntu.com/LibreOffice]("https://wiki.ubuntu.com/LibreOffice")

The steps for a typical install on 10.10 are:

```
sudo add-apt-repository ppa:libreoffice/ppa
```

```
sudo apt-get update
```

```
sudo apt-get install libreoffice
```
Complete the installation by including the Ubuntu (Gnome) desktop integration:
```
sudo apt-get install libreoffice-gnome
```

:KS

---

### Post by marl30 on 2011-02-24
To answer your question about whether Libreoffice is better... from my experience it seems to be better than OOo, only slightly though, at least for now. Yesterday Libreoffice 3.3.1 came out adding new icons and a bit more speed and stability. They promised that in a months time we'll see 3.3.2, which should bring further improvement and design changes. However, we'll need to wait until May to see most of the planned changes and the implementations of many of the new feathers requested by users. So, making the switch is the right choice, as Libreoffice is expected to evolve into the best ever open source Office. :)

---

### Post by rburkartjo on 2011-02-24
mar i agree about libre getting better with every new version.

---

### Post by Hagar Delest on 2011-02-27
See also that one: [LibreOffice broke my OpenOffice install ](http://ubuntuforums.org/showthread.php?p=10500663). LibO first RC used to remove OOo indeed but it isn't the case anymore. And they can run in parallel.

The PPA reps can lead to some troubles (see linked topic). That's why it's better to install through the official debs.

---

