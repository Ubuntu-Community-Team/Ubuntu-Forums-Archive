---
title: "loosing wifi after upgrade to Ubuntu 19.04"
date: 2019-06-14
forum: Networking &amp; Wireless
---

### Post by tj001 on 2019-06-14
After upgrading to Ubuntu 19.04 I have problems with the wifi. 8 out of 10 times the computer start up the wifi is not working. That means, the computer connects to the access-point (as far as I can see), but I have no internet and the wifi-icon in top of the screen shows a '?'. If I turn off wifi and then turn it on again, everything works perfect again. 

This happens, as I said, 8 out of 10 times when I turn the computer on, and it also (some times, some times not) loose the wifi while it is on and I am not using it for a couple of minutes.

It started after upgrading to Ubuntu 19.04, and before that everything was rock stable. 

Anyone have a clue about what could be wrong?

---

### Post by praseodym on 2019-06-14
Please run the wireless script from the sticky thread and show the output when working and not working

---

### Post by garvinrick4 on 2019-06-18
Try
Open a terminal
> sudo service network-manager stop
> sudo rm /var/lib/NetworkManager/NetworkManager.state
> sudo service network-manager start
> reboot
Done, 
Actually should work with ? before reboot but will change to normal after reboot.

Run this to see if file says all three true. Just so you no in future. 
> gedit /var/lib/NetworkManager/NetworkManager.state

---

