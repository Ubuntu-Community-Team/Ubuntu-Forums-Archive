---
title: "[SOLVED] Wireless Woes"
date: 2008-08-18
forum: Networking &amp; Wireless
---

### Post by sil3nt on 2008-08-18
Hi Guy's,
         I have had a few issues with the wireless connection using my laptop. After fiddling around I have found this to be an issue between me and the Access Point I use at work.

The AP is completely unsecured yet from time to time I get a auth challange, I have to restart the network interface and remove the access point from wireless connections to connect.

Most of the time when I do get a connection its good for around 5 seconds then I get disconnected. 

This is eating me up inside and as it works for my co-workers Windoze laptops :(

I don't have a problem with wireless otherwise, has anyone else had any problems similar to this?

For the record:
I am currently using the Madwifi-Hal drivers for my machine on Hardy.

Ps(I have tried ndiswrapper with the windows drivers instead of Madwifi and the results are no different)

Cheers in advance.

---

### Post by sil3nt on 2008-08-18
I fixed this guys, I used this post and driver :

[http://ubuntuforums.org/showthread.php?t=795984](http://ubuntuforums.org/showthread.php?t=795984)

And I ditched NW manager and using WICD and everything now works a treat. After using WICD I noticed two APs with identical names but one was secure and one was unsecure, it seems gnome NW manager could not differentiate between the two.

---

### Post by lswb on 2008-08-18
Just a thought, is there more than 1 wireless net at work? Sometimes NetworkManager (Almost wrote NetworkMangler there!) will disconnect from one AP and try another if the signal is stronger.

---

