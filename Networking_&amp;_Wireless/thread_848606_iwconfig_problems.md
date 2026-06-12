---
title: "iwconfig problems"
date: 2008-07-03
forum: Networking &amp; Wireless
---

### Post by cfree on 2008-07-03
can anyone help me i am trying to change the bit rate on my wireless usb it is a hwug1 with the rt73 chipset 

sudo iwconfig wlan0 rate 48m
Error for wireless request "Set Bit Rate" (8B20)

---

### Post by kevdog on 2008-07-03
Try this:

sudo iwconfig wlan0 rate 54M

Not sure is wlan0 is your interface..it may be something else.

---

### Post by cfree on 2008-07-04
yeah its wlan0 it does the same with 
sudo iwconfig wlan0 rate 50m 

but by the way i was trying to put it in 48m bit rate not 54

---

### Post by perrfekto on 2013-01-23
> **kevdog said:**
> Try this:

sudo iwconfig wlan0 rate 54M

Not sure is wlan0 is your interface..it may be something else.

Hi
I've tried to execute this command, but it doesn't seem to have any effect.
Before and after running the command on Ubuntu 12.04 LTS 64bit, iwconfig gave the following output :
wlan0     IEEE 802.11g  ESSID: off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          [COLOR=Red]_Bit Rate:300 Mb/s_[/COLOR]   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Encryption key: off
          Power Management: off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Can you please assist in setting a bit rate of 54M.

BTW - I'm trying to connect via a Netgear N300.

Thanks

---

