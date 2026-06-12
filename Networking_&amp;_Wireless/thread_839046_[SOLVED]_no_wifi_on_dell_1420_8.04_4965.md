---
title: "[SOLVED] no wifi on dell 1420 8.04 4965"
date: 2008-06-24
forum: Networking &amp; Wireless
---

### Post by hippomofatumas on 2008-06-24
hi all.

i upgraded to 8.04 a bit ago, and wifi wont work. i can see my network, and can sometimes "connect", but internet doesnt work. had problems with this 4965 network stuff before. i tried wicd which worked before but no such luck. 

help would be much appreciated. please try to be specific and noob-friendly, i havent been using linux as much i i did like a year ago.

thanks

---

### Post by pokipoki08 on 2008-06-24
Please post the output of these commands

```
cat /etc/network/interfaces
dmesg | grep wlan
cat /var/log/messages | grep wlan

```

Are you using ndiswrapper?

Are you trying to connect to a WEP/WPA wireless network?

---

### Post by hippomofatumas on 2008-06-25
response number one: 

auto lo
iface lo inet loopback

2:
37.538170 ADDRCONF(NETDEV_UP): wlan0: link is not ready

3:

the same output as before several times.

no i am not using ndiswrapper. i am connecting to a wpa1/2 personal wifi.

so i guess my wifi (wlan0) isnt even in place.

what's next?

---

### Post by chalewa on 2008-06-25
what does ```
ifconfig
``` look like

---

