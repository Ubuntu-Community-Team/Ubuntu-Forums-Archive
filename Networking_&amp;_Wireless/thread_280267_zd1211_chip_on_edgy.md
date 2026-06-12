---
title: "zd1211 chip on edgy"
date: 2006-10-19
forum: Networking &amp; Wireless
---

### Post by kthdsn on 2006-10-19
Hi, i have just installed edgy on my dell inspiron 8000 laptop it can see the wireless atick but wont let me connect with it iwconfig produces 

code

:lo        no wireless extensions.

eth1      no wireless extensions.

eth2      802.11g zd1211  ESSID:"mariocars"  
          Mode:Managed  Frequency:2.472 GHz  Access Point: Invalid   
          Bit Rate=1 Mb/s   
          Link Quality:12  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.


any ideas what ive done wrong?

---

### Post by cd-r80 on 2006-10-19
Do you have "mariocars" in your AP. Try without encryption. I have Usb zd1211 working on Dapper. But I had to compile own & deleted old.

---

