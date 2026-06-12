---
title: "Unable to set my essid"
date: 2008-05-21
forum: Networking &amp; Wireless
---

### Post by Cresta on 2008-05-21
Hello all
I'm trying to configure ndiswrapper(wlan0) + wpasupplicant(WPA-PSK)

I've got a slight problem, i dont seam to be able to get my ESSID to be saved or recognized, as you can see in the returns below. Can anyone point me in the right direction.

homepc@homepc-desktop:~$ sudo iwconfig wlan0 essid NETGEAR
homepc@homepc-desktop:~$ sudo iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:09:5B:D7:62:BC
                    [COLOR="Blue"]**ESSID:""**[/COLOR]
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:42/100  Signal level:-69 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

---

### Post by chili555 on 2008-05-21
You are comparing apples and oranges. *iwconfig* meams, roughly, I want my wireless card, wlan0, to connect to the station out there named NETGEAR. *scan* tells you some details about some of the wireless routers and access points within range of your wireless card. In this case, the router in question is not broadcasting it's name. You might try:```
sudo iwconfig wlan0 essid off
sudo iwconfig wlan0 ap 00:09:5B:07:62:BC
sudo iwconfig wlan0 key <ur_wireless_key>
sudo dhclient wlan0
```If you can't connect, I suggest you search this forum further for 'essid not broadcast.'

Also see *man iwconfig*

---

### Post by Cresta on 2008-05-23
I'm farely new to Ubuntu and have exhausted all i can "guess" to do.

I'll give this a go, fingers crossed. 

Thanks

---

