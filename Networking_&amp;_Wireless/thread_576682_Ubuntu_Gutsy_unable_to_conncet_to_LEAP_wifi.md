---
title: "Ubuntu Gutsy unable to conncet to LEAP wifi"
date: 2007-10-15
forum: Networking &amp; Wireless
---

### Post by Homie Bongo on 2007-10-15
Hi al,
I cannot connect to LEAP protected network. It used to work, and it even saved the login info to the keyring (only after I manually launched the keyring manager). However soon after nm-applet got stuck and was no longer able to connect to the network. I thought I could help it by removing the keyring entry, but nm-applet didn't ask for the key anymore. No when I try to connect it says: 
"Waiting for network key to the wireless network xy".
launching keyring-manager by myself does not help -- nm-applet still does not ask me for any login data.

---

### Post by rnewman38 on 2007-11-09
Yes,

 Remove the network-manager version 0.7.0 you used in feisty fawn(7.04), and use the current release from gutsy gibbon(7.10) which is 0.6.5. Be sure to remove ALL packages using the 0.7.0 version even the relevant libraries and reinstall.

 Details:

 Remove packages:

libnm-glib0_0.7.0-cvs20061010_i386.deb
libnm-util0_0.7.0-cvs20061010_i386.deb
network-manager_0.7.0-cvs20061010_i386.deb
network-manager-gnome_0.7.0-cvs20061010_i386.deb
network-manager-vpnc_0.7.0-cvs20061010-1_i386.deb

 Install Packages from gutsy gibbon... That will now have the LEAP capability.

 One other gotcha is remove the network manager scripts in the directory '/etc/dbus-1/event.d' of the files
'25NetworkManager'
'26NetworkManagerDispatcher'

 Before reinstall from gutsy (7.10) distro.

 Cheers,

 Rob

---

