---
title: "Where to get ndiswrapper outside of repositories"
date: 2008-04-29
forum: Networking &amp; Wireless
---

### Post by Iteria on 2008-04-29
I'm trying to to get a broadcom wireless card to work on a fresh install of Hardy. I was lucky enough to stumble upon the helpful guide for installing broadcom drivers using ndiswrapper, the only problem is my laptop has zero connectivity to the internet. I failed at getting the network card to work even with an ethernet cable. 

Thus, I can't just install ndiswrapper using the repositories. I tried visiting the sourceforge site for ndiswrapper, but version number is listed as 1.52 there and in the repository it's 1.9 (ndiswrapper-utils-1.9)

I don't know what to do.

---

### Post by dreamlusion on 2008-04-29
Hi Iteria,

I guess ndiskwrapper-utils-1.9 is a helper package that contains util scripts, it is not the actual ndiwrapper package. ndiwrapper module is in linux-ubuntu-modules-2.6.24-16-xxx package.

I'm not an expert, but I would suggest that you download the linux-ubuntu-modules-2.6.24-16-generic package for offline installation from here: [http://packages.ubuntu.com/hardy/linux-ubuntu-modules-2.6.24-16-generic](http://packages.ubuntu.com/hardy/linux-ubuntu-modules-2.6.24-16-generic). 

In order to install it follow these instructions [http://monkeyblog.org/ubuntu/installing/#installing_a_package_manually](http://monkeyblog.org/ubuntu/installing/#installing_a_package_manually)

As far as I saw it had not dependencies (sudo apt-cache depends <package>).

You may also want "ndisgtk" which is a graphical frontend for ndiswrapper. Please note that this package does have some dependencies.

Hope this helps,
Bye ;)

---

### Post by Ayuthia on 2008-04-29
ndiswrapper can also be found on the live CD.  You just need to add the CD to the repository list via Synaptic or by using sudo apt-cdrom add.  From there, you should be able to install ndiswrapper-common and ndiswrapper-utils-1.9.  The only thing that you would need from there is the Broadcom driver.

---

