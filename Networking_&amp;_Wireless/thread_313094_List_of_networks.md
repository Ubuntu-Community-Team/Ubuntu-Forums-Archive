---
title: "List of networks"
date: 2006-12-05
forum: Networking &amp; Wireless
---

### Post by aco on 2006-12-05
Ok i installed win driver thru ndiswraper its broadcom4318E chis asusw138gE card...works fine but now i need something where i could see all available networks..please help

---

### Post by KingBahamut on 2006-12-05
sudo apt-get install network-manager-gnome 

That gives you the little icon thingy that lists the networks when you click on it.

---

### Post by aco on 2006-12-05
Ok i installed network manager but it says no network connection and if i left click it says ni network devices..since my wireless is working perfectly something is obviously wrong....

---

### Post by KingBahamut on 2006-12-05
can you give me a 

sudo cat /etc/network/interfaces

---

### Post by aco on 2006-12-05
auto lo
iface lo inet loopback


iface eth0 inet dhcp


auto eth2iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


iface eth1 inet dhcp
wireless-essid Connection1



auto eth1
aleksandar@aleksandar-desktop:~$ 
Ok this is it

---

### Post by aco on 2006-12-06
Doesent anyone have a clue how to get a window with a kist of available networks

---

### Post by aco on 2006-12-06
ppl please im becoming desperate

---

### Post by celem on 2006-12-06
See [http://www.ubuntuforums.org/showthread.php?t=312372](http://www.ubuntuforums.org/showthread.php?t=312372) for related issue. You can use WiFi Radar mentioned there. You shouldn't normally need WiFi Radar but Edgy seems to be broken in this area as it worked fine in Dapper.

---

### Post by dbott67 on 2006-12-06
*EDIT:  Oops!  I should have followed **celem's** link.  I posted the same thing there.*

You can also type the following command from a terminal:
```
iwlist scanning
```

```
dbott@dapper:~$ **iwlist scanning**

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :

Cell 01 - Address: 00:40:05:B2:AF:YY
              ESSID:"bott"
              Mode:Master
              Frequency:2.437 GHz (Channel 6)
              Quality=34/100  Signal level=39/100  Noise level=11/100
              Encryption key:on
              Bit Rate:22 Mb/s

Cell 02 - Address: 00:05:5D:FA:B2:XX
              ESSID:"soni"
              Mode:Master
              Frequency:2.437 GHz (Channel 6)
              Quality=24/100  Signal level=27/100  Noise level=12/100
              Encryption key:on
              Bit Rate:54 Mb/s

sit0      Interface doesn't support scanning.
```

-Dave

---

