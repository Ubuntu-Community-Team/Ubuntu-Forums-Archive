---
title: "Ubuntu 12.04.3 LTS mini usb wireless not working"
date: 2013-11-12
forum: Networking &amp; Wireless
---

### Post by rhuysamen on 2013-11-12
I just installed Ubuntu 12.04.3 LTS and when I ran the live cd to test it before I stalled Ubuntu the wireless was working just fine. After in stall it's not working. Mini usb wireless adapter (Realtek) Any suggestions? I'm a first time Linux user so be gentle ;-)

So after some digging I followed this threat. Downloaded the latest drivers and did this[askubuntu.com/questions/246236/&#8230;]("http://askubuntu.com/questions/246236/compile-and-install-rtl8192cu-driver") Still not working &#8211; 

Also did all this - Remember I'm new to Ubuntu so I'm doing all this without knowing why. I'm just trying all sorts of stuff lol. Please help. [ubuntuforums.org/showthread.php?t=2150572]("http://ubuntuforums.org/showthread.php?t=2150572") &#8211; 

Step 1 sudo gedit /etc/modprobe.d/blacklist.conf # Blacklist native RealTek 8188CUs drivers blacklist rtl8192cu blacklist rtl8192c_common blacklist rtlwifi 
Step 2 Install the latest driver E.g went the folder CMD sudo bash ./install.sh I installed rtl8192cu-tjp-dkms_1.6_all.deb (from this thread) 
Step 3 CMD sudo gedit /etc/modules and added this line at the end of the file 8192cu and save 
Step 4 Rebooted the computer and plugged the USB adapter in.

Is this fixed in a later version of Ubuntu ? 12.10 or 13.04 or 13.10 ? Should I just go ahead and upgrade ?

---

