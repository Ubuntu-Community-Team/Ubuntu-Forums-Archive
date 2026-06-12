---
title: "Networking problems on ubuntu 14.04"
date: 2014-07-19
forum: Networking &amp; Wireless
---

### Post by adityaduggal on 2014-07-19
Hi Varun,

Even I am facing a similar issue, in fact I am able to see the wifi networks but unable to connect to them. Also I had activated the wifi hotspot but now when I try to switch off the hotspot the network crashes without any message. I have inserted the information regarding my wifi, kindly let me know if there is any other information that is needed by you.

Also the problem is that when I got network settings then the Wireless is showing a wireless hotspot as ON and when I try to switch that OFF it asks for a confirmation and on confirming the OFF the window closes but the syslog shows the following line:

kernel: unity-control-c [4366]: segfault at 8 ip (some no) sp (some no) error 4 in libnetwork.so[some no]```


########## wireless info START ##########


##### release #####


Distributor ID:    Ubuntu
Description:    Ubuntu 14.04 LTS
Release:    14.04
Codename:    trusty


##### kernel #####


Linux aditya 3.13.0-32-generic #57-Ubuntu SMP Tue Jul 15 03:51:08 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


##### lspci #####


00:19.0 Ethernet controller [0200]: Intel Corporation 82579LM Gigabit Network Connection [8086:1502] (rev 04)
    Subsystem: Lenovo Device [17aa:21f3]
    Kernel driver in use: e1000e


03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:8195]
    Kernel driver in use: rtl8192ce


##### lsusb #####


Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 04f2:b2da Chicony Electronics Co., Ltd 
Bus 001 Device 006: ID 0a5c:21e6 Broadcom Corp. BCM20702 Bluetooth 4.0 [ThinkPad]
Bus 001 Device 003: ID 147e:2020 Upek TouchChip Fingerprint Coprocessor (WBF advanced mode)
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 0781:5572 SanDisk Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA Card Info #####


##### rfkill #####


0: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
4: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no


##### lsmod #####


rtl8192ce              53550  0 
rtl_pci                26690  1 rtl8192ce
rtlwifi                63475  2 rtl_pci,rtl8192ce
rtl8192c_common        53172  1 rtl8192ce
mac80211              630653  3 rtl_pci,rtlwifi,rtl8192ce
cfg80211              484040  2 mac80211,rtlwifi


##### iw reg get #####


country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


##### interfaces #####


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


##### iwconfig #####


wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          


##### route #####


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface


##### resolv.conf #####


##### nm-tool #####


NetworkManager Tool


State: disconnected


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192ce
  State:             disconnected
  Default:           no
  HW Address:        <MAC address removed>


  Capabilities:


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points 
    RU:              Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 80 WPA WPA2
    Ahujas:          Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    MANJEET SINGH:   Infra, <MAC address removed>, Freq 2467 MHz, Rate 54 Mb/s, Strength 27 WPA


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off


##### NetworkManager.state #####


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


##### NetworkManager.conf #####


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false


##### iwlist #####


wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=62/70  Signal level=-48 dBm  
                    Encryption key:on
                    ESSID:"RU"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000002838fa44
                    Extra: Last beacon: 12ms ago
                    IE: Unknown: 00025255
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101870003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334E111BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4E111BFF00000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401051900000000000000000000000000000000000000
                    IE: Unknown: 3D1601051900000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000004000


##### iwlist channel #####


wlan0     13 channels in total; available frequencies :
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


##### modinfo #####


filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko
firmware:       rtlwifi/rtl8192cfwU_B.bin
firmware:       rtlwifi/rtl8192cfwU.bin
firmware:       rtlwifi/rtl8192cfw.bin
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     EF063698748457BBEDB4633
alias:          pci:v000010ECd00008176sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008177sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008178sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008191sv*sd*bc*sc*i*
depends:        rtlwifi,rtl_pci,rtl8192c-common,mac80211
intree:         Y
vermagic:       3.13.0-32-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:65:43:53:5F:A2:BB:5B:70:9E:84:F1:6D:A7:C7
sig_hashalgo:   sha512
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)


filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     D5E4890DC428FA5A1BF92DF
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       3.13.0-32-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:65:43:53:5F:A2:BB:5B:70:9E:84:F1:6D:A7:C7
sig_hashalgo:   sha512


filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     E1F4663325225EE8DBA54CA
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-32-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:65:43:53:5F:A2:BB:5B:70:9E:84:F1:6D:A7:C7
sig_hashalgo:   sha512


filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192c/rtl8192c-common.ko
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Ziv Huang    <ziv_huang@realtek.com>
author:         Georgia        <georgia@realtek.com>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     32F826C623BC49F764F7974
depends:        
intree:         Y
vermagic:       3.13.0-32-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:65:43:53:5F:A2:BB:5B:70:9E:84:F1:6D:A7:C7
sig_hashalgo:   sha512


##### modules #####


lp
rtc


##### blacklist #####


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


[/etc/modprobe.d/bumblebee.conf]
blacklist nouveau
blacklist nvidia
blacklist nvidia-current
blacklist nvidia-current-updates
blacklist nvidia-304
blacklist nvidia-304-updates
blacklist nvidia-experimental-304
blacklist nvidia-310
blacklist nvidia-310-updates
blacklist nvidia-experimental-310
blacklist nvidia-313
blacklist nvidia-313-updates
blacklist nvidia-experimental-313
blacklist nvidia-319
blacklist nvidia-319-updates
blacklist nvidia-experimental-319
blacklist nvidia-325
blacklist nvidia-325-updates
blacklist nvidia-experimental-325
blacklist nvidia-331
blacklist nvidia-331-updates
blacklist nvidia-experimental-331
blacklist nvidia-334
blacklist nvidia-334-updates
blacklist nvidia-experimental-334
blacklist nvidia-337
blacklist nvidia-337-updates
blacklist nvidia-experimental-337


[/etc/modprobe.d/fbdev-blacklist.conf]
blacklist arkfb
blacklist aty128fb
blacklist atyfb
blacklist radeonfb
blacklist cirrusfb
blacklist cyber2000fb
blacklist gx1fb
blacklist gxfb
blacklist kyrofb
blacklist matroxfb_base
blacklist mb862xxfb
blacklist neofb
blacklist nvidiafb
blacklist pm2fb
blacklist pm3fb
blacklist s3fb
blacklist savagefb
blacklist sisfb
blacklist tdfxfb
blacklist tridentfb
blacklist viafb
blacklist vt8623fb


##### udev rules #####


# PCI device 0x8086:0x1502 (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x10ec:0x8176 (rtl8192ce)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #####


[    8.895917] rtl8192ce: Using firmware rtlwifi/rtl8192cfw.bin
[    8.986761] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[    8.986986] rtlwifi: wireless switch is on
[    9.128678] usb 1-1.4: Direct firmware load failed with error -2
[    9.130371] Bluetooth: can't load firmware, may not work correctly
[   13.135532] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   13.136011] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   13.740503] psmouse serio2: trackpoint: IBM TrackPoint firmware: 0x0e, buttons: 3/3
[  840.610786] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1298.864489] rtlwifi: wireless switch is on
[ 1301.228415] WARNING: CPU: 2 PID: 2994 at /build/buildd/linux-3.13.0/drivers/base/firmware_class.c:1089 _request_firmware+0x5d9/0xb10()
[ 1301.228442] Modules linked in: nls_utf8 udf crc_itu_t hid_generic hidp hid bbswitch(OF) pci_stub vboxpci(OF) vboxnetadp(OF) vboxnetflt(OF) vboxdrv(OF) bnep rfcomm nls_iso8859_1 snd_hda_codec_hdmi snd_hda_codec_realtek joydev uvcvideo videobuf2_vmalloc videobuf2_memops btusb videobuf2_core bluetooth videodev snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_page_alloc arc4 intel_rapl x86_pkg_temp_thermal intel_powerclamp coretemp kvm_intel kvm crct10dif_pclmul crc32_pclmul ghash_clmulni_intel aesni_intel aes_x86_64 lrw gf128mul glue_helper ablk_helper cryptd thinkpad_acpi nvram snd_seq_midi snd_seq_midi_event snd_rawmidi psmouse serio_raw snd_seq rtl8192ce rtl_pci rtlwifi rtl8192c_common snd_seq_device mac80211 i915 snd_timer cfg80211 snd drm_kms_helper lpc_ich mei_me drm mei i2c_algo_bit wmi soundcore video mac_hid parport_pc ppdev lp parport sdhci_pci sdhci e1000e ahci ptp libahci pps_core
[ 1301.228473]  [<ffffffff814a4369>] _request_firmware+0x5d9/0xb10
[ 1301.228475]  [<ffffffff814a48d4>] request_firmware+0x34/0x50
[ 1301.228512] usb 1-1.4: firmware: fw-0a5c_21e6.hcd will not be loaded
[ 1301.228514] Bluetooth: can't load firmware, may not work correctly
[ 1302.255743] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1595.160766] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1595.290722] usb 1-1.4: Direct firmware load failed with error -2
[ 1595.292242] Bluetooth: can't load firmware, may not work correctly


########## wireless info END ############



```

