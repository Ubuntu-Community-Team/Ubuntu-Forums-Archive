---
title: "Removing KDE"
date: 2010-07-25
forum: New to Ubuntu
---

### Post by headbuster on 2010-07-25
Hello
I installed KDE but now I have lots of useless programs in my menu and I don't actually use KDE so how can I delete it? (and all the stuff it installed)
Thanks

---

### Post by collinp on 2010-07-25
You can probably take out most of the stragglers by removing the package kdebase, either through synaptic or through the following command:
```
sudo apt-get remove kdebase
```

---

### Post by headbuster on 2010-07-25
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package kdebase is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.

```

LOL?

---

### Post by warfacegod on 2010-07-25
You'll also want to remove the kubuntu-desktop package if it isn't removed by kde-base being taken out. You may want to search Synaptic for straggler KDE programs, afterward.

---

### Post by collinp on 2010-07-25
FAIL.

Alright, lets see..

```
sudo apt-get remove kdebase-bin libqt4-core
```

Try that.

---

### Post by headbuster on 2010-07-25
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libqt4-core is not installed, so not removed
The following packages will be REMOVED
  kdebase-bin konqueror kubuntu-konqueror-shortcuts
0 upgraded, 0 newly installed, 3 to remove and 4 not upgraded.
After this operation, 5,382kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 169643 files and directories currently installed.)
Removing kubuntu-konqueror-shortcuts ...
Removing konqueror ...
update-alternatives: using /usr/bin/chromium-browser to provide /usr/bin/x-www-browser (x-www-browser) in auto mode.
Removing kdebase-bin ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_GB.utf8.cache...
Processing triggers for man-db ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for python-support ...

```
....

---

### Post by headbuster on 2010-07-25
I went to the package manager there I went to installed and type KDE and clicked kde-base-"somethin" (i dont remember) and marked it for removal and a lot of things got marked. THen I removed it and now the programs are gone i think.
Does this mean that I am clear?

---

### Post by collinp on 2010-07-25
I **knew** it was one of the kdebase packages.

Yes, you should be clear now.

---

### Post by headbuster on 2010-07-25
Cool, thanks.
I also deleted some leftover stuff connected with KDE. some libs and stuff for the programs

---

### Post by headbuster on 2010-07-25
Only on thing left.
When I restart or boot there is a KUBUNTU logo on a blue background
.... and thats annoying :D
Do you know how to fix this?

---

### Post by warfacegod on 2010-07-25
Look for a Kubuntu splash of some kind in Synaptic. If you're running 10.04, splash is now called plymouth but I'm sure if that applies to kde as well.

---

### Post by headbuster on 2010-07-25
Thanks I found it!

---

