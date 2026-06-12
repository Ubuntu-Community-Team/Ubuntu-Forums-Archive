---
title: "Can't execute .deb files"
date: 2009-01-18
forum: New to Ubuntu
---

### Post by the8thstar on 2009-01-18
Hi there,

I can't execute .deb files in CrunchBang Linux. Each time I double click them, it opens the archive manager and not the installer.

Is there a way to solve this? CrunchBang uses Thunar as file manager.

Thanks in advance.

---

### Post by mrbiggbrain on 2009-01-18
DEB is the debian package manager, not all linuxes know how to handle them. maybe opening it as an archive is the best that your distro can do.

---

### Post by gjoellee on 2009-01-18
> **the8thstar said:**
> Hi there,

I can't execute .deb files in CrunchBang Linux. Each time I double click them, it opens the archive manager and not the installer.

Is there a way to solve this? CrunchBang uses Thunar as file manager.

Thanks in advance.

Right click on the the DEB file (package) and select "Open with". You should have a command option available. In the command option insert the following command.
```
gedebi
```

You can install the file from terminal easily:
1. Put the DEB file in your home folder
2. Open a terminal
3. If you don't know the name of the package (DEB file), but know that there are not other packages that you don't want to install in your home folder you can use this command:
```
sudo dpkg -i *.deb
```that will install all the DEB files in the selected directory (home folder)

---

### Post by Elfy on 2009-01-18
It's gdebi

---

### Post by the8thstar on 2009-01-18
Excellent. Thank you guys.

---

