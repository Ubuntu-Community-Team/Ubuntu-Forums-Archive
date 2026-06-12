---
title: "How to acces usb in windows xp running in virtualbox 3.2 (ubuntu 10.04)?"
date: 2010-06-04
forum: New to Ubuntu
---

### Post by Parkerf1231 on 2010-06-04
I am running ubuntu 10.04 and have just installed virtualbox ose (the newest version on the software center) and obtained windows xp black which i have set up in virtual box. Windows xp works perfectly and everything but i can't use the any usb ports. I've checked way too many videos and posts about the same problem however none seem to be for the new version of ubuntu. If anyone could help me with this it would be greatly appreciated.

---

### Post by sandyd on 2010-06-04
> **Parkerf1231 said:**
> I am running ubuntu 10.04 and have just installed virtualbox ose (the newest version on the software center) and obtained windows xp black which i have set up in virtual box. Windows xp works perfectly and everything but i can't use the any usb ports. I've checked way too many videos and posts about the same problem however none seem to be for the new version of ubuntu. If anyone could help me with this it would be greatly appreciated.
```

gksudo gedit /etc/apt/sources.list

```add
```

deb http://download.virtualbox.org/virtualbox/debian lucid non-free

```to the bottom.
save, and run
```

sudo apt-get remove virtualbox-ose
sudo apt-get update
wget -q http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc -O- | sudo apt-key add -
sudo apt-get install virtualbox-3.2 dkms
```

---

### Post by Parkerf1231 on 2010-06-04
wow thanks so much, i guess it was because i was using virtualbox ose? whatever it was thank you for helping me fix it.

---

### Post by anewguy on 2010-06-04
Yes, just to follow up on Carlee's great advice and solution, the OSE (Open Source Edition) of VirtualBox does not have USB support.  To get USB support in VirtualBox, you must install the PUEL (not sure, Private Use Enduser License?) version - it is free to download and install for non-commercial use, but it is not open source.


Dave ;)

---

