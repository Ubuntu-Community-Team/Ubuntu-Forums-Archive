---
title: "inspiron 1520 wi-fi urgent help needed??"
date: 2008-04-05
forum: Networking &amp; Wireless
---

### Post by mecp on 2008-04-05
Hello everyone, I am very new user to ubuntu(7.1.0 gutsy-gibbon). I have Dell Inspiron 1520 . Evrything is working fine except wi-fi. once It also worked nicely with wpa psk string authentication. But after a reboot it stuck surprisingly. wireless options were removed from network dropdown menu in top panel. It is working fine with eth0(Lan).i have intel3945 wiress adapter. Im in urgent need of help as i require necessary access to wifi......... 

results of some commands are::

**sudo iwlist scanning**

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:50:F1:21:10:10
                    ESSID:"III/13, Wi-CP"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 22 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Quality=88/100  Signal level=-45 dBm  Noise level=-45 dBm
                    IE: WPA Version 1
                        Group Cipher : WEP-40
                        Pairwise Ciphers (1) : WEP-40
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 248ms ago

ppp0      Interface doesn't support scanning.

**iwconfig**

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:off/any  
          Mode:Managed  Frequency=nan kHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:18   Missed beacon:0

ppp0      no wireless extensions.

**ifconfig**

eth0      Link encap:Ethernet  HWaddr 00:1C:B9:BB:EF:4A  
          inet6 addr: fe80::219:b9ff:fe83:ef4a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:715 errors:0 dropped:0 overruns:0 frame:0
          TX packets:699 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:579236 (565.6 KB)  TX bytes:101328 (98.9 KB)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 00:1B:77:C1:0C:EC  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:18 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 Base address:0xa000 Memory:f9fff000-f9ffffff 

eth0:avah Link encap:Ethernet  HWaddr 00:19:E9:83:FF:4A  
          inet addr:192.54.8.67  Bcast:192.54.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1176 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1176 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:64176 (62.6 KB)  TX bytes:64176 (62.6 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:177.196.110.193  P-t-P:177.196.110.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1460  Metric:1
          RX packets:652 errors:0 dropped:0 overruns:0 frame:0
          TX packets:610 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:558170 (545.0 KB)  TX bytes:76089 (74.3 KB)

if someone can help me out den plz, i'll b thankful...... !

---

