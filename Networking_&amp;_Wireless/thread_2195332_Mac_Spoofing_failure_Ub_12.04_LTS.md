---
title: "Mac Spoofing failure Ub 12.04 LTS"
date: 2013-12-23
forum: Networking &amp; Wireless
---

### Post by jimrone on 2013-12-23
Hi all,


I have been able to spoof my mac on my laptop (wireless card QualComm Aetheros ar9845) and connect to my network , that uses mac address filtering, successfully through a Kali linux Live boot USB
However when I try to do the same in my Ubuntu 12.04 LTS install that I use most often, the connection cannot be made. The mac I am spoofing is that of a device I have already whitelisted in the router, and it can connect on its own properly. That device is always off when I test to better simulate a lab enviroment.
Commands used:
root@kali:~# ifconfig wlan0 down hw ether "my new mac"
root@kali:~# ifconfig wlan0 up


This set always has worked without fault in Kali, but Ubuntu has failed and I have used both this and installed and used macchanger to try and solve it to no avail.
If anyone has any ideas or anything at all that can help me it would be greatly appreciated. Ive been rather stumped by this and hope to solve it. Thank you


gphoenix

---

### Post by mmweber on 2014-01-06
Hey mate,  just wrote a wee script that fixes that issue. Basically, it changes the mac-address of your wlan device and updates the wlan configuration network-manager uses to connect.   Check this out: [http://cyberandspace.wordpress.com/2013/12/30/macbot-0-1-an-interactive-commandline-script-for-macchanger/](http://cyberandspace.wordpress.com/2013/12/30/macbot-0-1-an-interactive-commandline-script-for-macchanger/)  Cheers,  Manuel

---

