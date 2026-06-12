---
title: "[SOLVED] invalid .inf driver straight from the install cd"
date: 2008-04-18
forum: Networking &amp; Wireless
---

### Post by mandrill on 2008-04-18
this is a netgear wpn311 v1.2....the driver version is higher now. but you cannot access the .inf file, just a .sys inside file - the .inf is inaccesible

Have gone around finding different versions of the .inf file, and ndiswrapper tells me they are ALL invalid. here is my iwconfig and ndiswrapper -l

jim@foobar:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"pogo"  Nickname:""
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1B:2F:0E:D0:CA   
          Bit Rate:54 Mb/s   Tx-Power:18 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=40/70  Signal level=-54 dBm  Noise level=-94 dBm
          Rx invalid nwid:20425  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

jim@foobar:~$ ndiswrapper -l 
jim@foobar:~$


My signal has always sucked - especially in light of the fact that I have a windows box with the same hardware sitting right next to the 'nix box with perfect signal strength and 
good SNR.

The only way I know to extract a needed driver from a .sys file is on windows,

---

