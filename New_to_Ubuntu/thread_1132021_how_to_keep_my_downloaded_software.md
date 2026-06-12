---
title: "how to keep my downloaded software?"
date: 2009-04-21
forum: New to Ubuntu
---

### Post by RajaAjmal on 2009-04-21
hi there,

currently, i'm using ubuntu 8.10, and i've downloaded and installed some programs from synaptic like nasm, xpda, pdfeditor, okular, also codecs to play dvd, mp3 and so on.

now i want to install ubuntu 9.04. Is there a way for me to install the new ubuntu and install the software that i've mentioned above without re-downloading them again?

please give step-by-step instructions if it is possible.

---

### Post by northern lights on 2009-04-21
Upgrade your system instead of re-installing.

Disable all third party repositories (System > Administration > Software Sources), execute```
sudo update-manager -d
``` and click the upgrade button. Make sure you won't need your machine for a while.

---

### Post by achase79 on 2009-04-21
in synaptic there is a way to "save markings"  I am not sure if this works across updates but is worth a look at.

---

### Post by Paqman on 2009-04-21
You can also [create a list of installed packages automatically]("http://ubuntuforums.org/showthread.php?t=261366").

---

### Post by RajaAjmal on 2009-04-21
thanks for the reply northern light.
but does that mean that it is impossible to install a fresh copy of ubuntu 9.04 and then install programs that i've already downloaded and installed from synaptic in ubuntu 8.10.

---

### Post by spupy on 2009-04-21
I haven't used it in a while, but I think that synaptic has the feature to generate script that installs all packages installed at the moment. You would still need to download them all.
Perhaps you could find the debs from wherever they are stored, copy them to a safe place, upgrade to 9.04, replace them in the folder where you found them and run the script that synaptic generated.

---

### Post by Paqman on 2009-04-21
> **RajaAjmal said:**
> thanks for the reply northern light.
but does that mean that it is impossible to install a fresh copy of ubuntu 9.04 and then install programs that i've already downloaded and installed from synaptic in ubuntu 8.10.

9.04 will have newer versions of most packages anyway, so you want to reinstall them from the 9.04 repos. All you settings and preferences will be retained if you copy your /home folder over (or if you have a separate /home)

Doing an upgrade instead of a reinstall will upgrade all your packages automatically.

---

### Post by northern lights on 2009-04-21
> **RajaAjmal said:**
> but does that mean that it is impossible to install a fresh copy of ubuntu 9.04 and then install programs that i've already downloaded and installed from synaptic in ubuntu 8.10.It is not impossible to keep a list of what you've installed:```
dpkg --get-selections > myapps
```It can be used later (after a reinstall or on another machine) to avoid having to manually select all the packages you want.
However, it will not spare you from having to download them again. A fresh install overwrites the entire partition.

If you want to avoid that also, you have to upgrade.

---

### Post by juancarlospaco on 2009-04-21
**Synaptics ---> File ---> Save selections...**

it generates a plain TXT file with selections inside, 
this file can be loaded on other systems to install the same software, 
or the same system with upgraded SO *(if the Software still existing)*

---

### Post by lovinglinux on 2009-04-21
> **northern lights said:**
> It is not impossible to keep a list of what you've installed:```
dpkg --get-selections > myapps
```It can be used later (after a reinstall or on another machine) to avoid having to manually select all the packages you want.
However, it will not spare you from having to download them again. A fresh install overwrites the entire partition.

If you want to avoid that also, you have to upgrade.

You have to download again, but it is pretty easy to use this method. The [link posted by Paqman](http://ubuntuforums.org/showthread.php?t=261366) provides instructions on how to download them again after re-installing the OS. Please notice that programs installed manually via [deb](http://en.wikipedia.org/wiki/deb) files or other methods won't be downloaded by this method. You have to install them again manually, so it is a good idea to keep copies of the [deb](http://en.wikipedia.org/wiki/deb) files when you install something this way.

If you don't have a separate [partition](http://en.wikipedia.org/wiki/partition) for the /home directory, then upgrading is the best choice, otherwise you will loose configurations and personal files if you don't backup them. If you decide to do a clean install, then I recommend[ creating a separate partition for your /home](http://www.psychocats.net/ubuntu/partitioning). This will allow you to install new versions without loosing your stuff and customizing all over again.

---

### Post by mkvnmtr on 2009-04-21
I am upgrading on one machine right now. It seems all my apps are being redownloaded so as to install the versions for 9.04. I assume that the versions for 8.10 will be deleted in the upgrade.

---

### Post by Paqman on 2009-04-22
> **mkvnmtr said:**
> I am upgrading on one machine right now. It seems all my apps are being redownloaded so as to install the versions for 9.04. I assume that the versions for 8.10 will be deleted in the upgrade.

Yep. In a lot of ways, upgrading from one version to another is just like running a normal package update.

---

