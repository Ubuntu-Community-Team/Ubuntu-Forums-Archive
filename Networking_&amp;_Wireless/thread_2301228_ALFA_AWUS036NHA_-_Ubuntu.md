---
title: "ALFA AWUS036NHA - Ubuntu"
date: 2015-10-31
forum: Networking &amp; Wireless
---

### Post by craig_boyle on 2015-10-31
Hello,

I've seen the previous posts about this adapter are at least a couple of years old with no answer about getting the AWUS036NHA to work under Ubuntu. Just wondering if anyone had an update/information to get this card up and running on Ubuntu 15.10. I've followed several tutorials and installed the ath9k_ht driver. It shows up after running 'lsusb' but not when running 'iwconfig'. I've attached the wireless-info.txt as recommended in the forum rules. 

Thanks very much.

---

### Post by jeremy31 on 2015-10-31
That is the same ID that the TP Link WN722N uses.  I have one and it works great in Ubuntu 14.04

---

### Post by craig_boyle on 2015-10-31
Hi Jeremy,

Are you saying I should use the driver for the WN722N?

Thanks

---

### Post by jeremy31 on 2015-10-31
I tried the Ubuntu 15.10 iso with my WN722N and I didn't have to download anything, it worked from the start.  I was able to put my wireless script results on dropbox as I couldn't remember my password for ubuntuforums

[https://www.dropbox.com/s/570ezx8fz75eu8z/wireless-info.txt?dl=0](https://www.dropbox.com/s/570ezx8fz75eu8z/wireless-info.txt?dl=0)

I haven't looked at it yet

---

### Post by craig_boyle on 2015-11-04
Hi Jeremy, sorry if I'm missing something here. Are you saying I should use the TP-Link [COLOR=#000000]WN722N [/COLOR]adapter instead of the ALFA? Is there no way to get the ALFA install on Ubuntu and working in a Virtualbox/Kali VM?

Thanks

---

### Post by jeremy31 on 2015-11-04
If you are using Ubuntu as a guest OS in VM, you might have to control the wifi from the host

---

### Post by craig_boyle on 2015-11-04
Ubuntu 15.10 desktop is host with Kali guest VM in VirtualBox. The problem is I can't get Ubuntu to recognise the card. Once that is achieved I should be able to add the adapter to the VM. Works fine on MacBook Pro with OS X 10.11 using Mediatek Wireless Utility on host with VirtualBox kali guest.

---

### Post by jeremy31 on 2015-11-04
Do you have access to another computer to see if the USB wifi works in it?

---

### Post by craig_boyle on 2015-11-04
Yes I have the card working on OS X 10.11

---

### Post by jeremy31 on 2015-11-04
What does ```
modprobe -c | grep 9271
``` return?

---

### Post by craig_boyle on 2015-11-05
This is the output:

alias usb:v0CF3p9271d*dc*dsc*dp*ic*isc*ip*in* ath9k_htc

---

### Post by jeremy31 on 2015-11-05
I noticed that you installed backports which shouldn't have been necessary, I would uninstall them.  In terminal get into the backports directory and
```
sudo make uninstall
```

reboot

I would also boot into the Ubuntu ISO and see if wifi works in Try Ubuntu

---

### Post by craig_boyle on 2015-11-05
Hi Jeremy, thanks for your continued assistance, much appreciated. When you go to the "backports directory" it appears the files are distributed across multiple directories. Because of this I'm not sure where to actually run the 'sudo make install' command. Would 'apt-get remove' or apt-get purge' not work? Obviously i could have just run those commands and found out but really don't want to break something I can't then fix 0_o

This is the result of 'locate backports'.

/usr/share/doc/xorg/reference/squeeze-backports.html
/usr/share/doc/xorg/reference/squeeze-backports.txt
/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_wily-backports_InRelease
/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_wily-backports_main_binary-amd64_Packages
/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_wily-backports_main_binary-i386_Packages
/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_wily-backports_main_i18n_Translation-en
/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_wily-backports_main_source_Sources
/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_wily-backports_multiverse_binary-amd64_Packages
/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_wily-backports_multiverse_binary-i386_Packages
/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_wily-backports_multiverse_i18n_Translation-en
/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_wily-backports_multiverse_source_Sources
/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_wily-backports_restricted_binary-amd64_Packages
/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_wily-backports_restricted_binary-i386_Packages
/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_wily-backports_restricted_i18n_Translation-en
/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_wily-backports_restricted_source_Sources
/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_wily-backports_universe_binary-amd64_Packages
/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_wily-backports_universe_binary-i386_Packages
/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_wily-backports_universe_i18n_Translation-en
/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_wily-backports_universe_source_Sources

My worry is that the /var/lib/apt/lists/ directory contains other packages. 

Thanks

---

### Post by jeremy31 on 2015-11-05
Lets try this to find it ```
ls | grep backports; ls Downloads/ | grep backports
```

There should be a folder somewhere named Backports-4.2-rc1-1 and usually it would be in Home or Downloads.  Check for updates and install, if you get newer kernel with the updates the backports won't install in the new kernel

---

### Post by craig_boyle on 2015-11-05
Ok, ran update and upgrade. Out from 'ls | grep backports; ls Downloads/ | grep backports'

~$ ls | grep backports; ls Downloads/ | grep backports
backports-4.2-rc1-1
backports-4.2-rc1-1.tar.gz

Both in the Downloads directory. So ran the 'sudo make uninstall' and get this output:


~/Downloads$ sudo make uninstall
make: *** No rule to make target 'uninstall'. Stop.

[ Sorry was in the wrong directory, now that seems to have removed backports ]

---

### Post by craig_boyle on 2015-11-05
Ok, now this is what I have when running 'iwconfig'. Appears the wireless card is now listed :) Great, it's now working and can connect to my WLAN. Jeremy you're a legend, fixed the problem and taught me a bunch of stuff in the process. Very much appreciated!

Probably in the wrong forum but have you nay expereince of adding this wireless card to a virtualbox VM as still not showing up in there :p. If not I'll pop over to the Kali forum and ask there. Thank again :)

---

### Post by jeremy31 on 2015-11-05
Check the virtualbox info first

---

### Post by craig_boyle on 2015-11-06
Will do. Thanks again for your support.

---

