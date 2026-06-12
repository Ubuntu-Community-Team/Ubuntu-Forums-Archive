---
title: "iwconfig/dhclient works... Network Manager not so much"
date: 2018-09-03
forum: Networking &amp; Wireless
---

### Post by olsiron on 2018-09-03
I'm running Ubuntu 18.04 on a macbook with broadcom drivers. I'm able to get Wifi working with iwconfig/dhclient fine => I'm all drivered and firmwared up. But Network manager doesn't want to play... 

Any tips on getting Network Manager working (which makes the whole Gnome3 setup nice and tidy).

Cheers

Olsiron

---

### Post by chili555 on 2018-09-03
Details! We need details!

Do you see the Network Manager icon? When you click on it, do you see your network? When you click on your network, what happens? Does it try? Does it ask for your password repeatedly? Any smoke or sparks?

May we see the result of:```
cat /etc/network/interfaces
cat /etc/NetworkManager/NetworkManager.conf
```

---

### Post by olsiron on 2018-09-04
```
$ iwconfig wlp3s0
wlp3s0    IEEE 802.11  ESSID:"hoppi"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: XX:XX:XX:XX:XX:XX   
          Bit Rate=12 Mb/s   Tx-Power=31 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=48/70  Signal level=-62 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:12  Invalid misc:0   Missed beacon:0


$ sudo nmcli d wifi list
IN-USE  SSID  MODE  CHAN  RATE  SIGNAL  BARS  SECURITY
 
$ cat /etc/NetworkManager/NetworkManager.conf 
[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false

[device]
wifi.scan-rand-mac-address=no
$ cat /etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

iface mon0 inet manual
iface wlp3s0 inet manual
```

---

### Post by chili555 on 2018-09-04
> $ cat /etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

iface mon0 inet manual
[COLOR="#FF0000"]iface wlp3s0 inet manual[/COLOR]That declaration tells Network Manager that you, not NM, will manage the interface. That's exactly what you have.

Remove or comment out the line and reboot. NM will take over again.

---

