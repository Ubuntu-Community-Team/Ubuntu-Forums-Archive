---
title: "wlan detection problem"
date: 2008-08-22
forum: Networking &amp; Wireless
---

### Post by aSmL on 2008-08-22
Hi, I am new with Linux and need some help with wlan on my Lenovo3000 N200,
Ubuntu 2.6.24-19-generic

04:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

after: iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
and
after:  iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

Thanks

---

### Post by sdide on 2008-08-22
The scan seems fine, it just doesn't see any AP's.

try doing (as root or with sudo)

# iwlist wlan0 scan

---

### Post by aSmL on 2008-08-23
OK, it works.Problem is with the manual wlan switch, if I boot with sw off, and after sw on not working, if I boot with sw on it is working If I sw off and on not working only reboot or "sudo rmmod -f iwl3945" helps, any solution for this.. :)

---

