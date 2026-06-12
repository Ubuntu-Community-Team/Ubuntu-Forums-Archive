---
title: "tp-linkwn722n not working"
date: 2014-10-23
forum: Networking &amp; Wireless
---

### Post by xkr34torx on 2014-10-23
```


########## wireless info START ##########


Report from: 23 Oct 2014 20:42 MST -0700


Booted last: 20 Oct 2014 19:25 MST -0700


Script from: 20 Sep 2014 23:04 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.1 LTS
Release:	14.04
Codename:	trusty


##### kernel ############################


Linux 3.13.0-37-generic #64-Ubuntu SMP Mon Sep 22 21:30:01 UTC 2014 i686 i686 i686 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################




03:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 1000 [Condor Peak] [8086:0083]
	Subsystem: Intel Corporation Centrino Wireless-N 1000 BGN [8086:1305]
	Kernel driver in use: iwlwifi


04:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8131 Gigabit Ethernet [1969:1063] (rev c0)
	Subsystem: ASUSTeK Computer Inc. Device [1043:1820]
	Kernel driver in use: atl1c


##### lsusb #############################


Bus 002 Device 003: ID 04f2:b036 Chicony Electronics Co., Ltd Asus Integrated 0.3M UVC Webcam
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 045e:074f Microsoft Corp. 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0cf3:9271 Atheros Communications, Inc. AR9271 802.11n
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


##### PCMCIA card info ##################




##### rfkill ############################


0: asus-wwan: Wireless WAN
	Soft blocked: no
	Hard blocked: no
1: asus-wimax: WiMAX
	Soft blocked: no
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


##### lsmod #############################


iwldvm                223488  0 
iwlwifi               157083  1 iwldvm
ath9k_common           20781  0 
ath9k_hw              405068  1 ath9k_common
ath                    24182  2 ath9k_common,ath9k_hw
mac80211              480506  1 iwldvm
cfg80211              430998  5 ath,iwlwifi,ath9k_common,mac80211,iwldvm
compat                 13617  5 cfg80211,iwlwifi,ath9k_common,mac80211,iwldvm
mxm_wmi                12893  0 
wmi                    18673  1 mxm_wmi


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eth0      Link encap:Ethernet  HWaddr e0:cb:4e:84:5b:99  
          inet addr:192.168.3.78  Bcast:192.168.3.255  Mask:255.255.255.0
          inet6 addr: 2002:4468:a581:e472:e4c2:f648:6395:56c2/64 Scope:Global
          inet6 addr: fe80::e2cb:4eff:fe84:5b99/64 Scope:Link
          inet6 addr: 2002:4468:a581:e472:7047:ec84:514c:249d/64 Scope:Global
          inet6 addr: 2002:4468:a581:e472:e2cb:4eff:fe84:5b99/64 Scope:Global
          inet6 addr: 2002:4468:a581:e472:1886:55ae:cf27:c34e/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:749843 errors:0 dropped:0 overruns:0 frame:0
          TX packets:936657 errors:0 dropped:0 overruns:0 carrier:2
          collisions:0 txqueuelen:1000 
          RX bytes:207050133 (207.0 MB)  TX bytes:623399906 (623.3 MB)


wlan0     Link encap:Ethernet  HWaddr 00:1e:64:41:01:de  
          inet addr:192.168.3.53  Bcast:192.168.3.255  Mask:255.255.255.0
          inet6 addr: 2002:4468:a581:e472:f5cf:9d4d:3cf0:27e3/64 Scope:Global
          inet6 addr: 2002:4468:a581:e472:21e:64ff:fe41:1de/64 Scope:Global
          inet6 addr: fe80::21e:64ff:fe41:1de/64 Scope:Link
          inet6 addr: 2002:4468:a581:e472:a07c:55dc:48cc:3687/64 Scope:Global
          inet6 addr: 2002:4468:a581:e472:4c81:6edf:735f:b616/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1494415 errors:0 dropped:1 overruns:0 frame:0
          TX packets:1181471 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:261631353 (261.6 MB)  TX bytes:1407081735 (1.4 GB)




##### iwconfig ##########################


lo        no wireless extensions.


eth0      no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"sou.l..fly"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: C4:3D:C7:B0:0D:2F   
          Bit Rate=1 Mb/s   Tx-Power=14 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=61/70  Signal level=-49 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:6  Invalid misc:483   Missed beacon:0




##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.3.43    0.0.0.0         UG    0      0        0 eth0
192.168.3.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
192.168.3.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0


##### resolv.conf #######################


nameserver 127.0.1.1


##### nm-tool ###########################




NetworkManager Tool


State: connected (global)


- Device: eth0  [Ethernet connection 1] ----------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             connected
  Default:           yes
  HW Address:        E0:CB:4E:84:5B:99


  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         192.168.3.78
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.3.43


    DNS:             192.168.3.43




- Device: wlan0  [sou.l..fly] --------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connected
  Default:           no
  HW Address:        00:1E:64:41:01:DE


  Capabilities:
    Speed:           1 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    *sou.l..fly:     Infra, C4:3D:C7:B0:0D:2F, Freq 2412 MHz, Rate 54 Mb/s, Strength 70 WPA2
    CenturyLink2935: Infra, 5C:F4:AB:29:9C:49, Freq 2462 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    CenturyLink8767: Infra, 10:9F:A9:A5:4C:64, Freq 2412 MHz, Rate 54 Mb/s, Strength 47 WPA WPA2
    HP-Print-57-Photosmart 7520: Infra, 10:60:4B:C6:41:57, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WPA2
    NETGEAR45:       Infra, 08:BD:43:C9:DA:9E, Freq 2462 MHz, Rate 54 Mb/s, Strength 40 WPA2
    HP-Print-D4-Deskjet 3510 series: Infra, 28:92:4A:96:85:D4, Freq 2462 MHz, Rate 54 Mb/s, Strength 24 WPA2
    Sonya's iPhone:  Infra, 2A:70:45:51:1A:56, Freq 2437 MHz, Rate 54 Mb/s, Strength 24 WPA2
    Biteme:          Infra, 20:76:00:04:7B:F4, Freq 2462 MHz, Rate 54 Mb/s, Strength 25 WPA2
    iTero:           Infra, 10:FE:ED:CA:54:62, Freq 2422 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2
    CenturyLink1793: Infra, 40:8B:07:80:70:04, Freq 2412 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2
    CenturyLink6430: Infra, 10:5F:06:8F:7F:B4, Freq 2412 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    Home:            Infra, 40:8B:07:70:CE:95, Freq 2437 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    myqwest5647:     Infra, 40:8B:07:77:44:B5, Freq 2437 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2
    Goldfighter 2.4: Infra, C4:04:15:13:F6:DF, Freq 2412 MHz, Rate 54 Mb/s, Strength 27 WPA2


  IPv4 Settings:
    Address:         192.168.3.53
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.3.43


    DNS:             192.168.3.43






##### NetworkManager.state ##############


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


##### NetworkManager.conf ###############


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false


##### NetworkManager profiles ###########
```

my intel works fine. used a backport and had the tplink working but then the intel wouldnt work, and used the backpoert instructions to get the intel working again.  is there a way for both to work at the same time or at least be able to choose between wlan0 or wlan1?

---

