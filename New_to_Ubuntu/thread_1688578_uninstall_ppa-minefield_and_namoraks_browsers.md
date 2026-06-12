---
title: "uninstall ppa-minefield and namoraks browsers??"
date: 2011-02-15
forum: New to Ubuntu
---

### Post by gmenfan83 on 2011-02-15
ok i tried to use the firefox beta and installed ppa minefield and namoraka browser,,,,
then i deleted them from synaptics manager and all was well ,,,then i did an update and they are back ,,,now when i search for them in synaptic i cant find them to delete again???im stumped!

---

### Post by sydbat on 2011-02-15
> **gmenfan83 said:**
> ok i tried to use the firefox beta and installed ppa minefield and namoraka browser,,,,
then i deleted them from synaptics manager and all was well ,,,then i did an update and they are back ,,,now when i search for them in synaptic i cant find them to delete again???im stumped!Did you go into "Software Sources" and uncheck the ppa? Otherwise, it will continue to want to install / update from the ppa.

---

### Post by TeoBigusGeekus on 2011-02-15
System>Administration>Software sources
Remove their repositories.

---

### Post by gmenfan83 on 2011-02-15
thank you guys for the fast responses ,,,only problem is i have no software source under administrations?

nm guys i found it in synaptics,,thanks again

---

### Post by TeoBigusGeekus on 2011-02-15
Right click your menus> Edit menus.
Find the system menu and tick Software Sources.

---

### Post by gmenfan83 on 2011-02-15
ok i deleted the ppa package ,and i was able to get rid of minefield but now i am trying to revert from namoraka to firefox using this 
```
sudo apt-get install --reinstall firefox
```and i get this output?

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reinstallation of firefox is not possible, it cannot be downloaded.
The following packages were automatically installed and are no longer required:
  libdesktop-agnostic0 fortunes-min libdesktop-agnostic-cfg-gconf fortune-mod
  librecode0 libdesktop-agnostic-vfs-gio libdesktop-agnostic-fdo-glib
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by TeoBigusGeekus on 2011-02-15
```
sudo add-apt-repository ppa:mozillateam/firefox-stable
sudo apt-get update
sudo apt-get install --reinstall firefox
```

---

### Post by gmenfan83 on 2011-02-15
> **TeoBigusGeekus said:**
> ```
sudo add-apt-repository ppa:mozillateam/firefox-stable
sudo apt-get update
sudo apt-get install --reinstall firefox
```
thank you ,,,,i actually just searched and found that i must have erased my mozilla repository when i was deleting the others hence no install

---

