---
title: "Wireless profile in network-manager-gnome isn't saved"
date: 2007-03-25
forum: Networking &amp; Wireless
---

### Post by kurbacik on 2007-03-25
I connect to my university's wireless network with network-manager-gnome (and wpa_supplicant) but when I want to connect to the network again I have to reinsert the values for the profile, since it isn't saved somehow. You can all understand how annoying this can be. I have recently compiled the newest version of ndiswrapper (1.39) on my laptop (an HP zv5000 with Broadcom 4306 wireless card and Edgy i386) and it seems to be working much better now (signal strength is now detected perfectly). Has anybody else observed this behavior?

---

### Post by Floppyjoe on 2007-03-25
When you installed network-manager did you compile it yourself and possibly not install it as root? If this is even possible it(network-manager) might not have the permissions to save the file.

---

### Post by kurbacik on 2007-03-25
There is a wireless entry in gconf for all of my wireless profiles, even for the university one. It just happens that network-manager-gnome doesn't connect at all automatically at the end of the boot. I have no problem at all for open wireless access points. I thought too that it might have to do with permission restrictions, but it shouldn't be the case here, since all profiles are saved in the .gconf folder in the home directory. I didn't compile it by source (I did try to compile it but I wasn't successful). I just installed the packages through synaptic. Could it have to do with the keyring-manager? I have to enter my keyring password before connection is established.

---

### Post by Floppyjoe on 2007-03-25
Did you make a wpasupplicant.conf file?(I'm not sure that that is the right name for it but this file keeps your WPA settings in it).
[https://help.ubuntu.com/community/WifiDocs/WPAHowTo](https://help.ubuntu.com/community/WifiDocs/WPAHowTo)

---

### Post by kurbacik on 2007-03-26
I tried that solution too but apparently it doesn't seem to be necessary, since connection is establish even without that file. To be precise, the profile exists in the .gconf/ folder but network-manager-gnome doesn't connect to the university wireless network automatically. I need to reinsert the whole profile just as if nothing has been saved. Do you think this might be a bug? I'm tempted to file it.

---

