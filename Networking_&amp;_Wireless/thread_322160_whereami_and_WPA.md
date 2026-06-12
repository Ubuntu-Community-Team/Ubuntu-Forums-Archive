---
title: "whereami and WPA"
date: 2006-12-20
forum: Networking &amp; Wireless
---

### Post by Richard Roy on 2006-12-20
I'm using whereami in my laptop (ubuntu edgy).
How can I use it with WPA? 
Do I need to change /etc/network/interfaces or can I do everything in /etc/whereami/detect.conf ?

Here is my /etc/whereami/detect.conf  (which works great, the only thing I can't do is use WPA):

default undocked
testmii eth0 lan

if down
  always at undocked
  always notat eth0,eth1
elif stop
  always at undocked
  always notat eth0,eth1
elif lan
  set INTERFACE eth0
  testdhcp restart dhcp
else
  set INTERFACE eth1
  testap scan wlan
fi

if wlan
  testap AAA,XXXXXXX wdhcp
  testap BBB,s:PASSWORD wdhcp
  testap CCC,XXXXXXX wdhcp
fi

if wdhcp
  testdhcp restart dhcp
fi

---

### Post by wieman01 on 2006-12-20
I would think that you have to do it using "/etc/network/interfaces"... Try the link in my signature and let us know if you need further help.

---

### Post by Richard Roy on 2006-12-20
wieman01, the problem is that with this approach you can set only 1 wireless network. Your solution is something like:
auto wlan0
iface wlan0 inet static
wpa-driver wext
wpa-conf managed
wpa-ssid <your_essid>
wpa-ap-scan 2
wpa-proto RSN
wpa-pairwise CCMP
wpa-group CCMP
wpa-key-mgmt WPA-PSK
wpa-psk <your_hex_key> [IMPORTANT: See "WPA-PSK key generation"]

But the reason I use whereami is that I'm using several wireless networks (home, work, etc..). If you put all this information in /etc/network/interfaces file you loose the great advantage of whereami.
I know there is another option to use wpa_supplicant with "roam" function. But again the main idea of whereami, is that everything is handled there.
If someone knows some solution - I'll be happy to know.

---

### Post by Richard Roy on 2006-12-20
someone? please?

---

### Post by wieman01 on 2006-12-20
The last thing I can offer is [this thread]("http://ubuntuforums.org/showthread.php?t=299462"). This refers to a new network-manager which allow for multiple network profiles depending on where you are. But that means you'll drop "whereami".

---

### Post by pestilence4hr on 2007-05-09
> **Richard Roy said:**
> 
But the reason I use whereami is that I'm using several wireless networks (home, work, etc..). If you put all this information in /etc/network/interfaces file you loose the great advantage of whereami.
I know there is another option to use wpa_supplicant with "roam" function. But again the main idea of whereami, is that everything is handled there.
If someone knows some solution - I'll be happy to know.

You can run any command after whereami detects the presence of your network.  e.g. you can run "cp /etc/network/interfaces.mynetwork /etc/network/interfaces".  Thus you can have multiple interfaces files.  That's how I use whereami.

---

