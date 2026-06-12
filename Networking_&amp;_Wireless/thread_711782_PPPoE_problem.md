---
title: "PPPoE problem"
date: 2008-03-01
forum: Networking &amp; Wireless
---

### Post by x.3r0 on 2008-03-01
i reinstalled my gutsy gibbon and when i connected to the internet using the livecd it was fine (i just run sudo pppoeconf and it instantly configured and connected itself). but when i rebooted on my installed gutsy on my harddrive and tried to configure the internet connection using the same method this message appears:

"Sorry, I scanned 1 interface, but the Access Concentrator of your provider did not respond. Please check your network and modem cables. Another reason for the scan failure may also be another running pppoe process which controls the modem."

I am using a Huawei ADSL CPE SmartAX MT880, while my built-in network adapter is a VIA compatible Fast-Ethernet adapter.

Thanks for the help in advance.

---

### Post by superprash2003 on 2008-03-01
why dont you make your modem do the dialing(change from bridge mode to ppoe modem in your modem).. so as soon as you switch on your modem your internet connection is on.. no need to do any dialing!!

---

### Post by Shakeysteve on 2008-03-02
I have the same error being given, and my adsl modem is permanently connected.
See Bug #197601.
Hope we get an answer.

---

### Post by kimosabe on 2008-05-08
I also am having the same problem.

I have just installed Ubuntu 8.04 and have not been able to access the internet. I am using a Netgear ADSL modem(only) connected directly to my dual boot XP / Ubuntu pc, with ethernet.

Under XP it all works fine.

Under Ubuntu I am not sure why this is happening or how to fix it. With pppoeconf (which i was told to try), i get the same Access Concentrator Error as above.

Has anyone come across this before, or know how to solve this problem?

Please help.

---

### Post by crojas on 2008-07-09
I had the same problem, and really never found an answer... but after intalling Xubuntu (insted of Ubuntu/Kubuntu) everything is going OK.

---

