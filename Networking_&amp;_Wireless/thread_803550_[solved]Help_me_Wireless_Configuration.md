---
title: "[solved]Help me: Wireless Configuration"
date: 2008-05-22
forum: Networking &amp; Wireless
---

### Post by salihumon on 2008-05-22
Dear all,

Can somebody help me. I use Windows Vista, which is an Acer Aspire 5610Z. I installed the newest version Ubuntu 8.04, but I can not connect to internet.

Can somebody help me in this issues:

1. to activate my wireless card (I think it is not activated)
2. to configure wireless network

maybe it will be helpful I'll post some screenshots of wireless network information currently from Vista:

[IMG]http://i79.photobucket.com/albums/j138/cartman_mon/screenshot4.jpg[/IMG]

[IMG]http://i79.photobucket.com/albums/j138/cartman_mon/screenshot1-1.jpg[/IMG]

[IMG]http://i79.photobucket.com/albums/j138/cartman_mon/screenshot2-1.jpg[/IMG]

[IMG]http://i79.photobucket.com/albums/j138/cartman_mon/screenshot3.jpg[/IMG]

Waiting for Your answer.

Thank You in advance,
mon

---

### Post by anystupidname on 2008-05-22
I'd suggest you post in this thread:
[http://ubuntuforums.org/showthread.php?t=779754&page=1](http://ubuntuforums.org/showthread.php?t=779754&page=1)
assuming the information already in it doesn't help you right off the bat.

Otherwise, provide "lspci -v" and "lsmod" output in this thread for starters.
It would be useful to know how the wireless router is configure too (wep or wpa etc...)

---

### Post by salihumon on 2008-05-22
> **anystupidname said:**
> I'd suggest you post in this thread:
[http://ubuntuforums.org/showthread.php?t=779754&page=1](http://ubuntuforums.org/showthread.php?t=779754&page=1)
assuming the information already in it doesn't help you right off the bat.

Otherwise, provide "lspci -v" and "lsmod" output in this thread for starters.
It would be useful to know how the wireless router is configure too (wep or wpa etc...)

It's a wep. Public network, I log in with students id, cuz it's actually a university network.

---

### Post by K.Mandla on 2008-05-26
Bump. I've been trying to help salihumon and it looks like the card is configured, an interface name is assigned, and the network is detected. However, the connection can't be established for some reason. 

If anyone has more experience with WPA than me, please chime in. It might be a authentication issue or something like that. Thanks in advance.

---

### Post by ubuntu_demon on 2008-06-05
This thread is solved. salihumon found the wiki page I created on how to do this and contacted me. The wiki page for connecting to MAASnet which is the wireless network of the university of Maastricht :

[https://help.ubuntu.com/community/WifiDocs/WirelessNetworkOfUniversityOfMaastricht](https://help.ubuntu.com/community/WifiDocs/WirelessNetworkOfUniversityOfMaastricht)

---

