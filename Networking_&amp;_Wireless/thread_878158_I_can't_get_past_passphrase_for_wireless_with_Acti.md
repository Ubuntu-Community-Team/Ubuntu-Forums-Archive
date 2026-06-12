---
title: "I can't get past passphrase for wireless with Actiontec DSL Gateway"
date: 2008-08-02
forum: Networking &amp; Wireless
---

### Post by JB_1980 on 2008-08-02
Yesterday I got a HP pavilion dv9810us laptop and installed ubuntu ultimate on it. The problem is I can not get the wireless to work. I installed a driver for the Atheros AR5007 according to the instructions found here:

[http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html](http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html). 

I went through the instructions for the AMD 64, and finished by using ndisgtk to install the driver. After going through that my wireless card now shows up and the networks are detected. When I try to connect to the Actiontec it ask for a passphrase, I give it the correct one, and it still does not connect. I know that it is the WEP 64-bit hex, but I have tried all the possible combinations to see if any would yield results. No luck. I even turned off the security feature of my Actiontec to see it that would change anything. No difference. The "Wireless Network Key Required" window still shows up. I have tried to unplug the ethernet, but to no avail. Still the same results. 

Here is my iwlist scan:
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          
          Cell 06 - Address: 00:0F:B3:2C:32:9F
                    ESSID:"ACTIONTEC"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.452 GHz (Channel 9)
                    Quality:92/100  Signal level:-37 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=200
                    Extra:atim=0
          
I only copied the one for Actiontec because I couldn't post 13 images. 
Any help will be greatly appreciated.

---

### Post by JB_1980 on 2008-08-05
This is just an update on my problem. I decided to do a fresh install of the system, and this time I used the How To found here:

[http://ubuntuforums.org/showthread.php?t=792158&highlight=atheros](http://ubuntuforums.org/showthread.php?t=792158&highlight=atheros)

The install was simple, and my wireless works great. I even have a 64-bit system, which according to the install should be iffy.

Anyways, Problem solved. And as a side note, Ubuntu rocks.

---

### Post by hyper_ch on 2008-08-05
pls use the Thread Tools on top to mark this one as solved.

---

