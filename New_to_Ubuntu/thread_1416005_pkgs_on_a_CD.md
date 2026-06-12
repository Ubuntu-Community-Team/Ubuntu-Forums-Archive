---
title: "pkgs on a CD"
date: 2010-02-25
forum: New to Ubuntu
---

### Post by squrl on 2010-02-25
Are the packages on synaptic available to put on a CD/DVD for local use ??

Thanks

---

### Post by sdlm on 2010-02-25
If I understand you correct then yes, they are. goto var/cache/apt/archives/ put the packages you want on a CD and then take them to an offline computer and use sudo dpkg -i [filename] to install them (or gdebi).

Not that directory usually includes the stuff you already have installed, IIRC you can download and not install .deb files from te repos I am sure someone here knows how.

---

### Post by n0dix on 2010-02-25
You will need more than one DVD ;)

---

### Post by ubunterooster on 2010-02-25
You can buy this from linuxcd.org or osdisc.com.
Or go to the repo site (the url can be found in synaptic [ [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic or similar]) or click packages to install but choose "download packages only" and copy those files to a cd

---

