---
title: "apt-cdrom can't find cdrom"
date: 2011-05-11
forum: New to Ubuntu
---

### Post by xfilecsm on 2011-05-11
I'm having trouble checking for updated. KPackageKit can't find the natty cdrom. Using apt-cdrom add gives the following error:

apt-cdrom add
Using CD-ROM mount point /media/apt/
Identifying.. [ce3c168e46b345c6adc05b209f603d08-2]
Scanning disc for index files..

E: Unable to stat the mount point /media/Kubuntu\04011.04\040amd64/ - stat (2: No such file or directory)
E: Unable to stat the mount point /media/Kubuntu\04011.04\040amd64/ - stat (2: No such file or directory)

What am I missing? (NOOB here)

---

### Post by beew on 2011-05-11
> **xfilecsm said:**
> I'm having trouble checking for updated. KPackageKit can't find the natty cdrom. Using apt-cdrom add gives the following error:

apt-cdrom add
Using CD-ROM mount point /media/apt/
Identifying.. [ce3c168e46b345c6adc05b209f603d08-2]
Scanning disc for index files..

E: Unable to stat the mount point /media/Kubuntu\04011.04\040amd64/ - stat (2: No such file or directory)
E: Unable to stat the mount point /media/Kubuntu\04011.04\040amd64/ - stat (2: No such file or directory)

What am I missing? (NOOB here)

kpackagekit should have a list of its software sources somewhere. Go there and uncheck the box that says cd rom.

Sorry, can't  be more specific as I don't use KDE. But it is the same idea in gnome/Unuty but different software manager.

---

### Post by wildmanne39 on 2011-05-11
> **xfilecsm said:**
> I'm having trouble checking for updated. KPackageKit can't find the natty cdrom. Using apt-cdrom add gives the following error:

apt-cdrom add
Using CD-ROM mount point /media/apt/
Identifying.. [ce3c168e46b345c6adc05b209f603d08-2]
Scanning disc for index files..

E: Unable to stat the mount point /media/Kubuntu\04011.04\040amd64/ - stat (2: No such file or directory)
E: Unable to stat the mount point /media/Kubuntu\04011.04\040amd64/ - stat (2: No such file or directory)

What am I missing? (NOOB here)

Hi, I have kubunu installed in virtualbox and I checked he settins I do not see any reason to use that command as long as your repositories are set. In a terminal to update the system you would type sudo apt-get update. If I missed something please repost and I will try to answer your question.:)

---

### Post by ivanovnegro on 2011-05-11
Yeah, just uncheck the CD ROM source, you dont need it for updating your system, normally its also unchecked but seems the KDE guys made a fault, had this also after installing fresh Kubuntu 11.04.

---

### Post by wildmanne39 on 2011-05-11
> **beew said:**
> kpackagekit should have a list of its software sources somewhere. Go there and uncheck the box that says cd rom.

Sorry, can't  be more specific as I don't use KDE. But it is the same idea in gnome/Unuty but different software manager.
Hi also when your issue is resolved please mark the thread solved by using thread tools at the top of the page, Thanks and happy Kubuntuing.:)

---