---

### Post by bapoumba on 2014-07-19
Moved to its own thread.

---

### Post by adityaduggal on 2014-07-19
I am also enclosing the output of the experimental script for wifi:

```



	======== Wireless-Info START ========


System-Info ~~~~~~~~~~~~~~~~~~~~~~~~


aditya 3.13.0-32-generic x86_64,  Ubuntu 14.04 LTS, trusty


CPU    : Intel(R) Core(TM) i5-3230M CPU @ 2.60GHz
Memory : 7803 MB
Uptime : 18:28:15 up  2:13,  3 users,  load average: 0.35, 0.23, 0.19




lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


00:19.0 Ethernet controller [0200]: Intel Corporation 82579LM Gigabit Network Connection [8086:1502] (rev 04)
	Subsystem: Lenovo Device [17aa:21f3]
	Kernel driver in use: e1000e
--
03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
	Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:8195]
	Kernel driver in use: rtl8192ce




lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 04f2:b2da Chicony Electronics Co., Ltd 
Bus 001 Device 006: ID 0a5c:21e6 Broadcom Corp. BCM20702 Bluetooth 4.0 [ThinkPad]
Bus 001 Device 003: ID 147e:2020 Upek TouchChip Fingerprint Coprocessor (WBF advanced mode)
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 004: ID 0781:5572 SanDisk Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub




PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~






iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          




rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


      Interface                    Soft blocked  Hard blocked
0: tpacpi_bluetooth_sw: Bluetooth      no            no
1: phy0: Wireless LAN                  no            no
7: hci0: Bluetooth                     no            no




lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


rtl8192ce              53550  0 
rtl_pci                26690  1 rtl8192ce
rtlwifi                63475  2 rtl_pci,rtl8192ce
rtl8192c_common        53172  1 rtl8192ce
mac80211              630653  3 rtl_pci,rtlwifi,rtl8192ce
cfg80211              484040  2 mac80211,rtlwifi
wmi                    19177  0 




module parameters ~~~~~~~~~~~~~~~~~~


cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
rtl8192ce     (5): debug=0 | fwlps=Y | ips=Y | swenc=N | swlps=N
wmi           (2): debug_dump_wdg=N | debug_event=N




nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


State: disconnected
================o=============o===========o==============o=========o===========o==============o===========
 Interface & ID | Type        | Driver    | State        | Default | Speed     | Support      | HW Addr   
================o=============o===========o==============o=========o===========o==============o===========
 wlan0          | 802.11 WiFi | rtl8192ce | disconnected | no      |           | WEP/WPA/WPA2 | <MAC wlan0>


    RU:              Infra, <MAC C-01 RU>, Freq 2412 MHz, Rate 54 Mb/s, Strength 77 WPA WPA2
    MANJEET SINGH:   Infra, <MAC C-02 MANJEET SINGH>, Freq 2467 MHz, Rate 54 Mb/s, Strength 34 WPA
----------------+-------------+-----------+--------------+---------+-----------+--------------+-----------
 eth0           | Wired       | e1000e    | unavailable  | no      |           |              | <MAC eth0>
----------------+-------------+-----------+--------------+---------+-----------+--------------+-----------




NetworkManager.state ~~~~~~~~~~~~~~~
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true




NetworkManager.conf ~~~~~~~~~~~~~~~~


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false




NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~


DLkspl               : ssid=DLkspl | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Hotspot              : ssid=aditya | autoconnect=false | mac-address=<MAC wlan0> | ipv4=shared | ipv6=auto 
MANJEET SINGH        : ssid=MANJEET SINGH | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
RIGPL                : ssid=RIGPL | permissions=user:guest-7DbLN2:; | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
RIGPL 1              : ssid=RIGPL | permissions=user:guest-NnSKSA:; | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
RIGPL 2              : ssid=RIGPL | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
RU                   : ssid=RU | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 




interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~






Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface




iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~


(Region : "en_IN")
country 00:
	(2402 - 2472 @ 40), (3, 20)
	(2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
	(5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS




iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     13 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 13 (2.472 GHz)




iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 RU>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=58/70  Signal level=-52 dBm  
                    Encryption key:on
                    ESSID:"RU"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000001cb7e7748
                    Extra: Last beacon: 8ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC C-02 MANJEET SINGH>
                    Channel:12
                    Frequency:2.467 GHz (Channel 12)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"MANJEET SINGH"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000010952f18a6
                    Extra: Last beacon: 21460ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC C-03 >
                    Channel:12
                    Frequency:2.467 GHz (Channel 12)
                    Quality=56/70  Signal level=-54 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000109675c9b7
                    Extra: Last beacon: 144ms ago




blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci




modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


[rtl8192ce]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko
firmware:       rtlwifi/rtl8192cfwU_B.bin
firmware:       rtlwifi/rtl8192cfwU.bin
firmware:       rtlwifi/rtl8192cfw.bin
srcversion:     EF063698748457BBEDB4633
depends:        rtlwifi,rtl_pci,rtl8192c-common,mac80211
parm:           swenc:Set to 1 for software crypto (default 0)
parm:           ips:Set to 0 to not use link power save (default 1)
parm:           swlps:Set to 1 to use SW control power save (default 0)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
parm:           debug:Set debug level (0-5) (default 0) (int)


[rtl_pci]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
srcversion:     D5E4890DC428FA5A1BF92DF
depends:        mac80211,rtlwifi


[rtlwifi]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
srcversion:     E1F4663325225EE8DBA54CA
depends:        mac80211,cfg80211


[rtl8192c_common]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192c/rtl8192c-common.ko
srcversion:     32F826C623BC49F764F7974
depends:        


[mac80211]
filename:       /lib/modules/3.13.0-32-generic/kernel/net/mac80211/mac80211.ko
srcversion:     8ADA881D348148A3358334C
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/3.13.0-32-generic/kernel/net/wireless/cfg80211.ko
srcversion:     E786D076B61F97809B04B64
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)




udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~


# PCI device 0x8086:0x1502 (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x10ec:0x8176 (rtl8192ce)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"




Custom files/entries ~~~~~~~~~~~~~~~


/etc/modules        : Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Default


[/etc/modprobe.d]
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
mlx4.conf         : softdep mlx4_core post: mlx4_en




Kernel boot line ~~~~~~~~~~~~~~~~~~~


BOOT_IMAGE=/boot/vmlinuz-3.13.0-32-generic.efi.signed root=UUID=431f00a3-5771-4f83-81f7-5cf14c37a934 ro quiet splash vt.handoff=7




dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


[    0.479587] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.479839] audit: initializing netlink socket (disabled)
[    8.679886] wmi: Mapper loaded
[    8.747135] rtl8192ce: Using firmware rtlwifi/rtl8192cfw.bin
[    8.754570] thinkpad_acpi: http://ibm-acpi.sf.net/
[    8.887248] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[    8.887475] rtlwifi: wireless switch is on
[    9.025782] usb 1-1.4: Direct firmware load failed with error -2
[    9.027105] Bluetooth: can't load firmware, may not work correctly
[   11.633805] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   13.020662] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   13.020908] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   13.658687] psmouse serio2: trackpoint: IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   74.509606] unity-control-c[2469]: segfault at 8 ip 00007f2c72b2e068 sp 00007fff67bd62f0 error 4 in libnetwork.so[7f2c72b20000+1f000]
[  118.555265] unity-control-c[2566]: segfault at 8 ip 00007f21a38cf068 sp 00007fff78a95c20 error 4 in libnetwork.so[7f21a38c1000+1f000]
[  132.022428] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  132.298269] usb 1-1.4: Direct firmware load failed with error -2
[  132.300044] Bluetooth: can't load firmware, may not work correctly
[ 2990.807010] rtlwifi: wireless switch is on
[ 2993.151057] WARNING: CPU: 1 PID: 631 at /build/buildd/linux-3.13.0/drivers/base/firmware_class.c:1089 _request_firmware+0x5d9/0xb10()
[ 2993.151084] Modules linked in: hid_generic hidp hid nls_utf8 udf crc_itu_t pci_stub vboxpci(OF) vboxnetadp(OF) vboxnetflt(OF) vboxdrv(OF) bnep rfcomm nls_iso8859_1 joydev uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_core videodev btusb bluetooth arc4 intel_rapl x86_pkg_temp_thermal intel_powerclamp coretemp kvm_intel kvm crct10dif_pclmul crc32_pclmul ghash_clmulni_intel aesni_intel aes_x86_64 lrw gf128mul glue_helper ablk_helper cryptd thinkpad_acpi nvram snd_hda_codec_realtek psmouse snd_seq_midi snd_seq_midi_event serio_raw snd_rawmidi rtl8192ce snd_seq rtl_pci rtlwifi snd_hda_intel rtl8192c_common i915 snd_hda_codec mac80211 snd_hwdep snd_pcm drm_kms_helper cfg80211 drm snd_seq_device snd_page_alloc lpc_ich snd_timer i2c_algo_bit mei_me mei snd wmi soundcore parport_pc mac_hid video ppdev lp parport ahci libahci e1000e sdhci_pci ptp sdhci pps_core
[ 2993.151113]  [<ffffffff814a4369>] _request_firmware+0x5d9/0xb10
[ 2993.151115]  [<ffffffff814a48d4>] request_firmware+0x34/0x50
[ 2993.151143] usb 1-1.4: firmware: fw-0a5c_21e6.hcd will not be loaded
[ 2993.151145] Bluetooth: can't load firmware, may not work correctly
[ 2994.168988] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4000.033166] unity-control-c[2590]: segfault at 8 ip 00007f7eec27c068 sp 00007fffa9a7a980 error 4 in libnetwork.so[7f7eec26e000+1f000]
[ 4475.046966] rtlwifi: wireless switch is on
[ 4477.404931] WARNING: CPU: 2 PID: 2706 at /build/buildd/linux-3.13.0/drivers/base/firmware_class.c:1089 _request_firmware+0x5d9/0xb10()
[ 4477.404958] Modules linked in: hid_generic hidp hid nls_utf8 udf crc_itu_t pci_stub vboxpci(OF) vboxnetadp(OF) vboxnetflt(OF) vboxdrv(OF) bnep rfcomm nls_iso8859_1 joydev uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_core videodev btusb bluetooth arc4 intel_rapl x86_pkg_temp_thermal intel_powerclamp coretemp kvm_intel kvm crct10dif_pclmul crc32_pclmul ghash_clmulni_intel aesni_intel aes_x86_64 lrw gf128mul glue_helper ablk_helper cryptd thinkpad_acpi nvram snd_hda_codec_realtek psmouse snd_seq_midi snd_seq_midi_event serio_raw snd_rawmidi rtl8192ce snd_seq rtl_pci rtlwifi snd_hda_intel rtl8192c_common i915 snd_hda_codec mac80211 snd_hwdep snd_pcm drm_kms_helper cfg80211 drm snd_seq_device snd_page_alloc lpc_ich snd_timer i2c_algo_bit mei_me mei snd wmi soundcore parport_pc mac_hid video ppdev lp parport ahci libahci e1000e sdhci_pci ptp sdhci pps_core
[ 4477.404988]  [<ffffffff814a4369>] _request_firmware+0x5d9/0xb10
[ 4477.404990]  [<ffffffff814a48d4>] request_firmware+0x34/0x50
[ 4477.405022] usb 1-1.4: firmware: fw-0a5c_21e6.hcd will not be loaded
[ 4477.405024] Bluetooth: can't load firmware, may not work correctly
[ 4478.319559] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 6963.749512] rtlwifi: wireless switch is on
[ 6966.110115] WARNING: CPU: 3 PID: 2706 at /build/buildd/linux-3.13.0/drivers/base/firmware_class.c:1089 _request_firmware+0x5d9/0xb10()
[ 6966.110149] Modules linked in: usb_storage hid_generic hidp hid nls_utf8 udf crc_itu_t pci_stub vboxpci(OF) vboxnetadp(OF) vboxnetflt(OF) vboxdrv(OF) bnep rfcomm nls_iso8859_1 joydev uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_core videodev btusb bluetooth arc4 intel_rapl x86_pkg_temp_thermal intel_powerclamp coretemp kvm_intel kvm crct10dif_pclmul crc32_pclmul ghash_clmulni_intel aesni_intel aes_x86_64 lrw gf128mul glue_helper ablk_helper cryptd thinkpad_acpi nvram snd_hda_codec_realtek psmouse snd_seq_midi snd_seq_midi_event serio_raw snd_rawmidi rtl8192ce snd_seq rtl_pci rtlwifi snd_hda_intel rtl8192c_common i915 snd_hda_codec mac80211 snd_hwdep snd_pcm drm_kms_helper cfg80211 drm snd_seq_device snd_page_alloc lpc_ich snd_timer i2c_algo_bit mei_me mei snd wmi soundcore parport_pc mac_hid video ppdev lp parport ahci libahci e1000e sdhci_pci ptp sdhci pps_core
[ 6966.110187]  [<ffffffff814a4369>] _request_firmware+0x5d9/0xb10
[ 6966.110189]  [<ffffffff814a48d4>] request_firmware+0x34/0x50
[ 6966.110223] usb 1-1.4: firmware: fw-0a5c_21e6.hcd will not be loaded
[ 6966.110224] Bluetooth: can't load firmware, may not work correctly
[ 6967.150570] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7443.154524] rtlwifi: wireless switch is on
[ 7445.502372] WARNING: CPU: 3 PID: 4571 at /build/buildd/linux-3.13.0/drivers/base/firmware_class.c:1089 _request_firmware+0x5d9/0xb10()
[ 7445.502399] Modules linked in: usb_storage hid_generic hidp hid nls_utf8 udf crc_itu_t pci_stub vboxpci(OF) vboxnetadp(OF) vboxnetflt(OF) vboxdrv(OF) bnep rfcomm nls_iso8859_1 joydev uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_core videodev btusb bluetooth arc4 intel_rapl x86_pkg_temp_thermal intel_powerclamp coretemp kvm_intel kvm crct10dif_pclmul crc32_pclmul ghash_clmulni_intel aesni_intel aes_x86_64 lrw gf128mul glue_helper ablk_helper cryptd thinkpad_acpi nvram snd_hda_codec_realtek psmouse snd_seq_midi snd_seq_midi_event serio_raw snd_rawmidi rtl8192ce snd_seq rtl_pci rtlwifi snd_hda_intel rtl8192c_common i915 snd_hda_codec mac80211 snd_hwdep snd_pcm drm_kms_helper cfg80211 drm snd_seq_device snd_page_alloc lpc_ich snd_timer i2c_algo_bit mei_me mei snd wmi soundcore parport_pc mac_hid video ppdev lp parport ahci libahci e1000e sdhci_pci ptp sdhci pps_core
[ 7445.502430]  [<ffffffff814a4369>] _request_firmware+0x5d9/0xb10
[ 7445.502432]  [<ffffffff814a48d4>] request_firmware+0x34/0x50
[ 7445.502462] usb 1-1.4: firmware: fw-0a5c_21e6.hcd will not be loaded
[ 7445.502464] Bluetooth: can't load firmware, may not work correctly
[ 7446.532105] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready


	======== Done ========



```

