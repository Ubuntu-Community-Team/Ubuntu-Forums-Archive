---
title: "Can't connect using Wireless"
date: 2008-07-16
forum: Networking &amp; Wireless
---

### Post by elegua on 2008-07-16
Hi Guys,

Please i need help with my wireless conection, i have a Toshiba P25 with Atheros  AR5211 802.11ab NIC, i installed the lastest version of **madwifi** and WICD Manager, i can see my router but i can't conect to it, i'm using WPA-PSK.

Here some output:

```
gabby@gabby-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 10
       serial: 00:02:3f:82:3c:02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.4.8 latency=32 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network:1
       description: Wireless interface
       product: AR5211 802.11ab NIC
       vendor: Atheros Communications Inc.
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: wifi0
       version: 01
       serial: 00:90:96:59:f5:dc
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11a
gabby@gabby-laptop:~$
``` 

**gedit /etc/network/interfaces**

```
auto lo
iface lo inet loopback

auto ath0
iface ath0 inet dhcp
```

 **sudo iwlist scan**

```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wifi0     Interface doesn't support scanning.

ath0      Scan completed :
          Cell 01 - Address: 00:13:10:27:24:31
                    ESSID:"thegirls"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=25/70  Signal level=-70 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
          Cell 02 - Address: 00:1A:2F:91:E2:D0
                    ESSID:"ITCS"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=43/70  Signal level=-52 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra:wme_ie=dd180050f2020101830003a4000027a4000042435e0062322f00
          Cell 03 - Address: 00:11:20:1B:5B:DC
                    ESSID:"ITCS"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=32/70  Signal level=-63 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra:wme_ie=dd180050f20201018c0003a4000027a4000042435e0062322f00
          Cell 04 - Address: 00:0A:95:F6:48:6C
                    ESSID:"Maxx Network"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=10/70  Signal level=-85 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
```




Do i need to do something else?.

Thanks in advance.

---

