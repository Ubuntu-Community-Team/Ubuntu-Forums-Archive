---
title: "Yet another wireless problem"
date: 2006-10-30
forum: Networking &amp; Wireless
---

### Post by kodat on 2006-10-30
alright i did get my wireless card to actually turn on, but i cant get any networks to show up..even with my SSID correctly written i cant scan the area for networks or connect to my own.

also: the only way i can turn it on is by doing sudo modprobe bcm43xx
anyone know how to make it start up without me having to use terminal

My iwconfig shows :

eth1      IEEE 802.11b/g  ESSID:"Blah"  Nickname:"Broadcom 4311"
          Mode:Managed  Frequency=2.484 GHz  Access Point: Invalid   
          Bit Rate=1 Mb/s   Tx-Power=18 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


so my card exists on ubuntu, i have drivers installed..but it is not finding any networks..when i change, in network connections, from eth0 (hard connect) to eth1 (wireless) it says disconnected..i dont know why.


ive already done :
hhttp://ubuntuforums.org/showthread.php?p=1071920&mode=linear

[http://www.ubuntuforums.org/showthread.php?t=25683&highlight=broadcom+chipset+ndiswrapper+howto](http://www.ubuntuforums.org/showthread.php?t=25683&highlight=broadcom+chipset+ndiswrapper+howto)

but still doesnt work..i even have wifiradar and kwifi manager..also ndiswrapper..but no luck


anyone?

---

