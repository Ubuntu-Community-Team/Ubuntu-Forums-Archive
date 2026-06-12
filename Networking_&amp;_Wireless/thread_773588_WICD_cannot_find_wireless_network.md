---
title: "WICD cannot find wireless network"
date: 2008-04-29
forum: Networking &amp; Wireless
---

### Post by 052d on 2008-04-29
because network manager cannot find my wireless card, i switch to wicd.
at first it works, i can use wireless network with it.
but soon wicd appears cannot find wireless network.
i use iwlist scan, it appears:

laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

irda0     Interface doesn't support scanning.

eth1      Failed to read scan data : Resource temporarily unavailable

i use iwconfig, it appears:

-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

eth1      IEEE 802.11b  ESSID:"TP-LINK"  Nickname:"Prism  I"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0A:AB:D9:96:1E   
          Bit Rate:2 Mb/s   Sensitivity:1/3  
          Retry short limit:8   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=28/92  Signal level=149/153  Noise level=107/153
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

please help me.

---

### Post by Alldan on 2008-04-29
first write your wireless setting in network administration tool then setup wicd (put your security encryption key in advanced settings and check automatically connect) then reboot

---

