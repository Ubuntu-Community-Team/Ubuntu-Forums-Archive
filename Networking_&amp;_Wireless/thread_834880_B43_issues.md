---
title: "B43 issues"
date: 2008-06-19
forum: Networking &amp; Wireless
---

### Post by MacAttack625 on 2008-06-19
Im using Hardy Haron

I have a Linksys wireless card and Im having trouble with it

Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
[Needs b43legacy]

Using fw-cutter I have installed b43 and b43legacy

when my computer boots I run the commands

sudo modprobe b43
sudo modprobe b43legacy

The network manager is able to see the network, but is never able to connect

 iwconfig:

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

iwlist scan:

wlan0     Scan completed :
          Cell 01 - Address: 00:0C:41:FB:D9:F1
                    ESSID:"linksys"
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=71/100  Signal level=-57 dBm  Noise level=-56 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=000001278e337188

---

### Post by minus24 on 2008-07-11
I have exactly the same problem with BCM4306.  After installing the B43 firmware, the network manager can see several networks, but cannot connect to any of them.

Can anyone shed any more light on this issue?

---

