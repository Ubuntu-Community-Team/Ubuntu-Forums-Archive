---
title: "Opera package installation problem!!"
date: 2009-09-07
forum: New to Ubuntu
---

### Post by | Gnome | on 2009-09-07
I wanted Opera on my Jaunty Ubuntu. So, I downloaded the opera (.deb) package from opera's site. Then, when I tried to install it the Package Installer says: E**rror: Dependency is not satisfiable: libqt3-mt (>= 3.3.4)**

Please tell me what might be the problem??
Same happens with the chromium package.

---

### Post by Cheezespread on 2009-09-07
It's just warning you that , you won;t be able to proceed further with the installation unless the dependencies are met . In this case being the package : libqt3-mt . The same needs to be installed or updated so that you can have Opera on your machine.

You can always install the same from Synaptic or using apt-get through terminal which will consider the dependencies and let you install them along.

Have a look [here]("http://ubuntuforums.org/showthread.php?t=1148100")

---

### Post by | Gnome | on 2009-09-07
I checked out the link. But there's not an exact solution. Installation link from repos also don't work. And I don't want to download deb package again. Isn't there any way to make that deb package that I downloaded to work? 
Or else please give me a "working" download link for repository download.

---

### Post by Cheezespread on 2009-09-10
Try [this ]("http://packages.ubuntu.com/jaunty/libqt3-mt"). Apologies . Was away .
Thats the package details your thread refers to. Hope this helps.

---

