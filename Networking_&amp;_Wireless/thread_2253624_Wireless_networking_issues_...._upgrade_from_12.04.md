---
title: "Wireless networking issues .... upgrade from 12.04 to 14.04"
date: 2014-11-21
forum: Networking &amp; Wireless
---

### Post by verber001 on 2014-11-21
My wireless radio keeps disconnecting so much so now....that I can even search at all on the net.  I ran iwconfig and got:

eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Encryption key:off
          Power Management:off
          
Power management is off which I´ve seen others say was the problem.  But I see no access point associated.  Not sure if this is the problem or not.  Can anyone help me out?

7

---

### Post by verber001 on 2014-11-21
information from wireless-info script from another thread.

---

### Post by verber001 on 2014-11-21
Attempted to turn power off but it failed:

root@john-Lenovo-G50-70:/home/john# iwconfig wlan0 power off
Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device wlan0 ; Operation not supported.

---

