---
title: "Default Gateway"
date: 2005-04-24
forum: Networking &amp; Wireless
---

### Post by tuxx54 on 2005-04-24
Hello, never had this problem before, I run my main ethernet (eth0) for my main connection, out to hub > cable modem. Then I run an internal network which runs from my router (eth1). The problem is when I installed 5.04 I checked to make eth0 my default gateway. But after the first reboot, it keeps changing to eth1 as default gateway. 

I run 2 ips, one for my router which has 3 windoze puters running from it, and one for my linux box. But for the speed of moving files to my ftp I like to have my linux box connected to the router. I have been running linux for several years and never have had this problem before.

I open up the network settings window and have switched the default gateway to eth0 and then hit "OK". But if I open up network settings again its gone back to eth1? Its driving me nuts!! Anyway to manually change it from the console? I still like the old way to configure my network from console, always seemed rock solid.

Any help....Thanks     :smile:

---

### Post by fdoving on 2005-04-25
[QUOTE=tuxx54]Hello, never had this problem before, I run my main ethernet (eth0) for my main connection, out to hub > cable modem. Then I run an internal network which runs from my router (eth1). The problem is when I installed 5.04 I checked to make eth0 my default gateway. But after the first reboot, it keeps changing to eth1 as default gateway. 

I run 2 ips, one for my router which has 3 windoze puters running from it, and one for my linux box. But for the speed of moving files to my ftp I like to have my linux box connected to the router. I have been running linux for several years and never have had this problem before.

I open up the network settings window and have switched the default gateway to eth0 and then hit "OK". But if I open up network settings again its gone back to eth1? Its driving me nuts!! Anyway to manually change it from the console? I still like the old way to configure my network from console, always seemed rock solid.

Any help....Thanks     :smile:[/QUOTE]
 Hello,

take a look at the file /etc/network/interfaces (example: sudo gedit /etc/network/interfaces )

Edit this file to match your desired network settings.

To restart networking, run the following command:
'sudo invoke-rc.d networking restart'


- Frode

---

