---
title: "WIFI signal strength problem"
date: 2006-11-19
forum: Networking &amp; Wireless
---

### Post by theophane on 2006-11-19
Hi folks.
I have a problem on Edgy with my wifi connection, or at least its strength.
Here is the screencap :

[IMG]http://unjourlinux.free.fr/screen/1.png[/IMG] 

As you can see, I am connected to my network, but all the networks seem to have a 100/100 link quality.

When I do *iwlist scan*, here is what I get :


eth1      Scan completed :
          Cell 01 - Address: 00:16:41:0B:F2:46
                    ESSID:"Wanadoo_6e85"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.457 GHz (Channel 10)
                    Quality:0/100  Signal level:-73 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: 00:0C:41:B6:93:82
                    ESSID:"WRT54G"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.452 GHz (Channel 9)
                    Quality:0/100  Signal level:-88 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 03 - Address: 00:16:CE:15:04:50
                    ESSID:"WANADOO-07D8"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:0/100  Signal level:-70 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK 
          Cell 04 - Address: 00:11:F5:C0:CD:65
                    ESSID:"SpeedTouch1FB36B"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:0/100  Signal level:-92 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 05 - Address: 00:11:50:36:46:1B
                    ESSID:"belkin54g"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:0/100  Signal level:-95 dBm  Noise level:-256 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

As you can see all the networks appears to have a 0/100 link quality...
If someone knows how to fix this, then, let me know :cool: 

Cheers

---

### Post by spd106 on 2006-11-19
What card and driver are you using? 

If you have ndiswrapper then it probably won't give you the real signal strength. It's a known limitation of the driver interface.

---

### Post by theophane on 2006-11-19
> **spd106 said:**
> What card and driver are you using? 

If you have ndiswrapper then it probably won't give you the real signal strength. It's a known limitation of the driver interface.

I have an acer aspire 3023 WLMi with a **BCM4318**, and yes, I use *ndiswrapper*...
So, if I understand, there is nothing I can do in order to get the real strength of my wifi network... ?

---

### Post by Rob2687 on 2006-11-19
The bcm43xx driver might work.

---

### Post by theophane on 2006-12-23
> **Rob2687 said:**
> The bcm43xx driver might work.

That's the driver I'm using right now, and it's not working :(

---

