---
title: "Installing Packages"
date: 2009-01-26
forum: New to Ubuntu
---

### Post by Tmoney1309 on 2009-01-26
Im confused about what to do after I have downloaded a package. I downloaded Cinelerra Movie Maker and when I try to open it it just comes up in Archive Manager. How do I start to use the program?

---

### Post by RomeReactor on 2009-01-26
Hi. If it's the .deb package, right click on it and select "Open with->GDebi package Installer". If you don't have that option, right click it, select "Properties", and on the "Open with" tab click "Add", then "Use custom command" and write **gdebi**. Then make sure GDebi is the selected application in the "Open with" tab.

You can also, however, add [Cinelerra's repository]("http://cinelerra.org/getting_cinelerra.php#intrepid") to the package managers: got to 'System->Administration->Software Sources" and on the "Third Party" tab, click "Add" and paste the following line:
```
deb http://akirad.cinelerra.org akirad-intrepid main
```

You'll be prompted to reload the repository information, so accept. Cinelerra will be available through Synaptic and the other package managers then, and will show up in the update manager whenever it gets updated.

---

### Post by Tmoney1309 on 2009-01-26
I changed it and now nothing happens when I click on it to open it?

---

### Post by RomeReactor on 2009-01-26
If you have the package in your desktop, please open a terminal (Applications->Accessories->Terminal) and paste the following:
```
cd Desktop
```
to change directory to the desktop, then:
```
sudo dpkg -i packagename.deb
```
where **packagename** is the actual name of the package. If I'm not mistaken it should be:
```
sudo dpkg -i addakirad.deb
```

---

