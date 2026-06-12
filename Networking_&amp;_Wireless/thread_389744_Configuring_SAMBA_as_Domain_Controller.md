---
title: "Configuring SAMBA as Domain Controller?"
date: 2007-03-21
forum: Networking &amp; Wireless
---

### Post by Sjoram on 2007-03-21
[http://wiki.samba.org/index.php/1.0._Configuring_Samba](http://wiki.samba.org/index.php/1.0._Configuring_Samba)

Trying to use this page to configure samba as a DC running on Ubuntu Server.  Stuck with step 3 as this seems to be for a RHEL distro? and I'm not sure what to do here with a Debian-based distro?

Any help appreciated!

Thanks in advance!

(FWIW, I'm migrating from a Windows domain - is this going to cause me problems trying to migrate machines from Windows to Linux DC? - Clients will still be WinXP)

(I'm running on an eval copy of Win2k3 at the mo with 27 days left before it dies on me!)

---

### Post by renzokuken on 2007-03-21
step 3 appears to be creating and installing rpms of the samba source specifically for RHEL.

all these are available in synaptic already packaged for Ubuntu

just run this instead of step 3 to install all those packages

```
sudo apt-get install samba
```

EDIT: by running this you can actaully skip all of steps 1-4

---

### Post by dmizer on 2007-03-21
as a dc, samba requires a static network.

for more information, see the first link in my sig.

---

