---
title: "RealTek RTL8821AE w/ Ubuntu 14.10 disconnect issues on heavy load"
date: 2014-12-12
forum: Networking &amp; Wireless
---

### Post by castor_fou on 2014-12-12
I use an Asus Transofrmer Book TX201LA.

And since beginning I am annoyed by wireless driver.

Here is the ouput of wireless_script :

```

	======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

transformer 3.16.0-28-generic x86_64,  Ubuntu 14.10, utopic

CPU    : Intel(R) Core(TM) i5-4200U CPU @ 1.60GHz
Memory : 3836 MB
Uptime : 00:21:15 up 27 min,  2 users,  load average: 1,19, 0,73, 0,72


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8821AE 802.11ac PCIe Wireless Network Adapter [10ec:8821]
	Subsystem: AzureWave Device [1a3b:2161]
	Kernel driver in use: rtl8821ae


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 04f2:b3ff Chicony Electronics Co., Ltd 
Bus 001 Device 006: ID 0b05:561f ASUSTek Computer, Inc. 
Bus 001 Device 003: ID 03eb:8c0c Atmel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11abgn  ESSID:"faidherbe_EXT"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC C-01 faidherbe_EXT>   
          Bit Rate=6.5 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=57/70  Signal level=-53 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface               Soft blocked  Hard blocked
2: asus-wlan: Wireless LAN        no            no
3: asus-bluetooth: Bluetooth      yes           no
7: phy4: Wireless LAN             no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

rtl8821ae             558952  0 
asus_nb_wmi            16990  0 
asus_wmi               24094  1 asus_nb_wmi
sparse_keymap          13948  1 asus_wmi
snd_soc_rt5640         93042  0 
snd_soc_rl6231         13037  1 snd_soc_rt5640
snd_soc_core          200108  1 snd_soc_rt5640
mac80211              660592  1 rtl8821ae
snd_pcm               104102  7 snd_soc_rt5640,snd_soc_core,snd_hda_codec_hdmi,snd  _hda_codec,snd_hda_intel,snd_hda_controller,snd_pc  m_dmaengine
cfg80211              510218  2 mac80211,rtl8821ae
wmi                    19193  1 asus_wmi
video                  20128  2 i915,asus_wmi


module parameters ~~~~~~~~~~~~~~~~~~

asus_nb_wmi   (1): wapf=0
cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
rtl8821ae     (4): fwlps=N | ips=N | swenc=N | swlps=N
snd_pcm       (2): maximum_substreams=4 | preallocate_dma=1
video         (3): allow_duplicates=N | brightness_switch_enabled=Y | use_native_backlight=-1
wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
========================o=============o===========  o===========o=========o===========o==============o  ===========
 Interface & ID         | Type        | Driver    | State     | Default | Speed     | Support      | HW Addr   
========================o=============o===========  o===========o=========o===========o==============o  ===========
 wlan0  [faidherbe_EXT] | 802.11 WiFi | rtl8821ae | connected | yes     | 6 Mb/s    | WEP/WPA/WPA2 | <MAC wlan0>

    faidherbe:       Infra, <MAC C-02 faidherbe>, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WPA2
    faidherbe5ghz:   Infra, <MAC C-04 faidherbe5ghz>, Freq 5240 MHz, Rate 54 Mb/s, Strength 50 WPA2
    invite:          Infra, <MAC C-03 invite>, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WEP
    *faidherbe_EXT:  Infra, <MAC C-01 faidherbe_EXT>, Freq 2412 MHz, Rate 54 Mb/s, Strength 67 WPA2

    Address:         192.168.1.37
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1
    DNS:             192.168.1.1
------------------------+-------------+-----------+-----------+---------+-----------+--------------+-----------


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

faidherbe            : ssid=faidherbe | autoconnect=false | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
faidherbe5ghz        : ssid=faidherbe5ghz | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
faidherbe_EXT        : ssid=faidherbe_EXT | autoconnect=false | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
les vallons          : ssid=les vallons | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 127.0.1.1


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Table de routage IP du noyau
Destination     Passerelle      Genmask         Indic Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

--- 192.168.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1002ms
rtt min/avg/max/mdev = 3.942/3.950/3.958/0.008 ms

--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.021/0.023/0.026/0.005 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "fr_FR.UTF-8")
country 00: DFS-UNSET
	(2402 - 2472 @ 40), (3, 20)
	(2457 - 2482 @ 40), (3, 20), NO-IR
	(2474 - 2494 @ 20), (3, 20), NO-OFDM, NO-IR
	(5170 - 5250 @ 40), (3, 20), NO-IR
	(5735 - 5835 @ 40), (3, 20), NO-IR


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     24 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 11 (2.462 GHz)
          Channel 36 (5.18 GHz)
          Channel 40 (5.2 GHz)
          Channel 44 (5.22 GHz)
          Channel 48 (5.24 GHz)
          Channel 52 (5.26 GHz)
          Channel 56 (5.28 GHz)
          Channel 60 (5.3 GHz)
          Channel 64 (5.32 GHz)
          Channel 149 (5.745 GHz)
          Channel 153 (5.765 GHz)
          Channel 157 (5.785 GHz)
          Channel 161 (5.805 GHz)
          Channel 165 (5.825 GHz)

          Current Frequency:2.412 GHz (Channel 1)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 faidherbe_EXT>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-38 dBm  
                    Encryption key:on
                    ESSID:"faidherbe_EXT"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001f927d095f4
                    Extra: Last beacon: 12ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC C-02 faidherbe>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-40 dBm  
                    Encryption key:on
                    ESSID:"faidherbe"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=640001f9731a49a4
                    Extra: Last beacon: 12ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC C-03 invite>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-40 dBm  
                    Encryption key:on
                    ESSID:"invite"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001f9731a5e87
                    Extra: Last beacon: 12ms ago
          Cell 04 - Address: <MAC C-04 faidherbe5ghz>
                    Channel:48
                    Frequency:5.24 GHz (Channel 48)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:on
                    ESSID:"faidherbe5ghz"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001f92967b03b
                    Extra: Last beacon: 3360ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK


blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[rtl8821ae]
filename:       /lib/modules/3.16.0-28-generic/kernel/drivers/staging/rtl8821ae/rtl8821ae.ko
firmware:       rtlwifi/rtl8821aefw.bin
srcversion:     EA439BC895EA5691716AF12
depends:        mac80211,cfg80211
parm:           swlps:bool
parm:           swenc:using hardware crypto (default 0 [hardware])
parm:           ips:using no link power save (default 1 is open)
parm:           fwlps:using linked fw control power save (default 1 is open)

[asus_nb_wmi]
filename:       /lib/modules/3.16.0-28-generic/kernel/drivers/platform/x86/asus-nb-wmi.ko
srcversion:     AE4F09ABD125394483A12C3
depends:        asus-wmi
parm:           wapf:WAPF value (uint)

[asus_wmi]
filename:       /lib/modules/3.16.0-28-generic/kernel/drivers/platform/x86/asus-wmi.ko
srcversion:     B5FEEAA49A8BE4D7FB6ABFD
depends:        sparse-keymap,wmi,video

[snd_soc_rt5640]
filename:       /lib/modules/3.16.0-28-generic/kernel/sound/soc/codecs/snd-soc-rt5640.ko
srcversion:     D9784021D8C822AC71D3297
depends:        snd-pcm,snd-soc-core,snd-soc-rl6231

[snd_soc_rl6231]
filename:       /lib/modules/3.16.0-28-generic/kernel/sound/soc/codecs/snd-soc-rl6231.ko
srcversion:     A9A4828818D1BE4F6603399
depends:        

[snd_soc_core]
filename:       /lib/modules/3.16.0-28-generic/kernel/sound/soc/snd-soc-core.ko
srcversion:     6393C3936E8F0C0753D28D3
depends:        snd-pcm,snd-pcm-dmaengine,snd,snd-compress
parm:           pmdown_time:DAPM stream powerdown time (msecs) (int)

[mac80211]
filename:       /lib/modules/3.16.0-28-generic/kernel/net/mac80211/mac80211.ko
srcversion:     BEA0C6DE6572AE84C25CD77
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[snd_pcm]
filename:       /lib/modules/3.16.0-28-generic/kernel/sound/core/snd-pcm.ko
srcversion:     CAFAB0DF7563356E447F07C
depends:        snd,snd-timer
parm:           preallocate_dma:Preallocate DMA memory when the PCM devices are initialized. (int)
parm:           maximum_substreams:Maximum substreams with preallocated DMA memory. (int)

[cfg80211]
filename:       /lib/modules/3.16.0-28-generic/kernel/net/wireless/cfg80211.ko
srcversion:     DEE8EAA48495E392CD51C2D
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[wmi]
filename:       /lib/modules/3.16.0-28-generic/kernel/drivers/platform/x86/wmi.ko
srcversion:     347CF30B94B5549A75865A8
depends:        
parm:           debug_event:Log WMI Events [0/1] (bool)
parm:           debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)

[video]
filename:       /lib/modules/3.16.0-28-generic/kernel/drivers/acpi/video.ko
srcversion:     032E6FC754C61ECF3067301
depends:        
parm:           brightness_switch_enabled:bool
parm:           allow_duplicates:bool
parm:           use_native_backlight:int


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x10ec:0x8821 (rtl8821ae)
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
modesetting.conf  : options cirrus modeset=1
                    options mgag200 modeset=1
modprobe.conf     : options rtl8192ce ips=1
                    options rtl8192ce fwlps=0
                    options rtl8192ce swenc=1


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/boot/vmlinuz-3.16.0-28-generic.efi.signed root=UUID=bfdc6176-d88e-4568-ad59-eb7e4993131a ro quiet splash acpi_osi= vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[   20.327606] rtl8821ae-0:rtl_op_set_key():<0-0> alg:CCMP
[   20.327608] rtl8821ae-0:rtl_op_set_key():<0-0> disable key delete one entry
[   20.327610] rtl8821ae-0:rtl_cam_delete_one_entry():<0-0> key_idx:2
[   20.327618] rtl8821ae-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A4: 0 
[   20.327619] rtl8821ae-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A0: 80010010 
[   20.412444] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[   21.027158] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[   22.430663] wlan0: authenticate with <MAC C-04 faidherbe5ghz>
[   22.430957] rtl8821ae-0:rtl_op_bss_info_changed():<0-0> bssid: <MAC C-04 faidherbe5ghz>
[   22.431016] wlan0: send auth to <MAC C-04 faidherbe5ghz> (try 1/3)
[   22.431023] rtl8821ae-0:rtl_tx_mgmt_proc():<200-1> MAC80211_LINKING
[   22.432722] wlan0: authenticated
[   22.434291] wlan0: associate with <MAC C-04 faidherbe5ghz> (try 1/3)
[   22.436083] wlan0: RX AssocResp from <MAC C-04 faidherbe5ghz> (capab=0x411 status=0 aid=1)
[   22.436091] rtl8821ae-0:rtl_op_sta_add():<0-0> Add sta addr is <MAC C-04 faidherbe5ghz>
[   22.436093] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> ratr_bitmap :ff000
[   22.436095] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> Rate_index:0, ratr_val:ff000, 0:81:1:0:f0:f:0
[   22.436127] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> ratr_bitmap :ff000
[   22.436128] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> Rate_index:0, ratr_val:ff000, 0:81:1:0:f0:f:0
[   22.436149] rtl8821ae-0:rtl_op_bss_info_changed():<0-0> BSS_CHANGED_ASSOC
[   22.436163] rtl8821ae-0:rtl8821ae_set_hw_reg():<0-0> switch case not process 5c
[   22.436182] rtl8821ae: 
[   22.436184] rtl8821ae_set_fw_rsvdpagepkt(): HW_VAR_SET_TX_CMD: ALL 
[   22.436190] rtl8821ae: 
[   22.436239] wlan0: associated
[   22.469771] rtl8821ae-0:rtl_is_special_data():<10000-1> 802.1X Rx EAPOL pkt!!
[   24.305400] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off for 2 s
[   26.709721] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off for 4 s
[   28.311171] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off for 6 s
[   30.313988] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off for 8 s
[   32.316941] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off for 10 s
[   32.316946] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off, try to reconnect now
[   32.316962] wlan0: Connection to AP <MAC C-04 faidherbe5ghz> lost
[   32.324976] rtl8821ae-0:rtl_op_sta_remove():<0-0> Remove sta addr is <MAC C-04 faidherbe5ghz>
[   32.325044] rtl8821ae-0:rtl_op_bss_info_changed():<0-0> BSS_CHANGED_UN_ASSOC
[   32.325071] rtl8821ae-0:rtl_op_bss_info_changed():<0-0> bssid: <MAC ID removed>
[   59.799743] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[   60.417222] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[   62.973868] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[   63.587472] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[   67.661024] wlan0: authenticate with <MAC C-01 faidherbe_EXT>
[   67.661049] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[   67.661396] rtl8821ae-0:rtl_op_bss_info_changed():<0-0> bssid: <MAC C-01 faidherbe_EXT>
[   67.661470] wlan0: send auth to <MAC C-01 faidherbe_EXT> (try 1/3)
[   67.661479] rtl8821ae-0:rtl_tx_mgmt_proc():<200-1> MAC80211_LINKING
[   67.664060] wlan0: authenticated
[   67.665168] wlan0: associate with <MAC C-01 faidherbe_EXT> (try 1/3)
[   67.668433] wlan0: RX AssocResp from <MAC C-01 faidherbe_EXT> (capab=0x411 status=0 aid=3)
[   67.668444] rtl8821ae-0:rtl_op_sta_add():<0-0> Add sta addr is <MAC C-01 faidherbe_EXT>
[   67.668448] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> ratr_bitmap :ff005
[   67.668451] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> Rate_index:0, ratr_val:ff005, 0:81:0:5:f0:f:0
[   67.668485] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> ratr_bitmap :ff005
[   67.668488] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> Rate_index:0, ratr_val:ff005, 0:81:0:5:f0:f:0
[   67.668510] rtl8821ae-0:rtl_op_bss_info_changed():<0-0> BSS_CHANGED_ASSOC
[   67.668526] rtl8821ae-0:rtl8821ae_set_hw_reg():<0-0> switch case not process 5c
[   67.668547] rtl8821ae: 
[   67.668551] rtl8821ae_set_fw_rsvdpagepkt(): HW_VAR_SET_TX_CMD: ALL 
[   67.668559] rtl8821ae: 
[   67.668611] wlan0: associated
[   67.676749] rtl8821ae-0:rtl_is_special_data():<10000-1> 802.1X Rx EAPOL pkt!!
[   67.686964] rtl8821ae-0:rtl_is_special_data():<10000-1> 802.1X Rx EAPOL pkt!!
[   67.687238] rtl8821ae-0:rtl_op_set_key():<0-0> Using hardware based encryption for keyidx: 0, mac: <MAC C-01 faidherbe_EXT>
[   67.687243] rtl8821ae-0:rtl_op_set_key():<0-0> alg:CCMP
[   67.687245] rtl8821ae-0:rtl_op_set_key():<0-0> set enable_hw_sec, key_type:4(OPEN:0 WEP40:1 TKIP:2 AES:4 WEP104:5)
[   67.687248] rtl8821ae-0:rtl8821ae_enable_hw_security_config():<0-0> PairwiseEncAlgorithm = 4 GroupEncAlgorithm = 0
[   67.687255] rtl8821ae-0:rtl8821ae_enable_hw_security_config():<0-0> The SECR-value cc 
[   67.687259] rtl8821ae-0:rtl_op_set_key():<0-0> set pairwise key
[   67.687261] rtl8821ae-0:rtl8821ae_set_key():<0-0> add one entry
[   67.687263] rtl8821ae-0:rtl8821ae_set_key():<0-0> set Pairwiase key
[   67.687265] rtl8821ae-0:rtl_cam_add_one_entry():<0-0> EntryNo:4, ulKeyId=0, ulEncAlg=4, ulUseDK=0 MacAddr <MAC C-01 faidherbe_EXT>
[   67.687267] rtl8821ae: 
[   67.687915] rtl8821ae-0:rtl_cam_add_one_entry():<0-0> end 
[   67.688046] rtl8821ae-0:rtl_op_set_key():<0-0> Using hardware based encryption for keyidx: 1, mac: <MAC ID removed>
[   67.688050] rtl8821ae-0:rtl_op_set_key():<0-0> alg:CCMP
[   67.688053] rtl8821ae-0:rtl_op_set_key():<0-0> set group key
[   67.688055] rtl8821ae-0:rtl8821ae_set_key():<0-0> add one entry
[   67.688058] rtl8821ae-0:rtl8821ae_set_key():<0-0> set group key
[   67.688060] rtl8821ae-0:rtl_cam_add_one_entry():<0-0> EntryNo:1, ulKeyId=1, ulEncAlg=4, ulUseDK=0 MacAddr <MAC ID removed>
[   67.688063] rtl8821ae: 
[   67.688713] rtl8821ae-0:rtl_cam_add_one_entry():<0-0> end 
[   67.737196] rtl8821ae-0:rtl_tx_agg_start():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0 seq:2
[   67.737223] rtl8821ae-0:rtl_action_proc():<200-1> Tx ACT_ADDBAREQ From :<MAC wlan0>
[   67.737227] rtl8821ae: 
[   67.739241] rtl8821ae-0:rtl_action_proc():<10000-1> Rx ACT_ADDBARSP From :<MAC C-01 faidherbe_EXT>
[   67.739294] rtl8821ae-0:rtl_tx_agg_oper():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0
[   71.999913] rtl8821ae-0:rtl_action_proc():<10000-1> Rx ACT_ADDBAREQ From :<MAC C-01 faidherbe_EXT>
[   71.999921] rtl8821ae: 
[   72.000014] rtl8821ae-0:rtl_rx_agg_start():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0 seq:19
[   72.000041] rtl8821ae-0:rtl_action_proc():<200-1> Tx ACT_ADDBARSP From :<MAC wlan0>
[   72.378626] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> ratr_bitmap :f0000
[   72.378631] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> Rate_index:0, ratr_val:f0000, 0:81:0:0:0:f:0
[   89.490018] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[   89.596277] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[   89.857765] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[   89.963911] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[   90.225325] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[   90.331544] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[   90.592931] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[   90.647252] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[   90.908630] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[   91.014836] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[   91.276247] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[   91.382432] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[   91.643835] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[   91.750076] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[   92.011435] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[   92.117681] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[   92.378996] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[   92.485299] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[   92.746653] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[   92.852921] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[   93.114250] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[   93.220510] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[   93.481825] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[   93.588119] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[   93.849416] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[   93.955837] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[   96.405138] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off for 2 s
[   98.407079] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off for 4 s
[  100.408951] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off for 6 s
[  102.410800] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off for 8 s
[  104.412720] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off for 10 s
[  104.412725] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off, try to reconnect now
[  104.412758] wlan0: Connection to AP <MAC C-01 faidherbe_EXT> lost
[  104.420635] rtl8821ae-0:rtl_tx_agg_stop():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0
[  104.420648] rtl8821ae-0:rtl_rx_agg_stop():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0
[  104.440664] rtl8821ae-0:rtl_op_set_key():<0-0> Disabling hardware based encryption for keyidx: 0, mac: <MAC C-01 faidherbe_EXT>
[  104.440670] rtl8821ae-0:rtl_op_set_key():<0-0> alg:CCMP
[  104.440673] rtl8821ae-0:rtl_op_set_key():<0-0> set enable_hw_sec, key_type:4(OPEN:0 WEP40:1 TKIP:2 AES:4 WEP104:5)
[  104.440675] rtl8821ae-0:rtl8821ae_enable_hw_security_config():<0-0> PairwiseEncAlgorithm = 4 GroupEncAlgorithm = 4
[  104.440683] rtl8821ae-0:rtl8821ae_enable_hw_security_config():<0-0> The SECR-value cc 
[  104.440687] rtl8821ae-0:rtl_op_set_key():<0-0> disable key delete one entry
[  104.440689] rtl8821ae-0:rtl_cam_delete_one_entry():<0-0> key_idx:0
[  104.440695] rtl8821ae-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A4: 0 
[  104.440697] rtl8821ae-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A0: 80010000 
[  104.440733] rtl8821ae-0:rtl_op_sta_remove():<0-0> Remove sta addr is <MAC C-01 faidherbe_EXT>
[  104.440803] rtl8821ae-0:rtl_op_bss_info_changed():<0-0> BSS_CHANGED_UN_ASSOC
[  104.440830] rtl8821ae-0:rtl_op_bss_info_changed():<0-0> bssid: <MAC ID removed>
[  104.456643] rtl8821ae-0:rtl_op_set_key():<0-0> Disabling hardware based encryption for keyidx: 1, mac: <MAC ID removed>
[  104.456649] rtl8821ae-0:rtl_op_set_key():<0-0> alg:CCMP
[  104.456651] rtl8821ae-0:rtl_op_set_key():<0-0> disable key delete one entry
[  104.456654] rtl8821ae-0:rtl_cam_delete_one_entry():<0-0> key_idx:1
[  104.456662] rtl8821ae-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A4: 0 
[  104.456664] rtl8821ae-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A0: 80010008 
[  105.155922] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  106.558471] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  106.559252] wlan0: authenticate with <MAC C-01 faidherbe_EXT>
[  106.559597] rtl8821ae-0:rtl_op_bss_info_changed():<0-0> bssid: <MAC C-01 faidherbe_EXT>
[  106.559723] wlan0: send auth to <MAC C-01 faidherbe_EXT> (try 1/3)
[  106.559741] rtl8821ae-0:rtl_tx_mgmt_proc():<200-1> MAC80211_LINKING
[  106.561331] wlan0: authenticated
[  106.562404] wlan0: associate with <MAC C-01 faidherbe_EXT> (try 1/3)
[  106.565719] wlan0: RX AssocResp from <MAC C-01 faidherbe_EXT> (capab=0x411 status=0 aid=3)
[  106.565733] rtl8821ae-0:rtl_op_sta_add():<0-0> Add sta addr is <MAC C-01 faidherbe_EXT>
[  106.565737] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> ratr_bitmap :ff005
[  106.565740] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> Rate_index:0, ratr_val:ff005, 0:81:0:5:f0:f:0
[  106.565776] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> ratr_bitmap :ff005
[  106.565779] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> Rate_index:0, ratr_val:ff005, 0:81:0:5:f0:f:0
[  106.565802] rtl8821ae-0:rtl_op_bss_info_changed():<0-0> BSS_CHANGED_ASSOC
[  106.565817] rtl8821ae-0:rtl8821ae_set_hw_reg():<0-0> switch case not process 5c
[  106.565839] rtl8821ae: 
[  106.565842] rtl8821ae_set_fw_rsvdpagepkt(): HW_VAR_SET_TX_CMD: ALL 
[  106.565852] rtl8821ae: 
[  106.565907] wlan0: associated
[  106.577518] rtl8821ae-0:rtl_is_special_data():<10000-1> 802.1X Rx EAPOL pkt!!
[  106.587529] rtl8821ae-0:rtl_is_special_data():<10000-1> 802.1X Rx EAPOL pkt!!
[  106.587822] rtl8821ae-0:rtl_op_set_key():<0-0> Using hardware based encryption for keyidx: 0, mac: <MAC C-01 faidherbe_EXT>
[  106.587828] rtl8821ae-0:rtl_op_set_key():<0-0> alg:CCMP
[  106.587830] rtl8821ae-0:rtl_op_set_key():<0-0> set enable_hw_sec, key_type:4(OPEN:0 WEP40:1 TKIP:2 AES:4 WEP104:5)
[  106.587832] rtl8821ae-0:rtl8821ae_enable_hw_security_config():<0-0> PairwiseEncAlgorithm = 4 GroupEncAlgorithm = 0
[  106.587839] rtl8821ae-0:rtl8821ae_enable_hw_security_config():<0-0> The SECR-value cc 
[  106.587843] rtl8821ae-0:rtl_op_set_key():<0-0> set pairwise key
[  106.587846] rtl8821ae-0:rtl8821ae_set_key():<0-0> add one entry
[  106.587847] rtl8821ae-0:rtl8821ae_set_key():<0-0> set Pairwiase key
[  106.587849] rtl8821ae-0:rtl_cam_add_one_entry():<0-0> EntryNo:4, ulKeyId=0, ulEncAlg=4, ulUseDK=0 MacAddr <MAC C-01 faidherbe_EXT>
[  106.587852] rtl8821ae: 
[  106.588498] rtl8821ae-0:rtl_cam_add_one_entry():<0-0> end 
[  106.588615] rtl8821ae-0:rtl_op_set_key():<0-0> Using hardware based encryption for keyidx: 1, mac: <MAC ID removed>
[  106.588618] rtl8821ae-0:rtl_op_set_key():<0-0> alg:CCMP
[  106.588620] rtl8821ae-0:rtl_op_set_key():<0-0> set group key
[  106.588622] rtl8821ae-0:rtl8821ae_set_key():<0-0> add one entry
[  106.588623] rtl8821ae-0:rtl8821ae_set_key():<0-0> set group key
[  106.588625] rtl8821ae-0:rtl_cam_add_one_entry():<0-0> EntryNo:1, ulKeyId=1, ulEncAlg=4, ulUseDK=0 MacAddr <MAC ID removed>
[  106.588627] rtl8821ae: 
[  106.589272] rtl8821ae-0:rtl_cam_add_one_entry():<0-0> end 
[  106.590524] rtl8821ae-0:rtl_action_proc():<10000-1> Rx ACT_ADDBAREQ From :<MAC C-01 faidherbe_EXT>
[  106.590528] rtl8821ae: 
[  106.590621] rtl8821ae-0:rtl_rx_agg_start():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0 seq:0
[  106.590630] rtl8821ae-0:rtl_action_proc():<200-1> Tx ACT_ADDBARSP From :<MAC wlan0>
[  106.630429] rtl8821ae-0:rtl_tx_agg_start():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0 seq:1
[  106.630451] rtl8821ae-0:rtl_action_proc():<200-1> Tx ACT_ADDBAREQ From :<MAC wlan0>
[  106.630454] rtl8821ae: 
[  106.631974] rtl8821ae-0:rtl_action_proc():<10000-1> Rx ACT_ADDBARSP From :<MAC C-01 faidherbe_EXT>
[  106.632016] rtl8821ae-0:rtl_tx_agg_oper():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0
[  114.426141] rtl8821ae-0:rtl_tx_agg_stop():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0
[  114.426172] rtl8821ae-0:rtl_action_proc():<400-1> ACT_ADDBADEL From :<MAC wlan0>
[  115.684759] rtl8821ae-0:rtl_tx_agg_start():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0 seq:13
[  115.684778] rtl8821ae-0:rtl_action_proc():<200-1> Tx ACT_ADDBAREQ From :<MAC wlan0>
[  115.684780] rtl8821ae: 
[  115.686241] rtl8821ae-0:rtl_action_proc():<10000-1> Rx ACT_ADDBARSP From :<MAC C-01 faidherbe_EXT>
[  115.686273] rtl8821ae-0:rtl_tx_agg_oper():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0
[  132.448687] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  132.554966] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  132.816358] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  132.922554] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  133.183948] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  133.290116] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  133.551547] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  133.605813] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  133.867213] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  133.973418] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  134.234802] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  134.341080] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  134.602363] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  134.708727] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  134.969996] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  135.076361] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  135.337665] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  135.443983] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  135.705266] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  135.811578] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  136.072843] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  136.179160] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  136.440485] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  136.546751] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  136.808111] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  136.914312] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  140.446695] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off for 2 s
[  142.448583] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off for 4 s
[  144.450446] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off for 6 s
[  146.452380] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off for 8 s
[  148.454163] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off for 10 s
[  148.454167] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off, try to reconnect now
[  148.454181] wlan0: Connection to AP <MAC C-01 faidherbe_EXT> lost
[  148.462188] rtl8821ae-0:rtl_tx_agg_stop():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0
[  148.462205] rtl8821ae-0:rtl_rx_agg_stop():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0
[  148.474180] rtl8821ae-0:rtl_op_set_key():<0-0> Disabling hardware based encryption for keyidx: 0, mac: <MAC C-01 faidherbe_EXT>
[  148.474188] rtl8821ae-0:rtl_op_set_key():<0-0> alg:CCMP
[  148.474190] rtl8821ae-0:rtl_op_set_key():<0-0> set enable_hw_sec, key_type:4(OPEN:0 WEP40:1 TKIP:2 AES:4 WEP104:5)
[  148.474192] rtl8821ae-0:rtl8821ae_enable_hw_security_config():<0-0> PairwiseEncAlgorithm = 4 GroupEncAlgorithm = 4
[  148.474200] rtl8821ae-0:rtl8821ae_enable_hw_security_config():<0-0> The SECR-value cc 
[  148.474204] rtl8821ae-0:rtl_op_set_key():<0-0> disable key delete one entry
[  148.474207] rtl8821ae-0:rtl_cam_delete_one_entry():<0-0> key_idx:0
[  148.474212] rtl8821ae-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A4: 0 
[  148.474214] rtl8821ae-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A0: 80010000 
[  148.474250] rtl8821ae-0:rtl_op_sta_remove():<0-0> Remove sta addr is <MAC C-01 faidherbe_EXT>
[  148.474320] rtl8821ae-0:rtl_op_bss_info_changed():<0-0> BSS_CHANGED_UN_ASSOC
[  148.474346] rtl8821ae-0:rtl_op_bss_info_changed():<0-0> bssid: <MAC ID removed>
[  148.490243] rtl8821ae-0:rtl_op_set_key():<0-0> Disabling hardware based encryption for keyidx: 1, mac: <MAC ID removed>
[  148.490249] rtl8821ae-0:rtl_op_set_key():<0-0> alg:CCMP
[  148.490251] rtl8821ae-0:rtl_op_set_key():<0-0> disable key delete one entry
[  148.490253] rtl8821ae-0:rtl_cam_delete_one_entry():<0-0> key_idx:1
[  148.490261] rtl8821ae-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A4: 0 
[  148.490263] rtl8821ae-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A0: 80010008 
[  149.189317] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  150.591954] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  150.592537] wlan0: authenticate with <MAC C-01 faidherbe_EXT>
[  150.592872] rtl8821ae-0:rtl_op_bss_info_changed():<0-0> bssid: <MAC C-01 faidherbe_EXT>
[  150.592984] wlan0: send auth to <MAC C-01 faidherbe_EXT> (try 1/3)
[  150.593012] rtl8821ae-0:rtl_tx_mgmt_proc():<200-1> MAC80211_LINKING
[  150.596138] wlan0: authenticated
[  150.599966] wlan0: associate with <MAC C-01 faidherbe_EXT> (try 1/3)
[  150.603041] wlan0: RX AssocResp from <MAC C-01 faidherbe_EXT> (capab=0x411 status=0 aid=3)
[  150.603058] rtl8821ae-0:rtl_op_sta_add():<0-0> Add sta addr is <MAC C-01 faidherbe_EXT>
[  150.603065] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> ratr_bitmap :ff005
[  150.603069] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> Rate_index:0, ratr_val:ff005, 0:81:0:5:f0:f:0
[  150.603108] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> ratr_bitmap :ff005
[  150.603112] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> Rate_index:0, ratr_val:ff005, 0:81:0:5:f0:f:0
[  150.603138] rtl8821ae-0:rtl_op_bss_info_changed():<0-0> BSS_CHANGED_ASSOC
[  150.603155] rtl8821ae-0:rtl8821ae_set_hw_reg():<0-0> switch case not process 5c
[  150.603178] rtl8821ae: 
[  150.603184] rtl8821ae_set_fw_rsvdpagepkt(): HW_VAR_SET_TX_CMD: ALL 
[  150.603196] rtl8821ae: 
[  150.603254] wlan0: associated
[  150.616255] rtl8821ae-0:rtl_is_special_data():<10000-1> 802.1X Rx EAPOL pkt!!
[  150.626156] rtl8821ae-0:rtl_is_special_data():<10000-1> 802.1X Rx EAPOL pkt!!
[  150.626464] rtl8821ae-0:rtl_op_set_key():<0-0> Using hardware based encryption for keyidx: 0, mac: <MAC C-01 faidherbe_EXT>
[  150.626470] rtl8821ae-0:rtl_op_set_key():<0-0> alg:CCMP
[  150.626472] rtl8821ae-0:rtl_op_set_key():<0-0> set enable_hw_sec, key_type:4(OPEN:0 WEP40:1 TKIP:2 AES:4 WEP104:5)
[  150.626474] rtl8821ae-0:rtl8821ae_enable_hw_security_config():<0-0> PairwiseEncAlgorithm = 4 GroupEncAlgorithm = 0
[  150.626482] rtl8821ae-0:rtl8821ae_enable_hw_security_config():<0-0> The SECR-value cc 
[  150.626488] rtl8821ae-0:rtl_op_set_key():<0-0> set pairwise key
[  150.626491] rtl8821ae-0:rtl8821ae_set_key():<0-0> add one entry
[  150.626493] rtl8821ae-0:rtl8821ae_set_key():<0-0> set Pairwiase key
[  150.626496] rtl8821ae-0:rtl_cam_add_one_entry():<0-0> EntryNo:4, ulKeyId=0, ulEncAlg=4, ulUseDK=0 MacAddr <MAC C-01 faidherbe_EXT>
[  150.626500] rtl8821ae: 
[  150.627154] rtl8821ae-0:rtl_cam_add_one_entry():<0-0> end 
[  150.627273] rtl8821ae-0:rtl_op_set_key():<0-0> Using hardware based encryption for keyidx: 1, mac: <MAC ID removed>
[  150.627276] rtl8821ae-0:rtl_op_set_key():<0-0> alg:CCMP
[  150.627278] rtl8821ae-0:rtl_op_set_key():<0-0> set group key
[  150.627280] rtl8821ae-0:rtl8821ae_set_key():<0-0> add one entry
[  150.627282] rtl8821ae-0:rtl8821ae_set_key():<0-0> set group key
[  150.627284] rtl8821ae-0:rtl_cam_add_one_entry():<0-0> EntryNo:1, ulKeyId=1, ulEncAlg=4, ulUseDK=0 MacAddr <MAC ID removed>
[  150.627286] rtl8821ae: 
[  150.627932] rtl8821ae-0:rtl_cam_add_one_entry():<0-0> end 
[  150.819650] rtl8821ae-0:rtl_tx_agg_start():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0 seq:1
[  150.819665] rtl8821ae-0:rtl_action_proc():<200-1> Tx ACT_ADDBAREQ From :<MAC wlan0>
[  150.819668] rtl8821ae: 
[  150.821374] rtl8821ae-0:rtl_action_proc():<10000-1> Rx ACT_ADDBARSP From :<MAC C-01 faidherbe_EXT>
[  150.821414] rtl8821ae-0:rtl_tx_agg_oper():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0
[  151.642598] rtl8821ae-0:rtl_action_proc():<10000-1> Rx ACT_ADDBAREQ From :<MAC C-01 faidherbe_EXT>
[  151.642604] rtl8821ae: 
[  151.642682] rtl8821ae-0:rtl_rx_agg_start():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0 seq:8
[  151.642694] rtl8821ae-0:rtl_action_proc():<200-1> Tx ACT_ADDBARSP From :<MAC wlan0>
[  170.474974] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> ratr_bitmap :ff000
[  170.474983] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> Rate_index:0, ratr_val:ff000, 0:81:0:0:f0:f:0
[  172.476929] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> ratr_bitmap :f0000
[  172.476935] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> Rate_index:0, ratr_val:f0000, 0:81:0:0:0:f:0
[  195.378249] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  195.484427] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  195.745794] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  195.852027] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  196.113454] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  196.219727] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  196.481037] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  196.535372] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  196.796747] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  196.903065] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  197.164381] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  197.270612] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  197.531971] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  197.638214] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  197.899564] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  198.005816] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  198.267132] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  198.373433] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  198.634778] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  198.741101] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  199.002434] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  199.108607] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  199.370015] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  199.476201] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  199.737641] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  199.843849] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  202.505105] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off for 2 s
[  204.507140] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off for 4 s
[  206.508858] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off for 6 s
[  208.510771] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off for 8 s
[  210.512833] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off for 10 s
[  210.512840] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off, try to reconnect now
[  210.512866] wlan0: Connection to AP <MAC C-01 faidherbe_EXT> lost
[  210.520655] rtl8821ae-0:rtl_tx_agg_stop():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0
[  210.520671] rtl8821ae-0:rtl_rx_agg_stop():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0
[  210.532611] rtl8821ae-0:rtl_op_set_key():<0-0> Disabling hardware based encryption for keyidx: 0, mac: <MAC C-01 faidherbe_EXT>
[  210.532617] rtl8821ae-0:rtl_op_set_key():<0-0> alg:CCMP
[  210.532620] rtl8821ae-0:rtl_op_set_key():<0-0> set enable_hw_sec, key_type:4(OPEN:0 WEP40:1 TKIP:2 AES:4 WEP104:5)
[  210.532622] rtl8821ae-0:rtl8821ae_enable_hw_security_config():<0-0> PairwiseEncAlgorithm = 4 GroupEncAlgorithm = 4
[  210.532630] rtl8821ae-0:rtl8821ae_enable_hw_security_config():<0-0> The SECR-value cc 
[  210.532634] rtl8821ae-0:rtl_op_set_key():<0-0> disable key delete one entry
[  210.532636] rtl8821ae-0:rtl_cam_delete_one_entry():<0-0> key_idx:0
[  210.532642] rtl8821ae-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A4: 0 
[  210.532643] rtl8821ae-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A0: 80010000 
[  210.532681] rtl8821ae-0:rtl_op_sta_remove():<0-0> Remove sta addr is <MAC C-01 faidherbe_EXT>
[  210.532737] rtl8821ae-0:rtl_op_bss_info_changed():<0-0> BSS_CHANGED_UN_ASSOC
[  210.532763] rtl8821ae-0:rtl_op_bss_info_changed():<0-0> bssid: <MAC ID removed>
[  210.548618] rtl8821ae-0:rtl_op_set_key():<0-0> Disabling hardware based encryption for keyidx: 1, mac: <MAC ID removed>
[  210.548624] rtl8821ae-0:rtl_op_set_key():<0-0> alg:CCMP
[  210.548626] rtl8821ae-0:rtl_op_set_key():<0-0> disable key delete one entry
[  210.548628] rtl8821ae-0:rtl_cam_delete_one_entry():<0-0> key_idx:1
[  210.548636] rtl8821ae-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A4: 0 
[  210.548638] rtl8821ae-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A0: 80010008 
[  211.247782] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  212.650345] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  212.650954] wlan0: authenticate with <MAC C-01 faidherbe_EXT>
[  212.651277] rtl8821ae-0:rtl_op_bss_info_changed():<0-0> bssid: <MAC C-01 faidherbe_EXT>
[  212.651379] wlan0: send auth to <MAC C-01 faidherbe_EXT> (try 1/3)
[  212.651392] rtl8821ae-0:rtl_tx_mgmt_proc():<200-1> MAC80211_LINKING
[  212.653346] wlan0: authenticated
[  212.654280] wlan0: associate with <MAC C-01 faidherbe_EXT> (try 1/3)
[  212.661008] wlan0: RX AssocResp from <MAC C-01 faidherbe_EXT> (capab=0x411 status=0 aid=3)
[  212.661026] rtl8821ae-0:rtl_op_sta_add():<0-0> Add sta addr is <MAC C-01 faidherbe_EXT>
[  212.661033] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> ratr_bitmap :ff005
[  212.661038] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> Rate_index:0, ratr_val:ff005, 0:81:0:5:f0:f:0
[  212.661078] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> ratr_bitmap :ff005
[  212.661082] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> Rate_index:0, ratr_val:ff005, 0:81:0:5:f0:f:0
[  212.661108] rtl8821ae-0:rtl_op_bss_info_changed():<0-0> BSS_CHANGED_ASSOC
[  212.661126] rtl8821ae-0:rtl8821ae_set_hw_reg():<0-0> switch case not process 5c
[  212.661150] rtl8821ae: 
[  212.661156] rtl8821ae_set_fw_rsvdpagepkt(): HW_VAR_SET_TX_CMD: ALL 
[  212.661170] rtl8821ae: 
[  212.661230] wlan0: associated
[  212.669740] rtl8821ae-0:rtl_is_special_data():<10000-1> 802.1X Rx EAPOL pkt!!
[  212.680160] rtl8821ae-0:rtl_is_special_data():<10000-1> 802.1X Rx EAPOL pkt!!
[  212.680423] rtl8821ae-0:rtl_op_set_key():<0-0> Using hardware based encryption for keyidx: 0, mac: <MAC C-01 faidherbe_EXT>
[  212.680429] rtl8821ae-0:rtl_op_set_key():<0-0> alg:CCMP
[  212.680432] rtl8821ae-0:rtl_op_set_key():<0-0> set enable_hw_sec, key_type:4(OPEN:0 WEP40:1 TKIP:2 AES:4 WEP104:5)
[  212.680435] rtl8821ae-0:rtl8821ae_enable_hw_security_config():<0-0> PairwiseEncAlgorithm = 4 GroupEncAlgorithm = 0
[  212.680443] rtl8821ae-0:rtl8821ae_enable_hw_security_config():<0-0> The SECR-value cc 
[  212.680448] rtl8821ae-0:rtl_op_set_key():<0-0> set pairwise key
[  212.680451] rtl8821ae-0:rtl8821ae_set_key():<0-0> add one entry
[  212.680453] rtl8821ae-0:rtl8821ae_set_key():<0-0> set Pairwiase key
[  212.680455] rtl8821ae-0:rtl_cam_add_one_entry():<0-0> EntryNo:4, ulKeyId=0, ulEncAlg=4, ulUseDK=0 MacAddr <MAC C-01 faidherbe_EXT>
[  212.680458] rtl8821ae: 
[  212.681110] rtl8821ae-0:rtl_cam_add_one_entry():<0-0> end 
[  212.681263] rtl8821ae-0:rtl_op_set_key():<0-0> Using hardware based encryption for keyidx: 1, mac: <MAC ID removed>
[  212.681267] rtl8821ae-0:rtl_op_set_key():<0-0> alg:CCMP
[  212.681269] rtl8821ae-0:rtl_op_set_key():<0-0> set group key
[  212.681271] rtl8821ae-0:rtl8821ae_set_key():<0-0> add one entry
[  212.681273] rtl8821ae-0:rtl8821ae_set_key():<0-0> set group key
[  212.681276] rtl8821ae-0:rtl_cam_add_one_entry():<0-0> EntryNo:1, ulKeyId=1, ulEncAlg=4, ulUseDK=0 MacAddr <MAC ID removed>
[  212.681279] rtl8821ae: 
[  212.681952] rtl8821ae-0:rtl_cam_add_one_entry():<0-0> end 
[  215.291585] rtl8821ae-0:rtl_tx_agg_start():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0 seq:4
[  215.291616] rtl8821ae-0:rtl_action_proc():<200-1> Tx ACT_ADDBAREQ From :<MAC wlan0>
[  215.291618] rtl8821ae: 
[  215.295672] rtl8821ae-0:rtl_action_proc():<10000-1> Rx ACT_ADDBARSP From :<MAC C-01 faidherbe_EXT>
[  215.295753] rtl8821ae-0:rtl_tx_agg_oper():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0
[  215.888656] rtl8821ae-0:rtl_action_proc():<10000-1> Rx ACT_ADDBAREQ From :<MAC C-01 faidherbe_EXT>
[  215.888666] rtl8821ae: 
[  215.888819] rtl8821ae-0:rtl_rx_agg_start():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0 seq:4
[  215.888848] rtl8821ae-0:rtl_action_proc():<200-1> Tx ACT_ADDBARSP From :<MAC wlan0>
[  231.502444] rtl8821ae-0:rtl_tx_agg_stop():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0
[  231.502484] rtl8821ae-0:rtl_action_proc():<400-1> ACT_ADDBADEL From :<MAC wlan0>
[  231.894046] rtl8821ae-0:rtl_tx_agg_start():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0 seq:70
[  231.894062] rtl8821ae-0:rtl_action_proc():<200-1> Tx ACT_ADDBAREQ From :<MAC wlan0>
[  231.894064] rtl8821ae: 
[  231.896121] rtl8821ae-0:rtl_action_proc():<10000-1> Rx ACT_ADDBARSP From :<MAC C-01 faidherbe_EXT>
[  231.896173] rtl8821ae-0:rtl_tx_agg_oper():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0
[  278.554328] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  278.660647] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  278.921954] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  279.028226] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  279.289531] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  279.395866] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  279.657183] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  279.711515] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  279.972815] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  280.083058] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  280.344454] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  280.450657] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  280.712102] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  280.818350] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  281.079622] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  281.185903] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  281.459260] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  281.565603] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  281.826925] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  281.933206] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  282.194503] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  282.300812] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  282.562131] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  282.668414] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  282.929736] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  283.036076] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  286.584272] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off for 2 s
[  288.586203] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off for 4 s
[  290.588066] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off for 6 s
[  292.589986] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off for 8 s
[  294.591838] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off for 10 s
[  294.591843] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off, try to reconnect now
[  294.591866] wlan0: Connection to AP <MAC C-01 faidherbe_EXT> lost
[  294.599788] rtl8821ae-0:rtl_tx_agg_stop():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0
[  294.599802] rtl8821ae-0:rtl_rx_agg_stop():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0
[  294.615789] rtl8821ae-0:rtl_op_set_key():<0-0> Disabling hardware based encryption for keyidx: 0, mac: <MAC C-01 faidherbe_EXT>
[  294.615795] rtl8821ae-0:rtl_op_set_key():<0-0> alg:CCMP
[  294.615798] rtl8821ae-0:rtl_op_set_key():<0-0> set enable_hw_sec, key_type:4(OPEN:0 WEP40:1 TKIP:2 AES:4 WEP104:5)
[  294.615800] rtl8821ae-0:rtl8821ae_enable_hw_security_config():<0-0> PairwiseEncAlgorithm = 4 GroupEncAlgorithm = 4
[  294.615809] rtl8821ae-0:rtl8821ae_enable_hw_security_config():<0-0> The SECR-value cc 
[  294.615813] rtl8821ae-0:rtl_op_set_key():<0-0> disable key delete one entry
[  294.615815] rtl8821ae-0:rtl_cam_delete_one_entry():<0-0> key_idx:0
[  294.615821] rtl8821ae-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A4: 0 
[  294.615822] rtl8821ae-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A0: 80010000 
[  294.615861] rtl8821ae-0:rtl_op_sta_remove():<0-0> Remove sta addr is <MAC C-01 faidherbe_EXT>
[  294.615917] rtl8821ae-0:rtl_op_bss_info_changed():<0-0> BSS_CHANGED_UN_ASSOC
[  294.615943] rtl8821ae-0:rtl_op_bss_info_changed():<0-0> bssid: <MAC ID removed>
[  294.631782] rtl8821ae-0:rtl_op_set_key():<0-0> Disabling hardware based encryption for keyidx: 1, mac: <MAC ID removed>
[  294.631789] rtl8821ae-0:rtl_op_set_key():<0-0> alg:CCMP
[  294.631791] rtl8821ae-0:rtl_op_set_key():<0-0> disable key delete one entry
[  294.631793] rtl8821ae-0:rtl_cam_delete_one_entry():<0-0> key_idx:1
[  294.631801] rtl8821ae-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A4: 0 
[  294.631803] rtl8821ae-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A0: 80010008 
[  295.331015] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  296.737547] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  296.738352] wlan0: authenticate with <MAC C-01 faidherbe_EXT>
[  296.738688] rtl8821ae-0:rtl_op_bss_info_changed():<0-0> bssid: <MAC C-01 faidherbe_EXT>
[  296.738795] wlan0: send auth to <MAC C-01 faidherbe_EXT> (try 1/3)
[  296.738809] rtl8821ae-0:rtl_tx_mgmt_proc():<200-1> MAC80211_LINKING
[  296.741525] wlan0: authenticated
[  296.745487] wlan0: associate with <MAC C-01 faidherbe_EXT> (try 1/3)
[  296.748857] wlan0: RX AssocResp from <MAC C-01 faidherbe_EXT> (capab=0x411 status=0 aid=3)
[  296.748876] rtl8821ae-0:rtl_op_sta_add():<0-0> Add sta addr is <MAC C-01 faidherbe_EXT>
[  296.748884] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> ratr_bitmap :ff005
[  296.748888] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> Rate_index:0, ratr_val:ff005, 0:81:0:5:f0:f:0
[  296.748929] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> ratr_bitmap :ff005
[  296.748932] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> Rate_index:0, ratr_val:ff005, 0:81:0:5:f0:f:0
[  296.748959] rtl8821ae-0:rtl_op_bss_info_changed():<0-0> BSS_CHANGED_ASSOC
[  296.748976] rtl8821ae-0:rtl8821ae_set_hw_reg():<0-0> switch case not process 5c
[  296.749001] rtl8821ae: 
[  296.749006] rtl8821ae_set_fw_rsvdpagepkt(): HW_VAR_SET_TX_CMD: ALL 
[  296.749021] rtl8821ae: 
[  296.749082] wlan0: associated
[  296.753135] rtl8821ae-0:rtl_is_special_data():<10000-1> 802.1X Rx EAPOL pkt!!
[  296.772794] rtl8821ae-0:rtl_is_special_data():<10000-1> 802.1X Rx EAPOL pkt!!
[  296.773199] rtl8821ae-0:rtl_op_set_key():<0-0> Using hardware based encryption for keyidx: 0, mac: <MAC C-01 faidherbe_EXT>
[  296.773208] rtl8821ae-0:rtl_op_set_key():<0-0> alg:CCMP
[  296.773211] rtl8821ae-0:rtl_op_set_key():<0-0> set enable_hw_sec, key_type:4(OPEN:0 WEP40:1 TKIP:2 AES:4 WEP104:5)
[  296.773215] rtl8821ae-0:rtl8821ae_enable_hw_security_config():<0-0> PairwiseEncAlgorithm = 4 GroupEncAlgorithm = 0
[  296.773224] rtl8821ae-0:rtl8821ae_enable_hw_security_config():<0-0> The SECR-value cc 
[  296.773229] rtl8821ae-0:rtl_op_set_key():<0-0> set pairwise key
[  296.773233] rtl8821ae-0:rtl8821ae_set_key():<0-0> add one entry
[  296.773235] rtl8821ae-0:rtl8821ae_set_key():<0-0> set Pairwiase key
[  296.773238] rtl8821ae-0:rtl_cam_add_one_entry():<0-0> EntryNo:4, ulKeyId=0, ulEncAlg=4, ulUseDK=0 MacAddr <MAC C-01 faidherbe_EXT>
[  296.773242] rtl8821ae: 
[  296.773941] rtl8821ae-0:rtl_cam_add_one_entry():<0-0> end 
[  296.774106] rtl8821ae-0:rtl_op_set_key():<0-0> Using hardware based encryption for keyidx: 1, mac: <MAC ID removed>
[  296.774110] rtl8821ae-0:rtl_op_set_key():<0-0> alg:CCMP
[  296.774113] rtl8821ae-0:rtl_op_set_key():<0-0> set group key
[  296.774116] rtl8821ae-0:rtl8821ae_set_key():<0-0> add one entry
[  296.774118] rtl8821ae-0:rtl8821ae_set_key():<0-0> set group key
[  296.774121] rtl8821ae-0:rtl_cam_add_one_entry():<0-0> EntryNo:1, ulKeyId=1, ulEncAlg=4, ulUseDK=0 MacAddr <MAC ID removed>
[  296.774123] rtl8821ae: 
[  296.774776] rtl8821ae-0:rtl_cam_add_one_entry():<0-0> end 
[  297.002765] rtl8821ae-0:rtl_action_proc():<10000-1> Rx ACT_ADDBAREQ From :<MAC C-01 faidherbe_EXT>
[  297.002775] rtl8821ae: 
[  297.002916] rtl8821ae-0:rtl_rx_agg_start():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0 seq:0
[  297.002939] rtl8821ae-0:rtl_action_proc():<200-1> Tx ACT_ADDBARSP From :<MAC wlan0>
[  301.140908] rtl8821ae-0:rtl_tx_agg_start():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0 seq:1
[  301.140923] rtl8821ae-0:rtl_action_proc():<200-1> Tx ACT_ADDBAREQ From :<MAC wlan0>
[  301.140926] rtl8821ae: 
[  301.142936] rtl8821ae-0:rtl_action_proc():<10000-1> Rx ACT_ADDBARSP From :<MAC C-01 faidherbe_EXT>
[  301.142970] rtl8821ae-0:rtl_tx_agg_oper():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0
[  319.665265] rtl8821ae-0:rtl_tx_agg_stop():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0
[  319.665309] rtl8821ae-0:rtl_action_proc():<400-1> ACT_ADDBADEL From :<MAC wlan0>
[  320.716163] rtl8821ae-0:rtl_tx_agg_start():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0 seq:3026
[  320.716192] rtl8821ae-0:rtl_action_proc():<200-1> Tx ACT_ADDBAREQ From :<MAC wlan0>
[  320.716196] rtl8821ae: 
[  320.719095] rtl8821ae-0:rtl_action_proc():<10000-1> Rx ACT_ADDBARSP From :<MAC C-01 faidherbe_EXT>
[  320.719402] rtl8821ae-0:rtl_tx_agg_oper():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0
[  354.648419] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off for 2 s
[  356.650336] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off for 4 s
[  358.652189] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off for 6 s
[  360.650058] rtl8821ae-0:rtl_tx_agg_stop():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0
[  360.650095] rtl8821ae-0:rtl_action_proc():<400-1> ACT_ADDBADEL From :<MAC wlan0>
[  360.654143] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off for 8 s
[  362.655972] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off for 10 s
[  362.655981] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off, try to reconnect now
[  362.656032] wlan0: Connection to AP <MAC C-01 faidherbe_EXT> lost
[  364.657797] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off for 2 s
[  366.659708] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off for 4 s
[  367.458823] rtl8821ae-0:rtl_rx_agg_stop():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0
[  367.458888] rtl8821ae-0:rtl_op_set_key():<0-0> Disabling hardware based encryption for keyidx: 0, mac: <MAC C-01 faidherbe_EXT>
[  367.458896] rtl8821ae-0:rtl_op_set_key():<0-0> alg:CCMP
[  367.458899] rtl8821ae-0:rtl_op_set_key():<0-0> set enable_hw_sec, key_type:4(OPEN:0 WEP40:1 TKIP:2 AES:4 WEP104:5)
[  367.458902] rtl8821ae-0:rtl8821ae_enable_hw_security_config():<0-0> PairwiseEncAlgorithm = 4 GroupEncAlgorithm = 4
[  367.458907] rtl8821ae-0:rtl8821ae_enable_hw_security_config():<0-0> The SECR-value cc 
[  367.458911] rtl8821ae-0:rtl_op_set_key():<0-0> disable key delete one entry
[  367.458914] rtl8821ae-0:rtl_cam_delete_one_entry():<0-0> key_idx:0
[  367.458919] rtl8821ae-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A4: 0 
[  367.458921] rtl8821ae-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A0: 80010000 
[  367.458954] rtl8821ae-0:rtl_op_sta_remove():<0-0> Remove sta addr is <MAC C-01 faidherbe_EXT>
[  367.459007] rtl8821ae-0:rtl_op_bss_info_changed():<0-0> BSS_CHANGED_UN_ASSOC
[  367.459031] rtl8821ae-0:rtl_op_bss_info_changed():<0-0> bssid: <MAC ID removed>
[  369.860521] rtl8821ae-0:rtl_op_set_key():<0-0> Disabling hardware based encryption for keyidx: 1, mac: <MAC ID removed>
[  369.860531] rtl8821ae-0:rtl_op_set_key():<0-0> alg:CCMP
[  369.860533] rtl8821ae-0:rtl_op_set_key():<0-0> disable key delete one entry
[  369.860537] rtl8821ae-0:rtl_cam_delete_one_entry():<0-0> key_idx:1
[  369.860545] rtl8821ae-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A4: 0 
[  369.860547] rtl8821ae-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A0: 80010008 
[  375.378422] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  376.780981] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  387.209948] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  388.616453] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  396.432178] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  397.834684] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  409.598296] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  411.000825] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  421.425725] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  422.828373] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  433.257320] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  434.663826] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  442.491546] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  443.894000] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  463.996749] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  465.399371] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  496.954001] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  498.356574] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  536.444288] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  537.846815] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  548.272706] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  549.675969] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  560.094078] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  561.497323] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  569.317019] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  570.720230] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  573.199296] rtl8821ae: module is from the staging directory, the quality is unknown, you have been warned.
[  573.201971] rtl8821ae-0:rtl_pci_probe():<0-0> mem mapped space: start: 0xf7c00000 len:00004000 flags:00140204, after map:0xffffc90004780000
[  573.201985] rtl8821ae-0:_rtl_pci_find_adapter():<0-0> Pci Bridge Vendor is found index: 0
[  573.201988] rtl8821ae-0:_rtl_pci_find_adapter():<0-0> pcidev busnumber:devnumber:funcnumber:vendor:link_ctl 2:0:0:10ec:0
[  573.201989] rtl8821ae-0:_rtl_pci_find_adapter():<0-0> pci_bridge busnumber:devnumber:funcnumber:vendor:pcie_cap:lin  k_ctl_reg:amd 0:28:3:8086:40:40:0
[  573.202014] rtl8821ae-0:rtl8821ae_read_eeprom_info():<0-0> Boot from EFUSE
[  573.214930] rtl8821ae: 
[  573.215079] rtl8821ae-0:_rtl8821ae_read_adapter_info():<0-0> dev_addr: <MAC wlan0>
[  573.215083] rtl8821ae:_rtl8821ae_get_chnl_group(): 5G, Channel 163 in Group not found 
[  573.215085] rtl8821ae:_rtl8821ae_get_chnl_group(): 5G, Channel 163 in Group not found 
[  573.215126] rtl8821ae-0:rtl_btc_init_hal_vars():<0-0> rtl_btc_init_hal_vars, antNum is 2
[  573.215128] rtl8821ae-0:rtl_btc_init_hal_vars():<0-0> rtl_btc_init_hal_vars, bt_exist is 1
[  573.215129] rtl8821ae-0:rtl_btc_init_hal_vars():<0-0> rtl_btc_init_hal_vars, bt_type is 7
[  573.215287] rtl8821ae-0:_rtl_init_hw_ht_capab():<0-0> 1T1R
[  573.215288] rtl8821ae-0:_rtl_init_hw_ht_capab():<0-0> 1T1R
[  573.215307] WARNING: CPU: 1 PID: 19066 at /build/buildd/linux-3.16.0/net/wireless/reg.c:1555 wiphy_apply_custom_regulatory+0x19e/0x1d0 [cfg80211]()
[  573.215309] Modules linked in: rtl8821ae(C+) ctr ccm rpcsec_gss_krb5 nfsv4 snd_hda_codec_conexant snd_hda_codec_generic snd_hda_codec_hdmi intel_rapl x86_pkg_temp_thermal arc4 intel_powerclamp coretemp kvm_intel kvm asus_nb_wmi asus_wmi sparse_keymap bnep rfcomm crct10dif_pclmul crc32_pclmul ghash_clmulni_intel nfsd snd_soc_rt5640 uvcvideo snd_soc_rl6231 snd_hda_intel auth_rpcgss videobuf2_vmalloc snd_soc_core aesni_intel nfs_acl snd_hda_controller mac80211 videobuf2_memops snd_compress nfs aes_x86_64 lrw snd_pcm_dmaengine gf128mul snd_hda_codec videobuf2_core glue_helper v4l2_common snd_hwdep lockd ablk_helper snd_pcm cryptd btusb videodev media sunrpc cfg80211 snd_seq_midi binfmt_misc snd_seq_midi_event fscache joydev snd_rawmidi serio_raw i915 bluetooth snd_seq mei_me mei wmi snd_seq_device 6lowpan_iphc
[  573.215333]  snd_timer shpchp lpc_ich hid_multitouch snd drm_kms_helper drm nls_iso8859_1 dw_dmac soundcore 8250_dw dw_dmac_core snd_soc_sst_acpi i2c_algo_bit i2c_hid i2c_designware_platform spi_pxa2xx_platform i2c_designware_core video mac_hid parport_pc ppdev lp parport hid_generic usbhid hid ahci libahci psmouse(OE) sdhci_acpi sdhci [last unloaded: rtl8821ae]
[  573.215374]  [<ffffffffc0c63780>] ? rtl_regd_init+0x2f0/0x2f0 [rtl8821ae]
[  573.215392]  [<ffffffffc0c63780>] ? rtl_regd_init+0x2f0/0x2f0 [rtl8821ae]
[  573.215396]  [<ffffffffc0c636a7>] rtl_regd_init+0x217/0x2f0 [rtl8821ae]
[  573.215402]  [<ffffffffc0c5df3c>] rtl_init_core+0x15c/0x810 [rtl8821ae]
[  573.215412]  [<ffffffffc0c72515>] rtl_pci_probe+0x355/0xc10 [rtl8821ae]
[  573.215446]  [<ffffffffc0b0702c>] rtl8821ae_module_init+0x2c/0x1000 [rtl8821ae]
[  573.217287] rtlwifi: wireless switch is on
[  573.217311] rtl8821ae-0:rtl_pci_intr_mode_legacy():<0-0> Pin-based Interrupt Mode!
[  573.220120] rtl8821ae-0:rtl_pci_start():<0-0>  rtl_pci_start 
[  573.229792] rtl8821ae-0:rtl8821ae_download_fw():<0-0> normal Firmware SIZE 28984 
[  573.229797] rtl8821ae-0:rtl8821ae_download_fw():<0-0> Firmware Version(20), Signature(0x2101),Size(32)
[  573.242661] rtl8821ae-0:_rtl8821ae_fw_free_to_go():<0-0> Checksum report OK ! REG_MCUFWDL:0x00070604 .
[  573.273948] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 0][RfPath 0][TxNum 0][RateSection 0] = 0x32343638
[  573.273952] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 0][RfPath 0][TxNum 0][RateSection 1] = 0x36363838
[  573.273953] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 0][RfPath 0][TxNum 0][RateSection 2] = 0x28303234
[  573.273955] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 0][RfPath 0][TxNum 0][RateSection 3] = 0x34363838
[  573.273956] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 0][RfPath 0][TxNum 0][RateSection 4] = 0x26283032
[  573.273957] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 0][RfPath 0][TxNum 0][RateSection 7] = 0x32343636
[  573.273958] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 0][RfPath 0][TxNum 0][RateSection 8] = 0x24262830
[  573.273960] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 0][RfPath 0][TxNum 0][RateSection 9] = 0x2022
[  573.273961] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 1][RfPath 0][TxNum 0][RateSection 1] = 0x34343636
[  573.273962] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 1][RfPath 0][TxNum 0][RateSection 2] = 0x26283032
[  573.273963] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 1][RfPath 0][TxNum 0][RateSection 3] = 0x32343636
[  573.273965] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 1][RfPath 0][TxNum 0][RateSection 4] = 0x24262830
[  573.273966] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 1][RfPath 0][TxNum 0][RateSection 7] = 0x32343636
[  573.273967] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 1][RfPath 0][TxNum 0][RateSection 8] = 0x24262830
[  573.273968] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 1][RfPath 0][TxNum 0][RateSection 9] = 0x2022
[  573.374458] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  573.374493] rtl8821ae-0:rtl8821ae_enable_hw_security_config():<0-0> PairwiseEncAlgorithm = 0 GroupEncAlgorithm = 0
[  573.374498] rtl8821ae-0:rtl8821ae_enable_hw_security_config():<0-0> The SECR-value cc 
[  573.374739] rtl8821ae-0:rtl8821ae_set_hw_reg():<0-0> switch case not process 3e
[  573.374747] rtl8821ae-0:rtl_pci_start():<0-0> rtl_pci_start OK
[  573.375215] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  574.018392] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  575.421641] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  584.392578] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  585.795861] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  585.796355] wlan0: authenticate with <MAC C-01 faidherbe_EXT>
[  585.796673] rtl8821ae-0:rtl_op_bss_info_changed():<0-0> bssid: <MAC C-01 faidherbe_EXT>
[  585.796764] wlan0: send auth to <MAC C-01 faidherbe_EXT> (try 1/3)
[  585.796775] rtl8821ae-0:rtl_tx_mgmt_proc():<200-1> MAC80211_LINKING
[  585.798829] wlan0: authenticated
[  585.799781] wlan0: associate with <MAC C-01 faidherbe_EXT> (try 1/3)
[  585.803073] wlan0: RX AssocResp from <MAC C-01 faidherbe_EXT> (capab=0x411 status=0 aid=3)
[  585.803083] rtl8821ae-0:rtl_op_sta_add():<0-0> Add sta addr is <MAC C-01 faidherbe_EXT>
[  585.803086] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> ratr_bitmap :ff005
[  585.803088] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> Rate_index:0, ratr_val:ff005, 0:81:0:5:f0:f:0
[  585.803133] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> ratr_bitmap :ff005
[  585.803135] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> Rate_index:0, ratr_val:ff005, 0:81:0:5:f0:f:0
[  585.803157] rtl8821ae-0:rtl_op_bss_info_changed():<0-0> BSS_CHANGED_ASSOC
[  585.803171] rtl8821ae-0:rtl8821ae_set_hw_reg():<0-0> switch case not process 5c
[  585.803191] rtl8821ae: 
[  585.803194] rtl8821ae_set_fw_rsvdpagepkt(): HW_VAR_SET_TX_CMD: ALL 
[  585.803202] rtl8821ae: 
[  585.803253] wlan0: associated
[  585.803278] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  585.890628] rtl8821ae-0:rtl_is_special_data():<10000-1> 802.1X Rx EAPOL pkt!!
[  585.932973] rtl8821ae-0:rtl_is_special_data():<10000-1> 802.1X Rx EAPOL pkt!!
[  585.933274] rtl8821ae-0:rtl_op_set_key():<0-0> Using hardware based encryption for keyidx: 0, mac: <MAC C-01 faidherbe_EXT>
[  585.933279] rtl8821ae-0:rtl_op_set_key():<0-0> alg:CCMP
[  585.933281] rtl8821ae-0:rtl_op_set_key():<0-0> set enable_hw_sec, key_type:4(OPEN:0 WEP40:1 TKIP:2 AES:4 WEP104:5)
[  585.933284] rtl8821ae-0:rtl8821ae_enable_hw_security_config():<0-0> PairwiseEncAlgorithm = 4 GroupEncAlgorithm = 0
[  585.933291] rtl8821ae-0:rtl8821ae_enable_hw_security_config():<0-0> The SECR-value cc 
[  585.933295] rtl8821ae-0:rtl_op_set_key():<0-0> set pairwise key
[  585.933297] rtl8821ae-0:rtl8821ae_set_key():<0-0> add one entry
[  585.933299] rtl8821ae-0:rtl8821ae_set_key():<0-0> set Pairwiase key
[  585.933301] rtl8821ae-0:rtl_cam_add_one_entry():<0-0> EntryNo:4, ulKeyId=0, ulEncAlg=4, ulUseDK=0 MacAddr <MAC C-01 faidherbe_EXT>
[  585.933303] rtl8821ae: 
[  585.933951] rtl8821ae-0:rtl_cam_add_one_entry():<0-0> end 
[  585.934069] rtl8821ae-0:rtl_op_set_key():<0-0> Using hardware based encryption for keyidx: 1, mac: <MAC ID removed>
[  585.934072] rtl8821ae-0:rtl_op_set_key():<0-0> alg:CCMP
[  585.934074] rtl8821ae-0:rtl_op_set_key():<0-0> set group key
[  585.934076] rtl8821ae-0:rtl8821ae_set_key():<0-0> add one entry
[  585.934078] rtl8821ae-0:rtl8821ae_set_key():<0-0> set group key
[  585.934079] rtl8821ae-0:rtl_cam_add_one_entry():<0-0> EntryNo:1, ulKeyId=1, ulEncAlg=4, ulUseDK=0 MacAddr <MAC ID removed>
[  585.934081] rtl8821ae: 
[  585.934727] rtl8821ae-0:rtl_cam_add_one_entry():<0-0> end 
[  585.963735] rtl8821ae-0:rtl_tx_agg_start():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0 seq:1
[  585.963766] rtl8821ae-0:rtl_action_proc():<200-1> Tx ACT_ADDBAREQ From :<MAC wlan0>
[  585.963770] rtl8821ae: 
[  585.965295] rtl8821ae-0:rtl_action_proc():<10000-1> Rx ACT_ADDBARSP From :<MAC C-01 faidherbe_EXT>
[  585.965332] rtl8821ae-0:rtl_tx_agg_oper():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0
[  587.394934] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> ratr_bitmap :f0000
[  587.394942] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> Rate_index:0, ratr_val:f0000, 0:81:0:0:0:f:0
[  590.076556] rtl8821ae-0:rtl_action_proc():<10000-1> Rx ACT_ADDBAREQ From :<MAC C-01 faidherbe_EXT>
[  590.076562] rtl8821ae: 
[  590.076650] rtl8821ae-0:rtl_rx_agg_start():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0 seq:19
[  590.076664] rtl8821ae-0:rtl_action_proc():<200-1> Tx ACT_ADDBARSP From :<MAC wlan0>
[  590.081317] rtl8821ae-0:rtl_action_proc():<10000-1> Rx ACT_ADDBAREQ From :<MAC C-01 faidherbe_EXT>
[  590.081322] rtl8821ae: 
[  590.081349] rtl8821ae: 
[  590.081429] rtl8821ae-0:rtl_rx_agg_stop():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0
[  590.081442] rtl8821ae-0:rtl_rx_agg_start():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0 seq:19
[  590.081454] rtl8821ae-0:rtl_action_proc():<200-1> Tx ACT_ADDBARSP From :<MAC wlan0>
[  591.400757] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> ratr_bitmap :ff000
[  591.400762] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> Rate_index:0, ratr_val:ff000, 0:81:0:0:f0:f:0
[  599.982094] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  600.088534] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  600.350110] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  600.456611] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  600.718132] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  600.824535] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  601.086091] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  601.192498] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  601.454118] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  601.560521] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  601.821993] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  601.928464] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  602.190046] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  602.296408] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  602.558039] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  602.664454] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  602.925997] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  603.032396] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  603.294024] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  603.400395] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  603.661946] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  603.768304] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  604.029964] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  604.136347] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  604.397904] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  604.504331] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  605.424247] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> ratr_bitmap :f0000
[  605.424252] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> Rate_index:0, ratr_val:f0000, 0:81:0:0:0:f:0
[  607.428243] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off for 2 s
[  609.432139] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off for 4 s
[  610.751931] rtl8821ae-0:rtl_tx_agg_stop():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0
[  610.751951] rtl8821ae-0:rtl_action_proc():<400-1> ACT_ADDBADEL From :<MAC wlan0>
[  611.435989] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off for 6 s
[  613.439909] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off for 8 s
[  615.443765] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off for 10 s
[  615.443770] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off, try to reconnect now
[  615.443785] wlan0: Connection to AP <MAC C-01 faidherbe_EXT> lost
[  615.443817] rtl8821ae-0:rtl_rx_agg_stop():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0
[  615.451805] rtl8821ae-0:rtl_op_set_key():<0-0> Disabling hardware based encryption for keyidx: 0, mac: <MAC C-01 faidherbe_EXT>
[  615.451817] rtl8821ae-0:rtl_op_set_key():<0-0> alg:CCMP
[  615.451821] rtl8821ae-0:rtl_op_set_key():<0-0> set enable_hw_sec, key_type:4(OPEN:0 WEP40:1 TKIP:2 AES:4 WEP104:5)
[  615.451826] rtl8821ae-0:rtl8821ae_enable_hw_security_config():<0-0> PairwiseEncAlgorithm = 4 GroupEncAlgorithm = 4
[  615.451837] rtl8821ae-0:rtl8821ae_enable_hw_security_config():<0-0> The SECR-value cc 
[  615.451843] rtl8821ae-0:rtl_op_set_key():<0-0> disable key delete one entry
[  615.451847] rtl8821ae-0:rtl_cam_delete_one_entry():<0-0> key_idx:0
[  615.451855] rtl8821ae-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A4: 0 
[  615.451858] rtl8821ae-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A0: 80010000 
[  615.451923] rtl8821ae-0:rtl_op_sta_remove():<0-0> Remove sta addr is <MAC C-01 faidherbe_EXT>
[  615.452052] rtl8821ae-0:rtl_op_bss_info_changed():<0-0> BSS_CHANGED_UN_ASSOC
[  615.452082] rtl8821ae-0:rtl_op_bss_info_changed():<0-0> bssid: <MAC ID removed>
[  615.452468] rtl8821ae-0:rtl_op_set_key():<0-0> Disabling hardware based encryption for keyidx: 1, mac: <MAC ID removed>
[  615.452476] rtl8821ae-0:rtl_op_set_key():<0-0> alg:CCMP
[  615.452481] rtl8821ae-0:rtl_op_set_key():<0-0> disable key delete one entry
[  615.452486] rtl8821ae-0:rtl_cam_delete_one_entry():<0-0> key_idx:1
[  615.452498] rtl8821ae-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A4: 0 
[  615.452504] rtl8821ae-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A0: 80010008 
[  616.167665] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  617.571619] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  617.572471] wlan0: authenticate with <MAC C-01 faidherbe_EXT>
[  617.572820] rtl8821ae-0:rtl_op_bss_info_changed():<0-0> bssid: <MAC C-01 faidherbe_EXT>
[  617.572956] wlan0: send auth to <MAC C-01 faidherbe_EXT> (try 1/3)
[  617.572975] rtl8821ae-0:rtl_tx_mgmt_proc():<200-1> MAC80211_LINKING
[  617.574476] wlan0: authenticated
[  617.575567] wlan0: associate with <MAC C-01 faidherbe_EXT> (try 1/3)
[  617.579255] wlan0: RX AssocResp from <MAC C-01 faidherbe_EXT> (capab=0x411 status=0 aid=3)
[  617.579271] rtl8821ae-0:rtl_op_sta_add():<0-0> Add sta addr is <MAC C-01 faidherbe_EXT>
[  617.579278] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> ratr_bitmap :ff005
[  617.579281] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> Rate_index:0, ratr_val:ff005, 0:81:0:5:f0:f:0
[  617.579320] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> ratr_bitmap :ff005
[  617.579323] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> Rate_index:0, ratr_val:ff005, 0:81:0:5:f0:f:0
[  617.579348] rtl8821ae-0:rtl_op_bss_info_changed():<0-0> BSS_CHANGED_ASSOC
[  617.579366] rtl8821ae-0:rtl8821ae_set_hw_reg():<0-0> switch case not process 5c
[  617.579389] rtl8821ae: 
[  617.579394] rtl8821ae_set_fw_rsvdpagepkt(): HW_VAR_SET_TX_CMD: ALL 
[  617.579407] rtl8821ae: 
[  617.579467] wlan0: associated
[  617.590344] rtl8821ae-0:rtl_is_special_data():<10000-1> 802.1X Rx EAPOL pkt!!
[  617.600829] rtl8821ae-0:rtl_is_special_data():<10000-1> 802.1X Rx EAPOL pkt!!
[  617.601086] rtl8821ae-0:rtl_op_set_key():<0-0> Using hardware based encryption for keyidx: 0, mac: <MAC C-01 faidherbe_EXT>
[  617.601091] rtl8821ae-0:rtl_op_set_key():<0-0> alg:CCMP
[  617.601093] rtl8821ae-0:rtl_op_set_key():<0-0> set enable_hw_sec, key_type:4(OPEN:0 WEP40:1 TKIP:2 AES:4 WEP104:5)
[  617.601095] rtl8821ae-0:rtl8821ae_enable_hw_security_config():<0-0> PairwiseEncAlgorithm = 4 GroupEncAlgorithm = 0
[  617.601103] rtl8821ae-0:rtl8821ae_enable_hw_security_config():<0-0> The SECR-value cc 
[  617.601107] rtl8821ae-0:rtl_op_set_key():<0-0> set pairwise key
[  617.601110] rtl8821ae-0:rtl8821ae_set_key():<0-0> add one entry
[  617.601112] rtl8821ae-0:rtl8821ae_set_key():<0-0> set Pairwiase key
[  617.601114] rtl8821ae-0:rtl_cam_add_one_entry():<0-0> EntryNo:4, ulKeyId=0, ulEncAlg=4, ulUseDK=0 MacAddr <MAC C-01 faidherbe_EXT>
[  617.601116] rtl8821ae: 
[  617.601765] rtl8821ae-0:rtl_cam_add_one_entry():<0-0> end 
[  617.601884] rtl8821ae-0:rtl_op_set_key():<0-0> Using hardware based encryption for keyidx: 1, mac: <MAC ID removed>
[  617.601887] rtl8821ae-0:rtl_op_set_key():<0-0> alg:CCMP
[  617.601889] rtl8821ae-0:rtl_op_set_key():<0-0> set group key
[  617.601891] rtl8821ae-0:rtl8821ae_set_key():<0-0> add one entry
[  617.601893] rtl8821ae-0:rtl8821ae_set_key():<0-0> set group key
[  617.601895] rtl8821ae-0:rtl_cam_add_one_entry():<0-0> EntryNo:1, ulKeyId=1, ulEncAlg=4, ulUseDK=0 MacAddr <MAC ID removed>
[  617.601897] rtl8821ae: 
[  617.602544] rtl8821ae-0:rtl_cam_add_one_entry():<0-0> end 
[  618.223636] rtl8821ae-0:rtl_tx_agg_start():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0 seq:1
[  618.223666] rtl8821ae-0:rtl_action_proc():<200-1> Tx ACT_ADDBAREQ From :<MAC wlan0>
[  618.223670] rtl8821ae: 
[  618.227495] rtl8821ae-0:rtl_action_proc():<10000-1> Rx ACT_ADDBARSP From :<MAC C-01 faidherbe_EXT>
[  618.227596] rtl8821ae-0:rtl_tx_agg_oper():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0
[  622.533050] rtl8821ae-0:rtl_action_proc():<10000-1> Rx ACT_ADDBAREQ From :<MAC C-01 faidherbe_EXT>
[  622.533055] rtl8821ae: 
[  622.533138] rtl8821ae-0:rtl_rx_agg_start():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0 seq:3
[  622.533152] rtl8821ae-0:rtl_action_proc():<200-1> Tx ACT_ADDBARSP From :<MAC wlan0>
[  637.126531] rtl8821ae-0:rtl_tx_agg_stop():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0
[  637.126555] rtl8821ae-0:rtl_action_proc():<400-1> ACT_ADDBADEL From :<MAC wlan0>
[  637.370422] rtl8821ae-0:rtl_tx_agg_start():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0 seq:14
[  637.370431] rtl8821ae-0:rtl_action_proc():<200-1> Tx ACT_ADDBAREQ From :<MAC wlan0>
[  637.370433] rtl8821ae: 
[  637.372106] rtl8821ae-0:rtl_action_proc():<10000-1> Rx ACT_ADDBARSP From :<MAC C-01 faidherbe_EXT>
[  637.372125] rtl8821ae-0:rtl_tx_agg_oper():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0
[  637.486475] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off for 2 s
[  642.983690] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  643.090109] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  643.351749] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  643.458165] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  643.719655] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  643.826072] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  644.087633] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  644.194035] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  644.455643] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  644.562083] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  644.823603] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  644.930063] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  645.191632] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  645.298035] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  645.559606] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  645.666039] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  645.931548] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  646.037959] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  646.299507] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  646.405904] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  646.667559] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  646.777928] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  647.039523] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  647.145921] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  647.407531] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  647.513852] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  649.509826] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off for 4 s
[  651.513704] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off for 6 s
[  653.517549] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> ratr_bitmap :ff000
[  653.517553] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> Rate_index:0, ratr_val:ff000, 0:81:0:0:f0:f:0
[  653.517608] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off for 8 s
[  655.521565] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off for 10 s
[  655.521571] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off, try to reconnect now
[  655.521641] wlan0: Connection to AP <MAC C-01 faidherbe_EXT> lost
[  655.529468] rtl8821ae-0:rtl_tx_agg_stop():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0
[  655.529482] rtl8821ae-0:rtl_rx_agg_stop():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0
[  655.541483] rtl8821ae-0:rtl_op_set_key():<0-0> Disabling hardware based encryption for keyidx: 0, mac: <MAC C-01 faidherbe_EXT>
[  655.541490] rtl8821ae-0:rtl_op_set_key():<0-0> alg:CCMP
[  655.541493] rtl8821ae-0:rtl_op_set_key():<0-0> set enable_hw_sec, key_type:4(OPEN:0 WEP40:1 TKIP:2 AES:4 WEP104:5)
[  655.541496] rtl8821ae-0:rtl8821ae_enable_hw_security_config():<0-0> PairwiseEncAlgorithm = 4 GroupEncAlgorithm = 4
[  655.541503] rtl8821ae-0:rtl8821ae_enable_hw_security_config():<0-0> The SECR-value cc 
[  655.541508] rtl8821ae-0:rtl_op_set_key():<0-0> disable key delete one entry
[  655.541510] rtl8821ae-0:rtl_cam_delete_one_entry():<0-0> key_idx:0
[  655.541515] rtl8821ae-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A4: 0 
[  655.541517] rtl8821ae-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A0: 80010000 
[  655.541552] rtl8821ae-0:rtl_op_sta_remove():<0-0> Remove sta addr is <MAC C-01 faidherbe_EXT>
[  655.541624] rtl8821ae-0:rtl_op_bss_info_changed():<0-0> BSS_CHANGED_UN_ASSOC
[  655.541650] rtl8821ae-0:rtl_op_bss_info_changed():<0-0> bssid: <MAC ID removed>
[  655.561486] rtl8821ae-0:rtl_op_set_key():<0-0> Disabling hardware based encryption for keyidx: 1, mac: <MAC ID removed>
[  655.561492] rtl8821ae-0:rtl_op_set_key():<0-0> alg:CCMP
[  655.561494] rtl8821ae-0:rtl_op_set_key():<0-0> disable key delete one entry
[  655.561497] rtl8821ae-0:rtl_cam_delete_one_entry():<0-0> key_idx:1
[  655.561504] rtl8821ae-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A4: 0 
[  655.561506] rtl8821ae-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A0: 80010008 
[  656.261428] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  657.665348] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  657.665795] wlan0: authenticate with <MAC C-01 faidherbe_EXT>
[  657.666109] rtl8821ae-0:rtl_op_bss_info_changed():<0-0> bssid: <MAC C-01 faidherbe_EXT>
[  657.666185] wlan0: send auth to <MAC C-01 faidherbe_EXT> (try 1/3)
[  657.666193] rtl8821ae-0:rtl_tx_mgmt_proc():<200-1> MAC80211_LINKING
[  657.667801] wlan0: authenticated
[  657.669319] wlan0: associate with <MAC C-01 faidherbe_EXT> (try 1/3)
[  657.672666] wlan0: RX AssocResp from <MAC C-01 faidherbe_EXT> (capab=0x411 status=0 aid=3)
[  657.672686] rtl8821ae-0:rtl_op_sta_add():<0-0> Add sta addr is <MAC C-01 faidherbe_EXT>
[  657.672693] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> ratr_bitmap :ff005
[  657.672698] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> Rate_index:0, ratr_val:ff005, 0:81:0:5:f0:f:0
[  657.672739] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> ratr_bitmap :ff005
[  657.672742] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> Rate_index:0, ratr_val:ff005, 0:81:0:5:f0:f:0
[  657.672775] rtl8821ae-0:rtl_op_bss_info_changed():<0-0> BSS_CHANGED_ASSOC
[  657.672794] rtl8821ae-0:rtl8821ae_set_hw_reg():<0-0> switch case not process 5c
[  657.672820] rtl8821ae: 
[  657.672827] rtl8821ae_set_fw_rsvdpagepkt(): HW_VAR_SET_TX_CMD: ALL 
[  657.672842] rtl8821ae: 
[  657.672905] wlan0: associated
[  657.681702] rtl8821ae-0:rtl_is_special_data():<10000-1> 802.1X Rx EAPOL pkt!!
[  657.689691] rtl8821ae-0:rtl_is_special_data():<10000-1> 802.1X Rx EAPOL pkt!!
[  657.689963] rtl8821ae-0:rtl_op_set_key():<0-0> Using hardware based encryption for keyidx: 0, mac: <MAC C-01 faidherbe_EXT>
[  657.689969] rtl8821ae-0:rtl_op_set_key():<0-0> alg:CCMP
[  657.689971] rtl8821ae-0:rtl_op_set_key():<0-0> set enable_hw_sec, key_type:4(OPEN:0 WEP40:1 TKIP:2 AES:4 WEP104:5)
[  657.689973] rtl8821ae-0:rtl8821ae_enable_hw_security_config():<0-0> PairwiseEncAlgorithm = 4 GroupEncAlgorithm = 0
[  657.689980] rtl8821ae-0:rtl8821ae_enable_hw_security_config():<0-0> The SECR-value cc 
[  657.689984] rtl8821ae-0:rtl_op_set_key():<0-0> set pairwise key
[  657.689987] rtl8821ae-0:rtl8821ae_set_key():<0-0> add one entry
[  657.689988] rtl8821ae-0:rtl8821ae_set_key():<0-0> set Pairwiase key
[  657.689990] rtl8821ae-0:rtl_cam_add_one_entry():<0-0> EntryNo:4, ulKeyId=0, ulEncAlg=4, ulUseDK=0 MacAddr <MAC C-01 faidherbe_EXT>
[  657.689993] rtl8821ae: 
[  657.690641] rtl8821ae-0:rtl_cam_add_one_entry():<0-0> end 
[  657.690754] rtl8821ae-0:rtl_op_set_key():<0-0> Using hardware based encryption for keyidx: 1, mac: <MAC ID removed>
[  657.690758] rtl8821ae-0:rtl_op_set_key():<0-0> alg:CCMP
[  657.690759] rtl8821ae-0:rtl_op_set_key():<0-0> set group key
[  657.690761] rtl8821ae-0:rtl8821ae_set_key():<0-0> add one entry
[  657.690763] rtl8821ae-0:rtl8821ae_set_key():<0-0> set group key
[  657.690765] rtl8821ae-0:rtl_cam_add_one_entry():<0-0> EntryNo:1, ulKeyId=1, ulEncAlg=4, ulUseDK=0 MacAddr <MAC ID removed>
[  657.690766] rtl8821ae: 
[  657.691412] rtl8821ae-0:rtl_cam_add_one_entry():<0-0> end 
[  660.021196] rtl8821ae-0:rtl_tx_agg_start():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0 seq:1
[  660.021214] rtl8821ae-0:rtl_action_proc():<200-1> Tx ACT_ADDBAREQ From :<MAC wlan0>
[  660.021216] rtl8821ae: 
[  660.022988] rtl8821ae-0:rtl_action_proc():<10000-1> Rx ACT_ADDBARSP From :<MAC C-01 faidherbe_EXT>
[  660.023023] rtl8821ae-0:rtl_tx_agg_oper():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0
[  660.458373] rtl8821ae-0:rtl_action_proc():<10000-1> Rx ACT_ADDBAREQ From :<MAC C-01 faidherbe_EXT>
[  660.458382] rtl8821ae: 
[  660.458503] rtl8821ae-0:rtl_rx_agg_start():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0 seq:1
[  660.458544] rtl8821ae-0:rtl_action_proc():<200-1> Tx ACT_ADDBARSP From :<MAC wlan0>
[  689.587584] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> ratr_bitmap :f0000
[  689.587594] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> Rate_index:0, ratr_val:f0000, 0:81:0:0:0:f:0
[  706.472177] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  706.578619] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  706.840138] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  706.946583] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  707.208200] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  707.314626] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  707.576180] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  707.630558] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  707.892178] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  707.998548] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  708.260104] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  708.366468] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  708.628101] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  708.734443] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  708.996055] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  709.102472] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  709.364101] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  709.470478] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  709.732059] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  709.838421] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  710.100030] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  710.206418] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  710.468022] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  710.574411] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  710.835931] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  710.942394] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  713.634272] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off for 2 s
[  715.638117] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off for 4 s
[  717.642047] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off for 6 s
[  719.645973] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off for 8 s
[  721.649816] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off for 10 s
[  721.649824] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off, try to reconnect now
[  721.649872] wlan0: Connection to AP <MAC C-01 faidherbe_EXT> lost
[  722.025827] rtl8821ae-0:rtl_tx_agg_stop():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0
[  722.025835] rtl8821ae-0:rtl_rx_agg_stop():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0
[  722.033757] rtl8821ae-0:rtl_op_set_key():<0-0> Disabling hardware based encryption for keyidx: 0, mac: <MAC C-01 faidherbe_EXT>
[  722.033764] rtl8821ae-0:rtl_op_set_key():<0-0> alg:CCMP
[  722.033766] rtl8821ae-0:rtl_op_set_key():<0-0> set enable_hw_sec, key_type:4(OPEN:0 WEP40:1 TKIP:2 AES:4 WEP104:5)
[  722.033769] rtl8821ae-0:rtl8821ae_enable_hw_security_config():<0-0> PairwiseEncAlgorithm = 4 GroupEncAlgorithm = 4
[  722.033777] rtl8821ae-0:rtl8821ae_enable_hw_security_config():<0-0> The SECR-value cc 
[  722.033781] rtl8821ae-0:rtl_op_set_key():<0-0> disable key delete one entry
[  722.033783] rtl8821ae-0:rtl_cam_delete_one_entry():<0-0> key_idx:0
[  722.033789] rtl8821ae-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A4: 0 
[  722.033791] rtl8821ae-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A0: 80010000 
[  722.033827] rtl8821ae-0:rtl_op_sta_remove():<0-0> Remove sta addr is <MAC C-01 faidherbe_EXT>
[  722.033895] rtl8821ae-0:rtl_op_bss_info_changed():<0-0> BSS_CHANGED_UN_ASSOC
[  722.033922] rtl8821ae-0:rtl_op_bss_info_changed():<0-0> bssid: <MAC ID removed>
[  722.049731] rtl8821ae-0:rtl_op_set_key():<0-0> Disabling hardware based encryption for keyidx: 1, mac: <MAC ID removed>
[  722.049737] rtl8821ae-0:rtl_op_set_key():<0-0> alg:CCMP
[  722.049739] rtl8821ae-0:rtl_op_set_key():<0-0> disable key delete one entry
[  722.049742] rtl8821ae-0:rtl_cam_delete_one_entry():<0-0> key_idx:1
[  722.049749] rtl8821ae-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A4: 0 
[  722.049751] rtl8821ae-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A0: 80010008 
[  722.749631] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  724.153616] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  724.154401] wlan0: authenticate with <MAC C-01 faidherbe_EXT>
[  724.154729] rtl8821ae-0:rtl_op_bss_info_changed():<0-0> bssid: <MAC C-01 faidherbe_EXT>
[  724.154834] wlan0: send auth to <MAC C-01 faidherbe_EXT> (try 1/3)
[  724.154848] rtl8821ae-0:rtl_tx_mgmt_proc():<200-1> MAC80211_LINKING
[  724.156814] wlan0: authenticated
[  724.157592] wlan0: associate with <MAC C-01 faidherbe_EXT> (try 1/3)
[  724.160859] wlan0: RX AssocResp from <MAC C-01 faidherbe_EXT> (capab=0x411 status=0 aid=3)
[  724.160879] rtl8821ae-0:rtl_op_sta_add():<0-0> Add sta addr is <MAC C-01 faidherbe_EXT>
[  724.160888] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> ratr_bitmap :ff005
[  724.160893] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> Rate_index:0, ratr_val:ff005, 0:81:0:5:f0:f:0
[  724.160938] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> ratr_bitmap :ff005
[  724.160943] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> Rate_index:0, ratr_val:ff005, 0:81:0:5:f0:f:0
[  724.160973] rtl8821ae-0:rtl_op_bss_info_changed():<0-0> BSS_CHANGED_ASSOC
[  724.160992] rtl8821ae-0:rtl8821ae_set_hw_reg():<0-0> switch case not process 5c
[  724.161017] rtl8821ae: 
[  724.161025] rtl8821ae_set_fw_rsvdpagepkt(): HW_VAR_SET_TX_CMD: ALL 
[  724.161042] rtl8821ae: 
[  724.161109] wlan0: associated
[  724.165112] rtl8821ae-0:rtl_is_special_data():<10000-1> 802.1X Rx EAPOL pkt!!
[  724.174844] rtl8821ae-0:rtl_is_special_data():<10000-1> 802.1X Rx EAPOL pkt!!
[  724.175136] rtl8821ae-0:rtl_op_set_key():<0-0> Using hardware based encryption for keyidx: 0, mac: <MAC C-01 faidherbe_EXT>
[  724.175141] rtl8821ae-0:rtl_op_set_key():<0-0> alg:CCMP
[  724.175143] rtl8821ae-0:rtl_op_set_key():<0-0> set enable_hw_sec, key_type:4(OPEN:0 WEP40:1 TKIP:2 AES:4 WEP104:5)
[  724.175145] rtl8821ae-0:rtl8821ae_enable_hw_security_config():<0-0> PairwiseEncAlgorithm = 4 GroupEncAlgorithm = 0
[  724.175153] rtl8821ae-0:rtl8821ae_enable_hw_security_config():<0-0> The SECR-value cc 
[  724.175157] rtl8821ae-0:rtl_op_set_key():<0-0> set pairwise key
[  724.175159] rtl8821ae-0:rtl8821ae_set_key():<0-0> add one entry
[  724.175161] rtl8821ae-0:rtl8821ae_set_key():<0-0> set Pairwiase key
[  724.175163] rtl8821ae-0:rtl_cam_add_one_entry():<0-0> EntryNo:4, ulKeyId=0, ulEncAlg=4, ulUseDK=0 MacAddr <MAC C-01 faidherbe_EXT>
[  724.175165] rtl8821ae: 
[  724.175811] rtl8821ae-0:rtl_cam_add_one_entry():<0-0> end 
[  724.175926] rtl8821ae-0:rtl_op_set_key():<0-0> Using hardware based encryption for keyidx: 1, mac: <MAC ID removed>
[  724.175929] rtl8821ae-0:rtl_op_set_key():<0-0> alg:CCMP
[  724.175931] rtl8821ae-0:rtl_op_set_key():<0-0> set group key
[  724.175933] rtl8821ae-0:rtl8821ae_set_key():<0-0> add one entry
[  724.175934] rtl8821ae-0:rtl8821ae_set_key():<0-0> set group key
[  724.175936] rtl8821ae-0:rtl_cam_add_one_entry():<0-0> EntryNo:1, ulKeyId=1, ulEncAlg=4, ulUseDK=0 MacAddr <MAC ID removed>
[  724.175938] rtl8821ae: 
[  724.176593] rtl8821ae-0:rtl_cam_add_one_entry():<0-0> end 
[  724.585672] rtl8821ae-0:rtl_tx_agg_start():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0 seq:2
[  724.585688] rtl8821ae-0:rtl_action_proc():<200-1> Tx ACT_ADDBAREQ From :<MAC wlan0>
[  724.585690] rtl8821ae: 
[  724.587266] rtl8821ae-0:rtl_action_proc():<10000-1> Rx ACT_ADDBARSP From :<MAC C-01 faidherbe_EXT>
[  724.587331] rtl8821ae-0:rtl_tx_agg_oper():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0
[  724.676637] rtl8821ae-0:rtl_action_proc():<10000-1> Rx ACT_ADDBAREQ From :<MAC C-01 faidherbe_EXT>
[  724.676643] rtl8821ae: 
[  724.676719] rtl8821ae-0:rtl_rx_agg_start():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0 seq:2
[  724.676744] rtl8821ae-0:rtl_action_proc():<200-1> Tx ACT_ADDBARSP From :<MAC wlan0>
[  733.673195] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off for 2 s
[  735.677052] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off for 4 s
[  737.680934] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off for 6 s
[  739.684792] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off for 8 s
[  741.688696] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off for 10 s
[  741.688704] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off, try to reconnect now
[  741.688758] wlan0: Connection to AP <MAC C-01 faidherbe_EXT> lost
[  743.692593] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off for 2 s
[  745.696450] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off for 4 s
[  746.504500] rtl8821ae-0:rtl_tx_agg_stop():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0
[  746.504511] rtl8821ae-0:rtl_rx_agg_stop():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0
[  746.512459] rtl8821ae-0:rtl_op_set_key():<0-0> Disabling hardware based encryption for keyidx: 0, mac: <MAC C-01 faidherbe_EXT>
[  746.512465] rtl8821ae-0:rtl_op_set_key():<0-0> alg:CCMP
[  746.512468] rtl8821ae-0:rtl_op_set_key():<0-0> set enable_hw_sec, key_type:4(OPEN:0 WEP40:1 TKIP:2 AES:4 WEP104:5)
[  746.512470] rtl8821ae-0:rtl8821ae_enable_hw_security_config():<0-0> PairwiseEncAlgorithm = 4 GroupEncAlgorithm = 4
[  746.512476] rtl8821ae-0:rtl8821ae_enable_hw_security_config():<0-0> The SECR-value cc 
[  746.512481] rtl8821ae-0:rtl_op_set_key():<0-0> disable key delete one entry
[  746.512483] rtl8821ae-0:rtl_cam_delete_one_entry():<0-0> key_idx:0
[  746.512488] rtl8821ae-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A4: 0 
[  746.512490] rtl8821ae-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A0: 80010000 
[  746.512528] rtl8821ae-0:rtl_op_sta_remove():<0-0> Remove sta addr is <MAC C-01 faidherbe_EXT>
[  746.512582] rtl8821ae-0:rtl_op_bss_info_changed():<0-0> BSS_CHANGED_UN_ASSOC
[  746.512606] rtl8821ae-0:rtl_op_bss_info_changed():<0-0> bssid: <MAC ID removed>
[  748.912498] rtl8821ae-0:rtl_op_set_key():<0-0> Disabling hardware based encryption for keyidx: 1, mac: <MAC ID removed>
[  748.912506] rtl8821ae-0:rtl_op_set_key():<0-0> alg:CCMP
[  748.912509] rtl8821ae-0:rtl_op_set_key():<0-0> disable key delete one entry
[  748.912513] rtl8821ae-0:rtl_cam_delete_one_entry():<0-0> key_idx:1
[  748.912520] rtl8821ae-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A4: 0 
[  748.912523] rtl8821ae-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A0: 80010008 
[  754.435927] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  755.839857] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  766.271294] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  767.675228] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  775.502754] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  776.906679] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  779.391020] rtl8821ae: module is from the staging directory, the quality is unknown, you have been warned.
[  779.392097] rtl8821ae-0:rtl_pci_probe():<0-0> mem mapped space: start: 0xf7c00000 len:00004000 flags:00140204, after map:0xffffc90004780000
[  779.392111] rtl8821ae-0:_rtl_pci_find_adapter():<0-0> Pci Bridge Vendor is found index: 0
[  779.392113] rtl8821ae-0:_rtl_pci_find_adapter():<0-0> pcidev busnumber:devnumber:funcnumber:vendor:link_ctl 2:0:0:10ec:0
[  779.392115] rtl8821ae-0:_rtl_pci_find_adapter():<0-0> pci_bridge busnumber:devnumber:funcnumber:vendor:pcie_cap:lin  k_ctl_reg:amd 0:28:3:8086:40:40:0
[  779.392139] rtl8821ae-0:rtl8821ae_read_eeprom_info():<0-0> Boot from EFUSE
[  779.405029] rtl8821ae: 
[  779.405198] rtl8821ae-0:_rtl8821ae_read_adapter_info():<0-0> dev_addr: <MAC wlan0>
[  779.405203] rtl8821ae:_rtl8821ae_get_chnl_group(): 5G, Channel 163 in Group not found 
[  779.405205] rtl8821ae:_rtl8821ae_get_chnl_group(): 5G, Channel 163 in Group not found 
[  779.405246] rtl8821ae-0:rtl_btc_init_hal_vars():<0-0> rtl_btc_init_hal_vars, antNum is 2
[  779.405248] rtl8821ae-0:rtl_btc_init_hal_vars():<0-0> rtl_btc_init_hal_vars, bt_exist is 1
[  779.405249] rtl8821ae-0:rtl_btc_init_hal_vars():<0-0> rtl_btc_init_hal_vars, bt_type is 7
[  779.405407] rtl8821ae-0:_rtl_init_hw_ht_capab():<0-0> 1T1R
[  779.405408] rtl8821ae-0:_rtl_init_hw_ht_capab():<0-0> 1T1R
[  779.405428] WARNING: CPU: 2 PID: 25699 at /build/buildd/linux-3.16.0/net/wireless/reg.c:1555 wiphy_apply_custom_regulatory+0x19e/0x1d0 [cfg80211]()
[  779.405429] Modules linked in: rtl8821ae(C+) ctr ccm rpcsec_gss_krb5 nfsv4 snd_hda_codec_conexant snd_hda_codec_generic snd_hda_codec_hdmi intel_rapl x86_pkg_temp_thermal arc4 intel_powerclamp coretemp kvm_intel kvm asus_nb_wmi asus_wmi sparse_keymap bnep rfcomm crct10dif_pclmul crc32_pclmul ghash_clmulni_intel nfsd snd_soc_rt5640 uvcvideo snd_soc_rl6231 snd_hda_intel auth_rpcgss videobuf2_vmalloc snd_soc_core aesni_intel nfs_acl snd_hda_controller mac80211 videobuf2_memops snd_compress nfs aes_x86_64 lrw snd_pcm_dmaengine gf128mul snd_hda_codec videobuf2_core glue_helper v4l2_common snd_hwdep lockd ablk_helper snd_pcm cryptd btusb videodev media sunrpc cfg80211 snd_seq_midi binfmt_misc snd_seq_midi_event fscache joydev snd_rawmidi serio_raw i915 bluetooth snd_seq mei_me mei wmi snd_seq_device 6lowpan_iphc
[  779.405457]  snd_timer shpchp lpc_ich hid_multitouch snd drm_kms_helper drm nls_iso8859_1 dw_dmac soundcore 8250_dw dw_dmac_core snd_soc_sst_acpi i2c_algo_bit i2c_hid i2c_designware_platform spi_pxa2xx_platform i2c_designware_core video mac_hid parport_pc ppdev lp parport hid_generic usbhid hid ahci libahci psmouse(OE) sdhci_acpi sdhci [last unloaded: rtl8821ae]
[  779.405501]  [<ffffffffc0a82780>] ? rtl_regd_init+0x2f0/0x2f0 [rtl8821ae]
[  779.405521]  [<ffffffffc0a82780>] ? rtl_regd_init+0x2f0/0x2f0 [rtl8821ae]
[  779.405526]  [<ffffffffc0a826a7>] rtl_regd_init+0x217/0x2f0 [rtl8821ae]
[  779.405532]  [<ffffffffc0a7cf3c>] rtl_init_core+0x15c/0x810 [rtl8821ae]
[  779.405543]  [<ffffffffc0a91515>] rtl_pci_probe+0x355/0xc10 [rtl8821ae]
[  779.405582]  [<ffffffffc0b0702c>] rtl8821ae_module_init+0x2c/0x1000 [rtl8821ae]
[  779.407353] rtlwifi: wireless switch is on
[  779.407376] rtl8821ae-0:rtl_pci_intr_mode_legacy():<0-0> Pin-based Interrupt Mode!
[  779.411953] rtl8821ae-0:rtl_pci_start():<0-0>  rtl_pci_start 
[  779.421600] rtl8821ae-0:rtl8821ae_download_fw():<0-0> normal Firmware SIZE 28984 
[  779.421605] rtl8821ae-0:rtl8821ae_download_fw():<0-0> Firmware Version(20), Signature(0x2101),Size(32)
[  779.434478] rtl8821ae-0:_rtl8821ae_fw_free_to_go():<0-0> Checksum report OK ! REG_MCUFWDL:0x00070604 .
[  779.465770] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 0][RfPath 0][TxNum 0][RateSection 0] = 0x32343638
[  779.465774] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 0][RfPath 0][TxNum 0][RateSection 1] = 0x36363838
[  779.465775] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 0][RfPath 0][TxNum 0][RateSection 2] = 0x28303234
[  779.465777] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 0][RfPath 0][TxNum 0][RateSection 3] = 0x34363838
[  779.465778] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 0][RfPath 0][TxNum 0][RateSection 4] = 0x26283032
[  779.465779] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 0][RfPath 0][TxNum 0][RateSection 7] = 0x32343636
[  779.465781] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 0][RfPath 0][TxNum 0][RateSection 8] = 0x24262830
[  779.465782] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 0][RfPath 0][TxNum 0][RateSection 9] = 0x2022
[  779.465783] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 1][RfPath 0][TxNum 0][RateSection 1] = 0x34343636
[  779.465784] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 1][RfPath 0][TxNum 0][RateSection 2] = 0x26283032
[  779.465786] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 1][RfPath 0][TxNum 0][RateSection 3] = 0x32343636
[  779.465787] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 1][RfPath 0][TxNum 0][RateSection 4] = 0x24262830
[  779.465788] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 1][RfPath 0][TxNum 0][RateSection 7] = 0x32343636
[  779.465790] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 1][RfPath 0][TxNum 0][RateSection 8] = 0x24262830
[  779.465791] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 1][RfPath 0][TxNum 0][RateSection 9] = 0x2022
[  779.566285] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  779.566320] rtl8821ae-0:rtl8821ae_enable_hw_security_config():<0-0> PairwiseEncAlgorithm = 0 GroupEncAlgorithm = 0
[  779.566325] rtl8821ae-0:rtl8821ae_enable_hw_security_config():<0-0> The SECR-value cc 
[  779.566574] rtl8821ae-0:rtl8821ae_set_hw_reg():<0-0> switch case not process 3e
[  779.566581] rtl8821ae-0:rtl_pci_start():<0-0> rtl_pci_start OK
[  779.567025] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  780.206493] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  781.610452] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  796.092360] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  797.495619] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  797.496642] wlan0: authenticate with <MAC C-01 faidherbe_EXT>
[  797.496990] rtl8821ae-0:rtl_op_bss_info_changed():<0-0> bssid: <MAC C-01 faidherbe_EXT>
[  797.497125] wlan0: send auth to <MAC C-01 faidherbe_EXT> (try 1/3)
[  797.497145] rtl8821ae-0:rtl_tx_mgmt_proc():<200-1> MAC80211_LINKING
[  797.500307] wlan0: authenticated
[  797.503603] wlan0: associate with <MAC C-01 faidherbe_EXT> (try 1/3)
[  797.506687] wlan0: RX AssocResp from <MAC C-01 faidherbe_EXT> (capab=0x411 status=0 aid=3)
[  797.506708] rtl8821ae-0:rtl_op_sta_add():<0-0> Add sta addr is <MAC C-01 faidherbe_EXT>
[  797.506717] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> ratr_bitmap :ff005
[  797.506723] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> Rate_index:0, ratr_val:ff005, 0:81:0:5:f0:f:0
[  797.506768] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> ratr_bitmap :ff005
[  797.506774] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> Rate_index:0, ratr_val:ff005, 0:81:0:5:f0:f:0
[  797.506804] rtl8821ae-0:rtl_op_bss_info_changed():<0-0> BSS_CHANGED_ASSOC
[  797.506824] rtl8821ae-0:rtl8821ae_set_hw_reg():<0-0> switch case not process 5c
[  797.506847] rtl8821ae: 
[  797.506855] rtl8821ae_set_fw_rsvdpagepkt(): HW_VAR_SET_TX_CMD: ALL 
[  797.506873] rtl8821ae: 
[  797.506943] wlan0: associated
[  797.506989] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  797.515951] rtl8821ae-0:rtl_is_special_data():<10000-1> 802.1X Rx EAPOL pkt!!
[  797.526517] rtl8821ae-0:rtl_is_special_data():<10000-1> 802.1X Rx EAPOL pkt!!
[  797.526820] rtl8821ae-0:rtl_op_set_key():<0-0> Using hardware based encryption for keyidx: 0, mac: <MAC C-01 faidherbe_EXT>
[  797.526828] rtl8821ae-0:rtl_op_set_key():<0-0> alg:CCMP
[  797.526832] rtl8821ae-0:rtl_op_set_key():<0-0> set enable_hw_sec, key_type:4(OPEN:0 WEP40:1 TKIP:2 AES:4 WEP104:5)
[  797.526836] rtl8821ae-0:rtl8821ae_enable_hw_security_config():<0-0> PairwiseEncAlgorithm = 4 GroupEncAlgorithm = 0
[  797.526845] rtl8821ae-0:rtl8821ae_enable_hw_security_config():<0-0> The SECR-value cc 
[  797.526851] rtl8821ae-0:rtl_op_set_key():<0-0> set pairwise key
[  797.526854] rtl8821ae-0:rtl8821ae_set_key():<0-0> add one entry
[  797.526857] rtl8821ae-0:rtl8821ae_set_key():<0-0> set Pairwiase key
[  797.526860] rtl8821ae-0:rtl_cam_add_one_entry():<0-0> EntryNo:4, ulKeyId=0, ulEncAlg=4, ulUseDK=0 MacAddr <MAC C-01 faidherbe_EXT>
[  797.526863] rtl8821ae: 
[  797.527552] rtl8821ae-0:rtl_cam_add_one_entry():<0-0> end 
[  797.527721] rtl8821ae-0:rtl_op_set_key():<0-0> Using hardware based encryption for keyidx: 1, mac: <MAC ID removed>
[  797.527727] rtl8821ae-0:rtl_op_set_key():<0-0> alg:CCMP
[  797.527729] rtl8821ae-0:rtl_op_set_key():<0-0> set group key
[  797.527732] rtl8821ae-0:rtl8821ae_set_key():<0-0> add one entry
[  797.527734] rtl8821ae-0:rtl8821ae_set_key():<0-0> set group key
[  797.527737] rtl8821ae-0:rtl_cam_add_one_entry():<0-0> EntryNo:1, ulKeyId=1, ulEncAlg=4, ulUseDK=0 MacAddr <MAC ID removed>
[  797.527739] rtl8821ae: 
[  797.528392] rtl8821ae-0:rtl_cam_add_one_entry():<0-0> end 
[  797.575570] rtl8821ae-0:rtl_tx_agg_start():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0 seq:2
[  797.575587] rtl8821ae-0:rtl_action_proc():<200-1> Tx ACT_ADDBAREQ From :<MAC wlan0>
[  797.575591] rtl8821ae: 
[  797.577071] rtl8821ae-0:rtl_action_proc():<10000-1> Rx ACT_ADDBARSP From :<MAC C-01 faidherbe_EXT>
[  797.577089] rtl8821ae-0:rtl_tx_agg_oper():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0
[  797.599546] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> ratr_bitmap :f0000
[  797.599551] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> Rate_index:0, ratr_val:f0000, 0:81:0:0:0:f:0
[  801.478093] rtl8821ae-0:rtl_action_proc():<10000-1> Rx ACT_ADDBAREQ From :<MAC C-01 faidherbe_EXT>
[  801.478105] rtl8821ae: 
[  801.478256] rtl8821ae-0:rtl_rx_agg_start():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0 seq:19
[  801.478275] rtl8821ae-0:rtl_action_proc():<200-1> Tx ACT_ADDBARSP From :<MAC wlan0>
[  831.637797] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off for 2 s
[  833.639686] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off for 4 s
[  845.211365] rtl8821ae-0:rtl_tx_agg_stop():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0
[  880.849693] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  880.957631] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  885.972228] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  886.080135] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  891.086816] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  891.194741] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  896.193485] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  896.301325] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  901.304032] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  901.411975] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  906.427604] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  906.535588] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  911.532760] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  911.640691] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  916.637915] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  916.745912] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  921.759123] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  921.867028] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  926.884269] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  926.992215] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  932.029359] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  932.137308] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  937.138501] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  937.246544] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  942.255660] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  942.363700] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  942.364104] rtl8821ae-0:rtl_action_proc():<400-1> ACT_ADDBADEL From :<MAC wlan0>
[  943.762942] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off for 6 s
[  945.765839] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off for 8 s
[  947.768652] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off for 10 s
[  947.768656] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off, try to reconnect now
[  947.768688] wlan0: Connection to AP <MAC C-01 faidherbe_EXT> lost
[  949.772096] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off for 2 s
[  951.774454] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off for 4 s
[  952.565937] rtl8821ae-0:rtl_rx_agg_stop():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0
[  952.565988] rtl8821ae-0:rtl_op_set_key():<0-0> Disabling hardware based encryption for keyidx: 0, mac: <MAC C-01 faidherbe_EXT>
[  952.565992] rtl8821ae-0:rtl_op_set_key():<0-0> alg:CCMP
[  952.565994] rtl8821ae-0:rtl_op_set_key():<0-0> set enable_hw_sec, key_type:4(OPEN:0 WEP40:1 TKIP:2 AES:4 WEP104:5)
[  952.565997] rtl8821ae-0:rtl8821ae_enable_hw_security_config():<0-0> PairwiseEncAlgorithm = 4 GroupEncAlgorithm = 4
[  952.566003] rtl8821ae-0:rtl8821ae_enable_hw_security_config():<0-0> The SECR-value cc 
[  952.566007] rtl8821ae-0:rtl_op_set_key():<0-0> disable key delete one entry
[  952.566009] rtl8821ae-0:rtl_cam_delete_one_entry():<0-0> key_idx:0
[  952.566014] rtl8821ae-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A4: 0 
[  952.566016] rtl8821ae-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A0: 80010000 
[  952.566048] rtl8821ae-0:rtl_op_sta_remove():<0-0> Remove sta addr is <MAC C-01 faidherbe_EXT>
[  952.566102] rtl8821ae-0:rtl_op_bss_info_changed():<0-0> BSS_CHANGED_UN_ASSOC
[  952.566126] rtl8821ae-0:rtl_op_bss_info_changed():<0-0> bssid: <MAC ID removed>
[  954.972699] rtl8821ae-0:rtl_op_set_key():<0-0> Disabling hardware based encryption for keyidx: 1, mac: <MAC ID removed>
[  954.972711] rtl8821ae-0:rtl_op_set_key():<0-0> alg:CCMP
[  954.972714] rtl8821ae-0:rtl_op_set_key():<0-0> disable key delete one entry
[  954.972717] rtl8821ae-0:rtl_cam_delete_one_entry():<0-0> key_idx:1
[  954.972725] rtl8821ae-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A4: 0 
[  954.972727] rtl8821ae-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A0: 80010008 
[  955.054239] rtl8821ae: module is from the staging directory, the quality is unknown, you have been warned.
[  955.055351] rtl8821ae-0:rtl_pci_probe():<0-0> mem mapped space: start: 0xf7c00000 len:00004000 flags:00140204, after map:0xffffc90004780000
[  955.055365] rtl8821ae-0:_rtl_pci_find_adapter():<0-0> Pci Bridge Vendor is found index: 0
[  955.055367] rtl8821ae-0:_rtl_pci_find_adapter():<0-0> pcidev busnumber:devnumber:funcnumber:vendor:link_ctl 2:0:0:10ec:0
[  955.055369] rtl8821ae-0:_rtl_pci_find_adapter():<0-0> pci_bridge busnumber:devnumber:funcnumber:vendor:pcie_cap:lin  k_ctl_reg:amd 0:28:3:8086:40:40:0
[  955.055393] rtl8821ae-0:rtl8821ae_read_eeprom_info():<0-0> Boot from EFUSE
[  955.068277] rtl8821ae: 
[  955.068448] rtl8821ae-0:_rtl8821ae_read_adapter_info():<0-0> dev_addr: <MAC wlan0>
[  955.068453] rtl8821ae:_rtl8821ae_get_chnl_group(): 5G, Channel 163 in Group not found 
[  955.068455] rtl8821ae:_rtl8821ae_get_chnl_group(): 5G, Channel 163 in Group not found 
[  955.068495] rtl8821ae-0:rtl_btc_init_hal_vars():<0-0> rtl_btc_init_hal_vars, antNum is 2
[  955.068496] rtl8821ae-0:rtl_btc_init_hal_vars():<0-0> rtl_btc_init_hal_vars, bt_exist is 1
[  955.068511] rtl8821ae-0:rtl_btc_init_hal_vars():<0-0> rtl_btc_init_hal_vars, bt_type is 7
[  955.068678] rtl8821ae-0:_rtl_init_hw_ht_capab():<0-0> 1T1R
[  955.068679] rtl8821ae-0:_rtl_init_hw_ht_capab():<0-0> 1T1R
[  955.068700] WARNING: CPU: 2 PID: 31307 at /build/buildd/linux-3.16.0/net/wireless/reg.c:1555 wiphy_apply_custom_regulatory+0x19e/0x1d0 [cfg80211]()
[  955.068702] Modules linked in: rtl8821ae(C+) ctr ccm rpcsec_gss_krb5 nfsv4 snd_hda_codec_conexant snd_hda_codec_generic snd_hda_codec_hdmi intel_rapl x86_pkg_temp_thermal arc4 intel_powerclamp coretemp kvm_intel kvm asus_nb_wmi asus_wmi sparse_keymap bnep rfcomm crct10dif_pclmul crc32_pclmul ghash_clmulni_intel nfsd snd_soc_rt5640 uvcvideo snd_soc_rl6231 snd_hda_intel auth_rpcgss videobuf2_vmalloc snd_soc_core aesni_intel nfs_acl snd_hda_controller mac80211 videobuf2_memops snd_compress nfs aes_x86_64 lrw snd_pcm_dmaengine gf128mul snd_hda_codec videobuf2_core glue_helper v4l2_common snd_hwdep lockd ablk_helper snd_pcm cryptd btusb videodev media sunrpc cfg80211 snd_seq_midi binfmt_misc snd_seq_midi_event fscache joydev snd_rawmidi serio_raw i915 bluetooth snd_seq mei_me mei wmi snd_seq_device 6lowpan_iphc
[  955.068729]  snd_timer shpchp lpc_ich hid_multitouch snd drm_kms_helper drm nls_iso8859_1 dw_dmac soundcore 8250_dw dw_dmac_core snd_soc_sst_acpi i2c_algo_bit i2c_hid i2c_designware_platform spi_pxa2xx_platform i2c_designware_core video mac_hid parport_pc ppdev lp parport hid_generic usbhid hid ahci libahci psmouse(OE) sdhci_acpi sdhci [last unloaded: rtl8821ae]
[  955.068777]  [<ffffffffc0c63780>] ? rtl_regd_init+0x2f0/0x2f0 [rtl8821ae]
[  955.068798]  [<ffffffffc0c63780>] ? rtl_regd_init+0x2f0/0x2f0 [rtl8821ae]
[  955.068803]  [<ffffffffc0c636a7>] rtl_regd_init+0x217/0x2f0 [rtl8821ae]
[  955.068809]  [<ffffffffc0c5df3c>] rtl_init_core+0x15c/0x810 [rtl8821ae]
[  955.068820]  [<ffffffffc0c72515>] rtl_pci_probe+0x355/0xc10 [rtl8821ae]
[  955.068859]  [<ffffffffc0b0702c>] rtl8821ae_module_init+0x2c/0x1000 [rtl8821ae]
[  955.071070] rtl8821ae-0:rtl8821ae_phy_set_bw_mode():<0-0> FALSE driver sleep or unload
[  955.071104] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  955.073160] rtlwifi: wireless switch is on
[  955.073176] rtl8821ae-0:rtl_pci_intr_mode_legacy():<0-0> Pin-based Interrupt Mode!
[  955.101669] rtl8821ae-0:rtl8821ae_phy_set_bw_mode():<0-0> FALSE driver sleep or unload
[  955.157202] rtl8821ae-0:rtl8821ae_phy_set_bw_mode():<0-0> FALSE driver sleep or unload
[  955.213603] rtl8821ae-0:rtl8821ae_phy_set_bw_mode():<0-0> FALSE driver sleep or unload
[  955.269564] rtl8821ae-0:rtl8821ae_phy_set_bw_mode():<0-0> FALSE driver sleep or unload
[  955.325058] rtl8821ae-0:rtl8821ae_phy_set_bw_mode():<0-0> FALSE driver sleep or unload
[  955.381191] rtl8821ae-0:rtl8821ae_phy_set_bw_mode():<0-0> FALSE driver sleep or unload
[  955.437048] rtl8821ae-0:rtl8821ae_phy_set_bw_mode():<0-0> FALSE driver sleep or unload
[  955.493011] rtl8821ae-0:rtl8821ae_phy_set_bw_mode():<0-0> FALSE driver sleep or unload
[  955.548963] rtl8821ae-0:rtl8821ae_phy_set_bw_mode():<0-0> FALSE driver sleep or unload
[  955.608887] rtl8821ae-0:rtl8821ae_phy_set_bw_mode():<0-0> FALSE driver sleep or unload
[  955.665829] rtl8821ae-0:rtl8821ae_phy_set_bw_mode():<0-0> FALSE driver sleep or unload
[  955.720828] rtl8821ae-0:rtl8821ae_phy_set_bw_mode():<0-0> FALSE driver sleep or unload
[  955.828811] rtl8821ae-0:rtl8821ae_phy_set_bw_mode():<0-0> FALSE driver sleep or unload
[  955.936790] rtl8821ae-0:rtl8821ae_phy_set_bw_mode():<0-0> FALSE driver sleep or unload
[  956.044732] rtl8821ae-0:rtl8821ae_phy_set_bw_mode():<0-0> FALSE driver sleep or unload
[  956.152617] rtl8821ae-0:rtl8821ae_phy_set_bw_mode():<0-0> FALSE driver sleep or unload
[  956.260534] rtl8821ae-0:rtl8821ae_phy_set_bw_mode():<0-0> FALSE driver sleep or unload
[  956.368460] rtl8821ae-0:rtl8821ae_phy_set_bw_mode():<0-0> FALSE driver sleep or unload
[  956.476427] rtl8821ae-0:rtl8821ae_phy_set_bw_mode():<0-0> FALSE driver sleep or unload
[  956.584336] rtl8821ae-0:rtl8821ae_phy_set_bw_mode():<0-0> FALSE driver sleep or unload
[  956.692335] rtl8821ae-0:rtl8821ae_phy_set_bw_mode():<0-0> FALSE driver sleep or unload
[  956.800331] rtl8821ae-0:rtl8821ae_phy_set_bw_mode():<0-0> FALSE driver sleep or unload
[  956.908210] rtl8821ae-0:rtl8821ae_phy_set_bw_mode():<0-0> FALSE driver sleep or unload
[  957.016167] rtl8821ae-0:rtl8821ae_phy_set_bw_mode():<0-0> FALSE driver sleep or unload
[  957.124081] rtl8821ae-0:rtl8821ae_phy_set_bw_mode():<0-0> FALSE driver sleep or unload
[  966.680195] rtl8821ae: module is from the staging directory, the quality is unknown, you have been warned.
[  966.681298] rtl8821ae-0:rtl_pci_probe():<0-0> mem mapped space: start: 0xf7c00000 len:00004000 flags:00140204, after map:0xffffc90004780000
[  966.681314] rtl8821ae-0:_rtl_pci_find_adapter():<0-0> Pci Bridge Vendor is found index: 0
[  966.681317] rtl8821ae-0:_rtl_pci_find_adapter():<0-0> pcidev busnumber:devnumber:funcnumber:vendor:link_ctl 2:0:0:10ec:0
[  966.681319] rtl8821ae-0:_rtl_pci_find_adapter():<0-0> pci_bridge busnumber:devnumber:funcnumber:vendor:pcie_cap:lin  k_ctl_reg:amd 0:28:3:8086:40:40:0
[  966.681346] rtl8821ae-0:rtl8821ae_read_eeprom_info():<0-0> Boot from EFUSE
[  966.694209] rtl8821ae: 
[  966.694358] rtl8821ae-0:_rtl8821ae_read_adapter_info():<0-0> dev_addr: <MAC wlan0>
[  966.694362] rtl8821ae:_rtl8821ae_get_chnl_group(): 5G, Channel 163 in Group not found 
[  966.694364] rtl8821ae:_rtl8821ae_get_chnl_group(): 5G, Channel 163 in Group not found 
[  966.694407] rtl8821ae-0:rtl_btc_init_hal_vars():<0-0> rtl_btc_init_hal_vars, antNum is 2
[  966.694408] rtl8821ae-0:rtl_btc_init_hal_vars():<0-0> rtl_btc_init_hal_vars, bt_exist is 1
[  966.694410] rtl8821ae-0:rtl_btc_init_hal_vars():<0-0> rtl_btc_init_hal_vars, bt_type is 7
[  966.694567] rtl8821ae-0:_rtl_init_hw_ht_capab():<0-0> 1T1R
[  966.694568] rtl8821ae-0:_rtl_init_hw_ht_capab():<0-0> 1T1R
[  966.694588] WARNING: CPU: 1 PID: 31738 at /build/buildd/linux-3.16.0/net/wireless/reg.c:1555 wiphy_apply_custom_regulatory+0x19e/0x1d0 [cfg80211]()
[  966.694590] Modules linked in: rtl8821ae(C+) ctr ccm rpcsec_gss_krb5 nfsv4 snd_hda_codec_conexant snd_hda_codec_generic snd_hda_codec_hdmi intel_rapl x86_pkg_temp_thermal arc4 intel_powerclamp coretemp kvm_intel kvm asus_nb_wmi asus_wmi sparse_keymap bnep rfcomm crct10dif_pclmul crc32_pclmul ghash_clmulni_intel nfsd snd_soc_rt5640 uvcvideo snd_soc_rl6231 snd_hda_intel auth_rpcgss videobuf2_vmalloc snd_soc_core aesni_intel nfs_acl snd_hda_controller mac80211 videobuf2_memops snd_compress nfs aes_x86_64 lrw snd_pcm_dmaengine gf128mul snd_hda_codec videobuf2_core glue_helper v4l2_common snd_hwdep lockd ablk_helper snd_pcm cryptd btusb videodev media sunrpc cfg80211 snd_seq_midi binfmt_misc snd_seq_midi_event fscache joydev snd_rawmidi serio_raw i915 bluetooth snd_seq mei_me mei wmi snd_seq_device 6lowpan_iphc
[  966.694614]  snd_timer shpchp lpc_ich hid_multitouch snd drm_kms_helper drm nls_iso8859_1 dw_dmac soundcore 8250_dw dw_dmac_core snd_soc_sst_acpi i2c_algo_bit i2c_hid i2c_designware_platform spi_pxa2xx_platform i2c_designware_core video mac_hid parport_pc ppdev lp parport hid_generic usbhid hid ahci libahci psmouse(OE) sdhci_acpi sdhci [last unloaded: rtl8821ae]
[  966.694656]  [<ffffffffc0a82780>] ? rtl_regd_init+0x2f0/0x2f0 [rtl8821ae]
[  966.694674]  [<ffffffffc0a82780>] ? rtl_regd_init+0x2f0/0x2f0 [rtl8821ae]
[  966.694678]  [<ffffffffc0a826a7>] rtl_regd_init+0x217/0x2f0 [rtl8821ae]
[  966.694684]  [<ffffffffc0a7cf3c>] rtl_init_core+0x15c/0x810 [rtl8821ae]
[  966.694694]  [<ffffffffc0a91515>] rtl_pci_probe+0x355/0xc10 [rtl8821ae]
[  966.694728]  [<ffffffffc0b0702c>] rtl8821ae_module_init+0x2c/0x1000 [rtl8821ae]
[  966.696572] rtlwifi: wireless switch is on
[  966.696589] rtl8821ae-0:rtl_pci_intr_mode_legacy():<0-0> Pin-based Interrupt Mode!
[  966.700920] rtl8821ae-0:rtl_pci_start():<0-0>  rtl_pci_start 
[  966.710603] rtl8821ae-0:rtl8821ae_download_fw():<0-0> normal Firmware SIZE 28984 
[  966.710607] rtl8821ae-0:rtl8821ae_download_fw():<0-0> Firmware Version(20), Signature(0x2101),Size(32)
[  966.723438] rtl8821ae-0:_rtl8821ae_fw_free_to_go():<0-0> Checksum report OK ! REG_MCUFWDL:0x00070604 .
[  966.754726] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 0][RfPath 0][TxNum 0][RateSection 0] = 0x32343638
[  966.754729] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 0][RfPath 0][TxNum 0][RateSection 1] = 0x36363838
[  966.754731] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 0][RfPath 0][TxNum 0][RateSection 2] = 0x28303234
[  966.754732] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 0][RfPath 0][TxNum 0][RateSection 3] = 0x34363838
[  966.754734] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 0][RfPath 0][TxNum 0][RateSection 4] = 0x26283032
[  966.754735] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 0][RfPath 0][TxNum 0][RateSection 7] = 0x32343636
[  966.754736] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 0][RfPath 0][TxNum 0][RateSection 8] = 0x24262830
[  966.754737] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 0][RfPath 0][TxNum 0][RateSection 9] = 0x2022
[  966.754739] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 1][RfPath 0][TxNum 0][RateSection 1] = 0x34343636
[  966.754740] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 1][RfPath 0][TxNum 0][RateSection 2] = 0x26283032
[  966.754741] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 1][RfPath 0][TxNum 0][RateSection 3] = 0x32343636
[  966.754742] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 1][RfPath 0][TxNum 0][RateSection 4] = 0x24262830
[  966.754744] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 1][RfPath 0][TxNum 0][RateSection 7] = 0x32343636
[  966.754745] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 1][RfPath 0][TxNum 0][RateSection 8] = 0x24262830
[  966.754746] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 1][RfPath 0][TxNum 0][RateSection 9] = 0x2022
[  966.855238] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  966.855274] rtl8821ae-0:rtl8821ae_enable_hw_security_config():<0-0> PairwiseEncAlgorithm = 0 GroupEncAlgorithm = 0
[  966.855280] rtl8821ae-0:rtl8821ae_enable_hw_security_config():<0-0> The SECR-value cc 
[  966.855522] rtl8821ae-0:rtl8821ae_set_hw_reg():<0-0> switch case not process 3e
[  966.855529] rtl8821ae-0:rtl_pci_start():<0-0> rtl_pci_start OK
[  966.855975] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  967.493693] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  968.900909] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  975.557143] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  976.960404] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  976.960804] wlan0: authenticate with <MAC C-01 faidherbe_EXT>
[  976.961119] rtl8821ae-0:rtl_op_bss_info_changed():<0-0> bssid: <MAC C-01 faidherbe_EXT>
[  976.961191] wlan0: send auth to <MAC C-01 faidherbe_EXT> (try 1/3)
[  976.961199] rtl8821ae-0:rtl_tx_mgmt_proc():<200-1> MAC80211_LINKING
[  976.963486] wlan0: authenticated
[  976.964378] wlan0: associate with <MAC C-01 faidherbe_EXT> (try 1/3)
[  976.967662] wlan0: RX AssocResp from <MAC C-01 faidherbe_EXT> (capab=0x411 status=0 aid=3)
[  976.967672] rtl8821ae-0:rtl_op_sta_add():<0-0> Add sta addr is <MAC C-01 faidherbe_EXT>
[  976.967676] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> ratr_bitmap :ff005
[  976.967678] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> Rate_index:0, ratr_val:ff005, 0:81:0:5:f0:f:0
[  976.967711] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> ratr_bitmap :ff005
[  976.967713] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> Rate_index:0, ratr_val:ff005, 0:81:0:5:f0:f:0
[  976.967734] rtl8821ae-0:rtl_op_bss_info_changed():<0-0> BSS_CHANGED_ASSOC
[  976.967749] rtl8821ae-0:rtl8821ae_set_hw_reg():<0-0> switch case not process 5c
[  976.967767] rtl8821ae: 
[  976.967770] rtl8821ae_set_fw_rsvdpagepkt(): HW_VAR_SET_TX_CMD: ALL 
[  976.967778] rtl8821ae: 
[  976.967829] wlan0: associated
[  976.967850] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  977.151816] rtl8821ae-0:rtl_is_special_data():<10000-1> 802.1X Rx EAPOL pkt!!
[  977.211091] rtl8821ae-0:rtl_is_special_data():<10000-1> 802.1X Rx EAPOL pkt!!
[  977.211369] rtl8821ae-0:rtl_op_set_key():<0-0> Using hardware based encryption for keyidx: 0, mac: <MAC C-01 faidherbe_EXT>
[  977.211374] rtl8821ae-0:rtl_op_set_key():<0-0> alg:CCMP
[  977.211376] rtl8821ae-0:rtl_op_set_key():<0-0> set enable_hw_sec, key_type:4(OPEN:0 WEP40:1 TKIP:2 AES:4 WEP104:5)
[  977.211379] rtl8821ae-0:rtl8821ae_enable_hw_security_config():<0-0> PairwiseEncAlgorithm = 4 GroupEncAlgorithm = 0
[  977.211386] rtl8821ae-0:rtl8821ae_enable_hw_security_config():<0-0> The SECR-value cc 
[  977.211390] rtl8821ae-0:rtl_op_set_key():<0-0> set pairwise key
[  977.211392] rtl8821ae-0:rtl8821ae_set_key():<0-0> add one entry
[  977.211394] rtl8821ae-0:rtl8821ae_set_key():<0-0> set Pairwiase key
[  977.211396] rtl8821ae-0:rtl_cam_add_one_entry():<0-0> EntryNo:4, ulKeyId=0, ulEncAlg=4, ulUseDK=0 MacAddr <MAC C-01 faidherbe_EXT>
[  977.211398] rtl8821ae: 
[  977.212046] rtl8821ae-0:rtl_cam_add_one_entry():<0-0> end 
[  977.212229] rtl8821ae-0:rtl_op_set_key():<0-0> Using hardware based encryption for keyidx: 1, mac: <MAC ID removed>
[  977.212234] rtl8821ae-0:rtl_op_set_key():<0-0> alg:CCMP
[  977.212237] rtl8821ae-0:rtl_op_set_key():<0-0> set group key
[  977.212240] rtl8821ae-0:rtl8821ae_set_key():<0-0> add one entry
[  977.212243] rtl8821ae-0:rtl8821ae_set_key():<0-0> set group key
[  977.212245] rtl8821ae-0:rtl_cam_add_one_entry():<0-0> EntryNo:1, ulKeyId=1, ulEncAlg=4, ulUseDK=0 MacAddr <MAC ID removed>
[  977.212248] rtl8821ae: 
[  977.212914] rtl8821ae-0:rtl_cam_add_one_entry():<0-0> end 
[  977.332235] rtl8821ae-0:rtl_tx_agg_start():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0 seq:3
[  977.332258] rtl8821ae-0:rtl_action_proc():<200-1> Tx ACT_ADDBAREQ From :<MAC wlan0>
[  977.332260] rtl8821ae: 
[  977.333978] rtl8821ae-0:rtl_action_proc():<10000-1> Rx ACT_ADDBARSP From :<MAC C-01 faidherbe_EXT>
[  977.334033] rtl8821ae-0:rtl_tx_agg_oper():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0
[  978.871380] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> ratr_bitmap :f0000
[  978.871387] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> Rate_index:0, ratr_val:f0000, 0:81:0:0:0:f:0
[  981.305969] rtl8821ae-0:rtl_action_proc():<10000-1> Rx ACT_ADDBAREQ From :<MAC C-01 faidherbe_EXT>
[  981.305974] rtl8821ae: 
[  981.306071] rtl8821ae-0:rtl_rx_agg_start():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0 seq:19
[  981.306082] rtl8821ae-0:rtl_action_proc():<200-1> Tx ACT_ADDBARSP From :<MAC wlan0>
[  981.310660] rtl8821ae-0:rtl_action_proc():<10000-1> Rx ACT_ADDBAREQ From :<MAC C-01 faidherbe_EXT>
[  981.310664] rtl8821ae: 
[  981.310688] rtl8821ae: 
[  981.310756] rtl8821ae-0:rtl_rx_agg_stop():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0
[  981.310769] rtl8821ae-0:rtl_rx_agg_start():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0 seq:19
[  981.310783] rtl8821ae-0:rtl_action_proc():<200-1> Tx ACT_ADDBARSP From :<MAC wlan0>
[  993.818762] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  993.925119] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  994.186695] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  994.293124] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  994.554661] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  994.661129] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  994.922653] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  995.029057] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  995.290639] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  995.397037] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  995.658581] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  995.765071] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  996.026563] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  996.133060] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  996.394574] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  996.501029] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  996.762550] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  996.868996] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  997.130563] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  997.236941] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  997.498530] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  997.605368] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  997.866494] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  997.972946] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  998.234507] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  998.340891] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1000.908797] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off for 2 s
[ 1002.912756] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off for 4 s
[ 1004.916577] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off for 6 s
[ 1006.920441] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off for 8 s
[ 1008.924389] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off for 10 s
[ 1008.924394] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off, try to reconnect now
[ 1008.924410] wlan0: Connection to AP <MAC C-01 faidherbe_EXT> lost
[ 1008.932355] rtl8821ae-0:rtl_tx_agg_stop():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0
[ 1008.932367] rtl8821ae-0:rtl_rx_agg_stop():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0
[ 1008.944411] rtl8821ae-0:rtl_op_set_key():<0-0> Disabling hardware based encryption for keyidx: 0, mac: <MAC C-01 faidherbe_EXT>
[ 1008.944418] rtl8821ae-0:rtl_op_set_key():<0-0> alg:CCMP
[ 1008.944420] rtl8821ae-0:rtl_op_set_key():<0-0> set enable_hw_sec, key_type:4(OPEN:0 WEP40:1 TKIP:2 AES:4 WEP104:5)
[ 1008.944423] rtl8821ae-0:rtl8821ae_enable_hw_security_config():<0-0> PairwiseEncAlgorithm = 4 GroupEncAlgorithm = 4
[ 1008.944431] rtl8821ae-0:rtl8821ae_enable_hw_security_config():<0-0> The SECR-value cc 
[ 1008.944435] rtl8821ae-0:rtl_op_set_key():<0-0> disable key delete one entry
[ 1008.944438] rtl8821ae-0:rtl_cam_delete_one_entry():<0-0> key_idx:0
[ 1008.944443] rtl8821ae-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A4: 0 
[ 1008.944445] rtl8821ae-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A0: 80010000 
[ 1008.944486] rtl8821ae-0:rtl_op_sta_remove():<0-0> Remove sta addr is <MAC C-01 faidherbe_EXT>
[ 1008.944548] rtl8821ae-0:rtl_op_bss_info_changed():<0-0> BSS_CHANGED_UN_ASSOC
[ 1008.944574] rtl8821ae-0:rtl_op_bss_info_changed():<0-0> bssid: <MAC ID removed>
[ 1008.960388] rtl8821ae-0:rtl_op_set_key():<0-0> Disabling hardware based encryption for keyidx: 1, mac: <MAC ID removed>
[ 1008.960395] rtl8821ae-0:rtl_op_set_key():<0-0> alg:CCMP
[ 1008.960397] rtl8821ae-0:rtl_op_set_key():<0-0> disable key delete one entry
[ 1008.960399] rtl8821ae-0:rtl_cam_delete_one_entry():<0-0> key_idx:1
[ 1008.960407] rtl8821ae-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A4: 0 
[ 1008.960409] rtl8821ae-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A0: 80010008 
[ 1009.660282] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1011.064212] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1011.065234] wlan0: authenticate with <MAC C-01 faidherbe_EXT>
[ 1011.065592] rtl8821ae-0:rtl_op_bss_info_changed():<0-0> bssid: <MAC C-01 faidherbe_EXT>
[ 1011.065744] wlan0: send auth to <MAC C-01 faidherbe_EXT> (try 1/3)
[ 1011.065764] rtl8821ae-0:rtl_tx_mgmt_proc():<200-1> MAC80211_LINKING
[ 1011.068702] wlan0: authenticated
[ 1011.072175] wlan0: associate with <MAC C-01 faidherbe_EXT> (try 1/3)
[ 1011.075328] wlan0: RX AssocResp from <MAC C-01 faidherbe_EXT> (capab=0x411 status=0 aid=3)
[ 1011.075349] rtl8821ae-0:rtl_op_sta_add():<0-0> Add sta addr is <MAC C-01 faidherbe_EXT>
[ 1011.075357] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> ratr_bitmap :ff005
[ 1011.075361] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> Rate_index:0, ratr_val:ff005, 0:81:0:5:f0:f:0
[ 1011.075402] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> ratr_bitmap :ff005
[ 1011.075405] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> Rate_index:0, ratr_val:ff005, 0:81:0:5:f0:f:0
[ 1011.075432] rtl8821ae-0:rtl_op_bss_info_changed():<0-0> BSS_CHANGED_ASSOC
[ 1011.075451] rtl8821ae-0:rtl8821ae_set_hw_reg():<0-0> switch case not process 5c
[ 1011.075476] rtl8821ae: 
[ 1011.075482] rtl8821ae_set_fw_rsvdpagepkt(): HW_VAR_SET_TX_CMD: ALL 
[ 1011.075497] rtl8821ae: 
[ 1011.075560] wlan0: associated
[ 1011.080472] rtl8821ae-0:rtl_is_special_data():<10000-1> 802.1X Rx EAPOL pkt!!
[ 1011.090224] rtl8821ae-0:rtl_is_special_data():<10000-1> 802.1X Rx EAPOL pkt!!
[ 1011.090657] rtl8821ae-0:rtl_op_set_key():<0-0> Using hardware based encryption for keyidx: 0, mac: <MAC C-01 faidherbe_EXT>
[ 1011.090666] rtl8821ae-0:rtl_op_set_key():<0-0> alg:CCMP
[ 1011.090669] rtl8821ae-0:rtl_op_set_key():<0-0> set enable_hw_sec, key_type:4(OPEN:0 WEP40:1 TKIP:2 AES:4 WEP104:5)
[ 1011.090673] rtl8821ae-0:rtl8821ae_enable_hw_security_config():<0-0> PairwiseEncAlgorithm = 4 GroupEncAlgorithm = 0
[ 1011.090682] rtl8821ae-0:rtl8821ae_enable_hw_security_config():<0-0> The SECR-value cc 
[ 1011.090688] rtl8821ae-0:rtl_op_set_key():<0-0> set pairwise key
[ 1011.090691] rtl8821ae-0:rtl8821ae_set_key():<0-0> add one entry
[ 1011.090694] rtl8821ae-0:rtl8821ae_set_key():<0-0> set Pairwiase key
[ 1011.090697] rtl8821ae-0:rtl_cam_add_one_entry():<0-0> EntryNo:4, ulKeyId=0, ulEncAlg=4, ulUseDK=0 MacAddr <MAC C-01 faidherbe_EXT>
[ 1011.090701] rtl8821ae: 
[ 1011.091358] rtl8821ae-0:rtl_cam_add_one_entry():<0-0> end 
[ 1011.091542] rtl8821ae-0:rtl_op_set_key():<0-0> Using hardware based encryption for keyidx: 1, mac: <MAC ID removed>
[ 1011.091547] rtl8821ae-0:rtl_op_set_key():<0-0> alg:CCMP
[ 1011.091550] rtl8821ae-0:rtl_op_set_key():<0-0> set group key
[ 1011.091553] rtl8821ae-0:rtl8821ae_set_key():<0-0> add one entry
[ 1011.091555] rtl8821ae-0:rtl8821ae_set_key():<0-0> set group key
[ 1011.091558] rtl8821ae-0:rtl_cam_add_one_entry():<0-0> EntryNo:1, ulKeyId=1, ulEncAlg=4, ulUseDK=0 MacAddr <MAC ID removed>
[ 1011.091561] rtl8821ae: 
[ 1011.092258] rtl8821ae-0:rtl_cam_add_one_entry():<0-0> end 
[ 1011.222315] rtl8821ae-0:rtl_action_proc():<10000-1> Rx ACT_ADDBAREQ From :<MAC C-01 faidherbe_EXT>
[ 1011.222320] rtl8821ae: 
[ 1011.222407] rtl8821ae-0:rtl_rx_agg_start():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0 seq:0
[ 1011.222421] rtl8821ae-0:rtl_action_proc():<200-1> Tx ACT_ADDBARSP From :<MAC wlan0>
[ 1011.776238] rtl8821ae-0:rtl_tx_agg_start():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0 seq:1
[ 1011.776268] rtl8821ae-0:rtl_action_proc():<200-1> Tx ACT_ADDBAREQ From :<MAC wlan0>
[ 1011.776271] rtl8821ae: 
[ 1011.778200] rtl8821ae-0:rtl_action_proc():<10000-1> Rx ACT_ADDBARSP From :<MAC C-01 faidherbe_EXT>
[ 1011.778262] rtl8821ae-0:rtl_tx_agg_oper():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0
[ 1031.387019] rtl8821ae-0:rtl_tx_agg_stop():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0
[ 1031.387038] rtl8821ae-0:rtl_action_proc():<400-1> ACT_ADDBADEL From :<MAC wlan0>
[ 1034.766945] rtl8821ae-0:rtl_tx_agg_start():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0 seq:1212
[ 1034.769315] rtl8821ae-0:rtl_action_proc():<10000-1> Rx ACT_ADDBARSP From :<MAC C-01 faidherbe_EXT>
[ 1035.770884] rtl8821ae-0:rtl_tx_agg_stop():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0
[ 1036.816405] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1036.922733] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1037.184338] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1037.290735] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1037.552279] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1037.658667] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1037.920271] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1037.974660] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1038.236254] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1038.342639] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1038.604225] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1038.710675] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1038.972287] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1039.078666] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1039.340157] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1039.446643] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1039.708195] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1039.814645] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1040.076147] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1040.182594] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1040.444153] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1040.550565] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1040.812083] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1040.918559] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1041.180135] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1041.286490] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1041.286956] rtl8821ae-0:rtl_action_proc():<400-1> ACT_ADDBADEL From :<MAC wlan0>
[ 1041.350565] rtl8821ae-0:rtl_tx_agg_start():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0 seq:1243
[ 1041.350585] rtl8821ae-0:rtl_action_proc():<200-1> Tx ACT_ADDBAREQ From :<MAC wlan0>
[ 1041.350588] rtl8821ae: 
[ 1041.352549] rtl8821ae-0:rtl_action_proc():<10000-1> Rx ACT_ADDBARSP From :<MAC C-01 faidherbe_EXT>
[ 1041.352594] rtl8821ae-0:rtl_tx_agg_oper():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0
[ 1044.993983] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off for 2 s
[ 1046.996881] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off for 4 s
[ 1048.999804] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off for 6 s
[ 1051.002733] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off for 8 s
[ 1053.005595] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off for 10 s
[ 1053.005600] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off, try to reconnect now
[ 1053.005661] wlan0: Connection to AP <MAC C-01 faidherbe_EXT> lost
[ 1053.013578] rtl8821ae-0:rtl_tx_agg_stop():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0
[ 1053.013603] rtl8821ae-0:rtl_rx_agg_stop():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0
[ 1053.025534] rtl8821ae-0:rtl_op_set_key():<0-0> Disabling hardware based encryption for keyidx: 0, mac: <MAC C-01 faidherbe_EXT>
[ 1053.025544] rtl8821ae-0:rtl_op_set_key():<0-0> alg:CCMP
[ 1053.025547] rtl8821ae-0:rtl_op_set_key():<0-0> set enable_hw_sec, key_type:4(OPEN:0 WEP40:1 TKIP:2 AES:4 WEP104:5)
[ 1053.025549] rtl8821ae-0:rtl8821ae_enable_hw_security_config():<0-0> PairwiseEncAlgorithm = 4 GroupEncAlgorithm = 4
[ 1053.025557] rtl8821ae-0:rtl8821ae_enable_hw_security_config():<0-0> The SECR-value cc 
[ 1053.025562] rtl8821ae-0:rtl_op_set_key():<0-0> disable key delete one entry
[ 1053.025564] rtl8821ae-0:rtl_cam_delete_one_entry():<0-0> key_idx:0
[ 1053.025570] rtl8821ae-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A4: 0 
[ 1053.025572] rtl8821ae-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A0: 80010000 
[ 1053.025641] rtl8821ae-0:rtl_op_sta_remove():<0-0> Remove sta addr is <MAC C-01 faidherbe_EXT>
[ 1053.025701] rtl8821ae-0:rtl_op_bss_info_changed():<0-0> BSS_CHANGED_UN_ASSOC
[ 1053.025727] rtl8821ae-0:rtl_op_bss_info_changed():<0-0> bssid: <MAC ID removed>
[ 1053.041600] rtl8821ae-0:rtl_op_set_key():<0-0> Disabling hardware based encryption for keyidx: 1, mac: <MAC ID removed>
[ 1053.041607] rtl8821ae-0:rtl_op_set_key():<0-0> alg:CCMP
[ 1053.041609] rtl8821ae-0:rtl_op_set_key():<0-0> disable key delete one entry
[ 1053.041611] rtl8821ae-0:rtl_cam_delete_one_entry():<0-0> key_idx:1
[ 1053.041619] rtl8821ae-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A4: 0 
[ 1053.041621] rtl8821ae-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A0: 80010008 
[ 1053.745117] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1055.148307] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1055.148981] wlan0: authenticate with <MAC C-01 faidherbe_EXT>
[ 1055.149310] rtl8821ae-0:rtl_op_bss_info_changed():<0-0> bssid: <MAC C-01 faidherbe_EXT>
[ 1055.149430] wlan0: send auth to <MAC C-01 faidherbe_EXT> (try 1/3)
[ 1055.149444] rtl8821ae-0:rtl_tx_mgmt_proc():<200-1> MAC80211_LINKING
[ 1055.151081] wlan0: authenticated
[ 1055.152274] wlan0: associate with <MAC C-01 faidherbe_EXT> (try 1/3)
[ 1055.155542] wlan0: RX AssocResp from <MAC C-01 faidherbe_EXT> (capab=0x411 status=0 aid=3)
[ 1055.155562] rtl8821ae-0:rtl_op_sta_add():<0-0> Add sta addr is <MAC C-01 faidherbe_EXT>
[ 1055.155569] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> ratr_bitmap :ff005
[ 1055.155574] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> Rate_index:0, ratr_val:ff005, 0:81:0:5:f0:f:0
[ 1055.155616] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> ratr_bitmap :ff005
[ 1055.155619] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> Rate_index:0, ratr_val:ff005, 0:81:0:5:f0:f:0
[ 1055.155646] rtl8821ae-0:rtl_op_bss_info_changed():<0-0> BSS_CHANGED_ASSOC
[ 1055.155663] rtl8821ae-0:rtl8821ae_set_hw_reg():<0-0> switch case not process 5c
[ 1055.155688] rtl8821ae: 
[ 1055.155695] rtl8821ae_set_fw_rsvdpagepkt(): HW_VAR_SET_TX_CMD: ALL 
[ 1055.155709] rtl8821ae: 
[ 1055.155771] wlan0: associated
[ 1055.159552] rtl8821ae-0:rtl_is_special_data():<10000-1> 802.1X Rx EAPOL pkt!!
[ 1055.169258] rtl8821ae-0:rtl_is_special_data():<10000-1> 802.1X Rx EAPOL pkt!!
[ 1055.169520] rtl8821ae-0:rtl_op_set_key():<0-0> Using hardware based encryption for keyidx: 0, mac: <MAC C-01 faidherbe_EXT>
[ 1055.169525] rtl8821ae-0:rtl_op_set_key():<0-0> alg:CCMP
[ 1055.169527] rtl8821ae-0:rtl_op_set_key():<0-0> set enable_hw_sec, key_type:4(OPEN:0 WEP40:1 TKIP:2 AES:4 WEP104:5)
[ 1055.169530] rtl8821ae-0:rtl8821ae_enable_hw_security_config():<0-0> PairwiseEncAlgorithm = 4 GroupEncAlgorithm = 0
[ 1055.169537] rtl8821ae-0:rtl8821ae_enable_hw_security_config():<0-0> The SECR-value cc 
[ 1055.169541] rtl8821ae-0:rtl_op_set_key():<0-0> set pairwise key
[ 1055.169544] rtl8821ae-0:rtl8821ae_set_key():<0-0> add one entry
[ 1055.169546] rtl8821ae-0:rtl8821ae_set_key():<0-0> set Pairwiase key
[ 1055.169548] rtl8821ae-0:rtl_cam_add_one_entry():<0-0> EntryNo:4, ulKeyId=0, ulEncAlg=4, ulUseDK=0 MacAddr <MAC C-01 faidherbe_EXT>
[ 1055.169550] rtl8821ae: 
[ 1055.170198] rtl8821ae-0:rtl_cam_add_one_entry():<0-0> end 
[ 1055.170311] rtl8821ae-0:rtl_op_set_key():<0-0> Using hardware based encryption for keyidx: 1, mac: <MAC ID removed>
[ 1055.170314] rtl8821ae-0:rtl_op_set_key():<0-0> alg:CCMP
[ 1055.170316] rtl8821ae-0:rtl_op_set_key():<0-0> set group key
[ 1055.170318] rtl8821ae-0:rtl8821ae_set_key():<0-0> add one entry
[ 1055.170320] rtl8821ae-0:rtl8821ae_set_key():<0-0> set group key
[ 1055.170321] rtl8821ae-0:rtl_cam_add_one_entry():<0-0> EntryNo:1, ulKeyId=1, ulEncAlg=4, ulUseDK=0 MacAddr <MAC ID removed>
[ 1055.170323] rtl8821ae: 
[ 1055.170970] rtl8821ae-0:rtl_cam_add_one_entry():<0-0> end 
[ 1055.228321] rtl8821ae-0:rtl_tx_agg_start():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0 seq:1
[ 1055.228341] rtl8821ae-0:rtl_action_proc():<200-1> Tx ACT_ADDBAREQ From :<MAC wlan0>
[ 1055.228344] rtl8821ae: 
[ 1055.229876] rtl8821ae-0:rtl_action_proc():<10000-1> Rx ACT_ADDBARSP From :<MAC C-01 faidherbe_EXT>
[ 1055.229930] rtl8821ae-0:rtl_tx_agg_oper():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0
[ 1055.456329] rtl8821ae-0:rtl_action_proc():<10000-1> Rx ACT_ADDBAREQ From :<MAC C-01 faidherbe_EXT>
[ 1055.456335] rtl8821ae: 
[ 1055.456411] rtl8821ae-0:rtl_rx_agg_start():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0 seq:4
[ 1055.456435] rtl8821ae-0:rtl_action_proc():<200-1> Tx ACT_ADDBARSP From :<MAC wlan0>
[ 1099.781050] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1099.887502] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1100.148872] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1100.255263] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1100.516702] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1100.623034] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1100.884482] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1100.938830] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1101.200297] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1101.306664] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1101.568057] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1101.674405] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1101.935896] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1102.042216] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1102.303665] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1102.410032] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1102.671466] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1102.777848] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1103.039288] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1103.145589] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1103.407035] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1103.513401] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1103.774847] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1103.881177] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1104.142634] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1104.249037] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1107.083522] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off for 2 s
[ 1109.086442] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off for 4 s
[ 1111.089334] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off for 6 s
[ 1113.092211] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off for 8 s
[ 1115.095108] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off for 10 s
[ 1115.095117] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off, try to reconnect now
[ 1115.095154] wlan0: Connection to AP <MAC C-01 faidherbe_EXT> lost
[ 1115.099142] rtl8821ae-0:rtl_tx_agg_stop():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0
[ 1115.099181] rtl8821ae-0:rtl_rx_agg_stop():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0
[ 1115.115069] rtl8821ae-0:rtl_op_set_key():<0-0> Disabling hardware based encryption for keyidx: 0, mac: <MAC C-01 faidherbe_EXT>
[ 1115.115080] rtl8821ae-0:rtl_op_set_key():<0-0> alg:CCMP
[ 1115.115084] rtl8821ae-0:rtl_op_set_key():<0-0> set enable_hw_sec, key_type:4(OPEN:0 WEP40:1 TKIP:2 AES:4 WEP104:5)
[ 1115.115089] rtl8821ae-0:rtl8821ae_enable_hw_security_config():<0-0> PairwiseEncAlgorithm = 4 GroupEncAlgorithm = 4
[ 1115.115099] rtl8821ae-0:rtl8821ae_enable_hw_security_config():<0-0> The SECR-value cc 
[ 1115.115105] rtl8821ae-0:rtl_op_set_key():<0-0> disable key delete one entry
[ 1115.115108] rtl8821ae-0:rtl_cam_delete_one_entry():<0-0> key_idx:0
[ 1115.115116] rtl8821ae-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A4: 0 
[ 1115.115119] rtl8821ae-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A0: 80010000 
[ 1115.115191] rtl8821ae-0:rtl_op_sta_remove():<0-0> Remove sta addr is <MAC C-01 faidherbe_EXT>
[ 1115.115305] rtl8821ae-0:rtl_op_bss_info_changed():<0-0> BSS_CHANGED_UN_ASSOC
[ 1115.115334] rtl8821ae-0:rtl_op_bss_info_changed():<0-0> bssid: <MAC ID removed>
[ 1115.135066] rtl8821ae-0:rtl_op_set_key():<0-0> Disabling hardware based encryption for keyidx: 1, mac: <MAC ID removed>
[ 1115.135075] rtl8821ae-0:rtl_op_set_key():<0-0> alg:CCMP
[ 1115.135078] rtl8821ae-0:rtl_op_set_key():<0-0> disable key delete one entry
[ 1115.135082] rtl8821ae-0:rtl_cam_delete_one_entry():<0-0> key_idx:1
[ 1115.135091] rtl8821ae-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A4: 0 
[ 1115.135094] rtl8821ae-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A0: 80010008 
[ 1115.830585] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1117.233808] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1117.234250] wlan0: authenticate with <MAC C-01 faidherbe_EXT>
[ 1117.234558] rtl8821ae-0:rtl_op_bss_info_changed():<0-0> bssid: <MAC C-01 faidherbe_EXT>
[ 1117.234631] wlan0: send auth to <MAC C-01 faidherbe_EXT> (try 1/3)
[ 1117.234638] rtl8821ae-0:rtl_tx_mgmt_proc():<200-1> MAC80211_LINKING
[ 1117.236780] wlan0: authenticated
[ 1117.237758] wlan0: associate with <MAC C-01 faidherbe_EXT> (try 1/3)
[ 1117.240788] wlan0: RX AssocResp from <MAC C-01 faidherbe_EXT> (capab=0x411 status=0 aid=3)
[ 1117.240802] rtl8821ae-0:rtl_op_sta_add():<0-0> Add sta addr is <MAC C-01 faidherbe_EXT>
[ 1117.240807] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> ratr_bitmap :ff005
[ 1117.240810] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> Rate_index:0, ratr_val:ff005, 0:81:0:5:f0:f:0
[ 1117.240844] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> ratr_bitmap :ff005
[ 1117.240846] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> Rate_index:0, ratr_val:ff005, 0:81:0:5:f0:f:0
[ 1117.240868] rtl8821ae-0:rtl_op_bss_info_changed():<0-0> BSS_CHANGED_ASSOC
[ 1117.240882] rtl8821ae-0:rtl8821ae_set_hw_reg():<0-0> switch case not process 5c
[ 1117.240903] rtl8821ae: 
[ 1117.240906] rtl8821ae_set_fw_rsvdpagepkt(): HW_VAR_SET_TX_CMD: ALL 
[ 1117.240913] rtl8821ae: 
[ 1117.240964] wlan0: associated
[ 1117.245448] rtl8821ae-0:rtl_is_special_data():<10000-1> 802.1X Rx EAPOL pkt!!
[ 1117.255176] rtl8821ae-0:rtl_is_special_data():<10000-1> 802.1X Rx EAPOL pkt!!
[ 1117.255460] rtl8821ae-0:rtl_op_set_key():<0-0> Using hardware based encryption for keyidx: 0, mac: <MAC C-01 faidherbe_EXT>
[ 1117.255465] rtl8821ae-0:rtl_op_set_key():<0-0> alg:CCMP
[ 1117.255467] rtl8821ae-0:rtl_op_set_key():<0-0> set enable_hw_sec, key_type:4(OPEN:0 WEP40:1 TKIP:2 AES:4 WEP104:5)
[ 1117.255469] rtl8821ae-0:rtl8821ae_enable_hw_security_config():<0-0> PairwiseEncAlgorithm = 4 GroupEncAlgorithm = 0
[ 1117.255476] rtl8821ae-0:rtl8821ae_enable_hw_security_config():<0-0> The SECR-value cc 
[ 1117.255480] rtl8821ae-0:rtl_op_set_key():<0-0> set pairwise key
[ 1117.255482] rtl8821ae-0:rtl8821ae_set_key():<0-0> add one entry
[ 1117.255484] rtl8821ae-0:rtl8821ae_set_key():<0-0> set Pairwiase key
[ 1117.255486] rtl8821ae-0:rtl_cam_add_one_entry():<0-0> EntryNo:4, ulKeyId=0, ulEncAlg=4, ulUseDK=0 MacAddr <MAC C-01 faidherbe_EXT>
[ 1117.255488] rtl8821ae: 
[ 1117.256135] rtl8821ae-0:rtl_cam_add_one_entry():<0-0> end 
[ 1117.256282] rtl8821ae-0:rtl_op_set_key():<0-0> Using hardware based encryption for keyidx: 1, mac: <MAC ID removed>
[ 1117.256285] rtl8821ae-0:rtl_op_set_key():<0-0> alg:CCMP
[ 1117.256287] rtl8821ae-0:rtl_op_set_key():<0-0> set group key
[ 1117.256289] rtl8821ae-0:rtl8821ae_set_key():<0-0> add one entry
[ 1117.256291] rtl8821ae-0:rtl8821ae_set_key():<0-0> set group key
[ 1117.256293] rtl8821ae-0:rtl_cam_add_one_entry():<0-0> EntryNo:1, ulKeyId=1, ulEncAlg=4, ulUseDK=0 MacAddr <MAC ID removed>
[ 1117.256295] rtl8821ae: 
[ 1117.256942] rtl8821ae-0:rtl_cam_add_one_entry():<0-0> end 
[ 1117.449687] rtl8821ae-0:rtl_tx_agg_start():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0 seq:2
[ 1117.449717] rtl8821ae-0:rtl_action_proc():<200-1> Tx ACT_ADDBAREQ From :<MAC wlan0>
[ 1117.449721] rtl8821ae: 
[ 1117.451656] rtl8821ae-0:rtl_action_proc():<10000-1> Rx ACT_ADDBARSP From :<MAC C-01 faidherbe_EXT>
[ 1117.451748] rtl8821ae-0:rtl_tx_agg_oper():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0
[ 1117.759791] rtl8821ae-0:rtl_action_proc():<10000-1> Rx ACT_ADDBAREQ From :<MAC C-01 faidherbe_EXT>
[ 1117.759796] rtl8821ae: 
[ 1117.759853] rtl8821ae-0:rtl_rx_agg_start():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0 seq:2
[ 1117.759871] rtl8821ae-0:rtl_action_proc():<200-1> Tx ACT_ADDBARSP From :<MAC wlan0>
[ 1182.738981] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1182.845320] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1183.106737] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1183.213143] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1183.474531] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1183.580872] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1183.842311] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1183.896733] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1184.158132] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1184.264473] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1184.525949] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1184.632246] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1184.893723] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1185.000118] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1185.261606] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1185.367955] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1185.629369] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1185.735743] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1185.997110] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1186.103460] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1186.364921] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1186.471237] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1186.732702] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1186.839021] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1187.100508] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1187.206819] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1189.201886] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off for 2 s
[ 1191.204734] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off for 4 s
[ 1193.207668] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off for 6 s
[ 1195.210433] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off for 8 s
[ 1197.213387] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off for 10 s
[ 1197.213391] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off, try to reconnect now
[ 1197.213407] wlan0: Connection to AP <MAC C-01 faidherbe_EXT> lost
[ 1197.221399] rtl8821ae-0:rtl_tx_agg_stop():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0
[ 1197.221411] rtl8821ae-0:rtl_rx_agg_stop():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0
[ 1197.233363] rtl8821ae-0:rtl_op_set_key():<0-0> Disabling hardware based encryption for keyidx: 0, mac: <MAC C-01 faidherbe_EXT>
[ 1197.233378] rtl8821ae-0:rtl_op_set_key():<0-0> alg:CCMP
[ 1197.233379] rtl8821ae-0:rtl_op_set_key():<0-0> set enable_hw_sec, key_type:4(OPEN:0 WEP40:1 TKIP:2 AES:4 WEP104:5)
[ 1197.233381] rtl8821ae-0:rtl8821ae_enable_hw_security_config():<0-0> PairwiseEncAlgorithm = 4 GroupEncAlgorithm = 4
[ 1197.233388] rtl8821ae-0:rtl8821ae_enable_hw_security_config():<0-0> The SECR-value cc 
[ 1197.233391] rtl8821ae-0:rtl_op_set_key():<0-0> disable key delete one entry
[ 1197.233393] rtl8821ae-0:rtl_cam_delete_one_entry():<0-0> key_idx:0
[ 1197.233397] rtl8821ae-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A4: 0 
[ 1197.233399] rtl8821ae-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A0: 80010000 
[ 1197.233440] rtl8821ae-0:rtl_op_sta_remove():<0-0> Remove sta addr is <MAC C-01 faidherbe_EXT>
[ 1197.233505] rtl8821ae-0:rtl_op_bss_info_changed():<0-0> BSS_CHANGED_UN_ASSOC
[ 1197.233529] rtl8821ae-0:rtl_op_bss_info_changed():<0-0> bssid: <MAC ID removed>
[ 1197.249368] rtl8821ae-0:rtl_op_set_key():<0-0> Disabling hardware based encryption for keyidx: 1, mac: <MAC ID removed>
[ 1197.249375] rtl8821ae-0:rtl_op_set_key():<0-0> alg:CCMP
[ 1197.249377] rtl8821ae-0:rtl_op_set_key():<0-0> disable key delete one entry
[ 1197.249379] rtl8821ae-0:rtl_cam_delete_one_entry():<0-0> key_idx:1
[ 1197.249387] rtl8821ae-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A4: 0 
[ 1197.249389] rtl8821ae-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A0: 80010008 
[ 1197.948870] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1199.352081] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1199.352594] wlan0: authenticate with <MAC C-01 faidherbe_EXT>
[ 1199.352914] rtl8821ae-0:rtl_op_bss_info_changed():<0-0> bssid: <MAC C-01 faidherbe_EXT>
[ 1199.353008] wlan0: send auth to <MAC C-01 faidherbe_EXT> (try 1/3)
[ 1199.353020] rtl8821ae-0:rtl_tx_mgmt_proc():<200-1> MAC80211_LINKING
[ 1199.356078] wlan0: authenticated
[ 1199.360076] wlan0: associate with <MAC C-01 faidherbe_EXT> (try 1/3)
[ 1199.363438] wlan0: RX AssocResp from <MAC C-01 faidherbe_EXT> (capab=0x411 status=0 aid=3)
[ 1199.363460] rtl8821ae-0:rtl_op_sta_add():<0-0> Add sta addr is <MAC C-01 faidherbe_EXT>
[ 1199.363464] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> ratr_bitmap :ff005
[ 1199.363467] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> Rate_index:0, ratr_val:ff005, 0:81:0:5:f0:f:0
[ 1199.363501] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> ratr_bitmap :ff005
[ 1199.363502] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> Rate_index:0, ratr_val:ff005, 0:81:0:5:f0:f:0
[ 1199.363525] rtl8821ae-0:rtl_op_bss_info_changed():<0-0> BSS_CHANGED_ASSOC
[ 1199.363539] rtl8821ae-0:rtl8821ae_set_hw_reg():<0-0> switch case not process 5c
[ 1199.363561] rtl8821ae: 
[ 1199.363564] rtl8821ae_set_fw_rsvdpagepkt(): HW_VAR_SET_TX_CMD: ALL 
[ 1199.363574] rtl8821ae: 
[ 1199.363625] wlan0: associated
[ 1199.367329] rtl8821ae-0:rtl_is_special_data():<10000-1> 802.1X Rx EAPOL pkt!!
[ 1199.376584] rtl8821ae-0:rtl_is_special_data():<10000-1> 802.1X Rx EAPOL pkt!!
[ 1199.376833] rtl8821ae-0:rtl_op_set_key():<0-0> Using hardware based encryption for keyidx: 0, mac: <MAC C-01 faidherbe_EXT>
[ 1199.376840] rtl8821ae-0:rtl_op_set_key():<0-0> alg:CCMP
[ 1199.376843] rtl8821ae-0:rtl_op_set_key():<0-0> set enable_hw_sec, key_type:4(OPEN:0 WEP40:1 TKIP:2 AES:4 WEP104:5)
[ 1199.376847] rtl8821ae-0:rtl8821ae_enable_hw_security_config():<0-0> PairwiseEncAlgorithm = 4 GroupEncAlgorithm = 0
[ 1199.376856] rtl8821ae-0:rtl8821ae_enable_hw_security_config():<0-0> The SECR-value cc 
[ 1199.376861] rtl8821ae-0:rtl_op_set_key():<0-0> set pairwise key
[ 1199.376864] rtl8821ae-0:rtl8821ae_set_key():<0-0> add one entry
[ 1199.376866] rtl8821ae-0:rtl8821ae_set_key():<0-0> set Pairwiase key
[ 1199.376869] rtl8821ae-0:rtl_cam_add_one_entry():<0-0> EntryNo:4, ulKeyId=0, ulEncAlg=4, ulUseDK=0 MacAddr <MAC C-01 faidherbe_EXT>
[ 1199.376872] rtl8821ae: 
[ 1199.377528] rtl8821ae-0:rtl_cam_add_one_entry():<0-0> end 
[ 1199.377687] rtl8821ae-0:rtl_op_set_key():<0-0> Using hardware based encryption for keyidx: 1, mac: <MAC ID removed>
[ 1199.377692] rtl8821ae-0:rtl_op_set_key():<0-0> alg:CCMP
[ 1199.377695] rtl8821ae-0:rtl_op_set_key():<0-0> set group key
[ 1199.377698] rtl8821ae-0:rtl8821ae_set_key():<0-0> add one entry
[ 1199.377701] rtl8821ae-0:rtl8821ae_set_key():<0-0> set group key
[ 1199.377704] rtl8821ae-0:rtl_cam_add_one_entry():<0-0> EntryNo:1, ulKeyId=1, ulEncAlg=4, ulUseDK=0 MacAddr <MAC ID removed>
[ 1199.377707] rtl8821ae: 
[ 1199.378362] rtl8821ae-0:rtl_cam_add_one_entry():<0-0> end 
[ 1199.767845] rtl8821ae-0:rtl_tx_agg_start():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0 seq:2
[ 1199.767860] rtl8821ae-0:rtl_action_proc():<200-1> Tx ACT_ADDBAREQ From :<MAC wlan0>
[ 1199.767862] rtl8821ae: 
[ 1199.769367] rtl8821ae-0:rtl_action_proc():<10000-1> Rx ACT_ADDBARSP From :<MAC C-01 faidherbe_EXT>
[ 1199.769419] rtl8821ae-0:rtl_tx_agg_oper():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0
[ 1200.694404] rtl8821ae-0:rtl_action_proc():<10000-1> Rx ACT_ADDBAREQ From :<MAC C-01 faidherbe_EXT>
[ 1200.694410] rtl8821ae: 
[ 1200.694499] rtl8821ae-0:rtl_rx_agg_start():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0 seq:6
[ 1200.694512] rtl8821ae-0:rtl_action_proc():<200-1> Tx ACT_ADDBARSP From :<MAC wlan0>
[ 1259.302821] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> ratr_bitmap :ff000
[ 1259.302826] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> Rate_index:0, ratr_val:ff000, 0:81:0:0:f0:f:0
[ 1275.325874] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> ratr_bitmap :f0000
[ 1275.325879] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> Rate_index:0, ratr_val:f0000, 0:81:0:0:0:f:0
[ 1285.937546] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1286.043851] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1286.305363] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1286.411681] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1286.673137] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1286.779462] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1287.040931] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1287.095277] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1287.356725] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1287.463079] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1287.724558] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1287.830870] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1288.092344] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1288.198657] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1288.460202] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1288.566517] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1288.827916] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1288.934326] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1289.195707] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1289.302062] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1289.563586] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1289.669870] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1289.931303] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1290.037628] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1290.299098] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1290.405515] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1293.351918] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off for 2 s
[ 1295.354775] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off for 4 s
[ 1297.357650] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off for 6 s
[ 1299.360582] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off for 8 s
[ 1301.363459] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off for 10 s
[ 1301.363464] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off, try to reconnect now
[ 1301.363525] wlan0: Connection to AP <MAC C-01 faidherbe_EXT> lost
[ 1301.371412] rtl8821ae-0:rtl_tx_agg_stop():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0
[ 1301.371430] rtl8821ae-0:rtl_rx_agg_stop():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0
[ 1301.387395] rtl8821ae-0:rtl_op_set_key():<0-0> Disabling hardware based encryption for keyidx: 0, mac: <MAC C-01 faidherbe_EXT>
[ 1301.387402] rtl8821ae-0:rtl_op_set_key():<0-0> alg:CCMP
[ 1301.387404] rtl8821ae-0:rtl_op_set_key():<0-0> set enable_hw_sec, key_type:4(OPEN:0 WEP40:1 TKIP:2 AES:4 WEP104:5)
[ 1301.387407] rtl8821ae-0:rtl8821ae_enable_hw_security_config():<0-0> PairwiseEncAlgorithm = 4 GroupEncAlgorithm = 4
[ 1301.387415] rtl8821ae-0:rtl8821ae_enable_hw_security_config():<0-0> The SECR-value cc 
[ 1301.387419] rtl8821ae-0:rtl_op_set_key():<0-0> disable key delete one entry
[ 1301.387421] rtl8821ae-0:rtl_cam_delete_one_entry():<0-0> key_idx:0
[ 1301.387427] rtl8821ae-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A4: 0 
[ 1301.387429] rtl8821ae-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A0: 80010000 
[ 1301.387463] rtl8821ae-0:rtl_op_sta_remove():<0-0> Remove sta addr is <MAC C-01 faidherbe_EXT>
[ 1301.387518] rtl8821ae-0:rtl_op_bss_info_changed():<0-0> BSS_CHANGED_UN_ASSOC
[ 1301.387543] rtl8821ae-0:rtl_op_bss_info_changed():<0-0> bssid: <MAC ID removed>
[ 1301.399470] rtl8821ae-0:rtl_op_set_key():<0-0> Disabling hardware based encryption for keyidx: 1, mac: <MAC ID removed>
[ 1301.399476] rtl8821ae-0:rtl_op_set_key():<0-0> alg:CCMP
[ 1301.399478] rtl8821ae-0:rtl_op_set_key():<0-0> disable key delete one entry
[ 1301.399480] rtl8821ae-0:rtl_cam_delete_one_entry():<0-0> key_idx:1
[ 1301.399488] rtl8821ae-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A4: 0 
[ 1301.399490] rtl8821ae-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A0: 80010008 
[ 1302.102987] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1303.506227] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1303.506675] wlan0: authenticate with <MAC C-01 faidherbe_EXT>
[ 1303.506982] rtl8821ae-0:rtl_op_bss_info_changed():<0-0> bssid: <MAC C-01 faidherbe_EXT>
[ 1303.507054] wlan0: send auth to <MAC C-01 faidherbe_EXT> (try 1/3)
[ 1303.507062] rtl8821ae-0:rtl_tx_mgmt_proc():<200-1> MAC80211_LINKING
[ 1303.610125] wlan0: send auth to <MAC C-01 faidherbe_EXT> (try 2/3)
[ 1303.610138] rtl8821ae-0:rtl_tx_mgmt_proc():<200-1> MAC80211_LINKING
[ 1303.714054] wlan0: send auth to <MAC C-01 faidherbe_EXT> (try 3/3)
[ 1303.714065] rtl8821ae-0:rtl_tx_mgmt_proc():<200-1> MAC80211_LINKING
[ 1303.817978] wlan0: authentication with <MAC C-01 faidherbe_EXT> timed out
[ 1303.826209] rtl8821ae-0:rtl_op_bss_info_changed():<0-0> bssid: <MAC ID removed>
[ 1304.941370] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1306.344588] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1306.345100] wlan0: authenticate with <MAC C-01 faidherbe_EXT>
[ 1306.345412] rtl8821ae-0:rtl_op_bss_info_changed():<0-0> bssid: <MAC C-01 faidherbe_EXT>
[ 1306.345498] wlan0: send auth to <MAC C-01 faidherbe_EXT> (try 1/3)
[ 1306.345511] rtl8821ae-0:rtl_tx_mgmt_proc():<200-1> MAC80211_LINKING
[ 1306.448490] wlan0: send auth to <MAC C-01 faidherbe_EXT> (try 2/3)
[ 1306.448503] rtl8821ae-0:rtl_tx_mgmt_proc():<200-1> MAC80211_LINKING
[ 1306.552469] wlan0: send auth to <MAC C-01 faidherbe_EXT> (try 3/3)
[ 1306.552487] rtl8821ae-0:rtl_tx_mgmt_proc():<200-1> MAC80211_LINKING
[ 1306.656451] wlan0: authentication with <MAC C-01 faidherbe_EXT> timed out
[ 1306.664605] rtl8821ae-0:rtl_op_bss_info_changed():<0-0> bssid: <MAC ID removed>
[ 1308.279555] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1309.630770] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1309.631209] wlan0: authenticate with <MAC C-01 faidherbe_EXT>
[ 1309.631525] rtl8821ae-0:rtl_op_bss_info_changed():<0-0> bssid: <MAC C-01 faidherbe_EXT>
[ 1309.631616] wlan0: send auth to <MAC C-01 faidherbe_EXT> (try 1/3)
[ 1309.631628] rtl8821ae-0:rtl_tx_mgmt_proc():<200-1> MAC80211_LINKING
[ 1309.634723] wlan0: authenticated
[ 1309.638755] wlan0: associate with <MAC C-01 faidherbe_EXT> (try 1/3)
[ 1309.642510] wlan0: RX AssocResp from <MAC C-01 faidherbe_EXT> (capab=0x411 status=0 aid=3)
[ 1309.642520] rtl8821ae-0:rtl_op_sta_add():<0-0> Add sta addr is <MAC C-01 faidherbe_EXT>
[ 1309.642525] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> ratr_bitmap :ff005
[ 1309.642527] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> Rate_index:0, ratr_val:ff005, 0:81:0:5:f0:f:0
[ 1309.642561] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> ratr_bitmap :ff005
[ 1309.642563] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> Rate_index:0, ratr_val:ff005, 0:81:0:5:f0:f:0
[ 1309.642585] rtl8821ae-0:rtl_op_bss_info_changed():<0-0> BSS_CHANGED_ASSOC
[ 1309.642600] rtl8821ae-0:rtl8821ae_set_hw_reg():<0-0> switch case not process 5c
[ 1309.642620] rtl8821ae: 
[ 1309.642624] rtl8821ae_set_fw_rsvdpagepkt(): HW_VAR_SET_TX_CMD: ALL 
[ 1309.642631] rtl8821ae: 
[ 1309.642684] wlan0: associated
[ 1309.653811] rtl8821ae-0:rtl_is_special_data():<10000-1> 802.1X Rx EAPOL pkt!!
[ 1309.664248] rtl8821ae-0:rtl_is_special_data():<10000-1> 802.1X Rx EAPOL pkt!!
[ 1309.664511] rtl8821ae-0:rtl_op_set_key():<0-0> Using hardware based encryption for keyidx: 0, mac: <MAC C-01 faidherbe_EXT>
[ 1309.664517] rtl8821ae-0:rtl_op_set_key():<0-0> alg:CCMP
[ 1309.664519] rtl8821ae-0:rtl_op_set_key():<0-0> set enable_hw_sec, key_type:4(OPEN:0 WEP40:1 TKIP:2 AES:4 WEP104:5)
[ 1309.664521] rtl8821ae-0:rtl8821ae_enable_hw_security_config():<0-0> PairwiseEncAlgorithm = 4 GroupEncAlgorithm = 0
[ 1309.664529] rtl8821ae-0:rtl8821ae_enable_hw_security_config():<0-0> The SECR-value cc 
[ 1309.664533] rtl8821ae-0:rtl_op_set_key():<0-0> set pairwise key
[ 1309.664536] rtl8821ae-0:rtl8821ae_set_key():<0-0> add one entry
[ 1309.664537] rtl8821ae-0:rtl8821ae_set_key():<0-0> set Pairwiase key
[ 1309.664539] rtl8821ae-0:rtl_cam_add_one_entry():<0-0> EntryNo:4, ulKeyId=0, ulEncAlg=4, ulUseDK=0 MacAddr <MAC C-01 faidherbe_EXT>
[ 1309.664542] rtl8821ae: 
[ 1309.665189] rtl8821ae-0:rtl_cam_add_one_entry():<0-0> end 
[ 1309.665319] rtl8821ae-0:rtl_op_set_key():<0-0> Using hardware based encryption for keyidx: 1, mac: <MAC ID removed>
[ 1309.665324] rtl8821ae-0:rtl_op_set_key():<0-0> alg:CCMP
[ 1309.665327] rtl8821ae-0:rtl_op_set_key():<0-0> set group key
[ 1309.665330] rtl8821ae-0:rtl8821ae_set_key():<0-0> add one entry
[ 1309.665332] rtl8821ae-0:rtl8821ae_set_key():<0-0> set group key
[ 1309.665335] rtl8821ae-0:rtl_cam_add_one_entry():<0-0> EntryNo:1, ulKeyId=1, ulEncAlg=4, ulUseDK=0 MacAddr <MAC ID removed>
[ 1309.665338] rtl8821ae: 
[ 1309.665991] rtl8821ae-0:rtl_cam_add_one_entry():<0-0> end 
[ 1309.742694] rtl8821ae-0:rtl_tx_agg_start():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0 seq:1
[ 1309.742709] rtl8821ae-0:rtl_action_proc():<200-1> Tx ACT_ADDBAREQ From :<MAC wlan0>
[ 1309.742713] rtl8821ae: 
[ 1309.744514] rtl8821ae-0:rtl_action_proc():<10000-1> Rx ACT_ADDBARSP From :<MAC C-01 faidherbe_EXT>
[ 1309.744579] rtl8821ae-0:rtl_tx_agg_oper():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0
[ 1310.343327] rtl8821ae-0:rtl_action_proc():<10000-1> Rx ACT_ADDBAREQ From :<MAC C-01 faidherbe_EXT>
[ 1310.343333] rtl8821ae: 
[ 1310.343418] rtl8821ae-0:rtl_rx_agg_start():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0 seq:2
[ 1310.343430] rtl8821ae-0:rtl_action_proc():<200-1> Tx ACT_ADDBARSP From :<MAC wlan0>
[ 1359.399142] rtl8821ae-0:rtl_tx_agg_stop():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0
[ 1359.399183] rtl8821ae-0:rtl_action_proc():<400-1> ACT_ADDBADEL From :<MAC wlan0>
[ 1375.186427] rtl8821ae-0:rtl_tx_agg_start():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0 seq:2707
[ 1375.186469] rtl8821ae-0:rtl_action_proc():<200-1> Tx ACT_ADDBAREQ From :<MAC wlan0>
[ 1375.186475] rtl8821ae: 
[ 1375.188258] rtl8821ae-0:rtl_action_proc():<10000-1> Rx ACT_ADDBARSP From :<MAC C-01 faidherbe_EXT>
[ 1375.188329] rtl8821ae-0:rtl_tx_agg_oper():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0
[ 1381.886719] rtl8821ae-0:rtl_tx_agg_stop():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0
[ 1381.886750] rtl8821ae-0:rtl_action_proc():<400-1> ACT_ADDBADEL From :<MAC wlan0>
[ 1382.294498] rtl8821ae-0:rtl_tx_agg_start():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0 seq:2713
[ 1382.294524] rtl8821ae-0:rtl_action_proc():<200-1> Tx ACT_ADDBAREQ From :<MAC wlan0>
[ 1382.294527] rtl8821ae: 
[ 1382.296075] rtl8821ae-0:rtl_action_proc():<10000-1> Rx ACT_ADDBARSP From :<MAC C-01 faidherbe_EXT>
[ 1382.296144] rtl8821ae-0:rtl_tx_agg_oper():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0
[ 1389.374466] rtl8821ae-0:rtl_tx_agg_stop():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0
[ 1389.374510] rtl8821ae-0:rtl_action_proc():<400-1> ACT_ADDBADEL From :<MAC wlan0>
[ 1405.177698] rtl8821ae-0:rtl_tx_agg_start():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0 seq:2719
[ 1405.179550] rtl8821ae-0:rtl_action_proc():<10000-1> Rx ACT_ADDBARSP From :<MAC C-01 faidherbe_EXT>
[ 1405.619032] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1405.725367] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1405.986816] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1406.093160] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1406.181175] rtl8821ae-0:rtl_tx_agg_stop():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0
[ 1406.354615] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1406.460955] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1406.722409] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1406.776787] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1407.038269] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1407.144617] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1407.406017] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1407.512380] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1407.773825] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1407.880176] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1408.141622] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1408.247959] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1408.509421] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1408.615763] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1408.877245] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1408.983564] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1409.245028] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1409.351297] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1409.612807] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1409.719150] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1409.980613] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1410.086964] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1410.087526] rtl8821ae-0:rtl_action_proc():<400-1> ACT_ADDBADEL From :<MAC wlan0>
[ 1413.533102] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off for 2 s
[ 1414.213636] rtl8821ae-0:rtl_tx_agg_start():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0 seq:2721
[ 1414.213668] rtl8821ae-0:rtl_action_proc():<200-1> Tx ACT_ADDBAREQ From :<MAC wlan0>
[ 1414.213675] rtl8821ae: 
[ 1414.217755] rtl8821ae-0:rtl_action_proc():<10000-1> Rx ACT_ADDBARSP From :<MAC C-01 faidherbe_EXT>
[ 1414.217850] rtl8821ae-0:rtl_tx_agg_oper():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0
[ 1415.535971] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off for 4 s
[ 1417.538858] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off for 6 s
[ 1419.369780] rtl8821ae-0:rtl_tx_agg_stop():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0
[ 1419.369817] rtl8821ae-0:rtl_action_proc():<400-1> ACT_ADDBADEL From :<MAC wlan0>
[ 1419.541752] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off for 8 s
[ 1421.544633] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off for 10 s
[ 1421.544638] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off, try to reconnect now
[ 1421.544653] wlan0: Connection to AP <MAC C-01 faidherbe_EXT> lost
[ 1421.544686] rtl8821ae-0:rtl_rx_agg_stop():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0
[ 1421.552632] rtl8821ae-0:rtl_op_set_key():<0-0> Disabling hardware based encryption for keyidx: 0, mac: <MAC C-01 faidherbe_EXT>
[ 1421.552639] rtl8821ae-0:rtl_op_set_key():<0-0> alg:CCMP
[ 1421.552641] rtl8821ae-0:rtl_op_set_key():<0-0> set enable_hw_sec, key_type:4(OPEN:0 WEP40:1 TKIP:2 AES:4 WEP104:5)
[ 1421.552644] rtl8821ae-0:rtl8821ae_enable_hw_security_config():<0-0> PairwiseEncAlgorithm = 4 GroupEncAlgorithm = 4
[ 1421.552652] rtl8821ae-0:rtl8821ae_enable_hw_security_config():<0-0> The SECR-value cc 
[ 1421.552656] rtl8821ae-0:rtl_op_set_key():<0-0> disable key delete one entry
[ 1421.552658] rtl8821ae-0:rtl_cam_delete_one_entry():<0-0> key_idx:0
[ 1421.552664] rtl8821ae-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A4: 0 
[ 1421.552666] rtl8821ae-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A0: 80010000 
[ 1421.552703] rtl8821ae-0:rtl_op_sta_remove():<0-0> Remove sta addr is <MAC C-01 faidherbe_EXT>
[ 1421.552758] rtl8821ae-0:rtl_op_bss_info_changed():<0-0> BSS_CHANGED_UN_ASSOC
[ 1421.552783] rtl8821ae-0:rtl_op_bss_info_changed():<0-0> bssid: <MAC ID removed>
[ 1421.576532] rtl8821ae-0:rtl_op_set_key():<0-0> Disabling hardware based encryption for keyidx: 1, mac: <MAC ID removed>
[ 1421.576538] rtl8821ae-0:rtl_op_set_key():<0-0> alg:CCMP
[ 1421.576539] rtl8821ae-0:rtl_op_set_key():<0-0> disable key delete one entry
[ 1421.576541] rtl8821ae-0:rtl_cam_delete_one_entry():<0-0> key_idx:1
[ 1421.576548] rtl8821ae-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A4: 0 
[ 1421.576550] rtl8821ae-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A0: 80010008 
[ 1422.268179] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1423.671403] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1423.671925] wlan0: authenticate with <MAC C-01 faidherbe_EXT>
[ 1423.672235] rtl8821ae-0:rtl_op_bss_info_changed():<0-0> bssid: <MAC C-01 faidherbe_EXT>
[ 1423.672320] wlan0: send auth to <MAC C-01 faidherbe_EXT> (try 1/3)
[ 1423.672329] rtl8821ae-0:rtl_tx_mgmt_proc():<200-1> MAC80211_LINKING
[ 1423.675161] wlan0: authenticated
[ 1423.679332] wlan0: associate with <MAC C-01 faidherbe_EXT> (try 1/3)
[ 1423.683610] wlan0: RX AssocResp from <MAC C-01 faidherbe_EXT> (capab=0x411 status=0 aid=3)
[ 1423.683621] rtl8821ae-0:rtl_op_sta_add():<0-0> Add sta addr is <MAC C-01 faidherbe_EXT>
[ 1423.683625] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> ratr_bitmap :ff005
[ 1423.683627] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> Rate_index:0, ratr_val:ff005, 0:81:0:5:f0:f:0
[ 1423.683661] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> ratr_bitmap :ff005
[ 1423.683663] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> Rate_index:0, ratr_val:ff005, 0:81:0:5:f0:f:0
[ 1423.683685] rtl8821ae-0:rtl_op_bss_info_changed():<0-0> BSS_CHANGED_ASSOC
[ 1423.683700] rtl8821ae-0:rtl8821ae_set_hw_reg():<0-0> switch case not process 5c
[ 1423.683721] rtl8821ae: 
[ 1423.683724] rtl8821ae_set_fw_rsvdpagepkt(): HW_VAR_SET_TX_CMD: ALL 
[ 1423.683734] rtl8821ae: 
[ 1423.683786] wlan0: associated
[ 1423.694282] rtl8821ae-0:rtl_is_special_data():<10000-1> 802.1X Rx EAPOL pkt!!
[ 1423.704162] rtl8821ae-0:rtl_is_special_data():<10000-1> 802.1X Rx EAPOL pkt!!
[ 1423.704435] rtl8821ae-0:rtl_op_set_key():<0-0> Using hardware based encryption for keyidx: 0, mac: <MAC C-01 faidherbe_EXT>
[ 1423.704440] rtl8821ae-0:rtl_op_set_key():<0-0> alg:CCMP
[ 1423.704442] rtl8821ae-0:rtl_op_set_key():<0-0> set enable_hw_sec, key_type:4(OPEN:0 WEP40:1 TKIP:2 AES:4 WEP104:5)
[ 1423.704445] rtl8821ae-0:rtl8821ae_enable_hw_security_config():<0-0> PairwiseEncAlgorithm = 4 GroupEncAlgorithm = 0
[ 1423.704452] rtl8821ae-0:rtl8821ae_enable_hw_security_config():<0-0> The SECR-value cc 
[ 1423.704457] rtl8821ae-0:rtl_op_set_key():<0-0> set pairwise key
[ 1423.704459] rtl8821ae-0:rtl8821ae_set_key():<0-0> add one entry
[ 1423.704461] rtl8821ae-0:rtl8821ae_set_key():<0-0> set Pairwiase key
[ 1423.704462] rtl8821ae-0:rtl_cam_add_one_entry():<0-0> EntryNo:4, ulKeyId=0, ulEncAlg=4, ulUseDK=0 MacAddr <MAC C-01 faidherbe_EXT>
[ 1423.704465] rtl8821ae: 
[ 1423.705113] rtl8821ae-0:rtl_cam_add_one_entry():<0-0> end 
[ 1423.705241] rtl8821ae-0:rtl_op_set_key():<0-0> Using hardware based encryption for keyidx: 1, mac: <MAC ID removed>
[ 1423.705246] rtl8821ae-0:rtl_op_set_key():<0-0> alg:CCMP
[ 1423.705249] rtl8821ae-0:rtl_op_set_key():<0-0> set group key
[ 1423.705252] rtl8821ae-0:rtl8821ae_set_key():<0-0> add one entry
[ 1423.705255] rtl8821ae-0:rtl8821ae_set_key():<0-0> set group key
[ 1423.705257] rtl8821ae-0:rtl_cam_add_one_entry():<0-0> EntryNo:1, ulKeyId=1, ulEncAlg=4, ulUseDK=0 MacAddr <MAC ID removed>
[ 1423.705260] rtl8821ae: 
[ 1423.705913] rtl8821ae-0:rtl_cam_add_one_entry():<0-0> end 
[ 1432.439977] rtl8821ae-0:rtl_action_proc():<10000-1> Rx ACT_ADDBAREQ From :<MAC C-01 faidherbe_EXT>
[ 1432.439983] rtl8821ae: 
[ 1432.440072] rtl8821ae-0:rtl_rx_agg_start():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0 seq:0
[ 1432.440085] rtl8821ae-0:rtl_action_proc():<200-1> Tx ACT_ADDBARSP From :<MAC wlan0>
[ 1432.454567] rtl8821ae-0:rtl_tx_agg_start():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0 seq:1
[ 1432.454588] rtl8821ae-0:rtl_action_proc():<200-1> Tx ACT_ADDBAREQ From :<MAC wlan0>
[ 1432.454590] rtl8821ae: 
[ 1432.456131] rtl8821ae-0:rtl_action_proc():<10000-1> Rx ACT_ADDBARSP From :<MAC C-01 faidherbe_EXT>
[ 1432.456173] rtl8821ae-0:rtl_tx_agg_oper():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0
[ 1451.343947] rtl8821ae-0:rtl_tx_agg_stop():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0
[ 1451.343976] rtl8821ae-0:rtl_action_proc():<400-1> ACT_ADDBADEL From :<MAC wlan0>
[ 1465.168344] rtl8821ae-0:rtl_tx_agg_start():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0 seq:17
[ 1465.168384] rtl8821ae-0:rtl_action_proc():<200-1> Tx ACT_ADDBAREQ From :<MAC wlan0>
[ 1465.168389] rtl8821ae: 
[ 1465.169959] rtl8821ae-0:rtl_action_proc():<10000-1> Rx ACT_ADDBARSP From :<MAC C-01 faidherbe_EXT>
[ 1465.170030] rtl8821ae-0:rtl_tx_agg_oper():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0
[ 1470.361378] rtl8821ae-0:rtl_tx_agg_stop():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0
[ 1470.361400] rtl8821ae-0:rtl_action_proc():<400-1> ACT_ADDBADEL From :<MAC wlan0>
[ 1474.260645] rtl8821ae-0:rtl_tx_agg_start():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0 seq:19
[ 1474.260668] rtl8821ae-0:rtl_action_proc():<200-1> Tx ACT_ADDBAREQ From :<MAC wlan0>
[ 1474.260674] rtl8821ae: 
[ 1474.265109] rtl8821ae-0:rtl_action_proc():<10000-1> Rx ACT_ADDBARSP From :<MAC C-01 faidherbe_EXT>
[ 1474.265169] rtl8821ae-0:rtl_tx_agg_oper():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0
[ 1479.888154] rtl8821ae-0:rtl_tx_agg_stop():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0
[ 1479.888196] rtl8821ae-0:rtl_action_proc():<400-1> ACT_ADDBADEL From :<MAC wlan0>
[ 1488.715184] rtl8821ae-0:rtl_tx_agg_start():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0 seq:21
[ 1488.715208] rtl8821ae-0:rtl_action_proc():<200-1> Tx ACT_ADDBAREQ From :<MAC wlan0>
[ 1488.715213] rtl8821ae: 
[ 1488.718251] rtl8821ae-0:rtl_action_proc():<10000-1> Rx ACT_ADDBARSP From :<MAC C-01 faidherbe_EXT>
[ 1488.718315] rtl8821ae-0:rtl_tx_agg_oper():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0
[ 1497.654274] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> ratr_bitmap :ff000
[ 1497.654283] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> Rate_index:0, ratr_val:ff000, 0:81:0:0:f0:f:0
[ 1502.335629] rtl8821ae-0:rtl_tx_agg_stop():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0
[ 1502.335668] rtl8821ae-0:rtl_action_proc():<400-1> ACT_ADDBADEL From :<MAC wlan0>
[ 1504.030767] rtl8821ae-0:rtl_tx_agg_start():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0 seq:31
[ 1504.030803] rtl8821ae-0:rtl_action_proc():<200-1> Tx ACT_ADDBAREQ From :<MAC wlan0>
[ 1504.030809] rtl8821ae: 
[ 1504.034154] rtl8821ae-0:rtl_action_proc():<10000-1> Rx ACT_ADDBARSP From :<MAC C-01 faidherbe_EXT>
[ 1504.034226] rtl8821ae-0:rtl_tx_agg_oper():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0
[ 1509.439652] rtl8821ae-0:rtl_tx_agg_stop():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0
[ 1509.439675] rtl8821ae-0:rtl_action_proc():<400-1> ACT_ADDBADEL From :<MAC wlan0>
[ 1520.221639] rtl8821ae-0:rtl_tx_agg_start():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0 seq:36
[ 1520.221662] rtl8821ae-0:rtl_action_proc():<200-1> Tx ACT_ADDBAREQ From :<MAC wlan0>
[ 1520.221665] rtl8821ae: 
[ 1520.223554] rtl8821ae-0:rtl_action_proc():<10000-1> Rx ACT_ADDBARSP From :<MAC C-01 faidherbe_EXT>
[ 1520.223596] rtl8821ae-0:rtl_tx_agg_oper():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0
[ 1525.548325] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1525.654660] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1525.916133] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1526.022462] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1526.283968] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1526.390257] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1526.651711] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1526.706077] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1526.967558] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1527.073914] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1527.335316] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1527.441665] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1527.703126] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1527.809416] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1528.070887] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1528.177224] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1528.438659] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1528.545059] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1528.806502] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1528.912881] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1529.174341] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1529.280673] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1529.542132] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1529.648453] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1529.909933] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1530.016259] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1533.706173] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> ratr_bitmap :f0000
[ 1533.706178] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> Rate_index:0, ratr_val:f0000, 0:81:0:0:0:f:0
[ 1533.706241] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off for 2 s
[ 1535.709132] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off for 4 s
[ 1537.712044] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off for 6 s
[ 1539.454932] rtl8821ae-0:rtl_tx_agg_stop():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0
[ 1539.454951] rtl8821ae-0:rtl_action_proc():<400-1> ACT_ADDBADEL From :<MAC wlan0>
[ 1539.714873] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off for 8 s
[ 1540.478445] rtl8821ae-0:rtl_tx_agg_start():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0 seq:205
[ 1540.478472] rtl8821ae-0:rtl_action_proc():<200-1> Tx ACT_ADDBAREQ From :<MAC wlan0>
[ 1540.478475] rtl8821ae: 
[ 1540.480286] rtl8821ae-0:rtl_action_proc():<10000-1> Rx ACT_ADDBARSP From :<MAC C-01 faidherbe_EXT>
[ 1540.480351] rtl8821ae-0:rtl_tx_agg_oper():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0
[ 1541.717791] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off for 10 s
[ 1541.717796] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off, try to reconnect now
[ 1541.717858] wlan0: Connection to AP <MAC C-01 faidherbe_EXT> lost
[ 1541.725735] rtl8821ae-0:rtl_tx_agg_stop():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0
[ 1541.725750] rtl8821ae-0:rtl_rx_agg_stop():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0
[ 1541.737795] rtl8821ae-0:rtl_op_set_key():<0-0> Disabling hardware based encryption for keyidx: 0, mac: <MAC C-01 faidherbe_EXT>
[ 1541.737801] rtl8821ae-0:rtl_op_set_key():<0-0> alg:CCMP
[ 1541.737804] rtl8821ae-0:rtl_op_set_key():<0-0> set enable_hw_sec, key_type:4(OPEN:0 WEP40:1 TKIP:2 AES:4 WEP104:5)
[ 1541.737807] rtl8821ae-0:rtl8821ae_enable_hw_security_config():<0-0> PairwiseEncAlgorithm = 4 GroupEncAlgorithm = 4
[ 1541.737815] rtl8821ae-0:rtl8821ae_enable_hw_security_config():<0-0> The SECR-value cc 
[ 1541.737819] rtl8821ae-0:rtl_op_set_key():<0-0> disable key delete one entry
[ 1541.737821] rtl8821ae-0:rtl_cam_delete_one_entry():<0-0> key_idx:0
[ 1541.737827] rtl8821ae-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A4: 0 
[ 1541.737829] rtl8821ae-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A0: 80010000 
[ 1541.737869] rtl8821ae-0:rtl_op_sta_remove():<0-0> Remove sta addr is <MAC C-01 faidherbe_EXT>
[ 1541.737928] rtl8821ae-0:rtl_op_bss_info_changed():<0-0> BSS_CHANGED_UN_ASSOC
[ 1541.737954] rtl8821ae-0:rtl_op_bss_info_changed():<0-0> bssid: <MAC ID removed>
[ 1541.757764] rtl8821ae-0:rtl_op_set_key():<0-0> Disabling hardware based encryption for keyidx: 1, mac: <MAC ID removed>
[ 1541.757771] rtl8821ae-0:rtl_op_set_key():<0-0> alg:CCMP
[ 1541.757773] rtl8821ae-0:rtl_op_set_key():<0-0> disable key delete one entry
[ 1541.757775] rtl8821ae-0:rtl_cam_delete_one_entry():<0-0> key_idx:1
[ 1541.757783] rtl8821ae-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A4: 0 
[ 1541.757785] rtl8821ae-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A0: 80010008 
[ 1542.457314] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1543.860562] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1543.861096] wlan0: authenticate with <MAC C-01 faidherbe_EXT>
[ 1543.861414] rtl8821ae-0:rtl_op_bss_info_changed():<0-0> bssid: <MAC C-01 faidherbe_EXT>
[ 1543.861511] wlan0: send auth to <MAC C-01 faidherbe_EXT> (try 1/3)
[ 1543.861523] rtl8821ae-0:rtl_tx_mgmt_proc():<200-1> MAC80211_LINKING
[ 1543.866079] wlan0: authenticated
[ 1543.868480] wlan0: associate with <MAC C-01 faidherbe_EXT> (try 1/3)
[ 1543.872587] wlan0: RX AssocResp from <MAC C-01 faidherbe_EXT> (capab=0x411 status=0 aid=3)
[ 1543.872603] rtl8821ae-0:rtl_op_sta_add():<0-0> Add sta addr is <MAC C-01 faidherbe_EXT>
[ 1543.872608] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> ratr_bitmap :ff005
[ 1543.872612] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> Rate_index:0, ratr_val:ff005, 0:81:0:5:f0:f:0
[ 1543.872650] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> ratr_bitmap :ff005
[ 1543.872654] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> Rate_index:0, ratr_val:ff005, 0:81:0:5:f0:f:0
[ 1543.872678] rtl8821ae-0:rtl_op_bss_info_changed():<0-0> BSS_CHANGED_ASSOC
[ 1543.872694] rtl8821ae-0:rtl8821ae_set_hw_reg():<0-0> switch case not process 5c
[ 1543.872719] rtl8821ae: 
[ 1543.872724] rtl8821ae_set_fw_rsvdpagepkt(): HW_VAR_SET_TX_CMD: ALL 
[ 1543.872735] rtl8821ae: 
[ 1543.872789] wlan0: associated
[ 1543.880839] rtl8821ae-0:rtl_is_special_data():<10000-1> 802.1X Rx EAPOL pkt!!
[ 1543.890739] rtl8821ae-0:rtl_is_special_data():<10000-1> 802.1X Rx EAPOL pkt!!
[ 1543.891034] rtl8821ae-0:rtl_op_set_key():<0-0> Using hardware based encryption for keyidx: 0, mac: <MAC C-01 faidherbe_EXT>
[ 1543.891040] rtl8821ae-0:rtl_op_set_key():<0-0> alg:CCMP
[ 1543.891042] rtl8821ae-0:rtl_op_set_key():<0-0> set enable_hw_sec, key_type:4(OPEN:0 WEP40:1 TKIP:2 AES:4 WEP104:5)
[ 1543.891044] rtl8821ae-0:rtl8821ae_enable_hw_security_config():<0-0> PairwiseEncAlgorithm = 4 GroupEncAlgorithm = 0
[ 1543.891051] rtl8821ae-0:rtl8821ae_enable_hw_security_config():<0-0> The SECR-value cc 
[ 1543.891056] rtl8821ae-0:rtl_op_set_key():<0-0> set pairwise key
[ 1543.891058] rtl8821ae-0:rtl8821ae_set_key():<0-0> add one entry
[ 1543.891060] rtl8821ae-0:rtl8821ae_set_key():<0-0> set Pairwiase key
[ 1543.891062] rtl8821ae-0:rtl_cam_add_one_entry():<0-0> EntryNo:4, ulKeyId=0, ulEncAlg=4, ulUseDK=0 MacAddr <MAC C-01 faidherbe_EXT>
[ 1543.891064] rtl8821ae: 
[ 1543.891711] rtl8821ae-0:rtl_cam_add_one_entry():<0-0> end 
[ 1543.891851] rtl8821ae-0:rtl_op_set_key():<0-0> Using hardware based encryption for keyidx: 1, mac: <MAC ID removed>
[ 1543.891856] rtl8821ae-0:rtl_op_set_key():<0-0> alg:CCMP
[ 1543.891859] rtl8821ae-0:rtl_op_set_key():<0-0> set group key
[ 1543.891862] rtl8821ae-0:rtl8821ae_set_key():<0-0> add one entry
[ 1543.891864] rtl8821ae-0:rtl8821ae_set_key():<0-0> set group key
[ 1543.891867] rtl8821ae-0:rtl_cam_add_one_entry():<0-0> EntryNo:1, ulKeyId=1, ulEncAlg=4, ulUseDK=0 MacAddr <MAC ID removed>
[ 1543.891870] rtl8821ae: 
[ 1543.892539] rtl8821ae-0:rtl_cam_add_one_entry():<0-0> end 
[ 1544.557037] rtl8821ae-0:rtl_action_proc():<10000-1> Rx ACT_ADDBAREQ From :<MAC C-01 faidherbe_EXT>
[ 1544.557043] rtl8821ae: 
[ 1544.557131] rtl8821ae-0:rtl_rx_agg_start():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0 seq:0
[ 1544.557147] rtl8821ae-0:rtl_action_proc():<200-1> Tx ACT_ADDBARSP From :<MAC wlan0>
[ 1544.568170] rtl8821ae-0:rtl_tx_agg_start():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0 seq:1
[ 1544.568193] rtl8821ae-0:rtl_action_proc():<200-1> Tx ACT_ADDBAREQ From :<MAC wlan0>
[ 1544.568196] rtl8821ae: 
[ 1544.569782] rtl8821ae-0:rtl_action_proc():<10000-1> Rx ACT_ADDBARSP From :<MAC C-01 faidherbe_EXT>
[ 1544.569836] rtl8821ae-0:rtl_tx_agg_oper():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0
[ 1551.732191] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> ratr_bitmap :ff000
[ 1551.732196] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> Rate_index:0, ratr_val:ff000, 0:81:0:0:f0:f:0
[ 1569.758310] rtl8821ae-0:rtl_tx_agg_stop():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0
[ 1569.758333] rtl8821ae-0:rtl_action_proc():<400-1> ACT_ADDBADEL From :<MAC wlan0>
[ 1570.629703] rtl8821ae-0:rtl_tx_agg_start():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0 seq:102
[ 1570.629724] rtl8821ae-0:rtl_action_proc():<200-1> Tx ACT_ADDBAREQ From :<MAC wlan0>
[ 1570.629727] rtl8821ae: 
[ 1570.631255] rtl8821ae-0:rtl_action_proc():<10000-1> Rx ACT_ADDBARSP From :<MAC C-01 faidherbe_EXT>
[ 1570.631301] rtl8821ae-0:rtl_tx_agg_oper():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0
[ 1576.286469] rtl8821ae-0:rtl_tx_agg_stop():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0
[ 1576.286495] rtl8821ae-0:rtl_action_proc():<400-1> ACT_ADDBADEL From :<MAC wlan0>
[ 1580.672056] rtl8821ae-0:rtl_tx_agg_start():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0 seq:103
[ 1580.672093] rtl8821ae-0:rtl_action_proc():<200-1> Tx ACT_ADDBAREQ From :<MAC wlan0>
[ 1580.672099] rtl8821ae: 
[ 1580.673607] rtl8821ae-0:rtl_action_proc():<10000-1> Rx ACT_ADDBARSP From :<MAC C-01 faidherbe_EXT>
[ 1580.673669] rtl8821ae-0:rtl_tx_agg_oper():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0
[ 1590.274696] rtl8821ae-0:rtl_tx_agg_stop():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0
[ 1590.274717] rtl8821ae-0:rtl_action_proc():<400-1> ACT_ADDBADEL From :<MAC wlan0>
[ 1590.714549] rtl8821ae-0:rtl_tx_agg_start():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0 seq:106
[ 1590.714571] rtl8821ae-0:rtl_action_proc():<200-1> Tx ACT_ADDBAREQ From :<MAC wlan0>
[ 1590.714574] rtl8821ae: 
[ 1590.716092] rtl8821ae-0:rtl_action_proc():<10000-1> Rx ACT_ADDBARSP From :<MAC C-01 faidherbe_EXT>
[ 1590.716136] rtl8821ae-0:rtl_tx_agg_oper():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0
[ 1645.481627] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1645.587968] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1645.849456] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1645.955811] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1646.217243] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1646.323504] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1646.585062] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1646.691376] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1646.952838] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1647.059174] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1647.320549] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1647.426950] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1647.688399] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1647.794795] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1648.056224] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1648.162566] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1648.423991] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1648.530331] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1648.791772] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1648.898124] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1649.159577] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1649.265858] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1649.527376] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1649.633689] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1649.895197] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1650.001505] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1650.361280] rtl8821ae-0:rtl_tx_agg_stop():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0
[ 1650.361304] rtl8821ae-0:rtl_action_proc():<400-1> ACT_ADDBADEL From :<MAC wlan0>
[ 1651.876463] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off for 2 s
[ 1653.879453] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off for 4 s
[ 1654.383093] rtl8821ae-0:rtl_tx_agg_start():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0 seq:674
[ 1654.383114] rtl8821ae-0:rtl_action_proc():<200-1> Tx ACT_ADDBAREQ From :<MAC wlan0>
[ 1654.383117] rtl8821ae: 
[ 1654.385208] rtl8821ae-0:rtl_action_proc():<10000-1> Rx ACT_ADDBARSP From :<MAC C-01 faidherbe_EXT>
[ 1654.385261] rtl8821ae-0:rtl_tx_agg_oper():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0
[ 1655.882298] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off for 6 s
[ 1657.885219] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off for 8 s
[ 1659.888032] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off for 10 s
[ 1659.888039] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off, try to reconnect now
[ 1659.888055] wlan0: Connection to AP <MAC C-01 faidherbe_EXT> lost
[ 1659.896070] rtl8821ae-0:rtl_tx_agg_stop():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0
[ 1659.896100] rtl8821ae-0:rtl_rx_agg_stop():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0
[ 1659.904076] rtl8821ae-0:rtl_op_set_key():<0-0> Disabling hardware based encryption for keyidx: 0, mac: <MAC C-01 faidherbe_EXT>
[ 1659.904087] rtl8821ae-0:rtl_op_set_key():<0-0> alg:CCMP
[ 1659.904091] rtl8821ae-0:rtl_op_set_key():<0-0> set enable_hw_sec, key_type:4(OPEN:0 WEP40:1 TKIP:2 AES:4 WEP104:5)
[ 1659.904095] rtl8821ae-0:rtl8821ae_enable_hw_security_config():<0-0> PairwiseEncAlgorithm = 4 GroupEncAlgorithm = 4
[ 1659.904105] rtl8821ae-0:rtl8821ae_enable_hw_security_config():<0-0> The SECR-value cc 
[ 1659.904110] rtl8821ae-0:rtl_op_set_key():<0-0> disable key delete one entry
[ 1659.904114] rtl8821ae-0:rtl_cam_delete_one_entry():<0-0> key_idx:0
[ 1659.904121] rtl8821ae-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A4: 0 
[ 1659.904124] rtl8821ae-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A0: 80010000 
[ 1659.904188] rtl8821ae-0:rtl_op_sta_remove():<0-0> Remove sta addr is <MAC C-01 faidherbe_EXT>
[ 1659.904304] rtl8821ae-0:rtl_op_bss_info_changed():<0-0> BSS_CHANGED_UN_ASSOC
[ 1659.904333] rtl8821ae-0:rtl_op_bss_info_changed():<0-0> bssid: <MAC ID removed>
[ 1659.920066] rtl8821ae-0:rtl_op_set_key():<0-0> Disabling hardware based encryption for keyidx: 1, mac: <MAC ID removed>
[ 1659.920075] rtl8821ae-0:rtl_op_set_key():<0-0> alg:CCMP
[ 1659.920078] rtl8821ae-0:rtl_op_set_key():<0-0> disable key delete one entry
[ 1659.920081] rtl8821ae-0:rtl_cam_delete_one_entry():<0-0> key_idx:1
[ 1659.920090] rtl8821ae-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A4: 0 
[ 1659.920093] rtl8821ae-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A0: 80010008 
[ 1660.619551] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1662.022819] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1662.023339] wlan0: authenticate with <MAC C-01 faidherbe_EXT>
[ 1662.023658] rtl8821ae-0:rtl_op_bss_info_changed():<0-0> bssid: <MAC C-01 faidherbe_EXT>
[ 1662.023751] wlan0: send auth to <MAC C-01 faidherbe_EXT> (try 1/3)
[ 1662.023760] rtl8821ae-0:rtl_tx_mgmt_proc():<200-1> MAC80211_LINKING
[ 1662.026761] wlan0: authenticated
[ 1662.030776] wlan0: associate with <MAC C-01 faidherbe_EXT> (try 1/3)
[ 1662.033899] wlan0: RX AssocResp from <MAC C-01 faidherbe_EXT> (capab=0x411 status=0 aid=3)
[ 1662.033911] rtl8821ae-0:rtl_op_sta_add():<0-0> Add sta addr is <MAC C-01 faidherbe_EXT>
[ 1662.033916] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> ratr_bitmap :ff005
[ 1662.033918] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> Rate_index:0, ratr_val:ff005, 0:81:0:5:f0:f:0
[ 1662.033953] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> ratr_bitmap :ff005
[ 1662.033955] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> Rate_index:0, ratr_val:ff005, 0:81:0:5:f0:f:0
[ 1662.033977] rtl8821ae-0:rtl_op_bss_info_changed():<0-0> BSS_CHANGED_ASSOC
[ 1662.033992] rtl8821ae-0:rtl8821ae_set_hw_reg():<0-0> switch case not process 5c
[ 1662.034012] rtl8821ae: 
[ 1662.034015] rtl8821ae_set_fw_rsvdpagepkt(): HW_VAR_SET_TX_CMD: ALL 
[ 1662.034023] rtl8821ae: 
[ 1662.034074] wlan0: associated
[ 1662.040218] rtl8821ae-0:rtl_is_special_data():<10000-1> 802.1X Rx EAPOL pkt!!
[ 1662.058948] rtl8821ae-0:rtl_is_special_data():<10000-1> 802.1X Rx EAPOL pkt!!
[ 1662.059241] rtl8821ae-0:rtl_op_set_key():<0-0> Using hardware based encryption for keyidx: 0, mac: <MAC C-01 faidherbe_EXT>
[ 1662.059247] rtl8821ae-0:rtl_op_set_key():<0-0> alg:CCMP
[ 1662.059249] rtl8821ae-0:rtl_op_set_key():<0-0> set enable_hw_sec, key_type:4(OPEN:0 WEP40:1 TKIP:2 AES:4 WEP104:5)
[ 1662.059251] rtl8821ae-0:rtl8821ae_enable_hw_security_config():<0-0> PairwiseEncAlgorithm = 4 GroupEncAlgorithm = 0
[ 1662.059259] rtl8821ae-0:rtl8821ae_enable_hw_security_config():<0-0> The SECR-value cc 
[ 1662.059263] rtl8821ae-0:rtl_op_set_key():<0-0> set pairwise key
[ 1662.059265] rtl8821ae-0:rtl8821ae_set_key():<0-0> add one entry
[ 1662.059267] rtl8821ae-0:rtl8821ae_set_key():<0-0> set Pairwiase key
[ 1662.059269] rtl8821ae-0:rtl_cam_add_one_entry():<0-0> EntryNo:4, ulKeyId=0, ulEncAlg=4, ulUseDK=0 MacAddr <MAC C-01 faidherbe_EXT>
[ 1662.059271] rtl8821ae: 
[ 1662.059918] rtl8821ae-0:rtl_cam_add_one_entry():<0-0> end 
[ 1662.060062] rtl8821ae-0:rtl_op_set_key():<0-0> Using hardware based encryption for keyidx: 1, mac: <MAC ID removed>
[ 1662.060067] rtl8821ae-0:rtl_op_set_key():<0-0> alg:CCMP
[ 1662.060070] rtl8821ae-0:rtl_op_set_key():<0-0> set group key
[ 1662.060072] rtl8821ae-0:rtl8821ae_set_key():<0-0> add one entry
[ 1662.060075] rtl8821ae-0:rtl8821ae_set_key():<0-0> set group key
[ 1662.060088] rtl8821ae-0:rtl_cam_add_one_entry():<0-0> EntryNo:1, ulKeyId=1, ulEncAlg=4, ulUseDK=0 MacAddr <MAC ID removed>
[ 1662.060090] rtl8821ae: 
[ 1662.060734] rtl8821ae-0:rtl_cam_add_one_entry():<0-0> end 
[ 1663.254099] rtl8821ae-0:rtl_tx_agg_start():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0 seq:1
[ 1663.254126] rtl8821ae-0:rtl_action_proc():<200-1> Tx ACT_ADDBAREQ From :<MAC wlan0>
[ 1663.254129] rtl8821ae: 
[ 1663.256001] rtl8821ae-0:rtl_action_proc():<10000-1> Rx ACT_ADDBARSP From :<MAC C-01 faidherbe_EXT>
[ 1663.256048] rtl8821ae-0:rtl_tx_agg_oper():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0
[ 1665.896622] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> ratr_bitmap :f0000
[ 1665.896627] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> Rate_index:0, ratr_val:f0000, 0:81:0:0:0:f:0
[ 1667.108586] rtl8821ae-0:rtl_action_proc():<10000-1> Rx ACT_ADDBAREQ From :<MAC C-01 faidherbe_EXT>
[ 1667.108592] rtl8821ae: 
[ 1667.108680] rtl8821ae-0:rtl_rx_agg_start():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0 seq:2
[ 1667.108692] rtl8821ae-0:rtl_action_proc():<200-1> Tx ACT_ADDBARSP From :<MAC wlan0>
[ 1680.670052] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1680.776412] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1681.037848] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1681.144185] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1681.405635] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1681.512019] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1681.773479] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1681.879818] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1682.141274] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1682.247528] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1682.509036] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1682.615375] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1682.876817] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1682.983187] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1683.244649] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1683.259114] rtl8821ae-0:rtl_tx_agg_stop():<0-0> on ra = <MAC C-01 faidherbe_EXT> tid = 0
[ 1683.350969] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1683.612422] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1683.718772] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1683.980220] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1684.086550] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1684.348003] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1684.454368] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1684.715798] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1684.822161] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1685.083618] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[ 1685.189968] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[ 1685.190503] rtl8821ae-0:rtl_action_proc():<400-1> ACT_ADDBADEL From :<MAC wlan0>

	======== Done ========
```

