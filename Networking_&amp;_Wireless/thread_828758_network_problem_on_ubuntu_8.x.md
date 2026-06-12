---
title: "network problem on ubuntu 8.x"
date: 2008-06-14
forum: Networking &amp; Wireless
---

### Post by guy2il on 2008-06-14
hello

i have two machines installed with ubuntu 8.x one is server installation and the other, a workstation. both has the same problem. i can ping my network and i can ping the web, i can also ping the linux machines from other machines inside my network. but as for using actual internet like web browsing or getting mail / IM / apt-get actions .. nothing. it hangs forever.

the network architecture is a b-focus router connected to the wall, after that an AP = home&office by 3com with 4 rj45 ports and wireless connection.

inside the network there are a powerbook with osx 10.4.11 - using wireless and works fine.
another machine, cable connected to the 3com running windows xp, works just fine.
anf the two linux, one with wireless and the other cable connected.

both can ping but not use applications to use the internet.

i assume the problem has to do with settings .. since running the same machines with older ver. of ubuntu was ok using the internet. also installing windows for a minute .. i was able to use the net.

 i had the setting checked again and again .. nothing looks different.
i get ip via dhcp and the numbers are just the for all the computers. include the mac and the windows.

i have apache on the mac but i can't surf it with the linux.  i so can with the XP.

----

during the installation, apt was able to update q upgrade the system, but after installation was over, apt-get hangs forever. syneptic also fail to connect.

it seems that the problem starts only after the installation is over.


please help.

thank you !

Guy

---

### Post by superprash2003 on 2008-06-14
try using opendns servers [http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html)

---

