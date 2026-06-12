---
title: "VMWare Fresh Install + system crash = VMWare vanished"
date: 2010-05-09
forum: New to Ubuntu
---

### Post by Iamiko on 2010-05-09
Hi all, hope someone can help me out with this one...

I had not long finished installing VMWare Workstation (which was working) when my system froze p and I had to reset it. Now I have no menu links to VMWare, nothing in my synaptic for VMWare beyond a graphics driver thingy (very technical term, i know) and the VMWare installer is insisting it has already ben installed and wont let me reinstall it....

... help please? I need to either reinstall VMWare or somehow work out how to start VMWare as things stand right now.

VMWare was installed from the .bundle package and i'm using Ubuntu 10.04 LTS 64 bit.

---

### Post by shae on 2010-05-09
VMware is just missing from the menu.  Unfortunately, there is a bug with Ubuntu and programs appearing in the menu.  The solution I found was to copy the following files to your home folder.

```
mkdir ~/.local/share/applications
cp /usr/share/applications/vmware-netcfg.desktop ~/.local/share/applications/vmware-netcfg.desktop
cp /usr/share/applications/vmware-player.desktop ~/.local/share/applications/vmware-player.desktop
cp /usr/share/applications/vmware-workstation.desktop ~/.local/share/applications/vmware-workstation.desktop
```

---

### Post by Iamiko on 2010-05-09
Thanks Shae :)

Had to set the files executable and do a reboot afterwards but that did the trick nicely :)

---

