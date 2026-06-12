---
title: "I can see wireless networks but cannot connect"
date: 2006-08-13
forum: Networking &amp; Wireless
---

### Post by hypnoticstate on 2006-08-13
Got my laptop setup running kubuntu 6.06. I installed automatix and installed all the wireless stuff needed, ie wpa_supplicant, ndiswrapper, i sucessfully installed my windows driver via ndiswrapper, all appears to be fine. Using knetworkmanager i can see available wpa protected networks but my router says no !! it won't authenticate. I had no problems on my last install, but i was using ubuntu + gnome + network manager, any ideas or how do I go about troubleshooting this, help appreciated, i'll post shots etc, run commands, whatever it takes, thx.

---

### Post by JDAAINOKI on 2006-08-13
Can you post the following information:

lspci

iwconfig 

ifconfig -a

dmesg | grep XXXX ---------> replace XXX with your wifi interface (ath0, eth1, ra0, etc...)

dmesg | grep XXXX ---------> replace XXX with your wifi driver 

cat /proc/interrupts

Thanks,
Jay

---

### Post by hypnoticstate on 2006-08-14
thx for help mate, problem solved, i compiled the latest ndiswrapper and all worked fine, very strange !!!

---

