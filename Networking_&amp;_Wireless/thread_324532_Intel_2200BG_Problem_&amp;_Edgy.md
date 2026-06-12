---
title: "Intel 2200BG Problem &amp; Edgy"
date: 2006-12-23
forum: Networking &amp; Wireless
---

### Post by reazn on 2006-12-23
reazn@asus:~$ lsmod | grep ieee
ieee80211              33608  1 ipw2200
ieee80211_crypt         6016  1 ieee80211
ieee1394              302904  2 sbp2,ohci1394


reazn@asus:~$ dmesg | grep ipw
[17179594.528000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.1.2kmprq
[17179594.528000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[17179594.528000] Driver 'ipw2200' needs updating - please use bus_type methods
[17179595.376000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[17179595.560000] ipw2200: Radio Frequency Kill Switch is On:
[17179595.560000] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[17182844.744000] ipw2200: Failed to send POWER_MODE: Command timed out.
[17184035.060000] ipw2200: Failed to send POWER_MODE: Command timed out.
[17185101.580000] ipw2200: Failed to send POWER_MODE: Command timed out.

reazn@asus:~$ iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

eth0      radio off  ESSID:off/any  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=off   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

reazn@asus:~$ sudo iwconfig eth0 power on
Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device eth0 ; Input/output error.


any idea's?

thanks in advance

---

### Post by zgornel on 2006-12-24
If you are using a laptop, enable wireless by key combination. It said the same thing on my laptop if my wireless card was off.

---

