---
title: "Boot screen resolution problem"
date: 2010-05-02
forum: New to Ubuntu
---

### Post by FotiX on 2010-05-02
I have Ubuntu 10.04.
I tried to install PlayonLinux from a deb file and there was a problem that left the process hanging. I used xkill on it, but when I rebooted i noticed that the purple loading screen had reduced its resolution from the slick 1280x800 to a measly 640x480 (i think). How can I revert it?

The problem with the installation was with the python packages.

---

### Post by Martin Marshalek on 2010-05-02
This isn't a problem with the playonlinux installation, you probably didn't notice on the first reboot after installing proprietary drivers. The new bootscreen uses Plymouth which uses Kernel Mode Setting. This is not available to restricted drivers so, without hacks to grub and/or Plymouth itself, you are stuck with this. As for killing the Playonlinux install, you should be able to purge what you did install and retry it.

---

