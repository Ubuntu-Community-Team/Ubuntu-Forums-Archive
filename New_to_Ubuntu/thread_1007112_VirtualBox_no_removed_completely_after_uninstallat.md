---
title: "VirtualBox no removed completely after uninstallation"
date: 2008-12-10
forum: New to Ubuntu
---

### Post by uarale on 2008-12-10
Hi,

since vmware player is a better virtual environment to work around with, i removed virtualbox from my machine.

but after uninstallation, each time starting my computer, i noticed a message that say:
>  * Starting VirtualBox kernel module vboxdrv                                    
 * No suitable module for running kernel found

it takes some time, and besides i dont like this clutter. so, how to completely uninstall virtualbox?

thank you.

---

### Post by taseedorf on 2008-12-10
not sure exactly, but i believe you need to remove it in the folder /etc/init.d/

---

### Post by theozzlives on 2008-12-10
Which version, the OSE or the one from VirtualBox.org?

---

### Post by Julita on 2008-12-10
There must be configuration files left on your disk. Open Synaptic, then find everything that is related to virtualbox, and with right click check (where available) "remove completely" or how is it called... I do not use Ubuntu in English, but it should be there.

---

### Post by uarale on 2008-12-10
I've found a file and a folder related to virtualbox remaining in the system (though the application was removed via $ sudo apt-get remove virtualbox :| )

file: /etc/init.d/vboxdrv
folder: /etc/vbox contains 2 files: interfaces, vbox.cfg

may be i will remove the file vboxdrv and see what happens. hope that don't lead to any harm to my machine.

---

### Post by uarale on 2008-12-10
> **theozzlives said:**
> Which version, the OSE or the one from VirtualBox.org?

I installed it from Applications > Add/Remove... , find for "virtualbox" and choose "VirtualBox OSE"

---

### Post by taseedorf on 2008-12-10
well, don't simply delete them.
you must remove the links too

update-rc.d vboxdrv remove

---

