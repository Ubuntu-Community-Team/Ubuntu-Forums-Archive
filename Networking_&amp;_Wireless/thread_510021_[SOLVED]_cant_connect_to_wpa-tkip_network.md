---
title: "[SOLVED] cant connect to wpa-tkip network"
date: 2007-07-26
forum: Networking &amp; Wireless
---

### Post by cyke on 2007-07-26
hello im fairly new to ubuntu or linux.  I have installed ubuntu 7.04 feisty fawn to dual boot with winXP.  Everything is fine until i tried to connect to my office's wpa-tkip wireless network.  in winXP i can connect but in ubuntu i could not. i have network manager seeing our wireless network but could not connect. at home however, i could connect to my wep network.  below is the configuration i have in winXP.

[IMG]http://img510.imageshack.us/img510/3841/wpatkipnu8.jpg[/IMG]

As you can see in the image, i have downloaded a certificate from our server win2k and under trusted root certificate it appeared automatically for me to choose.

how is this done in ubuntu?  all the help will be appreciated.  Thanks in advance.

---

### Post by cyke on 2007-07-26
output from lshw -C network:

Cell 04 - Address: 00:0C:DB:E2:02:F8
                    ESSID:"iAccess200-npi"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 9 Mb/s; 11 Mb/s
                              6 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=28/100  Signal level=-92 dBm  Noise level=-92 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : 802.1X  
                    Extra: Last beacon: 204ms ago


cyke@cyke-laptop-ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"iAccess200-npi"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:0C:DB:E2:02:F8   
          Bit Rate:2 Mb/s   Tx-Power:14 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=35/100  Signal level=-88 dBm  Noise level=-89 dBm
          Rx invalid nwid:0  Rx invalid crypt:12  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:10912   Missed beacon:0

anyone with an idea on how to properly configure this?

---

### Post by cyke on 2007-07-26
bump :(

---

### Post by wieman01 on 2007-07-27
You are on a PEAP network, right? 7.04 does support PEAP as far as I remember. Have you seen any options in Ubuntu?

On the other hand, your wireless adapter and more importantly, the driver must support PEAP. What card have you got? It is likely that the current Linux driver does not offer PEAP, so we may have to replace it using "ndiswrapper".

---

### Post by cyke on 2007-07-31
finally i was able to make my wifi work on wpa-tkip-peap configuration.  alhtough i have to configure it everytime i boot up. :(

---

### Post by arnicainthemembrane on 2008-02-01
How does one configure a PEAP/WPA/TKIP  wireless connection? I have the same problem as above, my computer connects without difficulty to almost all wireless networks, just not the tkip encrypted one at home.

Gutsy on a Thinkpad T40

---

### Post by wieman01 on 2008-02-01
> **arnicainthemembrane said:**
> How does one configure a PEAP/WPA/TKIP  wireless connection? I have the same problem as above, my computer connects without difficulty to almost all wireless networks, just not the tkip encrypted one at home.

Gutsy on a Thinkpad T40
Network Manager should support it. If not WICD is an option:

[http://wicd.sourceforge.net/]("http://wicd.sourceforge.net/")

---

