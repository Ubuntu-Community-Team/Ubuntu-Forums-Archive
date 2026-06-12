---
title: "Program not installing."
date: 2010-01-17
forum: New to Ubuntu
---

### Post by todayisgood on 2010-01-17
I'm trying to install Virtual Box but got this:

> Install finished

Failed to install package 'virtualbox-3.1_3.1.2-56127_Ubuntu_karmic_i386.deb'

TERMINAL:

Selecting previously deselected package libqt4-opengl.
(Reading database ... 140068 files and directories currently installed.)
Unpacking libqt4-opengl (from .../libqt4-opengl_4.5.3really4.5.2-0ubuntu1_i386.deb) ...
Setting up libqt4-opengl (4.5.3really4.5.2-0ubuntu1) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Selecting previously deselected package virtualbox-3.1.
dpkg: regarding .../virtualbox-3.1_3.1.2-56127_Ubuntu_karmic_i386.deb containing virtualbox-3.1:
 virtualbox-ose-source conflicts with virtualbox
  virtualbox-3.1 provides virtualbox and is to be installed.
dpkg: error processing /home/name/Downloads/virtualbox-3.1_3.1.2-56127_Ubuntu_karmic_i386.deb (--install):
 conflicting packages - not installing virtualbox-3.1
Errors were encountered while processing:
 /home/name/Downloads/virtualbox-3.1_3.1.2-56127_Ubuntu_karmic_i386.deb

---

### Post by mk1w86 on 2010-01-17
Try running:

```
sudo apt-get remove virtualbox-ose-source
```

then try installing VirtualBox

then run:

```
sudo apt-get install -f
```

if necessary which will install all unmet dependencies. ;)

---

### Post by ankspo71 on 2010-01-17
Hi,
By any chance... are you trying to upgrade virtualbox? I'm asking because it looks like you have the Open Source Edition (virtualbox-ose-source) package already installed. You will probably have to go in Synaptic Package Manager and uninstall the current virtuabox installation first if this is true.
Hope this helps.

---

