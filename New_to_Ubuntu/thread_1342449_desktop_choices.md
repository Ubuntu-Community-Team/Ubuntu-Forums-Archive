---
title: "desktop choices"
date: 2009-11-30
forum: New to Ubuntu
---

### Post by manny43 on 2009-11-30
When installing UBUNTU can we choose with desktop to install before the OS is installed?
It would be nice to have that choice during the install process.

---

### Post by mjwilson1313 on 2009-11-30
if you are installing with a livecd then yes you can choose.  You can even just demo it.

---

### Post by whoop on 2009-11-30
Generally no (if I understand you correctly). There are various releases: Ubuntu (Gnome), Kubuntu (KDE), Xubuntu (Xfce) etc.
You could install ubuntu with the minimal cd (without a desktop) and then install any desktop after you installed it (using apt).

However you can also install any of the releases ((X)(K)Ubuntu) and install a variety of desktops (window managers) using synaptic, software center or apt after you completed the install.
You can choose what window manager (as long as you installed it) to run when you login, to try them out.

---

### Post by momrocker on 2009-11-30
> **manny43 said:**
> When installing UBUNTU can we choose with desktop to install before the OS is installed?
It would be nice to have that choice [COLOR=Red]_during the install process_[/COLOR].

Actually, if you boot up from a LiveCD and install from there (assuming your connected to the internet) you will have a choice between Ubuntu, Kubuntu, etc. Also, if you want to install just Ubuntu and try out others later, its as simple as opening your command line and installing xubuntu-desktop or whatever desktop you want

---

### Post by manny43 on 2009-11-30
If running KUBUNTU or XUBUNTU are you still running UBUNTU?

---

### Post by jacobs444 on 2009-11-30
yes, just using a different display manager.

---

### Post by jacobs444 on 2009-11-30
> **manny43 said:**
> When installing UBUNTU can we choose with desktop to install before the OS is installed?
It would be nice to have that choice during the install process.

this is why they make many different live disks with different window managers as the default, as you can only fit 704mb on one cd.

---

### Post by momrocker on 2009-11-30
> **manny43 said:**
> If running KUBUNTU or XUBUNTU are you still running _[COLOR=Red]UBUNTU[/COLOR]_?

Ubuntu is a pretty general word for the basic operating system that Kubuntu, Xubuntu, gOS, Mythbuntu, etc.etc. all run off of. If you install a new Desktop Enviroment (DE), your files from the other OS will be converted over or slightly changed in the install process if you decide to change it after you have one installed, because, if you "scratch under the surface" (heard that somewhere on this forum) you will find good old Ubuntu.

---

### Post by HermanAB on 2009-11-30
Mandriva will do that.  You can install every desktop system under the sun and then select which one you feel like using today when you log in.

---

### Post by jbrown96 on 2009-12-01
You can't choose your Desktop Environment from the LiveCD. All the *buntus come on CDs and there isn't enough space to provide multiple DEs on one CD. You can install any DE you want after you install any version of Ubuntu. 

For Gnome (normal Ubuntu) ```
sudo apt-get install ubuntu-desktop
```

For KDE (Kubuntu) ```
sudo apt-get install kubuntu-desktop
```

For XFCE (Xubuntu) ```
sudo apt-get install xubuntu-desktop
```

---

### Post by donato roque on 2009-12-01
When installing from an Ubuntu live cd, what you have is Gnome desktop by default.  If you want to install a specific Desktop environment (Gnome, KDE, Xfce) from a live cd, try burning the specific download (Ubuntu for Gnome, Kubuntu for KDE, Xubuntu for Xfce).  Of course even if you install Ubuntu with Gnome, you can still download the KDE desktop from the repository.  In which case, you will have the option to choose which desktop environment to use during boot up.

---

### Post by whoop on 2009-12-01
You can always use the ubuntu minimal cd, this comes without a desktop, and you can choose between some window managers during the installation process...

---

### Post by Simian Man on 2009-12-01
Most distros offer a DVD install which includes exactly what you say.  Under Fedora, for example, you can install Gnome, KDE, both or neither.  If you have an internet connection when installing, you can also choose to install Xfce, Lxde or any window manager as well.

It'd be nice if Ubuntu offered something similar, but they tend to value not confusing beginners over giving experienced users options - which I can understand.  This is also why Ubuntu is the only distro to relegate the other desktops to separate "distributions" - so as to not clutter the website and confuse beginners.

---

