---
title: "Help getting my Ubuntu PC connected"
date: 2007-04-01
forum: Networking &amp; Wireless
---

### Post by Dominym on 2007-04-01
I've been trying for over an hour to get another PC connected to my wireless. The card inside it is a LinkSys WMP54G. I've gone to System>Admin>Networking, and I guess the one I should be using is the one labeled wlan0? The other three are wmaster0, wired, and modem. I have it set for default ESSID and DHCP, but it's not connecting.

---

### Post by chili555 on 2007-04-01
The default ESSID? Is that the actual ESSID broadcast by your router? You can find out for sure by opening a terminal and doing a command: *iwlist wlan0 scan* You, hopefully, see something like this:```
Cell 01 - Address: 99:13:19:62:8D:F7
                    ESSID:"**myrouter1**"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=75/100  Signal level=-59 dBm  Noise level=-59 dBm
``` You need the exact name of the ESSID, in my case, myrouter1. Linux is picky, due to security. myrouter1 is not the same as myrouter is not the same as Myrouter1, etc. 

Then try to connect again and post back.

---

### Post by Dominym on 2007-04-01
Yah, the SSID is listed as default. I tried that command, but it didn't scan anything.:(

---

### Post by Dominym on 2007-04-01
I tried the command a couple more times, and it got it. It did list the ESSID as "default", so that part's right. Why won't it connect, though?

---

### Post by chili555 on 2007-04-01
Let's try it the geek way. Open a terminal and do:```
sudo iwconfig wlan0 essid default
sudo dhclient wlan0
``` If that doesn't work, you can try putting in the MAC address of the access point you want to connect to:```
sudo iwconfig ap 99:13:19:62:8D:F7
sudo dhclient wlan0 
```You get the address from the scan, too. Please see my example.

---

### Post by Dominym on 2007-04-02
Okay, I tried the first command, but it said nothing was received. It wouldn't do a scan this time (did it about fifty times, but it kept saying scan failed), but I tried the second command, too, since I had written down the MAC addy. It said the address was unrecognized, though.

---

### Post by Dominym on 2007-04-04
Still trying to get this connected. :|
I tried the same commands again, and i got "No DHCPOFFERS received" and "No working leases in persistant database - sleeping" messages. What does that mean?

---

### Post by chili555 on 2007-04-04
No encryption on this router? WEP or WPA or...? MAC filtering turned off?

---

### Post by Dominym on 2007-04-04
It says WEP is disabled on the router settings. I don't think I have any MAC filters on.

---

