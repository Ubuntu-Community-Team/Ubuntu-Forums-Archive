---
title: "Excessively High Invalid Nwid"
date: 2007-01-03
forum: Networking &amp; Wireless
---

### Post by marx2k on 2007-01-03
Basically just wondering why my Rx invalid nwid is so high

lspci output:
02:0b.0 Ethernet controller: Atheros Communications, Inc. AR5005G 802.11abg NIC (rev 01)

iwconfig: 
```

ath0      IEEE 802.11g  ESSID:"ghostdog"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:18:39:DF:3F:0E   
          Bit Rate:54 Mb/s   Tx-Power:9 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=45/94  Signal level=-50 dBm  Noise level=-95 dBm
          Rx invalid nwid:17839  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
(notice the high nwid)

ifconfig sections that relate to this problem:
```

ath0      Link encap:Ethernet  HWaddr 00:11:50:D4:FD:E8  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:90303 errors:0 dropped:0 overruns:0 frame:0
          TX packets:86750 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:88180731 (84.0 MiB)  TX bytes:77658150 (74.0 MiB)

wifi0     Link encap:UNSPEC  HWaddr 00-11-50-D4-FD-E8-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:300905 errors:0 dropped:0 overruns:0 frame:6200
          TX packets:93080 errors:19 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:110457710 (105.3 MiB)  TX bytes:88097980 (84.0 MiB)
          Interrupt:185 Memory:f8a40000-f8a50000 

```

Router is a Linksys WRT54G v6 with Firmware: DD-WRT v23 SP2 (09/15/06) micro
router shows:
Wireless Packet Info
Received (RX): 122410 OK, 947 errors 
Transmitted (TX): 119707 OK, 4300 errors  

Mixed Network (also have a laptop with B), Channel 6, transmitting at 54Mbps rate at 70mW power.  (default is 28mW)
ACK timing = 2000
no WEP
MAC filtering is ON
Beacon Interval = 40 (dropped it down from 100ms)
DTIM interval = 1
Frag Threshold = 2346
RTS Threshold = 2347 
Preamble = Long


iwlist ath0 scan:
```

          Cell 02 - Address: 00:18:39:DF:3F:0E
                    ESSID:"ghostdog"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=45/94  Signal level=-50 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=40
          Cell 03 - Address: 00:15:E9:5E:09:25
                    ESSID:"default"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=2/94  Signal level=-93 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:wme_ie=dd180050f2020101000002a4000027a4000042435e0062322f00

```

Cell 01 is also 'ghostdog' which is my router, but just with no essid (ESSID:"") -- Im guessing it shows that since I have router set to not broadcast ESSID
Cell 02 is me
Cell 03 must be someone down the street somewhere. Although they are also on Channel 6, it seems to be a very weak signal and I doubt it is interfering with me (this problem also appears when this cell is not showing)

In the few minutes it took me to write this,  Rx invalid nwid is now 24216

Thank you in advance!

---

### Post by marx2k on 2007-01-04
Giving this a little bump here... Im trying out the network card on another computer and getting 0 Rx Invalid Nwid -- So Im not really sure what the problem could be!

---

### Post by kmcguire3413 on 2007-01-14
Rx invalid nwid stands for, "The wireless card read a packet that contained a invalid network identification." From my knowledge this does not mean the packet was corrupted but rather another access point using a different BSSID(similar to the SSID) is on the same frequency and your network card can hear it.

"man iwconfig"
"/nwid"

---

