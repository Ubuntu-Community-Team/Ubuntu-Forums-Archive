---
title: "Reinstall and keep settings/add-ons"
date: 2009-05-31
forum: New to Ubuntu
---

### Post by Diamond.Dave on 2009-05-31
I have installed 9.04 (my first linux/ubuntu ever). However, I want to use encryptfs but from what I've read on bodhi's pages I should have done that at install. Is there a way to backup/save all the add-ons, configs, etc that I've already done and then reinstall jaunty without losing what I've got? Can I just do a new install over the old one and keep that stuff? Any help is much appreciated as I move along the path. Thanks! :D

---

### Post by glennric on 2009-05-31
There are ways to back up your system and reinstall that will save your personal settings.  The system configurations files can be backed up also, but will need to be added back in later.  It all depends on what configurations and add-ons you are talking about.  You should give a link to this bodhi page that you are talking about so we can see what you are trying to do.  You should not need to reinstall to encrypt your drive.  It is probably easier to do at install, but it can be done later.

---

### Post by lovinglinux on 2009-05-31
You could backup your home partition and restore it after the new installation.

When you reinstall, make sure you [create a separate partition for /home](http://www.psychocats.net/ubuntu/separatehome), so next time you want to re-install you won't loose your settings and won't need additional steps to preserve them.

Additionally, you might want to save a list of installed software, to download them again all at once after the re-installation. To do that follow this:

> **lovinglinux said:**
> 
To replicate your packages selection on another machine (or restore it if re-installing), you can run this:

```
dpkg --get-selections > ~/my-packages
```

This will save a file called my-packages in your home directory. Make a backup of it, install the fresh release, then restore the file "my-packages" to new home partition and run this code in the terminal:

```
sudo dpkg --set-selections < my-packages && sudo apt-get dselect-upgrade
```

It will download and install all the programs for you, except those that you installed manually, if they are not in the new repository

---

### Post by sirgogo on 2009-05-31
You can also check out Remastesys ([http://en.wikipedia.org/wiki/Remastersys](http://en.wikipedia.org/wiki/Remastersys)), though you will have to deselect the kernel. Remastersys literally makes a ghost iso of your installation with all your files. If you deselct the proper boxes, you can keep all you add-ons and settings and still be able to install whatever it is you wanted to.

Good luck,
Abhejit Rajagopal

---

### Post by jou770d on 2009-05-31
> **lovinglinux said:**
> You could backup your home partition and restore it after the new installation.

When you reinstall, make sure you [create a separate partition for /home](http://www.psychocats.net/ubuntu/separatehome), so next time you want to re-install you won't loose your settings and won't need additional steps to preserve them.

Additionally, you might want to save a list of installed software, to download them again all at once after the re-installation. To do that follow this:
....

I find it a good idea as well to backup your /etc/apt/sources.list file if you added some resources.

---

