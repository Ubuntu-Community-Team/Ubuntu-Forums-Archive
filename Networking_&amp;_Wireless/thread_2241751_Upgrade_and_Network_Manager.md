---
title: "Upgrade and Network Manager"
date: 2014-08-28
forum: Networking &amp; Wireless
---

### Post by georgesgiralt on 2014-08-28
Hello !
On my laptop I ran 12.04LTS for a long time. It has been upgraded to 14.04LTS recently.
I use this laptop mostly at home and, as such, I need to bypass NetworkManager because my home directory is on a big PC and served by NFS to my laptop. So the Wifi interface is managed using /etc/network/interfaces and comes up at boot, not after login in. So far, so good. 
From time to time I take the laptop outside home for travel. Then, I used to comment out the definitions for the wifi card on the interface files and start the network-manager service from/etc/init.d in order to get network using either Wifi or a 3G USB card. 
Since my upgrade, the /etc/init.d/network-manager startup script is no longer present. 
So I've to evolve and change my thinking and process.
What would you consider be good practice regarding this issue. How to get the same behaviour as before (or an equivalent one ?)
Many thanks in advance for your wisdom and help.
Best regards.

---

### Post by ajgreeny on 2014-08-28
I don't understand all the implications of the change from init.d but it may help you to look at upstart, and I think a good place to start doing that is [http://askubuntu.com/questions/tagged/upstart](http://askubuntu.com/questions/tagged/upstart)

---