---

### Post by varunendra on 2014-07-19
After the developments during our chat on IRC, I'll await for a fresh wireless_script report plus other updates you may have.

---

### Post by adityaduggal on 2014-07-19
Hi Varun,

You have greatly helped me by getting the network manager tools installed which has enabled my notebook to connect to the internet. Now the problem left is that the network manager icon is not showing on the unity tool bar. I have tried and created a new profile as well but even with the new profile I am not seeing the network manager icons on the status bar. After the update on irc, I am again enclosing the output of the wireless_script_experimental.

First I am enclosing the output for nm-tools

```
NetworkManager Tool

State: connected (global)




** (process:8945): WARNING **: error: cannot retrieve connection: uid 1000 has no permission to perform this operation
- Device: wlan0  [DUGGALS] -----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192ce
  State:             connected
  Default:           yes
  HW Address:        B8:76:3F:D0:E7:1C


  Capabilities:
    Speed:           18 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    MTNL:            Infra, 0C:D2:B5:01:D4:F0, Freq 2457 MHz, Rate 54 Mb/s, Strength 50 WPA WPA2
    3:16:            Infra, 00:25:5E:C3:9E:6C, Freq 2417 MHz, Rate 54 Mb/s, Strength 10 WPA
    Torjan Virus:    Infra, 0C:D2:B5:19:6B:80, Freq 2437 MHz, Rate 54 Mb/s, Strength 77 WPA
    DUGGALS:         Infra, 10:FE:ED:8F:A3:46, Freq 2412 MHz, Rate 54 Mb/s, Strength 66 WPA2
    parveshkumar:    Infra, 00:22:75:48:56:F2, Freq 2412 MHz, Rate 54 Mb/s, Strength 74 WPA WPA2
    *DUGGALS:        Infra, 00:1C:10:93:06:1C, Freq 2437 MHz, Rate 54 Mb/s, Strength 66 WPA WPA2


  IPv4 Settings:
    Address:         10.0.0.4
    Prefix:          24 (255.255.255.0)
    Gateway:         10.0.0.1


    DNS:             10.0.0.1




- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             unavailable
  Default:           no
  HW Address:        3C:97:0E:AB:C4:1C


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off



```

