---
title: "wifi problems with toshiba laptop"
date: 2006-12-10
forum: Networking &amp; Wireless
---

### Post by oyen on 2006-12-10
my OS: ubuntu edgy. im having a problem with my wifi. i already have the wifi-radar but my network keeps on saying my wifi's disconnected (if i restart to windows, im easily connected). please help. im totally new with a linus OS.

---

### Post by CRCarl on 2006-12-10
Can you send the output of; 

ifconfig 
lspci -v
cat /etc/resolv.conf

Plus are you getting any errors? Can you browse the internet?

Craig

---

### Post by rvickers on 2006-12-10
I have a Satellite A105-S4284 which I bought about a month ago and immediately loaded edgy on. Wifi was too ureliable, it would work for awhile and then not work. I tried Wifi Radar and Network Manager with no success. After about a week I formatted and loaded dapper and it's worked perfect ever  since. I use dhcp at home and Wep and static IP at work. I found the best way to switch is to manually reconfigure /etc/network/interfaces and /etc/resolv.conf and issue the command sudo /etc/init.d/networking restart. I have the unused config in the two files commented out so I don't have to retype every time. I also found that System->Administration->Networking is the best way to get networking to work the first time.
Good Luck...

---

