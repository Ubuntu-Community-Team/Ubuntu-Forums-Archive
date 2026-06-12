---
title: "Dell lattitud D420 Can't searching Wireless Nework's"
date: 2013-12-17
forum: Networking &amp; Wireless
---

### Post by agerpark on 2013-12-17
Hi Man of Genies ~~

I'm very difficult problem..that Dell Latiitud D420 Wlan Network issued,
This issue, To ubuntu 10.04 32bit,,
i don't have solved..i want to get the ubuntu technician and advanced guy help.  

I was tied solution a few.
1. sudo apt-get install wicd
2. sudo apt-get remove --purge network-manager network-manager-gnome

but,,i couldn't solved for Wireless issue.
Please let me know any idea & answer 

My Laptop Wireless Network Device
home@home-laptop:~$ lspci -vnn | grep Network
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)

---

### Post by praseodym on 2013-12-17
You need the package "linux-firmware-nonfree". BTW: 10.04 is outdated! I recommend updating/reinstalling 12.04

---

### Post by agerpark on 2013-12-17
Thanks praseodym :D

i have got found.
first, 
My first solution 
1. sudo apt-get install wicd
2. sudo apt-get remove --purge network-manager network-manager-gnome

Second
 system - administrator - hardware drivers - brodcom check - active and then automatically setup and enable WIFI.

Thank you so much your advice.

---

