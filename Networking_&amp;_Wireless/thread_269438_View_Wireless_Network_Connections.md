---
title: "View Wireless Network Connections"
date: 2006-10-01
forum: Networking &amp; Wireless
---

### Post by Todd0060 on 2006-10-01
Does Ubuntu not have a place to view Available Wireless Networks like Windows XP, for example?  I am trying to install apps like Network Manager and GTKWifi which seem to provide that functionality, but shouldn't an OS come with that, for example like XP?  Trying to understand how to view wireless networks to decide, which one to connect to and trying to understand the logic of the Ubuntu OS not having it be automatically included like the office apps and such.  Tks.

---

### Post by muggins on 2006-10-01
If you install wifi radar it will show you any available networks.

---

### Post by ThaRabbit on 2006-10-02
You could just use this command:
```
iwlist wlan0 scan
``` ?

It outputs all you need to know:
```
stefan@lapsteef:~$ iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:13:5F:FB:E3:43
                    ESSID:""
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:0/100  Signal level:-73 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: 00:13:5F:FB:E3:40
                    ESSID:"GUEST"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:0/100  Signal level:-73 dBm  Noise level:-256 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 03 - Address: 00:13:5F:FB:E0:F3
                    ESSID:""
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:0/100  Signal level:-85 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 04 - Address: 00:13:5F:FB:EC:91
                    ESSID:"WLAN"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:0/100  Signal level:-80 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 05 - Address: 00:13:5F:FB:EB:72
                    ESSID:"eduroam"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:0/100  Signal level:-66 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 06 - Address: 00:13:5F:FB:EB:70
                    ESSID:"GUEST"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:0/100  Signal level:-100 dBm  Noise level:-256 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

```

*sidenote*

Just tried wifi radar, works fine :)

---

### Post by pacohc on 2008-03-25
ubuntu gutsy 7.10
in my case both iwlist and wifi-radar show ONLY the essid connected
it does no scan, therefore it's not possible to connect if I don't know the essid
am I missing something?
thanks

---

