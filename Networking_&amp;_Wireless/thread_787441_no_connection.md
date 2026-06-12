---
title: "no connection?"
date: 2008-05-08
forum: Networking &amp; Wireless
---

### Post by grndragon57 on 2008-05-08
I upgraded from 7.10 to 8.04 and got the busybox and was not able to fix it, so I did a fresh install of 7.10. 
 After the install I have been unable to connect to the internet or network over my wired connections. Previously 7.10 detected the network and worked fine on this system. 
 I tried changing some settings in network settings with no result. I then tried 

```
sudo ifdown eth0
sudo ifup eth0
```
 and the network connected. When I later rebooted the computer I again had no network connection and the above fix wouldn't work. I booted to the live disk and it detected the network so assuming it was a bad install I reformatted and reinstalled. The new install did not detect the network.

 The network is detected by the live cd and my XP, but not my Ubuntu. I would really appreciate any help I am totally lost. Thank you.

---

### Post by garyedwardjohnston on 2008-05-08
What does the connection information tell you?

[Right click the network connection in the system tray and select connection information]

---

### Post by grndragon57 on 2008-05-09
The option for Connection Information is greyed out in the box.

---

### Post by Ayuthia on 2008-05-09
What is your wireless card?  Can you post your lspci -nn and lshw -C network from the Terminal?

---

