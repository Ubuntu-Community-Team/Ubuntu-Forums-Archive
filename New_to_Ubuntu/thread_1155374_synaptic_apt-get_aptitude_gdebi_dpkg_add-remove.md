---
title: "synaptic apt-get aptitude gdebi dpkg add-remove"
date: 2009-05-10
forum: New to Ubuntu
---

### Post by wyhog on 2009-05-10
Can anyone tell me what each of these actually does and how they are related to each other and if each is only graphical or only command line? I have scoured the net and have come up with some partial answers and some conflicting answers. Here is some of what I've found.

synaptic = a graphical front end for apt-get? (also for aptitude?)

apt-get = command line package manager. Does not fully remove dependencies?

aptitude = command line and pseudo graphical replacement for apt-get which does fully remove dependencies?

gdebi = ? Installs deb packages that are _on my local computer_ but can't DL packages?

dpkg = ?

add-remove?

Thanks
Wyhog

---

### Post by mprince on 2009-05-10
Add/Remove is a completely graphical way to add applications/packages. It's probably best for anyone new to ubuntu.

---

### Post by Headbanger2510 on 2009-05-10
synaptic as you pointed out, is a graphical package manager (it has an autoremoving-like option).
apt-get is a command line tool for installing, removing, upgrading, updating, autoremoving (so it can remove dependencies), ... packages.
aptitude is a graphical package manager run in any terminal (i`m not sure about the function of removing non used dependencies).
dpkg has many uses i ignore but i know it can be used to install from the command line local packages.
gdebi can also install local packages but runs as a gui not in the cml (but i don`t know what you mean by dl packages).
add/remove is a synaptic-like program with an easier interface than synaptic, so it is not as usefull as synaptic.

---

### Post by Bölvaður on 2009-05-10
Basically they all are installers that follow which packages are install and which ones are used.
They use dpkg to install the packages, which you can also use if you like, but Add/Remove, synaptic and copying commands like sudo apt-get install inkscape

well and of course the great : [click this link]("apt:pidgin")

---

### Post by sgosnell on 2009-05-10
apt-get and dpkg are command-line apps.  dpkg installs packages on your filesystem, while apt-get downloads and installs packages, including dependencies.  It can remove dependencies and configuration files or not, depending on what you tell it to do.  Everything else is a gui for one of these.  gdebi is the front-end for dpkg, while synaptic, add-remove, and aptitude are front-ends for apt-get.  You can use any of the variations interchangeably.

---

### Post by wyhog on 2009-05-13
Thank you, sgosnell. That is the info I was looking for.
Wyhog

---

