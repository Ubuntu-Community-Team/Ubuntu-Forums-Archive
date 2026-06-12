---
title: "i cannot connect to network via wi-fi"
date: 2007-04-08
forum: Networking &amp; Wireless
---

### Post by szymon_g on 2007-04-08
hi
i'm beginner in linux.
i've installed a Feisty Fawn Beta release in text mode, as a command-line system (becouse i wanna customise my ubuntu from scratch :->)
i have a laptop with wi-fi card (intel 3945abg).
i cannot make connection with internet
this is my iwconfig's results :

eth1      IEEE 802.11g  ESSID:"SpeedTouchBCE72F"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:11:F5:AE:51:96   
          Bit Rate:54 Mb/s   Tx-Power:15 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=68/100  Signal level=-61 dBm  Noise level=-62 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:12   Missed beacon:0

and thats my iwlist eth1 scan results

eth1      Scan completed :
          Cell 01 - Address: 00:11:F5:AE:51:96
                    ESSID:"SpeedTouchBCE72F"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:1
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=72/100  Signal level=-62 dBm  Noise level=-62 dBm
                    Extra: Last beacon: 224ms ago

and thats my interfaces

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

i use a dhcp.... any suggestion what should i do to have this connection?

thanks
szymon

---

### Post by rolando on 2007-04-08
Well first thing I would try is sticking 

iface eth1 inet dhcp
wireless-essid SpeedTouchBCE72F

into /etc/network/interfaces

then try

sudo ifup eth1

:)

---

### Post by szymon_g on 2007-04-09
thanx, it works :->

---

