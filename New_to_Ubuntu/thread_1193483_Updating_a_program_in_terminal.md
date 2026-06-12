---
title: "Updating a program in terminal"
date: 2009-06-21
forum: New to Ubuntu
---

### Post by benjamin.s.vaccaro on 2009-06-21
Hi,


I am using 9.04 and I have Azureus(Vuze). It keeps trying to install 4.2.0.2 and each time I get an error message "Error: Data missing /tmp/Azureus4.2.02.jar".

What it boils down to is, can I update a program or install an upgrade via terminal?
something along the lines of:
Sudo aptitude install Azerus 4.2.0.2

---

### Post by Sealbhach on 2009-06-21
No, you can't install a specific version from the command line. By default you will install the latest version available in the repos. If you add third party repos, you will often get a later version than the one in the official repos.

I seem to recall having a similar problem with Vuze, in the end I went back to using Transmisson.

.

---

### Post by Temposs on 2009-06-21
I assume this means Azureus itself wants to upgrade to a higher version. No, you can't do this with aptitude. Ubuntu 9.04 uses Azureus version 3.1.1.0-4ubuntu1. I recommend using that version and turning off the update checker in Azureus.

If you really want the newest version, go download a .deb file from the Azureus website.

---

### Post by sideffects on 2009-06-21
> **benjamin.s.vaccaro said:**
> Hi,


I am using 9.04 and I have Azureus(Vuze). It keeps trying to install 4.2.0.2 and each time I get an error message "Error: Data missing /tmp/Azureus4.2.02.jar".

What it boils down to is, can I update a program or install an upgrade via terminal?
something along the lines of:
Sudo aptitude install Azerus 4.2.0.2
IMHO, you should use Transmission. I used to use azureus, until I found out that uTorrent was better. Then I installed Ubuntu and started using Transmission and have been quite pleased. (I do still like uTorrent better though.)

---

### Post by Cheesemill on 2009-06-21
> **sideffects said:**
> IMHO, you should use Transmission. I used to use azureus, until I found out that uTorrent was better. Then I installed Ubuntu and started using Transmission and have been quite pleased. (I do still like uTorrent better though.)

You should try Deluge, it's more like uTorrent than anything else I've found (especially if you use the latest version from the PPA's)

---

### Post by spiderbatdad on 2009-06-21
aptitude can only install packages from the repos. The version of azureus you want to run isnt in the repos. It is available here:[http://azureus.sourceforge.net/#](http://azureus.sourceforge.net/#)

If you want to run it, uninstall azureus/vuze via synaptic package manager, then make a folder in your home directory called azureus...download the tar.bz2 from source forge and extract it in the directory you made...by right click and select extract here. Then launch from the terminal:```
cd azureus/vuze
./azureus
```

---

### Post by benjamin.s.vaccaro on 2009-06-21
Thanks, I'll use transmission then.

---

### Post by sideffects on 2009-06-21
> **Cheesemill said:**
> You should try Deluge, it's more like uTorrent than anything else I've found (especially if you use the latest version from the PPA's)
Awesome! I'll check it out.

---

