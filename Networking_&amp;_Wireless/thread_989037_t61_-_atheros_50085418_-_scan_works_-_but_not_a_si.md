---
title: "t61 - atheros 5008/5418 - scan works - but not a single packet sent out ath0"
date: 2008-11-21
forum: Networking &amp; Wireless
---

### Post by hgans on 2008-11-21
had huge performace and re-associate issues with ath_5k/9k drivers dilivered with intrepid.
so i installed madwifi-hal-0.10.5.6-r3861-20080903 - which worked like charme since today.

since now i see that my wlan card is not sending out one single packet.
i verified this via my cisco ap- it gets nothing
and also verified via tcpdump on ath0
also athstats show 0 packets on TX:

```

$ athstats
7633 tx management frames
6 long on-chip tx retries
2712 tx frames with no ack marked
33 tx frames with short preamble
11142 rx failed due to bad CRC
1 rx failed due to frame too short
rssi of last ack: 4294967168
rssi of last rcv: 14
Antenna profile:
[0] tx     5763 rx    34872

```

**further tests:**

- i tried to re-compile the madwifi driver --> no change
- then i re-activated the ath_5k/8k modules --> no change
- booted my windows XP partition --> wlan worked as expected

**general information:** (dmesg attached)

```

uname -mr

2.6.27-7-generic i686

```


```

$ lspci | grep Network controller
03:00.0 Network controller: Atheros Communications Inc. AR5008 Wireless Network Adapter (rev 01)

```

```

$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:1e:4c:68:c9:a8  
          inet6 addr: fe80::21e:4cff:fe68:c9a8/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```


```

$ iwconfig

ath0      IEEE 802.11g  ESSID:"SpeedTouch80D217"  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Tx-Power:14 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=14/70  Signal level=-82 dBm  Noise level=-96 dBm
          Rx invalid nwid:8349  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

```


$ lsmod | grep ath
ath_rate_sample        21248  1 
ath_pci               216632  0 
wlan                  240752  7 wlan_scan_ap,wlan_tkip,wlan_ccmp,wlan_scan_sta,ath_rate_sample,ath_pci
ath_hal               312288  3 ath_rate_sample,ath_pci

$ lsmod | grep wlan
wlan_scan_ap           17536  0 
wlan_tkip              19584  0 
wlan_ccmp              15360  0 
wlan_scan_sta          21376  1 
wlan                  240752  7 wlan_scan_ap,wlan_tkip,wlan_ccmp,wlan_scan_sta,ath_rate_sample,ath_pci

```

```

$ sudo lshw -C network
  *-network
       description: Ethernet interface
       product: 82566MM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:1e:37:1e:fb:90
       size: 1GB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 10bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driververson=0.3.3.3-k6 duplex=full firmware=0.3-0 ip=192.168.10.228 latency=0 link=yes module=e1000e multicast=yes port=twisted pair speed=1GB/s

  *-network
       description: Wireless interface
       product: AR5008 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wifi0
       version: 01
       serial: 00:1e:4c:68:c9:a8
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci latency=0 module=ath_pci multicast=yes wireless=IEEE 802.11g

  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: fa:05:c2:97:aa:36
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```


```

$ iwlist scan
lo        Interface doesn't support scanning.
eth0      Interface doesn't support scanning.
wifi0     Interface doesn't support scanning.

ath0      Scan completed :
          Cell 01 - Address: 00:14:6C:3C:62:26
                    ESSID:"NETGEAR"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=13/70  Signal level=-82 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

          Cell 02 - Address: 00:1B:2F:D7:33:6C
                    ESSID:"SAMARO"
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality=14/70  Signal level=-81 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:wme_ie=dd180050f2020101800003a4000027a4000042435e0062322f00

          Cell 03 - Address: 00:90:D0:FF:1F:81
                    ESSID:"SpeedTouch80D217"
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality=16/70  Signal level=-79 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100

```

i have no idea how to troubleshoot any further and very appreciated for any help!
br
herwig

---

