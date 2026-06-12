---
title: "Many attempts before connect to Wifi"
date: 2014-04-23
forum: Networking &amp; Wireless
---

### Post by Raph_B on 2014-04-23
Hi,

Since few months , I have difficulty to connect to a network with signal not perfect (less then 90%). 
I need many tries before finally be able to have a connection ... worst is the connection more tries is needed  to have connection.
Unsecured or Secured Wifi is the problem is there...
On Window , there is no problem...
I was on Ubuntu 12.10 32 bit , now I'm with 14.04 , but the problem is still there. And like I said , the problem appeared few months ago ...
The problem seems to be with all the routers and connection type.

I already tried to disable N, and few other things (like use Wicd).
Nothing seem to work.... 

Looking for other ideas to solve is paintful problem...
Thank for the help!

iwconfig

```
 iwconfigwlan0     IEEE 802.11bg  ESSID:"UQAM Wi-Fi"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:3A:98:0A:49:02   
          Bit Rate=54 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=55/70  Signal level=-55 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:435   Missed beacon:0


lo        no wireless extensions.


eth0      no wireless extensions.



```

ifconfig
```
ifconfigeth0      Link encap:Ethernet  HWaddr e8:e0:b7:47:8d:62  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Memory:e0600000-e0620000 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2788 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2788 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:274474 (274.4 KB)  TX bytes:274474 (274.4 KB)


wlan0     Link encap:Ethernet  HWaddr 68:5d:43:b3:35:58  
          inet addr:172.29.126.188  Bcast:172.29.127.255  Mask:255.255.192.0
          inet6 addr: fe80::6a5d:43ff:feb3:3558/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15766 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14335 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13442553 (13.4 MB)  TX bytes:2836435 (2.8 MB)



```

iwlist
```
iwlist scanw
lan0     Scan completed :
          Cell 01 - Address: 00:3A:98:0A:49:02
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=60/70  Signal level=-50 dBm  
                    Encryption key:on
                    ESSID:"UQAM Wi-Fi"
                    Bit Rates:5.5 Mb/s; 6 Mb/s; 9 Mb/s; 11 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000d4d30614d
                    Extra: Last beacon: 464348ms ago
                    IE: Unknown: 000A5551414D2057692D4669
                    IE: Unknown: 01088B0C129618243048
                    IE: Unknown: 03010B
                    IE: Unknown: 0706434120010B1E
                    IE: Unknown: 0B0516001C8D5B
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 3202606C
                    IE: Unknown: 851E01008F000F00FF035900504B2D31412D4150320000000000000016000027
                    IE: Unknown: 9606004096001400
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD050040961401


lo        Interface doesn't support scanning.


eth0      Interface doesn't support scanning.



```


sudo lshw -C network
```
 *-network                      description: Ethernet interface
       product: 82579V Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 04
       serial: e8:e0:b7:47:8d:62
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=2.0.0-k firmware=0.13-4 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:41 memory:e0600000-e061ffff memory:e063b000-e063bfff ioport:2080(size=32)
  *-network
       description: Wireless interface
       product: Centrino Wireless-N 2230
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: c4
       serial: 68:5d:43:b3:35:58
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.5.0-45-generic firmware=18.168.6.1 ip=172.29.126.188 latency=0 link=yes multicast=yes wireless=IEEE 802.11bg
       resources: irq:45 memory:e0400000-e0401fff
```

---

### Post by sanderj on 2014-04-23
I now have the same with my 14.04. My workaround: disable Networking then re-enable, and my Wifi connects.

Oh, you could also look at the output of 'dmesg' in case of problems

FWIW: "I'm with 14.10 " ... really?

---

### Post by Raph_B on 2014-04-23
dmesg give me something like this , I will to other post if I can find why link is not ready...:

