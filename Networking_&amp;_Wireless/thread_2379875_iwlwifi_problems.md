---
title: "iwlwifi problems"
date: 2017-12-11
forum: Networking &amp; Wireless
---

### Post by Ed_Reed on 2017-12-11
OK, Intel 6205 wifi card, works fine until suspend and wont reconnect, even when I try. Correct drivers, etc.  Here is a section of the syslog ifit helps: (I've replaced part of SSID with ******)



```
Dec 10 23:43:28 ed-ThinkPad-T420 NetworkManager[1162]: <info> Activation (wlan0) starting connection 'Auto ATT*********'
Dec 10 23:43:28 ed-ThinkPad-T420 NetworkManager[1162]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Dec 10 23:43:28 ed-ThinkPad-T420 NetworkManager[1162]: <info> NetworkManager state is now CONNECTING
Dec 10 23:43:28 ed-ThinkPad-T420 NetworkManager[1162]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Dec 10 23:43:28 ed-ThinkPad-T420 NetworkManager[1162]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Dec 10 23:43:28 ed-ThinkPad-T420 NetworkManager[1162]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Dec 10 23:43:28 ed-ThinkPad-T420 NetworkManager[1162]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Dec 10 23:43:28 ed-ThinkPad-T420 NetworkManager[1162]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Dec 10 23:43:28 ed-ThinkPad-T420 NetworkManager[1162]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Dec 10 23:43:28 ed-ThinkPad-T420 NetworkManager[1162]: <info> Activation (wlan0/wireless): access point 'Auto ATT*********' has security, but secrets are required.
Dec 10 23:43:28 ed-ThinkPad-T420 NetworkManager[1162]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Dec 10 23:43:28 ed-ThinkPad-T420 NetworkManager[1162]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Dec 10 23:43:28 ed-ThinkPad-T420 NetworkManager[1162]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Dec 10 23:43:28 ed-ThinkPad-T420 NetworkManager[1162]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Dec 10 23:43:28 ed-ThinkPad-T420 NetworkManager[1162]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Dec 10 23:43:28 ed-ThinkPad-T420 NetworkManager[1162]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Dec 10 23:43:28 ed-ThinkPad-T420 NetworkManager[1162]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Dec 10 23:43:28 ed-ThinkPad-T420 NetworkManager[1162]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Dec 10 23:43:28 ed-ThinkPad-T420 NetworkManager[1162]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Dec 10 23:43:28 ed-ThinkPad-T420 NetworkManager[1162]: <info> Activation (wlan0/wireless): connection 'Auto ATT*********' has security, and secrets exist.  No new secrets needed.
Dec 10 23:43:28 ed-ThinkPad-T420 NetworkManager[1162]: <info> Config: added 'ssid' value 'ATT*********'
Dec 10 23:43:28 ed-ThinkPad-T420 NetworkManager[1162]: <info> Config: added 'scan_ssid' value '1'
Dec 10 23:43:28 ed-ThinkPad-T420 NetworkManager[1162]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Dec 10 23:43:28 ed-ThinkPad-T420 NetworkManager[1162]: <info> Config: added 'psk' value '<omitted>'
Dec 10 23:43:28 ed-ThinkPad-T420 NetworkManager[1162]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Dec 10 23:43:28 ed-ThinkPad-T420 NetworkManager[1162]: <info> Config: set interface ap_scan to 1
Dec 10 23:43:28 ed-ThinkPad-T420 NetworkManager[1162]: <info> (wlan0): supplicant interface state: disconnected -> scanning

Dec 10 23:43:38 ed-ThinkPad-T420 wpa_supplicant[1273]: wlan0: SME: Trying to authenticate with b0:93:5b:9d:7e:f0 (SSID='ATT*********' freq=2462 MHz)
Dec 10 23:43:38 ed-ThinkPad-T420 kernel: [49601.519468] wlan0: authenticate with b0:93:5b:9d:7e:f0
Dec 10 23:43:38 ed-ThinkPad-T420 kernel: [49601.520204] wlan0: send auth to b0:93:5b:9d:7e:f0 (try 1/3)
Dec 10 23:43:38 ed-ThinkPad-T420 kernel: [49601.522991] wlan0: authenticated
Dec 10 23:43:38 ed-ThinkPad-T420 NetworkManager[1162]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Dec 10 23:43:43 ed-ThinkPad-T420 wpa_supplicant[1273]: wlan0: SME: Deauth request to the driver failed
Dec 10 23:43:43 ed-ThinkPad-T420 wpa_supplicant[1273]: wlan0: CTRL-EVENT-SSID-TEMP-DISABLED id=0 ssid="ATT*********" auth_failures=1 duration=10
Dec 10 23:43:43 ed-ThinkPad-T420 NetworkManager[1162]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
```


Not sure if you can tell whats going on here.  I do have correct driver, as a reboot fixes the connection problem, until I suspend again.  This is the iwlwifi driver from Intel, which has Power Mangement off by default in the driver, as apprently it was causing other problems.  Any ideas? Thinkpad, so I have to use whitelist card or buy a usb.   Thanks in advance for any help you might be able to give.

---

### Post by Hadaka on 2017-12-11
have you tried...
[https://askubuntu.com/questions/748113/wifi-still-sleeping-when-resume/748130#748130](https://askubuntu.com/questions/748113/wifi-still-sleeping-when-resume/748130#748130)

---

### Post by Ed_Reed on 2017-12-11
Thanks for the advice, I hadn't seen that, but no, that doesn't work.  Even from terminal after suspend the command [COLOR=#111111][FONT=Consolas]sudo service network-manager restart  [/FONT][/COLOR]restarts the service successfully but doesn't get a connection.  It tries  can;t connect, repeats a few times and eventually takes the SSID off the list of available choices.  Restarting again  adds the correct SSID to the list, but still doesn't connect even if I try and select it. [COLOR=#111111][FONT=Consolas][/FONT][/COLOR]

---

### Post by Hadaka on 2017-12-11
restarting the network should work from a suspend.
please click "edit connections" and delete any and all references to
your ssid then add it back in again. please also check that "connect
automatically" box is checked. It worked before so something simple
has changed. *if the verification and re-entering the ssid info doesnt
allow it to connect on a restart...please copy and paste the following.
```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && chmod +x wireless-info && ./wireless-info 
```
This command writes a file to your home directory.The file name is wireless-info.txt
From your directory please copy,paste and post the wireless-info.txt
thanks.

---

### Post by Ed_Reed on 2017-12-11
This is the current result of the txt file, after a restart to reconnect, so not in the state of unable to connect.  Not sure if that matters.
Restarting the network after suspends "works" in terms of restarting the network, but it simply doesn't connect, nor does it allow me to force or select a connection to my SSID. 



```
########## wireless info START ##########


Report from: 11 Dec 2017 11:12 EST -0500


Booted last: 11 Dec 2017 09:25 EST -0500


Script from: 05 Dec 2017 03:13 UTC +0000


##### release ###########################


Distributor ID:    LinuxMint
Description:    Linux Mint 17.3 Rosa
Release:    17.3
Codename:    rosa


##### kernel ############################


Linux 4.4.0-67-generic #88~14.04.1-Ubuntu SMP Thu Mar 9 15:30:23 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Cinnamon


##### lspci #############################


00:19.0 Ethernet controller [0200]: Intel Corporation 82579LM Gigabit Network Connection [8086:1502] (rev 04)
    Subsystem: Lenovo Device [17aa:21ce]
    Kernel driver in use: e1000e


03:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6205 [Taylor Peak] [8086:0085] (rev 34)
    Subsystem: Intel Corporation Centrino Advanced-N 6205 AGN [8086:1311]
    Kernel driver in use: iwlwifi


##### lsusb #############################


Bus 002 Device 003: ID 17ef:1003 Lenovo Integrated Smart Card Reader
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 04f2:b221 Chicony Electronics Co., Ltd integrated camera
Bus 001 Device 004: ID 0a5c:217f Broadcom Corp. BCM2045B (BDC-2.1)
Bus 001 Device 003: ID 147e:2016 Upek Biometric Touchchip/Touchstrip Fingerprint Sensor
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no


##### lsmod #############################


iwldvm                229376  0 
mac80211              733184  1 iwldvm
iwlwifi               196608  1 iwldvm
cfg80211              561152  3 iwlwifi,mac80211,iwldvm
wmi                    20480  0 


##### interfaces ########################


auto lo
iface lo inet loopback


iface eth0 inet dhcp


##### ifconfig ##########################


eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF1]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Memory:d2500000-d2520000 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:14275 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14275 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:4553721 (4.5 MB)  TX bytes:4553721 (4.5 MB)


wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF2]>  
          inet addr:192.168.1.230  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlan0' [IF2]>/64 Scope:Link
          inet6 addr: 2602:306:3423:59d0:<IP6 'wlan0' [IF2]>/64 Scope:Global
          inet6 addr: 2602:306:3423:59d0:286b:5040:ccea:6eae/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:198973 errors:0 dropped:43 overruns:0 frame:0
          TX packets:134755 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:232332916 (232.3 MB)  TX bytes:25069664 (25.0 MB)


##### iwconfig ##########################


lo        no wireless extensions.


eth0      no wireless extensions.


wlan0     IEEE 802.11abg  ESSID:"ATTuHVDzMS"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC 'ATTuHVDzMS' [AN5]>   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=57/70  Signal level=-53 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:7528   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0


##### resolv.conf #######################


nameserver 127.0.1.1
search attlocal.net


##### network managers ##################


Installed:


    NetworkManager


Running:


root      1177     1  0 09:25 ?        00:00:02 NetworkManager


##### NetworkManager info ###############


** (process:5546): WARNING **: Could not initialize NMClient /org/freedesktop/NetworkManager: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.


NetworkManager Tool


State: connected (global)


- Device: <MAC address> ----------------------------------------------------
  Type:              Bluetooth
  Driver:            bluez
  State:             disconnected
  Default:           no


  Capabilities:


- Device: <MAC address> ----------------------------------------------------
  Type:              Bluetooth
  Driver:            bluez
  State:             disconnected
  Default:           no


  Capabilities:


- Device: wlan0  [Auto ATTuHVDzMS] ---------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF2]>


  Capabilities:
    Speed:           54 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    Belkin.4BF3:     Infra, <MAC 'Belkin.4BF3' [AN1]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 57 WPA WPA2
    Lackey_2GEXT:    Infra, <MAC 'Lackey_2GEXT' [AN2]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 40 WPA2
    HP-Print-81-Officejet Pro 8610: Infra, <MAC 'HP-Print-81-Officejet Pro 8610' [AN3]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 29 WPA2
    ATTuHVDzMS:      Infra, <MAC 'ATTuHVDzMS' [AN4]>, Freq 5765 MHz, Rate 54 Mb/s, Strength 58 WPA2
    *ATTuHVDzMS:     Infra, <MAC 'ATTuHVDzMS' [AN5]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 66 WPA WPA2
    NETGEAR59:       Infra, <MAC 'NETGEAR59' [AN6]>, Freq 2447 MHz, Rate 54 Mb/s, Strength 30 WPA2
    NETGEAR75:       Infra, <MAC 'NETGEAR75' [AN7]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 39 WPA2
    ATTKImyqgs:      Infra, <MAC 'ATTKImyqgs' [AN8]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    RJM345:          Infra, <MAC 'RJM345' [AN9]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 17 WPA WPA2
    ATT3q7a5z2:      Infra, <MAC 'ATT3q7a5z2' [AN10]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2
    foodie:          Infra, <MAC 'foodie' [AN11]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 20 WPA2
    BHNTG1682GEF92:  Infra, <MAC 'BHNTG1682GEF92' [AN12]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 19 WPA2
    HOMEX:           Infra, <MAC 'HOMEX' [AN13]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 15 WPA WPA2


  IPv4 Settings:
    Address:         192.168.1.230
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254


    DNS:             192.168.1.254


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth0' [IF1]>


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off


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


no-auto-default=<MAC 'eth0' [IF1]>,


[ifupdown]
managed=true


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/WSU-PUBLIC]] (600 root)
[connection] id=WSU-PUBLIC | type=802-11-wireless
[802-11-wireless] ssid=WSU-PUBLIC | mac-address=<MAC 'wlan0' [IF2]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/Amazon-A1S]] (600 root)
[connection] id=Amazon-A1S | type=802-11-wireless
[802-11-wireless] ssid=Amazon-A1S | mac-address=<MAC 'wlan0' [IF2]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/Free Airport WIFI]] (600 root)
[connection] id=Free Airport WIFI | type=802-11-wireless
[802-11-wireless] ssid=Free Airport WIFI | mac-address=<MAC 'wlan0' [IF2]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/NewThermostat_AF67A8]] (600 root)
[connection] id=NewThermostat_AF67A8 | type=802-11-wireless
[802-11-wireless] ssid=NewThermostat_AF67A8 | mac-address=<MAC 'wlan0' [IF2]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/Auto ATTuHVDzMS]] (600 root)
[connection] id=Auto ATTuHVDzMS | type=802-11-wireless
[802-11-wireless] ssid=ATTuHVDzMS | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=ignore


[[/etc/NetworkManager/system-connections/EMU-Wireless-Secure]] (600 root)
[ipv6] method=auto
[connection] id=EMU-Wireless-Secure | type=802-11-wireless
[802-11-wireless] ssid=EMU-Wireless-Secure | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/UNITE-1A82]] (600 root)
[connection] id=UNITE-1A82 | type=802-11-wireless
[802-11-wireless] ssid=UNITE-1A82 | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/XT1095 8801]] (600 root)
[connection] id=XT1095 8801 | type=802-11-wireless
[802-11-wireless] ssid=XT1095 8801 | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Reed1]] (600 root)
[connection] id=Reed1 | type=802-11-wireless
[802-11-wireless] ssid=Reed1 | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=ignore


[[/etc/NetworkManager/system-connections/attwifi]] (600 root)
[connection] id=attwifi | type=802-11-wireless
[802-11-wireless] ssid=attwifi | mac-address=<MAC 'wlan0' [IF2]>
[ipv6] method=auto
[ipv4] method=auto


##### Netplan config ####################


##### iw reg get ########################


Region: America/Detroit (based on set time zone)


country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


##### iwlist channels ###################


lo        no frequency information.


eth0      no frequency information.


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
          Current Frequency:2.462 GHz (Channel 11)


##### iwlist scan #######################


lo        Interface doesn't support scanning.


wlan0     Interface doesn't support scanning : Device or resource busy


eth0      Interface doesn't support scanning.


##### module infos ######################


[iwldvm]
filename:       /lib/modules/4.4.0-67-generic/kernel/drivers/net/wireless/iwlwifi/dvm/iwldvm.ko
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <ilw@linux.intel.com>
description:    Intel(R) Wireless WiFi Link AGN driver for Linux
srcversion:     27B4D15A0ED074811496FFF
depends:        mac80211,iwlwifi,cfg80211
intree:         Y
vermagic:       4.4.0-67-generic SMP mod_unload modversions 
parm:           force_cam:force continuously aware mode (no power saving at all) (bool)


[mac80211]
filename:       /lib/modules/4.4.0-67-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     95AEC776A5F508489477F0E
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-67-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[iwlwifi]
filename:       /lib/modules/4.4.0-67-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <ilw@linux.intel.com>
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
firmware:       iwlwifi-7265D-13.ucode
firmware:       iwlwifi-7265-13.ucode
firmware:       iwlwifi-3160-13.ucode
firmware:       iwlwifi-7260-13.ucode
firmware:       iwlwifi-8000-13.ucode
srcversion:     4116E844336D79483D28F6F
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-67-generic SMP mod_unload modversions 
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (default: 0 dB) (int)
parm:           nvm_file:NVM file name (charp)
parm:           d0i3_disable:disable d0i3 functionality (default: Y) (bool)
parm:           lar_disable:disable LAR functionality (default: N) (bool)
parm:           uapsd_disable:disable U-APSD functionality (default: Y) (bool)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)
parm:           fw_monitor:firmware monitor - to debug FW (default: false - needs lots of memory) (bool)


[cfg80211]
filename:       /lib/modules/4.4.0-67-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     A7DC879B6551813C20004F1
depends:        
intree:         Y
vermagic:       4.4.0-67-generic SMP mod_unload modversions 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[iwldvm]
force_cam: Y


[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
probe_wait_ms: 500


[iwlwifi]
11n_disable: 1
amsdu_size_8K: 0
antenna_coupling: 0
bt_coex_active: Y
d0i3_disable: Y
fw_monitor: N
fw_restart: Y
lar_disable: N
led_mode: 0
nvm_file: (null)
power_level: 0
power_save: N
swcrypto: 0
uapsd_disable: Y


[cfg80211]
bss_entries_limit: 1000
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00


##### /etc/modules ######################


lp
rtc


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


[/etc/modprobe.d/fred.conf]
options iwlwifi 11n_disable=1


[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


##### rc.local ##########################


exit 0


##### pm-utils ##########################


[/etc/pm/config.d/config] (644 root)
SUSPEND_MODULES="iwlwifi"


[/etc/pm/power.d/disable_wol] (777 root)
CONFFILE=/etc/default/tlp
LIBDIR='/usr/lib/pm-utils'
if [ -d "$LIBDIR/power.d" ]; then
    # pm-utils script dir exists
    blocked="$LIBDIR/power.d/${0##*/}"
    if [ -x "$blocked" ]; then
        # overridable pm-utils script exists --> check if TLP enabled
        if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
            # TLP is enabled --> disable $blocked
            echo "Notice: '${blocked}' disabled by TLP."
        else
            exec "$blocked" $*
        fi
    fi # else: nothing to disable -> don't read $CONFFILE
fi
exit 0


[/etc/pm/power.d/laptop-mode] (777 root)
CONFFILE=/etc/default/tlp
LIBDIR='/usr/lib/pm-utils'
if [ -d "$LIBDIR/power.d" ]; then
    # pm-utils script dir exists
    blocked="$LIBDIR/power.d/${0##*/}"
    if [ -x "$blocked" ]; then
        # overridable pm-utils script exists --> check if TLP enabled
        if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
            # TLP is enabled --> disable $blocked
            echo "Notice: '${blocked}' disabled by TLP."
        else
            exec "$blocked" $*
        fi
    fi # else: nothing to disable -> don't read $CONFFILE
fi
exit 0


[/etc/pm/power.d/pci_devices] (777 root)
CONFFILE=/etc/default/tlp
LIBDIR='/usr/lib/pm-utils'
if [ -d "$LIBDIR/power.d" ]; then
    # pm-utils script dir exists
    blocked="$LIBDIR/power.d/${0##*/}"
    if [ -x "$blocked" ]; then
        # overridable pm-utils script exists --> check if TLP enabled
        if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
            # TLP is enabled --> disable $blocked
            echo "Notice: '${blocked}' disabled by TLP."
        else
            exec "$blocked" $*
        fi
    fi # else: nothing to disable -> don't read $CONFFILE
fi
exit 0


[/etc/pm/power.d/pcie_aspm] (777 root)
CONFFILE=/etc/default/tlp
LIBDIR='/usr/lib/pm-utils'
if [ -d "$LIBDIR/power.d" ]; then
    # pm-utils script dir exists
    blocked="$LIBDIR/power.d/${0##*/}"
    if [ -x "$blocked" ]; then
        # overridable pm-utils script exists --> check if TLP enabled
        if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
            # TLP is enabled --> disable $blocked
            echo "Notice: '${blocked}' disabled by TLP."
        else
            exec "$blocked" $*
        fi
    fi # else: nothing to disable -> don't read $CONFFILE
fi
exit 0


[/etc/pm/power.d/sched-powersave] (777 root)
CONFFILE=/etc/default/tlp
LIBDIR='/usr/lib/pm-utils'
if [ -d "$LIBDIR/power.d" ]; then
    # pm-utils script dir exists
    blocked="$LIBDIR/power.d/${0##*/}"
    if [ -x "$blocked" ]; then
        # overridable pm-utils script exists --> check if TLP enabled
        if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
            # TLP is enabled --> disable $blocked
            echo "Notice: '${blocked}' disabled by TLP."
        else
            exec "$blocked" $*
        fi
    fi # else: nothing to disable -> don't read $CONFFILE
fi
exit 0


[/etc/pm/power.d/usb_bluetooth] (777 root)
CONFFILE=/etc/default/tlp
LIBDIR='/usr/lib/pm-utils'
if [ -d "$LIBDIR/power.d" ]; then
    # pm-utils script dir exists
    blocked="$LIBDIR/power.d/${0##*/}"
    if [ -x "$blocked" ]; then
        # overridable pm-utils script exists --> check if TLP enabled
        if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
            # TLP is enabled --> disable $blocked
            echo "Notice: '${blocked}' disabled by TLP."
        else
            exec "$blocked" $*
        fi
    fi # else: nothing to disable -> don't read $CONFFILE
fi
exit 0


[/etc/pm/power.d/wireless] (777 root)
CONFFILE=/etc/default/tlp
LIBDIR='/usr/lib/pm-utils'
if [ -d "$LIBDIR/power.d" ]; then
    # pm-utils script dir exists
    blocked="$LIBDIR/power.d/${0##*/}"
    if [ -x "$blocked" ]; then
        # overridable pm-utils script exists --> check if TLP enabled
        if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
            # TLP is enabled --> disable $blocked
            echo "Notice: '${blocked}' disabled by TLP."
        else
            exec "$blocked" $*
        fi
    fi # else: nothing to disable -> don't read $CONFFILE
fi
exit 0


[/etc/pm/power.d/xfs_buffer] (777 root)
CONFFILE=/etc/default/tlp
LIBDIR='/usr/lib/pm-utils'
if [ -d "$LIBDIR/power.d" ]; then
    # pm-utils script dir exists
    blocked="$LIBDIR/power.d/${0##*/}"
    if [ -x "$blocked" ]; then
        # overridable pm-utils script exists --> check if TLP enabled
        if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
            # TLP is enabled --> disable $blocked
            echo "Notice: '${blocked}' disabled by TLP."
        else
            exec "$blocked" $*
        fi
    fi # else: nothing to disable -> don't read $CONFFILE
fi
exit 0


[/etc/pm/sleep.d/resume_iwlwifi] (755 root)
rmmod iwldvm && rmmod iwlwifi && modprobe iwlwifi bt_coex_active=0


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x8086:0x1502 (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF1]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x8086:0x0085 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF2]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


[   31.513394] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[   31.513497] iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
[   31.783098] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled (repeated 2 times)
[   31.783454] iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
[   31.864601] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   35.684791] wlan0: authenticate with <MAC 'ATTuHVDzMS' [AN5]>
[   35.692782] wlan0: send auth to <MAC 'ATTuHVDzMS' [AN5]> (try 1/3)
[   35.695690] wlan0: authenticated
[   35.699063] wlan0: associate with <MAC 'ATTuHVDzMS' [AN5]> (try 1/3)
[   35.702350] wlan0: RX AssocResp from <MAC 'ATTuHVDzMS' [AN5]> (capab=0x1411 status=0 aid=4)
[   35.714850] wlan0: associated
[   35.714876] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 3351.950105] wlan0: authenticate with <MAC 'ATTuHVDzMS' [AN4]>
[ 3351.952361] wlan0: send auth to <MAC 'ATTuHVDzMS' [AN4]> (try 1/3)
[ 3351.965332] wlan0: authenticated
[ 3351.966752] wlan0: associate with <MAC 'ATTuHVDzMS' [AN4]> (try 1/3)
[ 3351.969792] wlan0: RX AssocResp from <MAC 'ATTuHVDzMS' [AN4]> (capab=0x511 status=0 aid=24)
[ 3351.970017] wlan0: AP has invalid WMM params (AIFSN=1 for ACI 2), will use 2
[ 3351.970019] wlan0: AP has invalid WMM params (AIFSN=1 for ACI 3), will use 2
[ 3351.972255] wlan0: associated
[ 3352.066859] wlan0: Limiting TX power to 30 (30 - 0) dBm as advertised by <MAC 'ATTuHVDzMS' [AN4]>
[ 3471.443146] wlan0: authenticate with <MAC 'ATTuHVDzMS' [AN5]>
[ 3471.445977] wlan0: send auth to <MAC 'ATTuHVDzMS' [AN5]> (try 1/3)
[ 3471.448737] wlan0: authenticated
[ 3471.451112] wlan0: associate with <MAC 'ATTuHVDzMS' [AN5]> (try 1/3)
[ 3471.454218] wlan0: RX AssocResp from <MAC 'ATTuHVDzMS' [AN5]> (capab=0x1411 status=0 aid=4)
[ 3471.456270] wlan0: associated
[ 4071.865258] wlan0: authenticate with <MAC 'ATTuHVDzMS' [AN4]>
[ 4071.868524] wlan0: send auth to <MAC 'ATTuHVDzMS' [AN4]> (try 1/3)
[ 4071.869514] wlan0: authenticated
[ 4071.872975] wlan0: associate with <MAC 'ATTuHVDzMS' [AN4]> (try 1/3)
[ 4071.876546] wlan0: RX AssocResp from <MAC 'ATTuHVDzMS' [AN4]> (capab=0x511 status=0 aid=25)
[ 4071.876813] wlan0: AP has invalid WMM params (AIFSN=1 for ACI 2), will use 2
[ 4071.876820] wlan0: AP has invalid WMM params (AIFSN=1 for ACI 3), will use 2
[ 4071.878923] wlan0: associated
[ 4071.978096] wlan0: Limiting TX power to 30 (30 - 0) dBm as advertised by <MAC 'ATTuHVDzMS' [AN4]>
[ 4311.332654] wlan0: authenticate with <MAC 'ATTuHVDzMS' [AN5]>
[ 4311.335176] wlan0: send auth to <MAC 'ATTuHVDzMS' [AN5]> (try 1/3)
[ 4311.339170] wlan0: authenticated
[ 4311.345523] wlan0: associate with <MAC 'ATTuHVDzMS' [AN5]> (try 1/3)
[ 4311.348667] wlan0: RX AssocResp from <MAC 'ATTuHVDzMS' [AN5]> (capab=0x1411 status=0 aid=4)
[ 4311.353172] wlan0: associated


########## wireless info END ############
```

---

### Post by Ed_Reed on 2017-12-13
Bump

---

### Post by Ed_Reed on 2017-12-18
Bump

---

### Post by chili555 on 2017-12-18
The guys in the back room have asked me, the old driver dawg, to take a look at your case. Perhaps we can find a few things to tweak that may help.

First, I see this:

> ATTuHVDzMS: Infra, <MAC 'ATTuHVDzMS' [AN5]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 66 WPA WPA2

When we see both WPA and WPA2, we suspect that the router remains in its default state; that is, set to connect in case Grandma shows up with her circa-2005 laptop that isn’t new enough to do WPA2-AES. Not only is this insecure, but some Linux drivers struggle to stay connected to a router that is set to automatically hop around always looking for a better connection. 

Please check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

Then set your regulatory domain explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
sudo nano /etc/default/crda
```Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save and close the text editor.

Next we see this:

> ATTuHVDzMS: Infra, <MAC 'ATTuHVDzMS' [AN4]>, Freq 5765 MHz, Rate 54 Mb/s, Strength 58 WPA2
*ATTuHVDzMS: Infra, <MAC 'ATTuHVDzMS' [AN5]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 66 WPA WPA2

No doubt that these are the 2.4 gHz and the 5 gHz segments of your router. In your dmesg log, we see your device roaming among them; you see it as a disconnect and reconnect.

I think you will have much better luck if you rename the segments; I suggest something like ATTuHVDzMS-2.4 and ATTuHVDzMS-5. Then, after you reboot the router, ask your wireless to connect to one and stick to it. I think you will have no disconnects as well as easier connections on boot and, hopefully, after suspend.

Of course, try each segment individually to see which works best. In my Intel wireless, I have better speed with the 5 gHz segment.

After making these changes, post back and report your results.

---

### Post by DuckHook on 2017-12-18
@Ed_Reed

...please post your output between [noparse]```
 and 
```[/noparse] tags for clarity. Or highlight the output and use the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the *Adv Reply* toolbar.

---

### Post by Darth4212 on 2017-12-20
Try unloading the driver with 

```
sudo rmmod iwlwifi
```

And then reloading it with

```
sudo modprobe iwlwifi
```

---

