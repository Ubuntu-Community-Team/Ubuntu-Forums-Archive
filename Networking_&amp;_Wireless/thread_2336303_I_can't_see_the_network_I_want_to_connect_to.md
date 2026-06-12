---
title: "I can't see the network I want to connect to"
date: 2016-09-06
forum: Networking &amp; Wireless
---

### Post by UltimatePredator on 2016-09-06
Hi all, I've had issues with my wireless before (as you can see from my previous thread). Anyways since travelling around I've been connecting to various wireless networks, but the other day the connection to the wireless network I've been using seemed to stop working (kept trying to connect but then ultimately would say disconnected). 

I deleted it and the other histories of network connections, and also reset my bios to default settings, and upon reboot it simply can't see the wireless network I'm trying to connect to, despite other networks showing in the area. I know it exists as my girlfriend is connected to it on her windows laptop! I also tried connecting to the network with puppy linux and even a xubuntu disc but the same problem arises, so I think this is a linux issue rather than a system issue? Anyway, here is the output form the wireless info script (I copied and pasted via usb), hope it helps;

```

 
 
  ########## wireless info START ##########
  
 
  Report from: 07 Sep 2016 14:50 NZST +1200
  
 
  Booted last: 07 Sep 2016 00:00 NZST +1200
  
 
  Script from: 08 Jul 2016 02:16 UTC +0000
  
 
  ##### release ###########################
  
 
  Distributor ID:    Ubuntu
  Description:    Ubuntu 16.04.1 LTS
  Release:    16.04
  Codename:    xenial
  
 
  ##### kernel ############################
  
 
  Linux 4.4.0-31-generic #50-Ubuntu SMP Wed Jul 13 00:06:14 UTC 2016 i686 i686 i686 GNU/Linux
  
 
  Parameters: ro, quiet, splash, vt.handoff=7
  
 
  ##### desktop ###########################
  
 
  Lubuntu
  
 
  ##### lspci #############################
  
 
  02:04.0 Network controller [0280]: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection [8086:4220] (rev 05)
      Subsystem: Hewlett-Packard Company nc6120/nx8220/nw8240 [103c:12f6]
      Kernel driver in use: ipw2200
  
 
  10:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5751M Gigabit Ethernet PCI Express [14e4:167d] (rev 11)
      Subsystem: Hewlett-Packard Company NetXtreme BCM5751M Gigabit Ethernet PCI Express [103c:0944]
      Kernel driver in use: tg3
  
 
  ##### lsusb #############################
  
 
  Bus 001 Device 004: ID 05ac:12a8 Apple, Inc. iPhone5/5C/5S/6
  Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
  Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
  Bus 003 Device 003: ID 03f0:011d Hewlett-Packard Bluetooth 1.2 Interface [Broadcom BCM2035]
  Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
  Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
  
 
  ##### PCMCIA card info ##################
  
 
  'pccardctl' is not installed (package "pcmciautils").
  
 
  ##### rfkill ############################
  
 
  1: phy0: Wireless LAN
      Soft blocked: no
      Hard blocked: no
  2: hp-wifi: Wireless LAN
      Soft blocked: no
      Hard blocked: no
  3: hp-bluetooth: Bluetooth
      Soft blocked: no
      Hard blocked: no
  4: hp-gps: GPS
      Soft blocked: no
      Hard blocked: yes
  5: hci0: Bluetooth
      Soft blocked: no
      Hard blocked: no
  
 
  ##### lsmod #############################
  
 
  hp_wmi                 16384  0
  sparse_keymap          16384  1 hp_wmi
  ipw2200               143360  0
  libipw                 36864  1 ipw2200
  cfg80211              499712  2 libipw,ipw2200
  wmi                    20480  1 hp_wmi
  
 
  ##### interfaces ########################
  
 
  auto lo
  iface lo inet loopback
  
 
  ##### ifconfig ##########################
  
 
  enp16s0   Link encap:Ethernet  HWaddr <MAC 'enp16s0' [IF1]>   
            UP BROADCAST MULTICAST  MTU:1500  Metric:1
            RX packets:0 errors:0 dropped:0 overruns:0 frame:0
            TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:1000  
            RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
            Interrupt:16  
  
 
  wlp2s4    Link encap:Ethernet  HWaddr <MAC 'wlp2s4' [IF2]>   
            UP BROADCAST MULTICAST  MTU:1500  Metric:1
            RX packets:0 errors:0 dropped:0 overruns:0 frame:0
            TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:1000  
            RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
  
 
  ##### iwconfig ##########################
  
 
  enp16s0   no wireless extensions.
  
 
  lo        no wireless extensions.
  
 
  wlp2s4    IEEE 802.11bg  ESSID:off/any   
            Mode:Managed  Channel:0  Access Point: Not-Associated    
            Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0   
            Retry limit:7   RTS thr:off   Fragment thr:off
            Power Management:off
            Link Quality:0  Signal level:0  Noise level:0
            Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
            Tx excessive retries:0  Invalid misc:0   Missed beacon:0
  
 
  ##### route #############################
  
 
  Kernel IP routing table
  Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
  
 
  ##### resolv.conf #######################
  
 
  ##### network managers ##################
  
 
  Installed:
  
 
      NetworkManager
  
 
  Running:
  
 
  root      2154     1  0 14:34 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon
  
 
  ##### NetworkManager info ###############
  
 
  GENERAL.DEVICE:                         wlp2s4
  GENERAL.TYPE:                           wifi
  GENERAL.NM-TYPE:                        NMDeviceWifi
  GENERAL.VENDOR:                         Intel Corporation
  GENERAL.PRODUCT:                        PRO/Wireless 2200BG [Calexico2] Network Connection (nc6120/nx8220/nw8240)
  GENERAL.DRIVER:                         ipw2200
  GENERAL.DRIVER-VERSION:                 1.2.2kmprq
  GENERAL.FIRMWARE-VERSION:               ABG:9.0.5.27 (Dec 12 2007)
  GENERAL.HWADDR:                         <MAC 'wlp2s4' [IF2]>
  GENERAL.MTU:                            0
  GENERAL.STATE:                          30 (disconnected)
  GENERAL.REASON:                         42 (The supplicant is now available)
  GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1e.0/0000:02:04.0/net/wlp2s4
  GENERAL.IP-IFACE:                        
  GENERAL.IS-SOFTWARE:                    no
  GENERAL.NM-MANAGED:                     yes
  GENERAL.AUTOCONNECT:                    yes
  GENERAL.FIRMWARE-MISSING:               no
  GENERAL.NM-PLUGIN-MISSING:              no
  GENERAL.PHYS-PORT-ID:                   --
  GENERAL.CONNECTION:                     --
  GENERAL.CON-UUID:                       --
  GENERAL.CON-PATH:                       --
  GENERAL.METERED:                        unknown
  CAPABILITIES.CARRIER-DETECT:            no
  CAPABILITIES.SPEED:                     unknown
  CAPABILITIES.IS-SOFTWARE:               no
  WIFI-PROPERTIES.WEP:                    yes
  WIFI-PROPERTIES.WPA:                    yes
  WIFI-PROPERTIES.WPA2:                   yes
  WIFI-PROPERTIES.TKIP:                   yes
  WIFI-PROPERTIES.CCMP:                   yes
  WIFI-PROPERTIES.AP:                     no
  WIFI-PROPERTIES.ADHOC:                  yes
  WIFI-PROPERTIES.2GHZ:                   yes
  WIFI-PROPERTIES.5GHZ:                   no
  CONNECTIONS.AVAILABLE-CONNECTION-PATHS:  
  
 
  GENERAL.DEVICE:                         enp16s0
  GENERAL.TYPE:                           ethernet
  GENERAL.NM-TYPE:                        NMDeviceEthernet
  GENERAL.VENDOR:                         Broadcom Corporation
  GENERAL.PRODUCT:                        NetXtreme BCM5751M Gigabit Ethernet PCI Express
  GENERAL.DRIVER:                         tg3
  GENERAL.DRIVER-VERSION:                 3.137
  GENERAL.FIRMWARE-VERSION:               5751m-v3.29a
  GENERAL.HWADDR:                         <MAC 'enp16s0' [IF1]>
  GENERAL.MTU:                            1500
  GENERAL.STATE:                          20 (unavailable)
  GENERAL.REASON:                         2 (Device is now managed)
  GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.0/0000:10:00.0/net/enp16s0
  GENERAL.IP-IFACE:                        
  GENERAL.IS-SOFTWARE:                    no
  GENERAL.NM-MANAGED:                     yes
  GENERAL.AUTOCONNECT:                    yes
  GENERAL.FIRMWARE-MISSING:               no
  GENERAL.NM-PLUGIN-MISSING:              no
  GENERAL.PHYS-PORT-ID:                   --
  GENERAL.CONNECTION:                     --
  GENERAL.CON-UUID:                       --
  GENERAL.CON-PATH:                       --
  GENERAL.METERED:                        unknown
  CAPABILITIES.CARRIER-DETECT:            yes
  CAPABILITIES.SPEED:                     unknown
  CAPABILITIES.IS-SOFTWARE:               no
  WIRED-PROPERTIES.CARRIER:               off
  CONNECTIONS.AVAILABLE-CONNECTION-PATHS:  
  
 
  SSID                       BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  *  
  --                         <MAC '' [AC1]>  Infra  2     2417 MHz  54 Mbit/s  69      &#9602;&#9604;&#9606;_  WPA1 WPA2  no         
  robrigado1993              <MAC 'robrigado1993' [AN2]>  Infra  11    2462 MHz  54 Mbit/s  44      &#9602;&#9604;__  WPA1 WPA2  no         
  Staffhouse1                <MAC 'Staffhouse1' [AN3]>  Infra  1     2412 MHz  54 Mbit/s  40      &#9602;&#9604;__  WPA1       no         
  vodafoneK7LB               <MAC 'vodafoneK7LB' [AN4]>  Infra  6     2437 MHz  54 Mbit/s  29      &#9602;___  WPA2       no         
  och's office               <MAC 'och's office' [AN5]>  Infra  11    2462 MHz  54 Mbit/s  27      &#9602;___  WPA2       no         
  2degrees Broadband - 808E  <MAC '2degrees Broadband - 808E' [AN6]>  Infra  1     2412 MHz  54 Mbit/s  25      &#9602;___  WPA2       no         
  
 
  ##### NetworkManager.state ##############
  
 
  [main]
  NetworkingEnabled=true
  WirelessEnabled=true
  WWANEnabled=true
  
 
  ##### NetworkManager.conf ###############
  
 
  [main]
  plugins=ifupdown,keyfile,ofono
  dns=dnsmasq
  
 
  [ifupdown]
  managed=false
  
 
  ##### NetworkManager profiles ###########
  
 
  ##### iw reg get ########################
  
 
  Region: Pacific/Auckland (based on set time zone)
  
 
  country 00: DFS-UNSET
      (2402 - 2472 @ 40), (N/A, 20), (N/A)
      (2457 - 2482 @ 40), (N/A, 20), (N/A), NO-IR
      (2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, NO-IR
      (5170 - 5250 @ 80), (N/A, 20), (N/A), NO-IR
      (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, NO-IR
      (5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, NO-IR
      (5735 - 5835 @ 80), (N/A, 20), (N/A), NO-IR
      (57240 - 63720 @ 2160), (N/A, 0), (N/A)
  
 
  ##### iwlist channels ###################
  
 
  enp16s0   no frequency information.
  
 
  lo        no frequency information.
  
 
  wlp2s4    14 channels in total; available frequencies :
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
            Channel 14 : 2.484 GHz
            Current Channel=0
  
 
  ##### iwlist scan #######################
  
 
  enp16s0   Interface doesn't support scanning.
  
 
  lo        Interface doesn't support scanning.
  
 
  Channel occupancy:
  
 
        1   APs on   Frequency:2.412 GHz (Channel 1)
        1   APs on   Frequency:2.417 GHz (Channel 2)
        1   APs on   Frequency:2.462 GHz (Channel 11)
  
 
  wlp2s4    Scan completed :
            Cell 01 - Address: <MAC '' [AC1]>
                      ESSID:""
                      Protocol:IEEE 802.11bg
                      Mode:Master
                      Frequency:2.417 GHz (Channel 2)
                      Encryption key:on
                      Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                                9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                                48 Mb/s; 54 Mb/s
                      Quality=68/100  Signal level=-59 dBm   
                      IE: WPA Version 1
                          Group Cipher : TKIP
                          Pairwise Ciphers (2) : CCMP TKIP
                          Authentication Suites (1) : PSK
                      IE: IEEE 802.11i/WPA2 Version 1
                          Group Cipher : TKIP
                          Pairwise Ciphers (2) : CCMP TKIP
                          Authentication Suites (1) : PSK
                      Extra: Last beacon: 188ms ago
            Cell 02 - Address: <MAC 'Staffhouse' [AC2]>
                      ESSID:"Staffhouse"
                      Protocol:IEEE 802.11bg
                      Mode:Master
                      Frequency:2.412 GHz (Channel 1)
                      Encryption key:on
                      Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                                9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                                48 Mb/s; 54 Mb/s
                      Quality=23/100  Signal level=-85 dBm   
                      IE: IEEE 802.11i/WPA2 Version 1
                          Group Cipher : CCMP
                          Pairwise Ciphers (1) : CCMP
                          Authentication Suites (1) : PSK
                      Extra: Last beacon: 224ms ago
            Cell 03 - Address: <MAC 'NetComm 5151' [AC3]>
                      ESSID:"NetComm 5151"
                      Protocol:IEEE 802.11bg
                      Mode:Master
                      Frequency:2.462 GHz (Channel 11)
                      Encryption key:on
                      Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 11 Mb/s
                                9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                                48 Mb/s; 54 Mb/s
                      Quality=39/100  Signal level=-77 dBm   
                      IE: IEEE 802.11i/WPA2 Version 1
                          Group Cipher : CCMP
                          Pairwise Ciphers (1) : CCMP
                          Authentication Suites (1) : PSK
                      Extra: Last beacon: 4ms ago
  
 
  ##### module infos ######################
  
 
  [ipw2200]
  filename:       /lib/modules/4.4.0-31-generic/kernel/drivers/net/wireless/ipw2x00/ipw2200.ko
  firmware:       ipw2200-bss.fw
  firmware:       ipw2200-sniffer.fw
  firmware:       ipw2200-ibss.fw
  license:        GPL
  author:         Copyright(c) 2003-2006 Intel Corporation
  version:        1.2.2kmprq
  description:    Intel(R) PRO/Wireless 2200/2915 Network Driver
  srcversion:     D9FB7ADDAA0ED935D9DF2BF
  depends:        cfg80211,libipw
  intree:         Y
  vermagic:       4.4.0-31-generic SMP mod_unload modversions 686  
  parm:           disable:manually disable the radio (default 0 [radio on]) (int)
  parm:           associate:auto associate when scanning (default off) (int)
  parm:           auto_create:auto create adhoc network (default on) (int)
  parm:           led:enable led control on some systems (default 1 on) (int)
  parm:           debug:debug output mask (int)
  parm:           channel:channel to limit associate to (default 0 [ANY]) (int)
  parm:           rtap_iface:create the rtap interface (1 - create, default 0) (int)
  parm:           qos_enable:enable all QoS functionalitis (int)
  parm:           qos_burst_enable:enable QoS burst mode (int)
  parm:           qos_no_ack_mask:mask Tx_Queue to no ack (int)
  parm:           burst_duration_CCK:set CCK burst value (int)
  parm:           burst_duration_OFDM:set OFDM burst value (int)
  parm:           mode:network mode (0=BSS,1=IBSS,2=Monitor) (int)
  parm:           bt_coexist:enable bluetooth coexistence (default off) (int)
  parm:           hwcrypto:enable hardware crypto (default off) (int)
  parm:           cmdlog:allocate a ring buffer for logging firmware commands (int)
  parm:           roaming:enable roaming support (default on) (int)
  parm:           antenna:select antenna 1=Main, 3=Aux, default 0 [both], 2=slow_diversity (choose the one with lower background noise) (int)
  
 
  [cfg80211]
  filename:       /lib/modules/4.4.0-31-generic/kernel/net/wireless/cfg80211.ko
  description:    wireless configuration support
  license:        GPL
  author:         Johannes Berg
  srcversion:     25A45701AAA64DAC1E47D9D
  depends:         
  intree:         Y
  vermagic:       4.4.0-31-generic SMP mod_unload modversions 686  
  parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
  parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)
  
 
  ##### module parameters #################
  
 
  [ipw2200]
  antenna: 0
  associate: 0
  auto_create: 1
  bt_coexist: 0
  burst_duration_CCK: 0
  burst_duration_OFDM: 0
  channel: 0
  cmdlog: 0
  debug: 0
  disable: 0
  hwcrypto: 0
  led: 1
  mode: 0
  qos_burst_enable: 0
  qos_enable: 0
  qos_no_ack_mask: 0
  roaming: 1
  rtap_iface: 0
  
 
  [cfg80211]
  cfg80211_disable_40mhz_24ghz: N
  ieee80211_regdom: 00
  
 
  ##### /etc/modules ######################
  
 
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
  
 
  [/etc/modprobe.d/libpisock9.conf]
  blacklist visor
  
 
  [/etc/modprobe.d/mlx4.conf]
  softdep mlx4_core post: mlx4_en
  
 
  ##### rc.local ##########################
  
 
  exit 0
  
 
  ##### pm-utils ##########################
  
 
  ##### udev rules ########################
  
 
  ##### dmesg #############################
  
 
  [   16.539610] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
  [   16.539616] ipw2200: Copyright(c) 2003-2006 Intel Corporation
  [   16.790015] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
  [   18.013657] ipw2200: Detected geography ZZR (14 802.11bg channels, 0 802.11a channels)
  [   18.188562] ipw2200 0000:02:04.0 wlp2s4: renamed from eth0
  [   35.469722] IPv6: ADDRCONF(NETDEV_UP): enp16s0: link is not ready (repeated 2 times)
  [   35.661863] IPv6: ADDRCONF(NETDEV_UP): wlp2s4: link is not ready
  
 
  ########## wireless info END ############
```


Thanks in advance for the help!

---