[ 1341.390370] e1000e 0000:00:19.0: irq 42 for MSI/MSI-X
[ 1341.699234] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[ 1341.706844] iwlwifi 0000:02:00.0: Radio type=0x2-0x0-0x0
[ 1341.785182] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1341.953131] e1000e 0000:00:19.0: irq 42 for MSI/MSI-X
[ 1342.054705] e1000e 0000:00:19.0: irq 42 for MSI/MSI-X
[ 1342.055454] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 1342.726208] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[ 1342.733791] iwlwifi 0000:02:00.0: Radio type=0x2-0x0-0x0
[ 1342.802307] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1352.837421] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[ 1352.844988] iwlwifi 0000:02:00.0: Radio type=0x2-0x0-0x0
[ 1352.912337] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1352.986315] wlan0: authenticate with 00:3a:98:0a:49:02
[ 1352.991075] wlan0: send auth to 00:3a:98:0a:49:02 (try 1/3)
[ 1352.992547] wlan0: authenticated
[ 1352.992569] iwlwifi 0000:02:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 1352.995567] wlan0: associate with 00:3a:98:0a:49:02 (try 1/3)
[ 1352.998926] wlan0: RX AssocResp from 00:3a:98:0a:49:02 (capab=0x401 status=17 aid=0)
[ 1352.998930] wlan0: 00:3a:98:0a:49:02 denied association (code=17)
[ 1353.017008] wlan0: deauthenticating from 00:3a:98:0a:49:02 by local choice (reason=3)
[ 1357.993554] wlan0: authenticate with 00:3a:98:0a:49:02
[ 1357.997520] wlan0: send auth to 00:3a:98:0a:49:02 (try 1/3)
[ 1357.997550] wlan0: deauthenticating from 00:3a:98:0a:49:02 by local choice (reason=3)
[ 1358.567628] wlan0: authenticate with 34:bd:c8:16:f4:a2
[ 1358.572504] wlan0: send auth to 34:bd:c8:16:f4:a2 (try 1/3)
[ 1358.574644] wlan0: authenticated
[ 1358.574674] iwlwifi 0000:02:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 1358.574679] wlan0: waiting for beacon from 34:bd:c8:16:f4:a2
[ 1358.594214] wlan0: associate with 34:bd:c8:16:f4:a2 (try 1/3)
[ 1358.598125] wlan0: RX AssocResp from 34:bd:c8:16:f4:a2 (capab=0x431 status=0 aid=8)
[ 1358.601682] wlan0: associated

---

### Post by enjoy10 on 2014-06-27
I have the same problem but with eth0 , sometime I can't get ip, I need to reboot and go to wind8 and then reboot on ubuntu 14.04
I have intel 
Ethernet Connection I217-LM
using same mod e1000e  version 3.0.4-NAPI

 




> **Raph_B said:**
> dmesg give me something like this , I will to other post if I can find why link is not ready...:

[ 1341.390370] e1000e 0000:00:19.0: irq 42 for MSI/MSI-X
[ 1341.699234] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[ 1341.706844] iwlwifi 0000:02:00.0: Radio type=0x2-0x0-0x0
[ 1341.785182] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1341.953131] e1000e 0000:00:19.0: irq 42 for MSI/MSI-X
[ 1342.054705] e1000e 0000:00:19.0: irq 42 for MSI/MSI-X
[ 1342.055454] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 1342.726208] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[ 1342.733791] iwlwifi 0000:02:00.0: Radio type=0x2-0x0-0x0
[ 1342.802307] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1352.837421] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[ 1352.844988] iwlwifi 0000:02:00.0: Radio type=0x2-0x0-0x0
[ 1352.912337] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1352.986315] wlan0: authenticate with 00:3a:98:0a:49:02
[ 1352.991075] wlan0: send auth to 00:3a:98:0a:49:02 (try 1/3)
[ 1352.992547] wlan0: authenticated
[ 1352.992569] iwlwifi 0000:02:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 1352.995567] wlan0: associate with 00:3a:98:0a:49:02 (try 1/3)
[ 1352.998926] wlan0: RX AssocResp from 00:3a:98:0a:49:02 (capab=0x401 status=17 aid=0)
[ 1352.998930] wlan0: 00:3a:98:0a:49:02 denied association (code=17)
[ 1353.017008] wlan0: deauthenticating from 00:3a:98:0a:49:02 by local choice (reason=3)
[ 1357.993554] wlan0: authenticate with 00:3a:98:0a:49:02
[ 1357.997520] wlan0: send auth to 00:3a:98:0a:49:02 (try 1/3)
[ 1357.997550] wlan0: deauthenticating from 00:3a:98:0a:49:02 by local choice (reason=3)
[ 1358.567628] wlan0: authenticate with 34:bd:c8:16:f4:a2
[ 1358.572504] wlan0: send auth to 34:bd:c8:16:f4:a2 (try 1/3)
[ 1358.574644] wlan0: authenticated
[ 1358.574674] iwlwifi 0000:02:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 1358.574679] wlan0: waiting for beacon from 34:bd:c8:16:f4:a2
[ 1358.594214] wlan0: associate with 34:bd:c8:16:f4:a2 (try 1/3)
[ 1358.598125] wlan0: RX AssocResp from 34:bd:c8:16:f4:a2 (capab=0x431 status=0 aid=8)
[ 1358.601682] wlan0: associated

---

