---
title: "Wireless help"
date: 2008-07-15
forum: Networking &amp; Wireless
---

### Post by rustyjr on 2008-07-15
I've just got back to using ubuntu and I've got a new wireless card after trying to install my old one to no avail. The problem I'm having is I can't see the hardware. I've used ndiswrapper and installed the driver but I can't get any wireless networking to work. Card 3CRGPC10075 7.04 ubuntu. any help would be great full. here is some of the stuff I've tried.
rustyjr@russell-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

rustyjr@russell-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

rustyjr@russell-laptop:~$ /sbin/iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

rustyjr@russell-laptop:~$ sudo apt-get install ndisgtk
Password:
Reading package lists... Done
Building dependency tree
Reading state information... Done
ndisgtk is already the newest version.
The following packages were automatically installed and are no longer required:
  libfreebob0 libmp4v2-0 libkonq4 libquicktime0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
rustyjr@russell-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

rustyjr@russell-laptop:~$

---

### Post by harmonica on 2008-07-15
im having the same problem. i just installed ubuntu on my brother's toshiba laptop and it wont recognize that there is a wireless device inside, though wireless worked fine with vista before i formatted and installed with ubuntu. i tried the same commands as rustyjr did, as per the wireless troubleshooting help guide right in the OS, but the computer simply won't recognize that the device is in there.

---

### Post by rustyjr on 2008-07-16
can anyone help please

---