The output for the wireless_script is as below:

```
    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~


aditya 3.13.0-32-generic x86_64,  Ubuntu 14.04 LTS, trusty


CPU    : Intel(R) Core(TM) i5-3230M CPU @ 2.60GHz
Memory : 7803 MB
Uptime : 22:49:31 up 23 min,  3 users,  load average: 0.49, 0.42, 0.41




lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


00:19.0 Ethernet controller [0200]: Intel Corporation 82579LM Gigabit Network Connection [8086:1502] (rev 04)
    Subsystem: Lenovo Device [17aa:21f3]
    Kernel driver in use: e1000e
--
03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:8195]
    Kernel driver in use: rtl8192ce




lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 04f2:b2da Chicony Electronics Co., Ltd 
Bus 001 Device 004: ID 0a5c:21e6 Broadcom Corp. BCM20702 Bluetooth 4.0 [ThinkPad]
Bus 001 Device 003: ID 147e:2020 Upek TouchChip Fingerprint Coprocessor (WBF advanced mode)
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub




PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~






iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     IEEE 802.11bgn  ESSID:"DUGGALS"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC C-01 DUGGALS>   
          Bit Rate=18 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=68/70  Signal level=-42 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1448   Missed beacon:0






rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


      Interface                    Soft blocked  Hard blocked
0: tpacpi_bluetooth_sw: Bluetooth      no            no
1: phy0: Wireless LAN                  no            no
2: hci0: Bluetooth                     no            no




lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


rtl8192ce              53550  0 
rtl_pci                26690  1 rtl8192ce
rtlwifi                63475  2 rtl_pci,rtl8192ce
rtl8192c_common        53172  1 rtl8192ce
mac80211              630653  3 rtl_pci,rtlwifi,rtl8192ce
cfg80211              484040  2 mac80211,rtlwifi
wmi                    19177  0 




module parameters ~~~~~~~~~~~~~~~~~~


cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
rtl8192ce     (5): debug=0 | fwlps=Y | ips=Y | swenc=N | swlps=N
wmi           (2): debug_dump_wdg=N | debug_event=N




nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


State: connected (global)
==================o=============o===========o==============o=========o===========o==============o===========
 Interface & ID   | Type        | Driver    | State        | Default | Speed     | Support      | HW Addr   
==================o=============o===========o==============o=========o===========o==============o===========
 wlan0  [DUGGALS] | 802.11 WiFi | rtl8192ce | connected    | yes     | 18 Mb/s   | WEP/WPA/WPA2 | <MAC wlan0>


    MTNL:            Infra, <MAC C-09 MTNL>, Freq 2457 MHz, Rate 54 Mb/s, Strength 50 WPA WPA2
    3:16:            Infra, <MAC C-04 3:16>, Freq 2417 MHz, Rate 54 Mb/s, Strength 10 WPA
    DUGGALS:         Infra, <MAC C-02 DUGGALS>, Freq 2412 MHz, Rate 54 Mb/s, Strength 62 WPA2
    *DUGGALS:        Infra, <MAC C-01 DUGGALS>, Freq 2437 MHz, Rate 54 Mb/s, Strength 76 WPA WPA2
    BATRA:           Infra, <MAC C-NA BATRA 1>, Freq 2412 MHz, Rate 54 Mb/s, Strength 7 WPA
    Torjan Virus:    Infra, <MAC C-05 Torjan Virus>, Freq 2437 MHz, Rate 54 Mb/s, Strength 97 WPA


    Address:         10.0.0.4
    Prefix:          24 (255.255.255.0)
    Gateway:         10.0.0.1
    DNS:             10.0.0.1
------------------+-------------+-----------+--------------+---------+-----------+--------------+-----------
 eth0             | Wired       | e1000e    | unavailable  | no      |           |              | <MAC eth0>
------------------+-------------+-----------+--------------+---------+-----------+--------------+-----------




NetworkManager.state ~~~~~~~~~~~~~~~
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true




NetworkManager.conf ~~~~~~~~~~~~~~~~


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false




NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~


3:16                 : ssid=3:16 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
DUGGALS              : ssid=DUGGALS | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
RIGPL                : ssid=RIGPL | permissions=user:guest-7DbLN2:; | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
RU                   : ssid=RU | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 




interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~


nameserver 127.0.1.1




Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.0.0.1        0.0.0.0         UG    0      0        0 wlan0
10.0.0.0        0.0.0.0         255.255.255.0   U     9      0        0 wlan0


--- 10.0.0.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 1.434/1.785/2.137/0.354 ms


--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.036/0.042/0.048/0.006 ms




iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~


(Region : "en_IN")
country IN:
    (2402 - 2482 @ 40), (N/A, 20)
    (5170 - 5250 @ 40), (N/A, 20)
    (5250 - 5330 @ 40), (N/A, 20), DFS
    (5735 - 5835 @ 40), (N/A, 20)




iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     13 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 13 (2.472 GHz)


          Current Frequency:2.437 GHz (Channel 6)




iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 DUGGALS>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-40 dBm  
                    Encryption key:on
                    ESSID:"DUGGALS"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000330367a42a
                    Extra: Last beacon: 8ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC C-02 DUGGALS>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=26 dBm  
                    Encryption key:on
                    ESSID:"DUGGALS"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000033029085f0
                    Extra: Last beacon: 8ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC C-03 >
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001c2ca267a5
                    Extra: Last beacon: 104ms ago
          Cell 04 - Address: <MAC C-04 3:16>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=58/70  Signal level=-52 dBm  
                    Encryption key:on
                    ESSID:"3:16"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000032e1d012e7
                    Extra: Last beacon: 8ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC C-05 Torjan Virus>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"Torjan Virus"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001c2ca2618a
                    Extra: Last beacon: 108ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC C-06 >
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:off
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000032e1d5684d
                    Extra: Last beacon: 3472ms ago
          Cell 07 - Address: <MAC C-07 >
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=58/70  Signal level=-52 dBm  
                    Encryption key:off
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000032e1d56b5e
                    Extra: Last beacon: 3472ms ago
          Cell 08 - Address: <MAC C-08 >
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:off
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000032e1d56e6f
                    Extra: Last beacon: 3472ms ago
          Cell 09 - Address: <MAC C-09 MTNL>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=70/70  Signal level=-40 dBm  
                    Encryption key:on
                    ESSID:"MTNL"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000006b1faa40
                    Extra: Last beacon: 8ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK




blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci




modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


[rtl8192ce]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko
firmware:       rtlwifi/rtl8192cfwU_B.bin
firmware:       rtlwifi/rtl8192cfwU.bin
firmware:       rtlwifi/rtl8192cfw.bin
srcversion:     EF063698748457BBEDB4633
depends:        rtlwifi,rtl_pci,rtl8192c-common,mac80211
parm:           swenc:Set to 1 for software crypto (default 0)
parm:           ips:Set to 0 to not use link power save (default 1)
parm:           swlps:Set to 1 to use SW control power save (default 0)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
parm:           debug:Set debug level (0-5) (default 0) (int)


[rtl_pci]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
srcversion:     D5E4890DC428FA5A1BF92DF
depends:        mac80211,rtlwifi


[rtlwifi]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
srcversion:     E1F4663325225EE8DBA54CA
depends:        mac80211,cfg80211


[rtl8192c_common]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192c/rtl8192c-common.ko
srcversion:     32F826C623BC49F764F7974
depends:        


[mac80211]
filename:       /lib/modules/3.13.0-32-generic/kernel/net/mac80211/mac80211.ko
srcversion:     8ADA881D348148A3358334C
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/3.13.0-32-generic/kernel/net/wireless/cfg80211.ko
srcversion:     E786D076B61F97809B04B64
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)




udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~


# PCI device 0x8086:0x1502 (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x10ec:0x8176 (rtl8192ce)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"




Custom files/entries ~~~~~~~~~~~~~~~


/etc/modules        : Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Default


[/etc/modprobe.d]
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
mlx4.conf         : softdep mlx4_core post: mlx4_en




Kernel boot line ~~~~~~~~~~~~~~~~~~~


BOOT_IMAGE=/boot/vmlinuz-3.13.0-32-generic.efi.signed root=UUID=431f00a3-5771-4f83-81f7-5cf14c37a934 ro quiet splash vt.handoff=7




dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


[    0.479284] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.479548] audit: initializing netlink socket (disabled)
[    8.473642] wmi: Mapper loaded
[    8.575637] thinkpad_acpi: http://ibm-acpi.sf.net/
[    8.575674] rtl8192ce: Using firmware rtlwifi/rtl8192cfw.bin
[    8.650539] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[    8.650734] rtlwifi: wireless switch is on
[    8.756774] usb 1-1.4: Direct firmware load failed with error -2
[    8.763663] Bluetooth: can't load firmware, may not work correctly
[   11.459063] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   12.737717] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   12.738109] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   13.439597] psmouse serio2: trackpoint: IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   46.544537] wlan0: authenticate with <MAC C-02 DUGGALS>
[   46.564283] wlan0: send auth to <MAC C-02 DUGGALS> (try 1/3)
[   46.566816] wlan0: authenticated
[   46.567953] wlan0: associate with <MAC C-02 DUGGALS> (try 1/3)
[   46.571748] wlan0: RX AssocResp from <MAC C-02 DUGGALS> (capab=0x411 status=0 aid=2)
[   46.571871] wlan0: associated
[   46.571882] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   46.933527] IPv6: wlan0: IPv6 duplicate address fe80::ba76:3fff:fed0:e71c detected!
[   47.465434] IPv6: wlan0: IPv6 duplicate address fe80::ba76:3fff:fed0:e71c detected!
[   52.210025] wlan0: deauthenticating from <MAC C-02 DUGGALS> by local choice (reason=3)
[   57.057725] wlan0: authenticate with <MAC C-01 DUGGALS>
[   57.401763] wlan0: send auth to <MAC C-01 DUGGALS> (try 1/3)
[   57.403425] wlan0: authenticated
[   57.403544] rtl8192ce 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   57.403547] rtl8192ce 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   57.407025] wlan0: associate with <MAC C-01 DUGGALS> (try 1/3)
[   57.409160] wlan0: RX AssocResp from <MAC C-01 DUGGALS> (capab=0x411 status=0 aid=3)
[   57.409281] wlan0: associated
[   84.322404] wlan0: authenticate with <MAC C-02 DUGGALS>
[   84.332639] wlan0: send auth to <MAC C-02 DUGGALS> (try 1/3)
[   84.334154] wlan0: authenticated
[   84.335737] wlan0: associate with <MAC C-02 DUGGALS> (try 1/3)
[   84.344964] wlan0: RX AssocResp from <MAC C-02 DUGGALS> (capab=0x411 status=0 aid=2)
[   84.345116] wlan0: associated
[  127.363864] wlan0: authenticate with <MAC C-01 DUGGALS>
[  127.374035] wlan0: send auth to <MAC C-01 DUGGALS> (try 1/3)
[  127.380757] wlan0: authenticated
[  127.381053] rtl8192ce 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  127.381057] rtl8192ce 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  127.382459] wlan0: associate with <MAC C-01 DUGGALS> (try 1/3)
[  127.384898] wlan0: RX AssocResp from <MAC C-01 DUGGALS> (capab=0x411 status=0 aid=3)
[  127.385035] wlan0: associated


    ======== Done ========
```


Let me know if you need for information.

---

### Post by varunendra on 2014-07-20
No clues in the script output, but for nm-tool, try running it as root (for a test only) -
```
sudo nm-applet
```
Do you get the icon in the notification area (the top-right corner, where date, battery icon etc. are displayed)?

And what is the error that you get when running it normally from terminal - please post that.

To see permission and whether it is set to autostart at startup or not, please show us the output of -
```
ls -l /etc/xdg/autostart/nm-applet.desktop
cat /etc/xdg/autostart/nm-applet.desktop
```

Also, even though I know from our IRC chat that your user groups are okay, please post the following here too for the record -
```
id
```

**PS:**
Your current Access-Point in the wireless_script report is again using WPA/WPA2 mixed mode. This is not related to the current problem, but itself can cause connectivity or performance issues. It is highly recommended to use pure WPA2-PSK with AES. No mixed mode, no TKIP.

---

