---
title: "Wireless usually difficult to get started, but solid once it's working"
date: 2008-12-15
forum: New to Ubuntu
---

### Post by uzrlfr on 2008-12-15
I'm using 8.10 on a vaio txn, and my wireless works very inconsistently:

- Usually, when I startup, the wireless claims to be connected, but I can't access anything on the web.
- To fix this, I either reboot (but it takes several reboots, usually), or run "/etc/init.d/networking restart" (several times, but usually it's ineffective), or I restart my router (most effective but inconvenient, usually fixes the problem with one restart).
- Once wireless is working normally (i.e. I can access the web), it is solid until I reboot.
- After I reboot, back to step 1.

Note that several other machines are connected wirelessly to this router, without these symptoms, including the very same vaio, when booted into vista (dual-boot).

Any help would be appreciated.

---

### Post by Michael.Godawski on 2008-12-15
hi uzrlfr,

please give us some more info about your wlan. To do so run the terminal
applications > accessories > terminal
and run these commands:

```
sudo lshw -C network
iwconfig
ifconfig
sudo iwlst scan
```Run each of these commands separately and post the output here, using the code brackets to make it easier for reading. 

After the sudo commands the login password must be entered.

---

### Post by uzrlfr on 2008-12-19
Thanks for your reply.

```

$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 02
       serial: 00:19:d2:ba:32:52
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 ip=192.168.100.8 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg
  *-network
       description: Ethernet interface
       product: PRO/100 VM Network Connection
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:06:08.0
       logical name: eth0
       version: 02
       serial: 00:13:a9:f9:8a:9b
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=half firmware=N/A latency=66 link=no maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=10MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 5a:c6:5a:dd:ac:3e
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

eth1      IEEE 802.11abg  ESSID:"2e37"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:14:A4:16:D4:6C   
          Bit Rate=24 Mb/s   Tx-Power=14 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=81/100  Signal level:-53 dBm  Noise level=-88 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:13:a9:f9:8a:9b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth1      Link encap:Ethernet  HWaddr 00:19:d2:ba:32:52  
          inet addr:192.168.100.8  Bcast:192.168.100.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12822 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10873 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:15411128 (15.4 MB)  TX bytes:1780327 (1.7 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:246 errors:0 dropped:0 overruns:0 frame:0
          TX packets:246 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15416 (15.4 KB)  TX bytes:15416 (15.4 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-19-D2-BA-32-52-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:18:39:7D:DE:E4
                    ESSID:"bill"
                    Mode:Master
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=31/100  Signal level:-90 dBm  Noise level=-92 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=0000002b6d251183
                    Extra: Last beacon: 4344ms ago
          Cell 02 - Address: 00:1C:10:AF:F7:6E
                    ESSID:"Moon"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=45/100  Signal level:-82 dBm  Noise level=-90 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=0000008d674ac18b
                    Extra: Last beacon: 3512ms ago
          Cell 03 - Address: 00:14:BF:DA:E5:4A
                    ESSID:"linksys"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=40/100  Signal level:-85 dBm  Noise level=-90 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=0000041de8465184
                    Extra: Last beacon: 3672ms ago
          Cell 04 - Address: 00:1D:7E:69:FF:03
                    ESSID:""
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=31/100  Signal level:-90 dBm  Noise level=-90 dBm
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=00000e2843b8037a
                    Extra: Last beacon: 3676ms ago
          Cell 05 - Address: 00:0F:B5:E0:F0:DC
                    ESSID:"Private"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=37/100  Signal level:-87 dBm  Noise level=-90 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=000001e2018f9181
                    Extra: Last beacon: 3456ms ago
          Cell 06 - Address: 00:14:A4:16:D4:6C
                    ESSID:"2e37"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=86/100  Signal level:-47 dBm  Noise level=-90 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=000000b19903c186
                    Extra: Last beacon: 64ms ago
          Cell 07 - Address: 00:17:3F:84:0C:82
                    ESSID:"Zoe"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=28/100  Signal level:-92 dBm  Noise level=-90 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=000000804bb38177
                    Extra: Last beacon: 2644ms ago
          Cell 08 - Address: 00:16:B6:68:1E:20
                    ESSID:""
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=43/100  Signal level:-83 dBm  Noise level=-90 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=0000012c671b51de
                    Extra: Last beacon: 2712ms ago

pan0      Interface doesn't support scanning.

$ 


```

---

### Post by uzrlfr on 2008-12-20
The prior post was when I was connected and could access the web.  Below is the output when I cannot connect to the web:

Thanks!

```

$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 02
       serial: 00:19:d2:ba:32:52
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 ip=192.168.100.8 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg
  *-network
       description: Ethernet interface
       product: PRO/100 VM Network Connection
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:06:08.0
       logical name: eth0
       version: 02
       serial: 00:13:a9:f9:8a:9b
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=half firmware=N/A latency=66 link=no maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=10MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 9e:a7:44:55:e7:42
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

eth1      IEEE 802.11abg  ESSID:"2e37"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:14:A4:16:D4:6C   
          Bit Rate=54 Mb/s   Tx-Power=14 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=97/100  Signal level:-29 dBm  Noise level=-64 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:13:a9:f9:8a:9b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth1      Link encap:Ethernet  HWaddr 00:19:d2:ba:32:52  
          inet addr:192.168.100.8  Bcast:192.168.100.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:41 errors:0 dropped:0 overruns:0 frame:0
          TX packets:312 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4740 (4.7 KB)  TX bytes:31136 (31.1 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:246 errors:0 dropped:0 overruns:0 frame:0
          TX packets:246 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15416 (15.4 KB)  TX bytes:15416 (15.4 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-19-D2-BA-32-52-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:18:39:7D:DE:E4
                    ESSID:"bill"
                    Mode:Master
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=40/100  Signal level:-85 dBm  Noise level=-61 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=0000003f34ed3183
                    Extra: Last beacon: 3888ms ago
          Cell 02 - Address: 00:0F:B5:E0:F0:DC
                    ESSID:"Private"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=42/100  Signal level:-84 dBm  Noise level=-61 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=00000002ca8b7181
                    Extra: Last beacon: 3244ms ago
          Cell 03 - Address: 00:14:BF:DA:E5:4A
                    ESSID:"linksys"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=37/100  Signal level:-87 dBm  Noise level=-61 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=00000431b017d186
                    Extra: Last beacon: 3484ms ago
          Cell 04 - Address: 00:1C:10:AF:F7:6E
                    ESSID:"Moon"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=38/100  Signal level:-86 dBm  Noise level=-61 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=000000050c5a51f1
                    Extra: Last beacon: 3656ms ago
          Cell 05 - Address: 00:14:A4:16:D4:6C
                    ESSID:"2e37"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=97/100  Signal level:-28 dBm  Noise level=-61 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=000000c560c5a18c
                    Extra: Last beacon: 36ms ago
          Cell 06 - Address: 00:12:17:B5:0D:97
                    ESSID:""
                    Mode:Master
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=35/100  Signal level:-88 dBm  Noise level=-61 dBm
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=0000057aa0ed9008
                    Extra: Last beacon: 3048ms ago
          Cell 07 - Address: 00:1D:7E:65:FB:83
                    ESSID:"kunal"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=33/100  Signal level:-89 dBm  Noise level=-61 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=000000118eb55183
                    Extra: Last beacon: 3688ms ago
          Cell 08 - Address: 00:16:B6:E3:6D:12
                    ESSID:"linksys"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=28/100  Signal level:-92 dBm  Noise level=-61 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=000000b5cf223bee
                    Extra: Last beacon: 3652ms ago
          Cell 09 - Address: 00:17:3F:84:0C:82
                    ESSID:"Zoe"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=30/100  Signal level:-91 dBm  Noise level=-61 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=0000009413788177
                    Extra: Last beacon: 2620ms ago
          Cell 10 - Address: 00:16:B6:68:1E:20
                    ESSID:""
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=30/100  Signal level:-91 dBm  Noise level=-61 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=000001402ee9b181
                    Extra: Last beacon: 2616ms ago

pan0      Interface doesn't support scanning.


```

---

### Post by SunnyRabbiera on 2008-12-20
Wireless is still a tricky subject, Linux is getting better though but its usually more of an issue with the company that makes your wireless devices then linux itself.

---

