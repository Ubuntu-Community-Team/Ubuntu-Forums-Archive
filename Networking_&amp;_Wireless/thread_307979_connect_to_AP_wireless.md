---
title: "connect to AP wireless"
date: 2006-11-27
forum: Networking &amp; Wireless
---

### Post by MySweetTedy on 2006-11-27
hi i am trying for few days to configure everything on my wireless card and finally i got it working, in my university i got connected to the LRZ server, i had traffic with it and was able to open different sites. At home i have installed a wireless router, i can connect through Ethernet cable and everything works quite ok, also i got a xp laptop to have wireless Internet, all security and mac adr filters are off, my ath0 seems to work also fine <b>BUT</b> i cannot connect to neighter the router preferences via [http://192.168.0.1/](http://192.168.0.1/) nor to the Internet. here what i get from the iwlist scan:

```
ath0      Scan completed :
          Cell 01 - Address: 00:01:E3:D0:26:91
                    ESSID:""
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=7/94  Signal level=-88 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:wme_ie=dd180050f2020101000003a4000027a4000042435e0062322f00
                    Extra:ath_ie=dd0900037f0101000dff7f
          Cell 02 - Address: 00:0C:F6:21:7B:33
                    ESSID:"Sitecom"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=55/94  Signal level=-40 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
          Cell 03 - Address: 00:15:AF:08:00:84
                    ESSID:"Powerserver - X6800"
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality=13/94  Signal level=-82 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK  


```
any help will be usefull, i tried 2 wireless clients wifi-radar and wireless assistant

---

### Post by darrenm on 2006-11-27
what does sudo ifconfig -a say?

---

### Post by MySweetTedy on 2006-11-29
```
ath0      Link encap:Ethernet  HWaddr 00:0F:A3:46:89:E3  
          inet6 addr: fe80::20f:a3ff:fe46:89e3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

eth0      Link encap:Ethernet  HWaddr 00:0A:E4:EB:11:DD  
          inet addr:192.168.0.102  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20a:e4ff:feeb:11dd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1509 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1550 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:882792 (862.1 KiB)  TX bytes:205896 (201.0 KiB)
          Interrupt:225 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wifi0     Link encap:UNSPEC  HWaddr 00-0F-A3-46-89-E3-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6726 errors:0 dropped:0 overruns:0 frame:8520
          TX packets:316 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:869397 (849.0 KiB)  TX bytes:15064 (14.7 KiB)
          Interrupt:169 Memory:d0340000-d0350000 


```

---

