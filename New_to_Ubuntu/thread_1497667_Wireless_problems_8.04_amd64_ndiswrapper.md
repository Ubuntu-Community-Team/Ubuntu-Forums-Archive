---
title: "Wireless problems 8.04 amd64 ndiswrapper"
date: 2010-05-30
forum: New to Ubuntu
---

### Post by Stigmata13 on 2010-05-30
Hello. I just installed 64-bit Ubuntu 8.04 on my Acer Aspire 5515. The wireless didn't work correctly out of the box; it said it was using propriety drivers but nothing worked. I switched on ethernet connection and downloaded ndiswrapper from the repositories, and managed to install the windows xp 64 bit wireless drivers for my card, but the speed seems unusually slow as opposed to what it should be.

iwconfig outputs the following:
```
patrick@Hollow:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"BECKETT"  
          Mode:Managed  Frequency:2.452 GHz  Access Point: 00:0F:B3:FE:C8:54   
          Bit Rate=54 Mb/s   
          Power Management:off
          Link Quality:43/100  Signal level:-68 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:185126  Invalid misc:452811   Missed beacon:0
```
I would be much obliged if someone could help me solve this problem and get the wireless working as it should be. Thanks.

---

### Post by anewguy on 2010-05-31
Obviously you are having network problems:

```
          Tx excessive retries:185126  Invalid misc:452811   Missed beacon:0
```

What's causing those?  Hard to know, at least for me.  The excessive retries and the invalid packets would make your connection seem very slow.

Dave ;)

---

