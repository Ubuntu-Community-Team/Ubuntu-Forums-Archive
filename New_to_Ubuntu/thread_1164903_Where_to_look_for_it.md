---
title: "Where to look for it?"
date: 2009-05-20
forum: New to Ubuntu
---

### Post by HugoB on 2009-05-20
Hi

(a previously question similar to this one was posted by me, but I can't find it)

Is it possible to backup all installs of packages / applications that was automatically downloaded and installed on a Ubuntu machine?

I would like to know if there is a location on the Ubuntu system that stores the installation files of those packages / applications so that it can be backed up for future usage.

This might be useful, if I had to reinstall Ubuntu and then manually install those packages / applications onto the new Ubuntu installation.

Thank you in advance.

---

### Post by mcduck on 2009-05-20
All the packages downloaded when you install/update things with package management tools are cached in /var/cache/apt/archives. Unless you have removed them at some point (by hand, or by running "sudo apt-get clean) they should still be there.

You can pretty much just copy them to same location on new machine, and package management tools will then use those packages instead of downloading the same packages again from repositories. Alternatively you can also just use "sudo dpkg -i *.deb" to install them all.

OF course that won't save your program settings, only the program packages. To save the settings just copy the hidden configuration files from your home directory.

---

### Post by Didius Falco on 2009-05-20
There is a package called "aptoncd" in Synaptic Package Manager. Here is the relevant part of the description:

> This tool will allow you to create a media (CD or DVD) to use to install
software via APT in a non-connected machine, as well upgrade and install
the same set of softwares in several machines with no need to re-download
the packages again.You can also just tell it to create an iso. That way you could just mount the iso as a cd and use that to install the packages.

Works a treat for me.

I hope this helps...

Regards,

Didius

---

### Post by HugoB on 2009-05-20
Hi people

Thank you very much for the advice. I haven't tried it yet, but I will do so very soon.

2 more questions (it might be a general question, but I am still very new to this) I would like to ask:

1) Does Ubuntu have some sort of location under the Synaptic Package Manager that shows only the new packages that was installed on top of the Ubuntu installation?

2) Does anyone know if the packages of EnvyNG (it was downloaded and installed) are also included under the Synaptic Package Manager when an iso is created of the packages (using the tool that someone mentioned earlier in the forum)?

Thanks! :)

---

