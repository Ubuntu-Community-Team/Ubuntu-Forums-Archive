---
title: "Setting up s static ip for home network"
date: 2007-01-11
forum: Networking &amp; Wireless
---

### Post by Alz on 2007-01-11
I installed the wifi card using these instructions: [http://ubuntuforums.org/showthread.php?p=1071920&mode=linear](http://ubuntuforums.org/showthread.php?p=1071920&mode=linear)

but I cant manage to get a static IP setup for network-manager-gnome. I setup static IP in System->Administration->Networking, but the network-manager-gnome seems to override them and use dhcp instead, which means I can't connect to my network. Anyone have a pointer on how to get it working? I had a look here: [http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539) 
but I got lost at instruction #3 :/. I messed about with the interfaces files, but I almost messed it up >.<. Thanks. :)

---

### Post by spd106 on 2007-01-11
Basically you need to disable/remove network manager and just use wpa_supplicant. FYI N-M uses wpa_supplicant to perform all of the background encryption. To get it set up you can either put all of the settings in the /etc/network/inrterfaces file as in the linked guide or if you're on edgy you can put the encryption settings (all those prefixed with wpa) in the wpa_supplicant.conf file.

Have a read through this wiki page to help out a bit [http://www.ubuntuforums.org/showthread.php?t=185174](http://www.ubuntuforums.org/showthread.php?t=185174) (hint: scroll down to wpa_supplicant)

---

### Post by compwiz18 on 2007-01-11
Try link to Connection Manager is my sig - allows static ips.

---

### Post by Alz on 2007-01-11
Thanks guys, I will try this tomorrow :)

---

