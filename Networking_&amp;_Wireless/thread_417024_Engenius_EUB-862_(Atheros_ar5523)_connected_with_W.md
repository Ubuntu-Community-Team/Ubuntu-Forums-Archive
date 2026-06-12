---
title: "Engenius EUB-862 (Atheros ar5523) connected with WPA - easy way - ndiswrapper + Wicd"
date: 2007-04-21
forum: Networking &amp; Wireless
---

### Post by sionghua on 2007-04-21
I got the above mentioned connected on Feisty. First thing is to use the synaptic package manager to remove these 2 packages
network-manager
network-manager-gnome

then follow the instruction in Yelp
Internet - Connecting to the Internet
to install the ndiswrapper driver. By the way I have attached the necessary files with this post.
then install Wicd, configure it and you are done! Easy isn't it? Should also work with WPA2.

---

### Post by sionghua on 2007-04-22
Although it works alright there is still a small glitch. The adapter will not be available when the computer is restarted but if I shut it down before starting again it works ok.

The adapter light will still blink but will not be detected by any OS (not working either in Feisty or XP), but in XP I can disconnect it and reconnect back and it works, but in Feisty if I disconnect it Feisty will freeze. How do I disable it before disconnecting it?

---

