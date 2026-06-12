---
title: "problems with NetworkManager Applet 0.7.0.100"
date: 2009-05-04
forum: New to Ubuntu
---

### Post by carrierpilot1357 on 2009-05-04
I had ubuntu 8.04, then I upgraded to 8.10 so I could upgrade to 9.04, and I noticed in 8.10 that the little network icon in the panel (the two computer screens side by side)were showing a little x in the corner, so I right clicked on it, clicked on connection information, but it said that there was no valid active connections found. It did the same after I upgraded to ubuntu 9.04.(by the way, despite this, my internet connection still works anyway)

this is  just one of those little things on my desktop that are really annoying. and because of this, I can't configure my network connection either.

---

### Post by mprince on 2009-05-04
I think you should have a menu item to configure networking. Check here:

System > Administration > Network

---

### Post by carrierpilot1357 on 2009-05-04
that button doesnt exist in 9.04. there is just system> administration> network tools(not what im looking for), system> preferences> network connections(everything is blank here),and system> preferences> network proxy

---

### Post by s_g_robertson on 2009-05-07
I'm seeing the almost the same issue.  However my icon looks like a wireless signal strength indicator(There is no wireless in the machine)  Clicking on the icon gives "Wired Network device not managed" in greyed out text.  As per the OP my network connection still works fine and I also went 8.04 to 8.10 to 9.04.

Stephen

---

### Post by SchoonerMonaro on 2009-06-09
I had the same  problem and fixed it after reading this post:
 [http://ubuntuforums.org/showpost.php?p=6385527&postcount=9](http://ubuntuforums.org/showpost.php?p=6385527&postcount=9)

---

### Post by Iowan on 2009-06-09
Network Manager gets a li'l grouchy when it isn't boss. You *probably* have your interface configured in */etc/network/interfaces*. You can try commenting out the configuration there, then use Network Manager to build a connection. (If it doesn't work, you can uncomment your "working" configuration in */etc/network/interfaces*.

---

