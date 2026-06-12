---
title: "another lan problem ?"
date: 2005-11-10
forum: Networking &amp; Wireless
---

### Post by marcel.patoulachi on 2005-11-10
yop

i cant access my wifi-lan (i cant ping my gateway) and the internet from my station. from my laptop it works with the same configuration ! help !

configuration :

/etc/resolv.conf :
nameserver 195.185.1.108
nameserver 195.186.4.109

/etc/hosts : nothing changed (i installed kubuntu on monday)

/etc/network/interfaces :
iface wlan0 inet static
wireless-key blahblahblah (in clear, without *) 
wireless-essid mynet
address 192.168.0.53
netmask 255.255.255.0
gateway 192.168.0.254


any idea ? please ...

ps.: ipv6 is desactived. and my access point and station card got the same channel 4

---

### Post by marcel.patoulachi on 2005-11-10
youhouhouhouhouhou it WORKS !

HAMMER !

find the solution here : [http://ubuntuforums.org/showthread.php?t=88383](http://ubuntuforums.org/showthread.php?t=88383)

thanx a lot Maverick911 !

in fact i reinstalled ndiswrapper + in my /etc/network/interfaces i added the lines
wireless-mode managed
wireless-freq 2.427G

and to the line password i added the word "open" for the encryption method
wireless-key open XXXXXX

yeah !

---

