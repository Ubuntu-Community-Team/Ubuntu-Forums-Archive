---
title: "adding usb to virtualbox"
date: 2008-12-04
forum: New to Ubuntu
---

### Post by RadiationHazard on 2008-12-04
I have installed VirtualBox with Windows XP running in it. I'm running Ubuntu 8.10 how do I configure  Ubuntu so that it will let the VirtualBox OSE access the usb ports on my computer?

---

### Post by adult swim on 2008-12-04
i dont think virtualbox OSE will work with usb's, you need virtualbox PUEL and then have to edit a file to get usb's to work.  you can find info on that if you google "virtualbox, magic to get usb working"

---

### Post by linux6994 on 2008-12-08
I have usb devices working in virtualbox (xp)

1. I installed the virtualbox via [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads) installing the package right from the site selecting intrepid i386. 

2. Once it was installed I went to system/administration/users and groups looked for the virtualbox user and checked myself noting the group number (125).

3. Next step was to enable the usbfs
    sudo gedit /etc/fstab
and add      none /proc/bus/usb usbfs devgid=125,devmode=664 0 0
to the last line. save and reboot.

4. Open virtualbox via the menus and on a created machine under the usb section add filter1.

This will give you usb support and one the machine is up add guest additions to XP then you can connect any of the devices that are connected by just checking them in the top device menu.

good luck.

---

### Post by anewguy on 2008-12-08
As mentioned prior, I believe you have to install the PUEL (free, but not open source) version instead of the OSE (open source edition) to get USB support.  Then follow the above post for configuring Ubuntu for USB support.  When setting USB filter 1 in the virtual machine configuration, leave it just empty - this allows all USB devices.

Dave

---

