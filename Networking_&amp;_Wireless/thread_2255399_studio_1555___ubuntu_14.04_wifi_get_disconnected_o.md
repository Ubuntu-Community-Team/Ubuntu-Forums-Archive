---
title: "studio 1555   ubuntu 14.04 wifi get disconnected often"
date: 2014-12-04
forum: Networking &amp; Wireless
---

### Post by skkmaths on 2014-12-04
I have installed ubuntu 14.04 in my studio 1555 dell laptop. In the wifi it displays all the signals but never get connected. Kindly help me to resolve this issue. Thank you

---

### Post by jeremy31 on 2014-12-04
> **skkmaths said:**
> I have installed ubuntu 14.04 in my studio 1555 dell laptop. In the wifi it displays all the signals but never get connected. Kindly help me to resolve this issue. Thank you

Could you look at the sticky posts in the forum, starting with the broadcom one to see if it fits your issue, if not read the other one 'Before posting in networking and wireless' then post the results of the wireless script using code tags if copying a text file- explained [http://ubuntuforums.org/showthread.php?p=12776168#post12776168](http://ubuntuforums.org/showthread.php?p=12776168#post12776168)

There are a few that are very good troubleshooting wifi posting here, Wild Man, Chili555, Varunendra to name a few

---

### Post by skkmaths on 2014-12-04
I have tried that sticky post but could not resolve my issue. Please help me

---

### Post by mörgæs on 2014-12-04
You are already being helped. Please run he wireless script as mentioned above.

---

### Post by skkmaths on 2014-12-04
```


########## wireless info START ##########

Report from: 04 Dec 2014 22:27 CLST -0300

Booted last: 04 Dec 2014 22:22 CLST -0300

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.13.0-41-generic #70-Ubuntu SMP Tue Nov 25 14:40:34 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

sed: can't read /root/.dmrc: No such file or directory
Could not be determined.

##### lspci #############################

04:00.0 Network controller [0280]: Intel Corporation WiFi Link 5100 [8086:4232]
    Subsystem: Intel Corporation WiFi Link 5100 AGN [8086:1321]
    Kernel driver in use: iwlwifi

08:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe [14e4:1698] (rev 10)
    Subsystem: Dell Device [1028:02be]
    Kernel driver in use: tg3

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0c45:63ea Microdia 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 005: ID 413c:8156 Dell Computer Corp. Wireless 370 Bluetooth Mini-card
Bus 003 Device 004: ID 413c:8158 Dell Computer Corp. Integrated Touchpad / Trackstick
Bus 003 Device 003: ID 413c:8157 Dell Computer Corp. Integrated Keyboard
Bus 003 Device 002: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

dell_wmi               12761  0 
sparse_keymap          13948  1 dell_wmi
dell_laptop            18168  0 
dcdbas                 14928  1 dell_laptop
iwldvm                232285  0 
iwlwifi               169932  1 iwldvm
wmi                    19177  1 dell_wmi
b43                   387371  0 
bcma                   52096  1 b43
mac80211              630653  2 b43,iwldvm
cfg80211              484040  4 b43,iwlwifi,mac80211,iwldvm
ssb                    62379  1 b43

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.1.158  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::222:19ff:fefc:7416/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2379 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2578 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1351151 (1.3 MB)  TX bytes:323655 (323.6 KB)
          Interrupt:17 

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1
search iptv.microsoft.com

##### nm-tool ###########################

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.158
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             disconnected
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    OSRM:            Infra, <MAC 'OSRM' [AN1]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 45 WPA2
    Cochrane:        Infra, <MAC 'Cochrane' [AN2]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2
    Gladys:          Infra, <MAC 'Gladys' [AN3]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2
    WIFI_TELSUR_MATIAS: Infra, <MAC 'WIFI_TELSUR_MATIAS' [AN4]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 47 WPA2
    MARIA 1:         Infra, <MAC 'MARIA 1' [AN5]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 42 WPA
    wifiISIDORA:     Infra, <MAC 'wifiISIDORA' [AN6]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 37 WPA
    90s:             Infra, <MAC '90s' [AN7]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 40 WPA WPA2
    zarate massri:   Infra, <MAC 'zarate massri' [AN8]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    CAMILA:          Infra, <MAC 'CAMILA' [AN9]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    BiancaCantudelosSantos: Infra, <MAC 'BiancaCantudelosSantos' [AN10]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2
    mazzarini:       Infra, <MAC 'mazzarini' [AN11]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 27 WPA
    Wifitelsur_DURAN1: Infra, <MAC 'Wifitelsur_DURAN1' [AN12]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 39 WEP
    GDUNRO:          Infra, <MAC 'GDUNRO' [AN13]>, Freq 2447 MHz, Rate 54 Mb/s, Strength 39 WEP
    Nicolas:         Infra, <MAC 'Nicolas' [AN14]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 34 WEP
    nflores:         Infra, <MAC 'nflores' [AN15]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 30 WEP
    Caymaco1:        Infra, <MAC 'Caymaco1' [AN16]>, Freq 2427 MHz, Rate 54 Mb/s, Strength 49 WPA2
    1820:            Infra, <MAC '1820' [AN17]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    felipebello:     Infra, <MAC 'felipebello' [AN18]>, Freq 2422 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    Clau:            Infra, <MAC 'Clau' [AN19]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 32 WPA2
    HUAC R2:         Infra, <MAC 'HUAC R2' [AN20]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 30 WPA2
    CEPCON2014:      Infra, <MAC 'CEPCON2014' [AN21]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    LSandoval:       Infra, <MAC 'LSandoval' [AN22]>, Freq 2417 MHz, Rate 54 Mb/s, Strength 50 WPA WPA2
    ABRAHAM:         Infra, <MAC 'ABRAHAM' [AN23]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 50 WPA WPA2
    Felipe:          Infra, <MAC 'Felipe' [AN24]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 37 WPA WPA2
    Nora Au Diaz:    Infra, <MAC 'Nora Au Diaz' [AN25]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    Warifaiflai:     Infra, <MAC 'Warifaiflai' [AN26]>, Freq 2457 MHz, Rate 54 Mb/s, Strength 30 WPA
    depto 1806:      Infra, <MAC 'depto 1806' [AN27]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 29 WPA
    Nonos:           Infra, <MAC 'Nonos' [AN28]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 25 WPA2
    VALE:            Infra, <MAC 'VALE' [AN29]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    gaby:            Infra, <MAC 'gaby' [AN30]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    MRM.1:           Infra, <MAC 'MRM.1' [AN31]>, Freq 2447 MHz, Rate 54 Mb/s, Strength 27 WPA
    Ricardo:         Infra, <MAC 'Ricardo' [AN32]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 34 WPA
    Javiera_Mozo:    Infra, <MAC 'Javiera_Mozo' [AN33]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 39 WPA WPA2
    Belen:           Infra, <MAC 'Belen' [AN34]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 35 WPA WPA2
    valeska:         Infra, <MAC 'valeska' [AN35]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    JOSE LUIS PAREDES: Infra, <MAC 'JOSE LUIS PAREDES' [AN36]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 37 WPA WPA2
    VILLAGRA_2309:   Infra, <MAC 'VILLAGRA_2309' [AN37]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2
    Telsur_FMacaya:  Infra, <MAC 'Telsur_FMacaya' [AN38]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    Max:             Infra, <MAC 'Max' [AN39]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    Wifitelsur_Cami: Infra, <MAC 'Wifitelsur_Cami' [AN40]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2
    Carolina:        Infra, <MAC 'Carolina' [AN41]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2
    Telsur_JVB:      Infra, <MAC 'Telsur_JVB' [AN42]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 35 WEP
    Clinica Red 182: Infra, <MAC 'Clinica Red 182' [AN43]>, Freq 2422 MHz, Rate 11 Mb/s, Strength 37 WEP
    CL-CCPVPN001:    Infra, <MAC 'CL-CCPVPN001' [AN44]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 30
    Bastian:         Infra, <MAC 'Bastian' [AN45]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 55 WPA WPA2
    Carolina:        Infra, <MAC 'Carolina' [AN46]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    wifitelsur_LAIS: Infra, <MAC 'wifitelsur_LAIS' [AN47]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2
    Osvaldo:         Infra, <MAC 'Osvaldo' [AN48]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    francisca_v:     Infra, <MAC 'francisca_v' [AN49]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 34 WPA
    CL-CCPWLC001:    Infra, <MAC 'CL-CCPWLC001' [AN50]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 45 WEP
    Officetest:      Infra, <MAC 'Officetest' [AN51]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 34 WPA2 Enterprise
    Wifitelsur_Medina: Infra, <MAC 'Wifitelsur_Medina' [AN52]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 40 WPA
    parserconfig:    Infra, <MAC 'parserconfig' [AN53]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    Meds:            Infra, <MAC 'Meds' [AN54]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2
    PITRA:           Infra, <MAC 'PITRA' [AN55]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 37 WPA
    THE JUNGLE:      Infra, <MAC 'THE JUNGLE' [AN56]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 27 WPA
    WORKINGHOUSE:    Infra, <MAC 'WORKINGHOUSE' [AN57]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 27 WPA2
    bornita:         Infra, <MAC 'bornita' [AN58]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 24 WPA
    benjamin:        Infra, <MAC 'benjamin' [AN59]>, Freq 2422 MHz, Rate 54 Mb/s, Strength 20 WPA2
    Officetest:      Infra, <MAC 'Officetest' [AN60]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 37 WPA2 Enterprise
     _Contanza_ 1:   Infra, <MAC '_Contanza_ 1' [AN61]>, Freq 2447 MHz, Rate 54 Mb/s, Strength 30 WPA2
    wifitelsur_JARAGALINDO: Infra, <MAC 'wifitelsur_JARAGALINDO' [AN62]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    Paola Paz  :     Infra, <MAC 'Paola Paz  ' [AN63]>, Freq 2422 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    Martina:         Infra, <MAC 'Martina' [AN64]>, Freq 2422 MHz, Rate 54 Mb/s, Strength 27 WPA
    Caracol:         Infra, <MAC 'Caracol' [AN65]>, Freq 2422 MHz, Rate 54 Mb/s, Strength 34 WPA
    WifiTelsur_COPITO: Infra, <MAC 'WifiTelsur_COPITO' [AN66]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 27 WPA
    movistar_wifi2:  Infra, <MAC 'movistar_wifi2' [AN67]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 27 WPA2
    HP-Print-07-Deskjet 3520 series: Infra, <MAC 'HP-Print-07-Deskjet 3520 series' [AN68]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 35
    depto 505:       Infra, <MAC 'depto 505' [AN69]>, Freq 2447 MHz, Rate 54 Mb/s, Strength 24 WPA
    CL-CCPWLC001:    Infra, <MAC 'CL-CCPWLC001' [AN70]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 34 WEP
    any:             Infra, <MAC 'any' [AN71]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2
    Telsur_0002712150BD: Infra, <MAC 'Telsur_0002712150BD' [AN72]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 25 WEP
    HFM:             Infra, <MAC 'HFM' [AN73]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    aeurus-M:        Infra, <MAC 'aeurus-M' [AN74]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 27 WPA2
    man:             Infra, <MAC 'man' [AN75]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 29 WEP
    gvanes:          Infra, <MAC 'gvanes' [AN76]>, Freq 2427 MHz, Rate 54 Mb/s, Strength 24 WPA
    NeuroManagement: Infra, <MAC 'NeuroManagement' [AN77]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 34 WPA2
    sudarshan:       Infra, <MAC 'sudarshan' [AN78]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 50 WPA WPA2

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

[[/etc/NetworkManager/system-connections/Deptopro 905]] (600 root)
[connection] id=Deptopro 905 | type=802-11-wireless
[802-11-wireless] ssid=Deptopro 905 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/SpeedTouch2912FA]] (600 root)
[connection] id=SpeedTouch2912FA | type=802-11-wireless
[802-11-wireless] ssid=SpeedTouch2912FA | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Windsor_Eventos]] (600 root)
[connection] id=Windsor_Eventos | type=802-11-wireless
[802-11-wireless] ssid=Windsor_Eventos | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/HP-Print-7A-LaserJet 1102]] (600 root)
[connection] id=HP-Print-7A-LaserJet 1102 | type=802-11-wireless
[802-11-wireless] ssid=HP-Print-7A-LaserJet 1102 | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/CI2MA-1]] (600 root)
[connection] id=CI2MA-1 | type=802-11-wireless
[802-11-wireless] ssid=CI2MA-1 | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Movistar-Vex]] (600 root)
[connection] id=Movistar-Vex | type=802-11-wireless
[802-11-wireless] ssid=Movistar-Vex | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/ANNIVERSARY]] (600 root)
[connection] id=ANNIVERSARY | type=802-11-wireless
[802-11-wireless] ssid=ANNIVERSARY | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/GRU WIFI]] (600 root)
[connection] id=GRU WIFI | type=802-11-wireless
[802-11-wireless] ssid=GRU WIFI | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/AndroidAP]] (600 root)
[connection] id=AndroidAP | type=802-11-wireless
[802-11-wireless] ssid=AndroidAP | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/CI2MA-1 1]] (600 root)
[connection] id=CI2MA-1 1 | type=802-11-wireless
[802-11-wireless] ssid=CI2MA-1 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Lili 1]] (600 root)
[connection] id=Lili 1 | type=802-11-wireless
[802-11-wireless] ssid=Lili | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/geodoc]] (600 root)
[connection] id=geodoc | type=802-11-wireless
[802-11-wireless] ssid=geodoc | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/MARIA 1]] (600 root)
[connection] id=MARIA 1 | type=802-11-wireless
[802-11-wireless] ssid=MARIA 1 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Rocca Piso 1]] (600 root)
[connection] id=Rocca Piso 1 | type=802-11-wireless
[802-11-wireless] ssid=Rocca Piso 1 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Depto 1907]] (600 root)
[connection] id=Depto 1907 | type=802-11-wireless
[802-11-wireless] ssid=Depto 1907 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/sudarshan]] (600 root)
[connection] id=sudarshan | type=802-11-wireless
[802-11-wireless] ssid=sudarshan | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Rocca Piso 3*1]] (600 root)
[connection] id=Rocca Piso 1 | type=802-11-wireless
[802-11-wireless] ssid=Rocca Piso 1 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/ThomsonAEE16E]] (600 root)
[connection] id=ThomsonAEE16E | type=802-11-wireless
[802-11-wireless] ssid=ThomsonAEE16E | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Lili]] (600 root)
[connection] id=Lili | type=802-11-wireless | permissions=user:guest-p5sivE:;
[802-11-wireless] ssid=Lili | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/CI2MA-2]] (600 root)
[connection] id=CI2MA-2 | type=802-11-wireless
[802-11-wireless] ssid=CI2MA-2 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/CI2MA]] (600 root)
[connection] id=CI2MA | type=802-11-wireless
[802-11-wireless] ssid=CI2MA | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/impa-nwl]] (600 root)
[connection] id=impa-nwl | type=802-11-wireless
[802-11-wireless] ssid=impa-nwl | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/CARAPEBUS]] (600 root)
[connection] id=CARAPEBUS | type=802-11-wireless
[802-11-wireless] ssid=CARAPEBUS | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/ibis Copacabana]] (600 root)
[connection] id=ibis Copacabana | type=802-11-wireless
[802-11-wireless] ssid=ibis Copacabana | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Windsor Plaza Hospedes]] (600 root)
[connection] id=Windsor Plaza Hospedes | type=802-11-wireless
[802-11-wireless] ssid=Windsor Plaza Hospedes | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/TNCAPE4F635]] (600 root)
[connection] id=TNCAPE4F635 | type=802-11-wireless
[802-11-wireless] ssid=TNCAPE4F635 | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/LATLA]] (600 root)
[connection] id=LATLA | type=802-11-wireless
[802-11-wireless] ssid=LATLA | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/CL-CCPVPN001]] (600 root)
[connection] id=CL-CCPVPN001 | type=802-11-wireless
[802-11-wireless] ssid=CL-CCPVPN001 | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Sala de Computacion]] (600 root)
[connection] id=Sala de Computacion | type=802-11-wireless
[802-11-wireless] ssid=Sala de Computacion | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Hotel Castillo]] (600 root)
[connection] id=Hotel Castillo | type=802-11-wireless
[802-11-wireless] ssid=Hotel Castillo | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Catalunya]] (600 root)
[connection] id=Catalunya | type=802-11-wireless
[802-11-wireless] ssid=Catalunya | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: America/Santiago (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

wlan0     32 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 104 : 5.52 GHz
          Channel 108 : 5.54 GHz
          Channel 112 : 5.56 GHz
          Channel 116 : 5.58 GHz
          Channel 120 : 5.6 GHz
          Channel 124 : 5.62 GHz
          Channel 128 : 5.64 GHz
          Channel 132 : 5.66 GHz
          Channel 136 : 5.68 GHz
          Channel 140 : 5.7 GHz

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Failed to read scan data : Resource temporarily unavailable

##### module infos ######################

[iwldvm]
filename:       /lib/modules/3.13.0-41-generic/kernel/drivers/net/wireless/iwlwifi/dvm/iwldvm.ko
license:        GPL
author:         Copyright(c) 2003-2013 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi Link AGN driver for Linux
srcversion:     9ABCB275EC05F363D958754
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-41-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        B8:04:A2:24:C5:07:BF:33:9F:38:2F:81:73:AA:07:C2:0D:99:D0:6B
sig_hashalgo:   sha512

[iwlwifi]
filename:       /lib/modules/3.13.0-41-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
license:        GPL
author:         Copyright(c) 2003-2013 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi driver for Linux
firmware:       iwlwifi-100-5.ucode
firmware:       iwlwifi-1000-5.ucode
firmware:       iwlwifi-135-6.ucode
firmware:       iwlwifi-105-6.ucode
firmware:       iwlwifi-2030-6.ucode
firmware:       iwlwifi-2000-6.ucode
firmware:       iwlwifi-5150-2.ucode
firmware:       iwlwifi-5000-5.ucode
firmware:       iwlwifi-6000g2b-6.ucode
firmware:       iwlwifi-6000g2a-5.ucode
firmware:       iwlwifi-6050-5.ucode
firmware:       iwlwifi-6000-4.ucode
firmware:       iwlwifi-7265-7.ucode
firmware:       iwlwifi-3160-7.ucode
firmware:       iwlwifi-7260-7.ucode
srcversion:     72E4ECE7C2CBAA62E552DCE
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-41-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        B8:04:A2:24:C5:07:BF:33:9F:38:2F:81:73:AA:07:C2:0D:99:D0:6B
sig_hashalgo:   sha512
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (defualt: 0 dB) (int)
parm:           wd_disable:Disable stuck queue watchdog timer 0=system default, 1=disable, 2=enable (default: 0) (int)
parm:           nvm_file:NVM file name (charp)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)

[b43]
filename:       /lib/modules/3.13.0-41-generic/kernel/drivers/net/wireless/b43/b43.ko
firmware:       b43/ucode9.fw
firmware:       b43/ucode5.fw
firmware:       b43/ucode16_mimo.fw
firmware:       b43/ucode15.fw
firmware:       b43/ucode14.fw
firmware:       b43/ucode13.fw
firmware:       b43/ucode11.fw
license:        GPL
author:         RafaÅ&#130; MiÅ&#130;ecki
author:         GÃ¡bor Stefanik
author:         Michael Buesch
author:         Stefano Brivio
author:         Martin Langer
description:    Broadcom B43 wireless driver
srcversion:     7ABBDDCA84C087640B27AE6
depends:        bcma,ssb,mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-41-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        B8:04:A2:24:C5:07:BF:33:9F:38:2F:81:73:AA:07:C2:0D:99:D0:6B
sig_hashalgo:   sha512
parm:           bad_frames_preempt:enable(1) / disable(0) Bad Frames Preemption (int)
parm:           fwpostfix:Postfix for the .fw files to load. (string)
parm:           hwpctl:Enable hardware-side power control (default off) (int)
parm:           nohwcrypt:Disable hardware encryption. (int)
parm:           hwtkip:Enable hardware tkip. (int)
parm:           qos:Enable QOS support (default on) (int)
parm:           btcoex:Enable Bluetooth coexistence (default on) (int)
parm:           verbose:Log message verbosity: 0=error, 1=warn, 2=info(default), 3=debug (int)
parm:           pio:Use PIO accesses by default: 0=DMA, 1=PIO (int)
parm:           allhwsupport:Enable support for all hardware (even it if overlaps with the brcmsmac driver) (int)

[bcma]
filename:       /lib/modules/3.13.0-41-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     E41B811D88783DD5BC38565
depends:        
intree:         Y
vermagic:       3.13.0-41-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        B8:04:A2:24:C5:07:BF:33:9F:38:2F:81:73:AA:07:C2:0D:99:D0:6B
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.13.0-41-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     446B3604A9C5461044DD691
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-41-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        B8:04:A2:24:C5:07:BF:33:9F:38:2F:81:73:AA:07:C2:0D:99:D0:6B
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-41-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     C2478077E22138832B71659
depends:        
intree:         Y
vermagic:       3.13.0-41-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        B8:04:A2:24:C5:07:BF:33:9F:38:2F:81:73:AA:07:C2:0D:99:D0:6B
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[ssb]
filename:       /lib/modules/3.13.0-41-generic/kernel/drivers/ssb/ssb.ko
license:        GPL
description:    Sonics Silicon Backplane driver
srcversion:     3DE188310F77C566C2E8CB3
depends:        
intree:         Y
vermagic:       3.13.0-41-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        B8:04:A2:24:C5:07:BF:33:9F:38:2F:81:73:AA:07:C2:0D:99:D0:6B
sig_hashalgo:   sha512

##### module parameters #################

[iwlwifi]
11n_disable: 1
amsdu_size_8K: 0
antenna_coupling: 0
bt_coex_active: Y
fw_restart: Y
led_mode: 0
nvm_file: (null)
power_level: 0
power_save: N
swcrypto: 0
wd_disable: 1

[b43]
allhwsupport: 0
bad_frames_preempt: 0
btcoex: 1
hwpctl: 0
hwtkip: 0
nohwcrypt: 0
pio: 0
qos: 1
verbose: 2

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
probe_wait_ms: 500

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

lp
rtc
b43

##### modprobe options ##################

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac

[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off

[/etc/modprobe.d/iwlwifi.conf]
options iwlwifi 11n_disable=1

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

exit 0

##### pm-utils ##########################

[/etc/pm/power.d/wireless] (755 root)
/sbin/iwconfig wlan0 power off

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x14e4:0x1698 (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x8086:0x4232 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[   64.576026] wlan0: direct probe to <MAC 'NeuroManagement' [AN77]> (try 3/3)
[   64.780045] wlan0: authentication with <MAC 'NeuroManagement' [AN77]> timed out
[   92.045567] wlan0: authenticate with <MAC 'NeuroManagement' [AN77]>
[   92.046615] wlan0: direct probe to <MAC 'NeuroManagement' [AN77]> (try 1/3)
[   92.248048] wlan0: direct probe to <MAC 'NeuroManagement' [AN77]> (try 2/3)
[   92.452036] wlan0: direct probe to <MAC 'NeuroManagement' [AN77]> (try 3/3)
[   92.656033] wlan0: authentication with <MAC 'NeuroManagement' [AN77]> timed out
[  124.279275] wlan0: authenticate with <MAC 'sudarshan' [AN78]>
[  124.291551] wlan0: direct probe to <MAC 'sudarshan' [AN78]> (try 1/3)
[  124.492059] wlan0: direct probe to <MAC 'sudarshan' [AN78]> (try 2/3)
[  124.696251] wlan0: direct probe to <MAC 'sudarshan' [AN78]> (try 3/3)
[  124.900072] wlan0: authentication with <MAC 'sudarshan' [AN78]> timed out
[  138.163072] wlan0: authenticate with <MAC 'sudarshan' [AN78]>
[  138.164286] wlan0: direct probe to <MAC 'sudarshan' [AN78]> (try 1/3)
[  138.368238] wlan0: direct probe to <MAC 'sudarshan' [AN78]> (try 2/3)
[  138.572244] wlan0: direct probe to <MAC 'sudarshan' [AN78]> (try 3/3)
[  138.776059] wlan0: authentication with <MAC 'sudarshan' [AN78]> timed out
[  161.586045] wlan0: authenticate with <MAC 'sudarshan' [AN78]>
[  161.596814] wlan0: direct probe to <MAC 'sudarshan' [AN78]> (try 1/3)
[  161.800108] wlan0: direct probe to <MAC 'sudarshan' [AN78]> (try 2/3)
[  162.004090] wlan0: direct probe to <MAC 'sudarshan' [AN78]> (try 3/3)
[  162.208167] wlan0: authentication with <MAC 'sudarshan' [AN78]> timed out

########## wireless info END ############



```

---

### Post by skkmaths on 2014-12-04
Please see the above wifiscript.

---

### Post by jeremy31 on 2014-12-05
One thing to try before a reboot, in terminal ```
gksudo gedit /etc/modprobe.d/iwlwifi.conf
```
delete what is there and paste the following```
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211
options iwlwifi 11n_disable=8
```
save, exit program, reboot computer

Disabling(ignore) IPv6 in network manager for your connection may help
If you have access to the router security settings, changing encryption to WPA2-AES only works better than a WPA/WPA2 mixed mode.  See if you get disconnected with the ethernet cable unplugged.  If you still have issues after a reboot run the wireless script again and post the new results, you should only need to run this now```
./wireless_script
```

---

### Post by skkmaths on 2014-12-05
I have done  as you have suggested, but still after the reboot wifi could not connect. Please see the wifiscript after the reboot.
```

########## wireless info START ##########

Report from: 05 Dec 2014 11:20 CLST -0300

Booted last: 05 Dec 2014 11:15 CLST -0300

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.13.0-41-generic #70-Ubuntu SMP Tue Nov 25 14:40:34 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

04:00.0 Network controller [0280]: Intel Corporation WiFi Link 5100 [8086:4232]
    Subsystem: Intel Corporation WiFi Link 5100 AGN [8086:1321]
    Kernel driver in use: iwlwifi

08:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe [14e4:1698] (rev 10)
    Subsystem: Dell Device [1028:02be]
    Kernel driver in use: tg3

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 002: ID 046d:c03d Logitech, Inc. M-BT96a Pilot Optical Mouse
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0c45:63ea Microdia 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 005: ID 413c:8156 Dell Computer Corp. Wireless 370 Bluetooth Mini-card
Bus 003 Device 004: ID 413c:8158 Dell Computer Corp. Integrated Touchpad / Trackstick
Bus 003 Device 003: ID 413c:8157 Dell Computer Corp. Integrated Keyboard
Bus 003 Device 002: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

dell_wmi               12761  0 
sparse_keymap          13948  1 dell_wmi
dell_laptop            18168  0 
dcdbas                 14928  1 dell_laptop
iwldvm                232285  0 
iwlwifi               169932  1 iwldvm
wmi                    19177  1 dell_wmi
b43                   387371  0 
bcma                   52096  1 b43
mac80211              630653  2 b43,iwldvm
cfg80211              484040  4 b43,iwlwifi,mac80211,iwldvm
ssb                    62379  1 b43

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:152.74.35.143  Bcast:152.74.35.255  Mask:255.255.255.0
          inet6 addr: fe80::222:19ff:fefc:7416/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1520 errors:0 dropped:0 overruns:0 frame:0
          TX packets:869 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:334626 (334.6 KB)  TX bytes:114351 (114.3 KB)
          Interrupt:17 

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         152.74.35.1     0.0.0.0         UG    0      0        0 eth0
152.74.35.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1
search ci2ma.udec.cl

##### nm-tool ###########################

** (process:2789): WARNING **: error: cannot retrieve connection: uid 1000 has no permission to perform this operation

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         152.74.35.143
    Prefix:          24 (255.255.255.0)
    Gateway:         152.74.35.1

    DNS:             152.74.35.2
    DNS:             152.74.16.14
    DNS:             152.74.217.2
    DNS:             152.74.50.10
    DNS:             8.8.8.8
    DNS:             4.4.4.4

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             disconnected
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    geodoc:          Infra, <MAC 'geodoc' [AN1]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2
    Oscar wifi:      Infra, <MAC 'Oscar wifi' [AN2]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2
    geodoc-invitado: Infra, <MAC 'geodoc-invitado' [AN3]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 44
    CI2MA:           Infra, <MAC 'CI2MA' [AN4]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2
    linksys:         Infra, <MAC 'linksys' [AN5]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 22 WEP
    Postgrado Oceanografia: Infra, <MAC 'Postgrado Oceanografia' [AN6]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 22 WPA
    CI2MA-2:         Infra, <MAC 'CI2MA-2' [AN7]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 24 WPA
    HP-Print-7A-LaserJet 1102: Infra, <MAC 'HP-Print-7A-LaserJet 1102' [AN8]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 22
    Jacqueline Ojeda's iMac: Infra, <MAC 'Jacqueline Ojeda's iMac' [AN9]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 20 WEP
    MikroTik:        Infra, <MAC 'MikroTik' [AN10]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 29 WPA2
    La Anaconda que te vuelve loca: Infra, <MAC 'La Anaconda que te vuelve loca' [AC1]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2
    R COHN:          Infra, <MAC 'R COHN' [AN12]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2
    HotMattSpot:     Ad-Hoc, <MAC 'HotMattSpot' [AN13]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 22 WEP
    DEE:             Infra, <MAC 'DEE' [AN14]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2
    CI2MA-1:         Infra, <MAC 'CI2MA-1' [AN15]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA

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

[[/etc/NetworkManager/system-connections/CI2MA-1]] (600 root)
[connection] id=CI2MA-1 | type=802-11-wireless
[802-11-wireless] ssid=CI2MA-1 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/AndroidAP]] (600 root)
[connection] id=AndroidAP | type=802-11-wireless
[802-11-wireless] ssid=AndroidAP | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Cochrane]] (600 root)
[connection] id=Cochrane | type=802-11-wireless
[802-11-wireless] ssid=Cochrane | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/sudarshan]] (600 root)
[connection] id=sudarshan | type=802-11-wireless
[802-11-wireless] ssid=sudarshan | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=shared
[ipv6] method=ignore

[[/etc/NetworkManager/system-connections/Lili]] (600 root)
[connection] id=Lili | type=802-11-wireless | permissions=user:guest-p5sivE:;
[802-11-wireless] ssid=Lili | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: America/Santiago (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

wlan0     32 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 104 : 5.52 GHz
          Channel 108 : 5.54 GHz
          Channel 112 : 5.56 GHz
          Channel 116 : 5.58 GHz
          Channel 120 : 5.6 GHz
          Channel 124 : 5.62 GHz
          Channel 128 : 5.64 GHz
          Channel 132 : 5.66 GHz
          Channel 136 : 5.68 GHz
          Channel 140 : 5.7 GHz

##### iwlist scan #######################

Channel occupancy:

      1   APs on   Frequency:2.437 GHz (Channel 6)

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'La Anaconda que te vuelve loca' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"La Anaconda que te vuelve loca"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000018ba1d7922f
                    Extra: Last beacon: 6280ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

##### module infos ######################

[iwldvm]
filename:       /lib/modules/3.13.0-41-generic/kernel/drivers/net/wireless/iwlwifi/dvm/iwldvm.ko
license:        GPL
author:         Copyright(c) 2003-2013 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi Link AGN driver for Linux
srcversion:     9ABCB275EC05F363D958754
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-41-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        B8:04:A2:24:C5:07:BF:33:9F:38:2F:81:73:AA:07:C2:0D:99:D0:6B
sig_hashalgo:   sha512

[iwlwifi]
filename:       /lib/modules/3.13.0-41-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
license:        GPL
author:         Copyright(c) 2003-2013 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi driver for Linux
firmware:       iwlwifi-100-5.ucode
firmware:       iwlwifi-1000-5.ucode
firmware:       iwlwifi-135-6.ucode
firmware:       iwlwifi-105-6.ucode
firmware:       iwlwifi-2030-6.ucode
firmware:       iwlwifi-2000-6.ucode
firmware:       iwlwifi-5150-2.ucode
firmware:       iwlwifi-5000-5.ucode
firmware:       iwlwifi-6000g2b-6.ucode
firmware:       iwlwifi-6000g2a-5.ucode
firmware:       iwlwifi-6050-5.ucode
firmware:       iwlwifi-6000-4.ucode
firmware:       iwlwifi-7265-7.ucode
firmware:       iwlwifi-3160-7.ucode
firmware:       iwlwifi-7260-7.ucode
srcversion:     72E4ECE7C2CBAA62E552DCE
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-41-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        B8:04:A2:24:C5:07:BF:33:9F:38:2F:81:73:AA:07:C2:0D:99:D0:6B
sig_hashalgo:   sha512
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (defualt: 0 dB) (int)
parm:           wd_disable:Disable stuck queue watchdog timer 0=system default, 1=disable, 2=enable (default: 0) (int)
parm:           nvm_file:NVM file name (charp)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)

[b43]
filename:       /lib/modules/3.13.0-41-generic/kernel/drivers/net/wireless/b43/b43.ko
firmware:       b43/ucode9.fw
firmware:       b43/ucode5.fw
firmware:       b43/ucode16_mimo.fw
firmware:       b43/ucode15.fw
firmware:       b43/ucode14.fw
firmware:       b43/ucode13.fw
firmware:       b43/ucode11.fw
license:        GPL
author:         Rafa&#322; Mi&#322;ecki
author:         Gábor Stefanik
author:         Michael Buesch
author:         Stefano Brivio
author:         Martin Langer
description:    Broadcom B43 wireless driver
srcversion:     7ABBDDCA84C087640B27AE6
depends:        bcma,ssb,mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-41-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        B8:04:A2:24:C5:07:BF:33:9F:38:2F:81:73:AA:07:C2:0D:99:D0:6B
sig_hashalgo:   sha512
parm:           bad_frames_preempt:enable(1) / disable(0) Bad Frames Preemption (int)
parm:           fwpostfix:Postfix for the .fw files to load. (string)
parm:           hwpctl:Enable hardware-side power control (default off) (int)
parm:           nohwcrypt:Disable hardware encryption. (int)
parm:           hwtkip:Enable hardware tkip. (int)
parm:           qos:Enable QOS support (default on) (int)
parm:           btcoex:Enable Bluetooth coexistence (default on) (int)
parm:           verbose:Log message verbosity: 0=error, 1=warn, 2=info(default), 3=debug (int)
parm:           pio:Use PIO accesses by default: 0=DMA, 1=PIO (int)
parm:           allhwsupport:Enable support for all hardware (even it if overlaps with the brcmsmac driver) (int)

[bcma]
filename:       /lib/modules/3.13.0-41-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     E41B811D88783DD5BC38565
depends:        
intree:         Y
vermagic:       3.13.0-41-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        B8:04:A2:24:C5:07:BF:33:9F:38:2F:81:73:AA:07:C2:0D:99:D0:6B
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.13.0-41-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     446B3604A9C5461044DD691
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-41-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        B8:04:A2:24:C5:07:BF:33:9F:38:2F:81:73:AA:07:C2:0D:99:D0:6B
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-41-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     C2478077E22138832B71659
depends:        
intree:         Y
vermagic:       3.13.0-41-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        B8:04:A2:24:C5:07:BF:33:9F:38:2F:81:73:AA:07:C2:0D:99:D0:6B
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[ssb]
filename:       /lib/modules/3.13.0-41-generic/kernel/drivers/ssb/ssb.ko
license:        GPL
description:    Sonics Silicon Backplane driver
srcversion:     3DE188310F77C566C2E8CB3
depends:        
intree:         Y
vermagic:       3.13.0-41-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        B8:04:A2:24:C5:07:BF:33:9F:38:2F:81:73:AA:07:C2:0D:99:D0:6B
sig_hashalgo:   sha512

##### module parameters #################

[iwlwifi]
11n_disable: 8
amsdu_size_8K: 0
antenna_coupling: 0
bt_coex_active: Y
fw_restart: Y
led_mode: 0
nvm_file: (null)
power_level: 0
power_save: N
swcrypto: 0
wd_disable: 1

[b43]
allhwsupport: 0
bad_frames_preempt: 0
btcoex: 1
hwpctl: 0
hwtkip: 0
nohwcrypt: 0
pio: 0
qos: 1
verbose: 2

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
probe_wait_ms: 500

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

lp
rtc
b43

##### modprobe options ##################

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac

[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211
options iwlwifi 11n_disable=8

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

exit 0

##### pm-utils ##########################

[/etc/pm/power.d/wireless] (755 root)
/sbin/iwconfig wlan0 power off

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x14e4:0x1698 (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x8086:0x4232 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[  110.524061] wlan0: direct probe to <MAC 'CI2MA-1' [AN15]> (try 2/3)
[  110.728046] wlan0: direct probe to <MAC 'CI2MA-1' [AN15]> (try 3/3)
[  110.932048] wlan0: authentication with <MAC 'CI2MA-1' [AN15]> timed out
[  121.688090] wlan0: authenticate with <MAC 'CI2MA-1' [AN15]>
[  121.689565] wlan0: direct probe to <MAC 'CI2MA-1' [AN15]> (try 1/3)
[  121.892059] wlan0: direct probe to <MAC 'CI2MA-1' [AN15]> (try 2/3)
[  122.096057] wlan0: direct probe to <MAC 'CI2MA-1' [AN15]> (try 3/3)
[  122.300051] wlan0: authentication with <MAC 'CI2MA-1' [AN15]> timed out
[  169.621495] wlan0: authenticate with <MAC 'CI2MA-1' [AN15]>
[  169.624365] wlan0: direct probe to <MAC 'CI2MA-1' [AN15]> (try 1/3)
[  169.828185] wlan0: direct probe to <MAC 'CI2MA-1' [AN15]> (try 2/3)
[  170.032052] wlan0: direct probe to <MAC 'CI2MA-1' [AN15]> (try 3/3)
[  170.236057] wlan0: authentication with <MAC 'CI2MA-1' [AN15]> timed out
[  213.152598] wlan0: authenticate with <MAC 'CI2MA-1' [AN15]>
[  213.153707] wlan0: direct probe to <MAC 'CI2MA-1' [AN15]> (try 1/3)
[  213.356239] wlan0: direct probe to <MAC 'CI2MA-1' [AN15]> (try 2/3)
[  213.560038] wlan0: direct probe to <MAC 'CI2MA-1' [AN15]> (try 3/3)
[  213.764081] wlan0: authentication with <MAC 'CI2MA-1' [AN15]> timed out
[  235.129184] wlan0: authenticate with <MAC 'CI2MA-1' [AN15]>
[  235.132255] wlan0: direct probe to <MAC 'CI2MA-1' [AN15]> (try 1/3)
[  235.336071] wlan0: direct probe to <MAC 'CI2MA-1' [AN15]> (try 2/3)
[  235.540079] wlan0: direct probe to <MAC 'CI2MA-1' [AN15]> (try 3/3)
[  235.744046] wlan0: authentication with <MAC 'CI2MA-1' [AN15]> timed out
[  298.201464] wlan0: authenticate with <MAC 'CI2MA-1' [AN15]>
[  298.207658] wlan0: direct probe to <MAC 'CI2MA-1' [AN15]> (try 1/3)
[  298.408110] wlan0: direct probe to <MAC 'CI2MA-1' [AN15]> (try 2/3)
[  298.612064] wlan0: direct probe to <MAC 'CI2MA-1' [AN15]> (try 3/3)
[  298.816046] wlan0: authentication with <MAC 'CI2MA-1' [AN15]> timed out
[  312.018767] wlan0: authenticate with <MAC 'CI2MA-1' [AN15]>
[  312.020103] wlan0: direct probe to <MAC 'CI2MA-1' [AN15]> (try 1/3)
[  312.224081] wlan0: direct probe to <MAC 'CI2MA-1' [AN15]> (try 2/3)
[  312.428277] wlan0: direct probe to <MAC 'CI2MA-1' [AN15]> (try 3/3)
[  312.632051] wlan0: authentication with <MAC 'CI2MA-1' [AN15]> timed out

########## wireless info END ############


```

---

### Post by jeremy31 on 2014-12-05
Missed one thing ```
gksudo gedit /etc/modules
``` delete b43, then save and exit ```
sudo modprobe -r b43 && sudo modprobe -r ssb
```
for some reason the dmesg part of the info isn't showing firmware getting loaded for the wifi, show the results from ```
dmesg | grep iwl
```

And the one access point that is found is using mixed mode encryption, TKIP doesn't work the greatest with Linux```
 IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
```

---

### Post by skkmaths on 2014-12-05
I have done as you directed, please see the output of 
dmesg | grep iwl
```

[   21.967172] iwlwifi 0000:04:00.0: can't disable ASPM; OS doesn't have ASPM control
[   21.968720] iwlwifi 0000:04:00.0: irq 46 for MSI/MSI-X
[   22.483934] iwlwifi 0000:04:00.0: loaded firmware version 8.83.5.1 build 33692 op_mode iwldvm
[   22.489880] iwlwifi 0000:04:00.0: CONFIG_IWLWIFI_DEBUG disabled
[   22.489884] iwlwifi 0000:04:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[   22.489886] iwlwifi 0000:04:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[   22.489888] iwlwifi 0000:04:00.0: Detected Intel(R) WiFi Link 5100 AGN, REV=0x54
[   22.489947] iwlwifi 0000:04:00.0: L1 Enabled - LTR Disabled
[   22.516465] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   28.058210] iwlwifi 0000:04:00.0: L1 Enabled - LTR Disabled
[   28.061224] iwlwifi 0000:04:00.0: Radio type=0x1-0x2-0x0
[   28.159178] iwlwifi 0000:04:00.0: L1 Enabled - LTR Disabled
[   28.162187] iwlwifi 0000:04:00.0: Radio type=0x1-0x2-0x0
sudarshan@sudarshan-Studio-1555:~$ 



```

---

### Post by jeremy31 on 2014-12-05
That looks good, can you connect after unplugging ethernet?

---

