---
title: "I have nearly given up hope"
date: 2016-06-22
forum: Networking &amp; Wireless
---

### Post by Vikram_Kumaran on 2016-06-22
Hi there, For the past few days I have been trying to get my AC 7260 to work with Ubuntu. And I keep failing every time. that is until I found a script that you guys said would help determine my problem. So I have taken the liberty of running that script on Ubuntu 16.04 and displaying the results here.
```

########## wireless info START ##########






Report from: 22 Jun 2016 15:07 CDT -0500






Booted last: 22 Jun 2016 00:00 CDT -0500






Script from: 26 May 2016 21:56 UTC +0000






##### release ###########################






Distributor ID:	Ubuntu


Description:	Ubuntu 16.04 LTS


Release:	16.04


Codename:	xenial






##### kernel ############################






Linux 4.4.0-21-generic #37-Ubuntu SMP Mon Apr 18 18:33:37 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux






Parameters: ro, quiet, splash, vt.handoff=7






##### desktop ###########################






Ubuntu






##### lspci #############################






09:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b1] (rev c3)


	Subsystem: Intel Corporation Dual Band Wireless-AC 7260 [8086:c070]


	Kernel driver in use: iwlwifi






##### lsusb #############################






Bus 002 Device 004: ID 0bc2:ab26 Seagate RSS LLC 


Bus 002 Device 003: ID 050d:0128 Belkin Components 


Bus 002 Device 002: ID 2109:0812 VIA Labs, Inc. VL812 Hub


Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub


Bus 001 Device 005: ID 04d9:0161 Holtek Semiconductor, Inc. 


Bus 001 Device 004: ID 1bcf:2c7d Sunplus Innovation Technology Inc. 


Bus 001 Device 003: ID 8087:07dc Intel Corp. 


Bus 001 Device 007: ID 04f3:2016 Elan Microelectronics Corp. 


Bus 001 Device 008: ID 12ba:0030 Licensed by Sony Computer Entertainment America 


Bus 001 Device 006: ID 2109:2812 VIA Labs, Inc. VL812 Hub


Bus 001 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver


Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub






##### PCMCIA card info ##################






##### rfkill ############################






0: acer-wireless: Wireless LAN


	Soft blocked: yes


	Hard blocked: no


1: phy0: Wireless LAN


	Soft blocked: no


	Hard blocked: no


2: hci0: Bluetooth


	Soft blocked: no


	Hard blocked: no






##### lsmod #############################






iwlmvm                311296  0


acer_wmi               20480  0


hp_wmi                 16384  0


sparse_keymap          16384  2 acer_wmi,hp_wmi


mac80211              737280  1 iwlmvm


snd_soc_rt5640        114688  0


iwlwifi               200704  1 iwlmvm


snd_soc_rl6231         16384  1 snd_soc_rt5640


snd_soc_core          212992  2 snd_soc_rt5640,snd_soc_ssm4567


cfg80211              565248  3 iwlwifi,mac80211,iwlmvm


snd_pcm               106496  8 


snd_soc_rt5640,snd_usb_audio,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_pcm_dmaengine,snd_hda_core


mxm_wmi                16384  1 nouveau


wmi                    20480  4 acer_wmi,hp_wmi,mxm_wmi,nouveau


video                  40960  3 i915,acer_wmi,nouveau






##### interfaces ########################






auto lo


iface lo inet loopback






##### ifconfig ##########################






wlp9s0    Link encap:Ethernet  HWaddr <MAC 'wlp9s0' [IF1]>  


          BROADCAST MULTICAST  MTU:1500  Metric:1


          RX packets:0 errors:0 dropped:0 overruns:0 frame:0


          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0


          collisions:0 txqueuelen:1000 


          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)






##### iwconfig ##########################






lo        no wireless extensions.






wlp9s0    IEEE 802.11abgn  ESSID:off/any  


          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   


          Retry short limit:7   RTS thr:off   Fragment thr:off


          Power Management:on


          






##### route #############################






Kernel IP routing table


Destination     Gateway         Genmask         Flags Metric Ref    Use Iface






##### resolv.conf #######################






##### network managers ##################






Installed:






	NetworkManager






Running:






root       806     1  0 15:04 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon






##### NetworkManager info ###############






GENERAL.DEVICE:                         wlp9s0


GENERAL.TYPE:                           wifi


GENERAL.NM-TYPE:                        NMDeviceWifi


GENERAL.VENDOR:                         Intel Corporation


GENERAL.PRODUCT:                        Wireless 7260 (Dual Band Wireless-AC 7260)


GENERAL.DRIVER:                         iwlwifi


GENERAL.DRIVER-VERSION:                 4.4.0-21-generic


GENERAL.FIRMWARE-VERSION:               16.242414.0


GENERAL.HWADDR:                         <MAC 'wlp9s0' [IF1]>


GENERAL.MTU:                            1500


GENERAL.STATE:                          20 (unavailable)


GENERAL.REASON:                         0 (No reason given)


GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.5/0000:09:00.0/net/
wlp9s0


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


WIFI-PROPERTIES.AP:                     yes


WIFI-PROPERTIES.ADHOC:                  yes


WIFI-PROPERTIES.2GHZ:                   yes


WIFI-PROPERTIES.5GHZ:                   yes


CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 






SSID  BSSID  MODE  CHAN  FREQ  RATE  SIGNAL  BARS  SECURITY  ACTIVE  * 






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






Region: America/Chicago (based on set time zone)






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






lo        no frequency information.






wlp9s0    32 channels in total; available frequencies :


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






wlp9s0    Interface doesn't support scanning : Network is down






lo        Interface doesn't support scanning.






##### module infos ######################






[iwlmvm]


filename:       /lib/modules/4.4.0-21-generic/kernel/drivers/net/wireless/iwlwifi/mvm/iwlmvm.ko


license:        GPL


author:         Copyright(c) 2003- 2015 Intel Corporation <ilw@linux.intel.com>


description:    The new Intel(R) wireless AGN driver for Linux


srcversion:     B01679C94B40E1E864F75F2


depends:        iwlwifi,mac80211,cfg80211


intree:         Y


vermagic:       4.4.0-21-generic SMP mod_unload modversions 


parm:           init_dbg:set to true to debug an ASSERT in INIT fw (default: false (bool)


parm:           power_scheme:power management scheme: 1-active, 2-balanced, 3-low power, default: 
2 (int)


parm:           tfd_q_hang_detect:TFD queues hang detection (default: true (bool)






[mac80211]


filename:       /lib/modules/4.4.0-21-generic/kernel/net/mac80211/mac80211.ko


license:        GPL


description:    IEEE 802.11 subsystem


srcversion:     A882F4FE63500846E1C859E


depends:        cfg80211


intree:         Y


vermagic:       4.4.0-21-generic SMP mod_unload modversions 


parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)


parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)


parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)


parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. 
(int)


parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting 
(reason 4). (int)


parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use 
(charp)






[iwlwifi]


filename:       /lib/modules/4.4.0-21-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko


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


srcversion:     ADE77491D89FDFCBEBF6E35


depends:        cfg80211


intree:         Y


vermagic:       4.4.0-21-generic SMP mod_unload modversions 


parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)


parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: 
disable agg RX, 8 enable agg TX (uint)


parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)


parm:           fw_restart:restart firmware in case of error (default true) (bool)


parm:           antenna_coupling:specify antenna coupling in dB (default: 0 dB) (int)


parm:           nvm_file:NVM file name (charp)


parm:           d0i3_disable:disable d0i3 functionality (default: Y) (bool)


parm:           lar_disable:disable LAR functionality (default: N) (bool)


parm:           uapsd_disable:disable U-APSD functionality (default: Y) (bool)


parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)


parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) 
(int)


parm:           power_save:enable WiFi power management (default: disable) (bool)


parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)


parm:           fw_monitor:firmware monitor - to debug FW (default: false - needs lots of memory) 
(bool)






[cfg80211]


filename:       /lib/modules/4.4.0-21-generic/kernel/net/wireless/cfg80211.ko


description:    wireless configuration support


license:        GPL


author:         Johannes Berg


srcversion:     00D8DA6D3B739DDD31FFF50


depends:        


intree:         Y


vermagic:       4.4.0-21-generic SMP mod_unload modversions 


parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)


parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)






##### module parameters #################






[iwlmvm]


init_dbg: N


power_scheme: 2


tfd_q_hang_detect: Y






[mac80211]


beacon_loss_count: 7


ieee80211_default_rc_algo: minstrel_ht


max_nullfunc_tries: 2


max_probe_tries: 5


minstrel_vht_only: Y


probe_wait_ms: 500






[iwlwifi]


11n_disable: 0


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






[/etc/modprobe.d/mlx4.conf]


softdep mlx4_core post: mlx4_en






##### rc.local ##########################






exit 0






##### pm-utils ##########################






##### udev rules ########################






##### dmesg #############################






[    4.920862] iwlwifi 0000:09:00.0: L1 Enabled - LTR Enabled (repeated 2 times)


[    4.935820] IPv6: ADDRCONF(NETDEV_UP): wlp9s0: link is not ready (repeated 2 times)


[   14.013756] iwlwifi 0000:09:00.0: L1 Enabled - LTR Enabled (repeated 4 times)


[   14.228863] IPv6: ADDRCONF(NETDEV_UP): wlp9s0: link is not ready (repeated 2 times)






########## wireless info END ############

```

Please see if you can make use of the information that I have provided.

---

### Post by wildmanne39 on 2016-06-22
Please do:
```
echo "blacklist acer-wmi" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Then reboot and if it does not connect run the script again and post a new file.
Thanks

---

### Post by Vikram_Kumaran on 2016-06-23
> **Wild Man said:**
> Please do:
```
echo "blacklist acer-wmi" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Then reboot and if it does not connect run the script again and post a new file.
Thanks

I am currently talking from ubuntu to let you know that it does in fact work. Thank you so much for your help man! If you don't mind me asking, what exactly was the problem.

---

### Post by wildmanne39 on 2016-06-23
That acer module that we removed is supposed to tell the system to turn on the wireless but it does not in many cases so you had what is called a softblock.
Glad it is working!

---

