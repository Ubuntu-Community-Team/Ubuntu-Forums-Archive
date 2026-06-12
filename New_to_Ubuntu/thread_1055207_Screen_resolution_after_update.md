---
title: "Screen resolution after update"
date: 2009-01-30
forum: New to Ubuntu
---

### Post by garrydog on 2009-01-30
Hi
All was well,then the update came up on the top bar.So i downloaded the 39 updates ,computer up to date ,restart required .Did the restart,now i can only start in recovery,if I do a normal boot the screen is mostly black with 3 green ubuntu across the top of the screen .
And also in recovery my screen resolution is stuck in 800x600 as if the ATI driver has been  uninstalled .
Can someone tell me how to get out of this one .
Thanks .

---

### Post by avtolle on 2009-01-30
Cutting to the chase, you will need to reinstall the ATI driver due to the kernel upgrade.

---

### Post by dorkdork777 on 2009-01-30
Go into Recovery Mode, and drop back to root terminal.

Then run:
```
dpkg-reconfigure -phigh xserver-xorg
```

(Note: If there's an option to "reconfigure X" in Recovery, this does the same thing, so you could just pick that instead.)

When it asks you about video or graphics drivers, pick one of them. Go through everything else, then see if it boots normally. If not, try again, selecting a different video driver. Repeat until it boots.

By my knowledge, this should at least get you into a working desktop; we can work from there.

---

### Post by avtolle on 2009-01-30
From his post, it seems he's in a working desktop under recovery mode, as he says his screen resolution is 800x600 (as I read it).

---

### Post by garrydog on 2009-01-30
Hi
yes that's right i am working in recovery mode .

---

### Post by garrydog on 2009-01-30
can I install the ATI driver in recovery mode.

---

### Post by avtolle on 2009-01-30
> **garrydog said:**
> can I install the ATI driver in recovery mode.
Yes you can.

---

### Post by garrydog on 2009-01-30
david@david-desktop:~$ sudo dpkg-reconfigure -phigh xserver-xorg
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20090130192054

---

### Post by garrydog on 2009-01-30
david@david-desktop:~$  sudo dpkg-reconfigure x -phigh xserver-xorg
Package `x' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: x is not installed.
david@david-desktop:~$

---

### Post by garrydog on 2009-01-31
Hi
I have now reinstalled ubuntu 8.10,and i am back to the 800x600 screen resolution .I have the driver that i want to install ati-driver-installer-9-1-x86.x86_64.run.Can someone tell me how to get the automatic installer to work .To install the ATI Proprietary Linux driver using the Automatic option, follow
these steps:
1 Launch the Terminal Application/Window and navigate to the ATI Propri-
    etary Linux driver download.
2 Enter the command sh ./ati-driver-installer-8.573-x86.x86_64 to launch the
    ATI Proprietary Linux driver installer.
The ATI Proprietary Linux Driver Setup dialog box is displayed.how do I enter above command to start the installer .
Thanks

---

