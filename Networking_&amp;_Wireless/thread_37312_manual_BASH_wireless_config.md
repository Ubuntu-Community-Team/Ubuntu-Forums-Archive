---
title: "manual BASH wireless config?"
date: 2005-05-26
forum: Networking &amp; Wireless
---

### Post by benplaut on 2005-05-26
what are the steps required to connect to a dhcp wireless network with WEP? I am trying to write a BASH script for it, but want to be sure that i have it all down before i give up:

--
sudo ifdown eth0
sudo ifdown lo
sudo ifdown ath0
sudo iwconfig ath0 essid "MYNETWORK"
sudo iwconfig ath0 key restricted MYKEY
sudo iwconfig ath0 channel 11
sudo ifup ath0
--

am i missing anything? i have a problem that when i sudo ifdown ath0, it shuts off the radio. the only way i can get it back on is to reboot. Is there an iwconfig command to enable dhcp? i seem to be missing it...

thanks!  :)

---

### Post by dave9191 on 2005-05-27
You can have a look at mine if you like [http://ubuntuforums.org/showthread.php?t=28869](http://ubuntuforums.org/showthread.php?t=28869) post 7. 

And to request dhcp ip address you use the dhclient command. 

Dave

---

