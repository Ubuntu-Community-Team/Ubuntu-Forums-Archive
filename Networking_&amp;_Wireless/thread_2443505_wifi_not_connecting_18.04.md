---
title: "wifi not connecting 18.04"
date: 2020-05-16
forum: Networking &amp; Wireless
---

### Post by sam622 on 2020-05-16
I recently installed ubuntu 18.04 LTS in dual boot with windows7, but  wifi fails to connect. My network is detected but when I enter my  password it takes some time and send me again the password window  without connecting, whereas I can get a wired connection. my laptop Acer  has a wifi card broadcom; BCM 43225. the preinstalled driver is brcmsmac, I shifted to broadcom 802.11 linux STA, but it's the same! when I type ''sudo iwconfig'' in a terminal I got the answer below. It seems like all is in place, but not able to connect to the router? 
lo        no wireless extensions.

wlp3s0    IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=200 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          
enp2s0    no wireless extensions.

---