Anyone having any idea to help?

---

### Post by castor_fou on 2015-01-03
Switching to rtlwifi_new seems to fix my issues :

cd Applications/lwfinger
git clone [https://github.com/lwfinger/rtlwifi_new.git](https://github.com/lwfinger/rtlwifi_new.git)
cd rtlwifi_new/
make
sudo make install
sudo depmod -a

sudo mv /lib/modules/3.16.0-28-generic/kernel/drivers/staging/rtl8821ae/rtl8821ae.ko /lib/modules/3.16.0-28-generic/kernel/drivers/staging/rtl8821ae/rtl8821ae.ko.save
sudo mv /lib/modules/3.16.0-28-generic/kernel/drivers/staging/rtl8192ee/r8192ee.ko /lib/modules/3.16.0-28-generic/kernel/drivers/staging/rtl8192ee/r8192ee.ko.save

sudo modprobe -v rtl8821ae

---

### Post by neeseius on 2015-06-22
> **castor_fou said:**
> Switching to rtlwifi_new seems to fix my issues :

cd Applications/lwfinger
git clone [https://github.com/lwfinger/rtlwifi_new.git](https://github.com/lwfinger/rtlwifi_new.git)
cd rtlwifi_new/
make
sudo make install
sudo depmod -a

sudo mv /lib/modules/3.16.0-28-generic/kernel/drivers/staging/rtl8821ae/rtl8821ae.ko /lib/modules/3.16.0-28-generic/kernel/drivers/staging/rtl8821ae/rtl8821ae.ko.save
sudo mv /lib/modules/3.16.0-28-generic/kernel/drivers/staging/rtl8192ee/r8192ee.ko /lib/modules/3.16.0-28-generic/kernel/drivers/staging/rtl8192ee/r8192ee.ko.save

sudo modprobe -v rtl8821ae

Latest build of Centos 7 doesn't have even have a driver for the rtl8821. Will these directions work in centos 7?

What is Applications/lwfinger and git clone, is that similar to wget? I am trying to get this adapter working.

---

