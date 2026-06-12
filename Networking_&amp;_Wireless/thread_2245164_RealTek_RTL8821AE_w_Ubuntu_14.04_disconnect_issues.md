---
title: "RealTek RTL8821AE w/ Ubuntu 14.04 disconnect issues"
date: 2014-09-21
forum: Networking &amp; Wireless
---

### Post by icurays1 on 2014-09-21
Yet another one of these "random disconnect" problems.  My WiFi is stable for anywhere from 5 minutes to several hours, then disconnects.   I've tried several suggestions from other forum posts, etc, but these things seem fairly case-dependent? 


Here is the output of my wireless_script: 

```

    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

Hilbert 3.13.0-35-generic x86_64,  Ubuntu 14.04.1 LTS, trusty

CPU    : Intel(R) Core(TM) i3-4150 CPU @ 3.50GHz
Memory : 7937 MB
Uptime : 12:27:26 up 1 min,  2 users,  load average: 0.63, 0.22, 0.08


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

03:00.0 Ethernet controller [0200]: Qualcomm Atheros QCA8171 Gigabit Ethernet [1969:10a1] (rev 10)
    Subsystem: ASRock Incorporation Device [1849:10a1]
    Kernel driver in use: alx
04:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8821AE 802.11ac PCIe Wireless Network Adapter [10ec:8821]
    Subsystem: Realtek Semiconductor Co., Ltd. RTL8821AE 802.11ac PCIe Wireless Network Adapter [10ec:8821]
    Kernel driver in use: rtl8821ae


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 002 Device 002: ID 8087:8001 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8009 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 004: ID 413c:2003 Dell Computer Corp. Keyboard
Bus 003 Device 003: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 003 Device 002: ID 1bcf:0c31 Sunplus Innovation Technology Inc. SPIF30x Serial-ATA bridge
Bus 003 Device 005: ID 0bda:0821 Realtek Semiconductor Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11abgn  ESSID:"Orchestra"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC C-NA *Orchestra 1>   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=60/70  Signal level=-50 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:5   Missed beacon:0



rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface        Soft blocked  Hard blocked
0: phy0: Wireless LAN      no            no
1: hci0: Bluetooth         no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

rtl8821ae             575923  0 
mac80211              630653  1 rtl8821ae
cfg80211              484040  2 mac80211,rtl8821ae


module parameters ~~~~~~~~~~~~~~~~~~

cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
rtl8821ae     (4): fwlps=N | ips=N | swenc=N | swlps=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
====================o=============o===========o=============o=========o===========o==============o===========
 Interface & ID     | Type        | Driver    | State       | Default | Speed     | Support      | HW Addr   
====================o=============o===========o=============o=========o===========o==============o===========
 wlan0  [Orchestra] | 802.11 WiFi | rtl8821ae | connected   | yes     | 72 Mb/s   | WEP/WPA/WPA2 | <MAC wlan0>

    *Orchestra:      Infra, <MAC C-NA *Orchestra 1>, Freq 2437 MHz, Rate 54 Mb/s, Strength 76 WPA2
    1 cent spot:     Infra, <MAC C-NA 1 cent spot 1>, Freq 2437 MHz, Rate 54 Mb/s, Strength 80 WPA
    CenturyLink5671: Infra, <MAC C-NA CenturyLink5671 1>, Freq 2412 MHz, Rate 54 Mb/s, Strength 77 WPA WPA2

    Address:         192.168.1.107
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1
    DNS:             192.168.1.1
--------------------+-------------+-----------+-------------+---------+-----------+--------------+-----------
 eth0               | Wired       | alx       | unavailable | no      |           |              | <MAC eth0>
--------------------+-------------+-----------+-------------+---------+-----------+--------------+-----------


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

Orchestra            : ssid=Orchestra | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 127.0.1.1


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

--- 192.168.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 2.814/17.482/32.151/14.669 ms

--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1000ms
rtt min/avg/max/mdev = 0.038/0.040/0.042/0.002 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "en_US.UTF-8")
country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


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

          Current Frequency:2.437 GHz (Channel 6)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~



blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[rtl8821ae]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/staging/rtl8821ae/rtl8821ae.ko
firmware:       rtlwifi/rtl8821aefw.bin
srcversion:     91658B35399978A03EFFBA7
depends:        mac80211,cfg80211
parm:           swlps:bool
parm:           swenc:using hardware crypto (default 0 [hardware])
parm:           ips:using no link power save (default 1 is open)
parm:           fwlps:using linked fw control power save (default 1 is open)

[mac80211]
filename:       /lib/modules/3.13.0-35-generic/kernel/net/mac80211/mac80211.ko
srcversion:     D491AB7C521706DA5F4BE7C
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-35-generic/kernel/net/wireless/cfg80211.ko
srcversion:     C2478077E22138832B71659
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x1969:/sys/devices/pci0000:00/0000:00:1c.2/0000:02:00.0 (alx)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x10ec:0x8821 (rtl8821ae)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


Custom files/entries ~~~~~~~~~~~~~~~

/etc/modules        : Not Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Not Default

[/etc/modules]
loop
coretemp
nct6775

[/etc/modprobe.d]
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
mlx4.conf         : softdep mlx4_core post: mlx4_en
nvidia-installer-disable-nouveau.conf: blacklist nouveau
                    options nouveau modeset=0

[/etc/pm/power.d/wireless]


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/boot/vmlinuz-3.13.0-35-generic root=UUID=66dd172c-a0d7-4ca9-8405-46256e8063ea ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    0.426501] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.426682] audit: initializing netlink socket (disabled)
[    0.525547] alx 0000:03:00.0 eth0: Qualcomm Atheros AR816x/AR817x Ethernet [<MAC eth0>]
[    1.163546] rtl8821ae: module is from the staging directory, the quality is unknown, you have been warned.
[    1.164553] rtl8821ae 0000:04:00.0: enabling device (0000 -> 0003)
[    1.164638] rtl8821ae-0:rtl_pci_probe():<0-0> mem mapped space: start: 0xf7100000 len:00004000 flags:00140204, after map:0xffffc90004c88000
[    1.164652] rtl8821ae-0:_rtl_pci_find_adapter():<0-0> Pci Bridge Vendor is found index: 0
[    1.164654] rtl8821ae-0:_rtl_pci_find_adapter():<0-0> pcidev busnumber:devnumber:funcnumber:vendor:link_ctl 4:0:0:10ec:0
[    1.164656] rtl8821ae-0:_rtl_pci_find_adapter():<0-0> pci_bridge busnumber:devnumber:funcnumber:vendor:pcie_cap:link_ctl_reg:amd 0:28:7:8086:40:40:0
[    1.164683] rtl8821ae-0:rtl8821ae_read_eeprom_info():<0-0> Boot from EFUSE
[    1.177801] rtl8821ae: 
[    1.177986] rtl8821ae-0:_rtl8821ae_read_adapter_info():<0-0> dev_addr: <MAC wlan0>
[    1.177990] rtl8821ae:_rtl8821ae_get_chnl_group(): 5G, Channel 163 in Group not found 
[    1.177993] rtl8821ae:_rtl8821ae_get_chnl_group(): 5G, Channel 163 in Group not found 
[    1.235390] rtl8821ae-0:rtl_btc_init_hal_vars():<0-0> rtl_btc_init_hal_vars, antNum is 2
[    1.235393] rtl8821ae-0:rtl_btc_init_hal_vars():<0-0> rtl_btc_init_hal_vars, bt_exist is 1
[    1.235394] rtl8821ae-0:rtl_btc_init_hal_vars():<0-0> rtl_btc_init_hal_vars, bt_type is 7
[    1.235555] rtl8821ae-0:_rtl_init_hw_ht_capab():<0-0> 1T1R
[    1.235557] rtl8821ae-0:_rtl_init_hw_ht_capab():<0-0> 1T1R
[    1.253186] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[    1.253729] rtlwifi: wireless switch is on
[    1.253748] rtl8821ae-0:rtl_pci_intr_mode_legacy():<0-0> Pin-based Interrupt Mode!
[    1.520105] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    1.627137] rtl8821ae-0:rtl_pci_start():<0-0>  rtl_pci_start 
[    1.636757] rtl8821ae-0:rtl8821ae_download_fw():<0-0> normal Firmware SIZE 29198 
[    1.636760] rtl8821ae-0:rtl8821ae_download_fw():<0-0> Firmware Version(18), Signature(0x2101),Size(32)
[    1.650637] rtl8821ae-0:_rtl8821ae_fw_free_to_go():<0-0> Checksum report OK ! REG_MCUFWDL:0x00070604 .
[    1.680195] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 0][RfPath 0][TxNum 0][RateSection 0] = 0x32343638
[    1.680198] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 0][RfPath 0][TxNum 0][RateSection 1] = 0x36363838
[    1.680199] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 0][RfPath 0][TxNum 0][RateSection 2] = 0x28303234
[    1.680200] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 0][RfPath 0][TxNum 0][RateSection 3] = 0x34363838
[    1.680201] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 0][RfPath 0][TxNum 0][RateSection 4] = 0x26283032
[    1.680202] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 0][RfPath 0][TxNum 0][RateSection 7] = 0x32343636
[    1.680203] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 0][RfPath 0][TxNum 0][RateSection 8] = 0x24262830
[    1.680204] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 0][RfPath 0][TxNum 0][RateSection 9] = 0x2022
[    1.680205] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 1][RfPath 0][TxNum 0][RateSection 1] = 0x34343636
[    1.680206] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 1][RfPath 0][TxNum 0][RateSection 2] = 0x26283032
[    1.680207] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 1][RfPath 0][TxNum 0][RateSection 3] = 0x32343636
[    1.680208] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 1][RfPath 0][TxNum 0][RateSection 4] = 0x24262830
[    1.680209] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 1][RfPath 0][TxNum 0][RateSection 7] = 0x32343636
[    1.680210] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 1][RfPath 0][TxNum 0][RateSection 8] = 0x24262830
[    1.680211] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 1][RfPath 0][TxNum 0][RateSection 9] = 0x2022
[    1.780689] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[    1.780726] rtl8821ae-0:rtl8821ae_enable_hw_security_config():<0-0> PairwiseEncAlgorithm = 0 GroupEncAlgorithm = 0
[    1.780731] rtl8821ae-0:rtl8821ae_enable_hw_security_config():<0-0> The SECR-value cc 
[    1.780974] rtl8821ae-0:rtl8821ae_set_hw_reg():<0-0> switch case not process 3e
[    1.780981] rtl8821ae-0:rtl_pci_start():<0-0> rtl_pci_start OK
[    1.781412] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    1.781577] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    2.453214] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[    3.860027] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[    3.866727] wlan0: authenticate with <MAC C-NA *Orchestra 1>
[    3.867058] rtl8821ae-0:rtl_op_bss_info_changed():<0-0> bssid: <MAC C-NA *Orchestra 1>
[    3.867111] wlan0: send auth to <MAC C-NA *Orchestra 1> (try 1/3)
[    3.867116] rtl8821ae-0:rtl_tx_mgmt_proc():<200-1> MAC80211_LINKING
[    3.904540] wlan0: authenticated
[    3.907958] wlan0: associate with <MAC C-NA *Orchestra 1> (try 1/3)
[    3.924613] wlan0: RX AssocResp from <MAC C-NA *Orchestra 1> (capab=0x411 status=0 aid=4)
[    3.924617] rtl8821ae-0:rtl_op_sta_add():<0-0> Add sta addr is <MAC C-NA *Orchestra 1>
[    3.924619] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> ratr_bitmap :ff005
[    3.924620] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> Rate_index:0, ratr_val:ff005, 0:81:0:5:f0:f:0
[    3.924657] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> ratr_bitmap :ff005
[    3.924658] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> Rate_index:0, ratr_val:ff005, 0:81:0:5:f0:f:0
[    3.924683] rtl8821ae-0:rtl_op_bss_info_changed():<0-0> BSS_CHANGED_ASSOC
[    3.924704] rtl8821ae-0:rtl8821ae_set_hw_reg():<0-0> switch case not process 5c
[    3.924726] rtl8821ae: 
[    3.924727] In process "kworker/u8:5" (pid 150):rtl8821ae_set_fw_rsvdpagepkt(): HW_VAR_SET_TX_CMD: ALL 
[    3.924732] rtl8821ae: 
[    3.924791] wlan0: associated
[    3.924806] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[    3.930063] rtl8821ae-0:rtl_action_proc():<10000-1> Rx ACT_ADDBAREQ From :<MAC C-NA *Orchestra 1>
[    3.930066] rtl8821ae: 
[    3.930109] rtl8821ae-0:rtl_rx_agg_start():<0-0> on ra = <MAC C-NA *Orchestra 1> tid = 0 seq:0
[    3.930116] rtl8821ae-0:rtl_action_proc():<200-1> Tx ACT_ADDBARSP From :<MAC wlan0>
[    4.011331] rtl8821ae-0:rtl_is_special_data():<10000-1> 802.1X Rx EAPOL pkt!!
[    4.012007] rtl8821ae-0:rtl_is_special_data():<200-1> 802.1X Tx EAPOL pkt!!
[    4.012045] rtl8821ae-0:rtl_is_special_data():<100-1> 802.1X Tx EAPOL pkt!!
[    4.031380] rtl8821ae-0:rtl_is_special_data():<10000-1> 802.1X Rx EAPOL pkt!!
[    4.031490] rtl8821ae-0:rtl_is_special_data():<200-1> 802.1X Tx EAPOL pkt!!
[    4.031526] rtl8821ae-0:rtl_is_special_data():<100-1> 802.1X Tx EAPOL pkt!!
[    4.076074] rtl8821ae-0:rtl_op_set_key():<0-0> Using hardware based encryption for keyidx: 0, mac: <MAC C-NA *Orchestra 1>
[    4.076077] rtl8821ae-0:rtl_op_set_key():<0-0> alg:CCMP
[    4.076078] rtl8821ae-0:rtl_op_set_key():<0-0> set enable_hw_sec, key_type:4(OPEN:0 WEP40:1 TKIP:2 AES:4 WEP104:5)
[    4.076079] rtl8821ae-0:rtl8821ae_enable_hw_security_config():<0-0> PairwiseEncAlgorithm = 4 GroupEncAlgorithm = 0
[    4.076085] rtl8821ae-0:rtl8821ae_enable_hw_security_config():<0-0> The SECR-value cc 
[    4.076088] rtl8821ae-0:rtl_op_set_key():<0-0> set pairwise key
[    4.076090] rtl8821ae-0:rtl8821ae_set_key():<0-0> add one entry
[    4.076090] rtl8821ae-0:rtl8821ae_set_key():<0-0> set Pairwiase key
[    4.076091] rtl8821ae-0:rtl_cam_add_one_entry():<0-0> EntryNo:4, ulKeyId=0, ulEncAlg=4, ulUseDK=0 MacAddr <MAC C-NA *Orchestra 1>
[    4.076092] rtl8821ae: 
[    4.076731] rtl8821ae-0:rtl_cam_add_one_entry():<0-0> end 
[    4.076863] rtl8821ae-0:rtl_op_set_key():<0-0> Using hardware based encryption for keyidx: 1, mac: <MAC ID removed>
[    4.076867] rtl8821ae-0:rtl_op_set_key():<0-0> alg:CCMP
[    4.076868] rtl8821ae-0:rtl_op_set_key():<0-0> set group key
[    4.076870] rtl8821ae-0:rtl8821ae_set_key():<0-0> add one entry
[    4.076871] rtl8821ae-0:rtl8821ae_set_key():<0-0> set group key
[    4.076873] rtl8821ae-0:rtl_cam_add_one_entry():<0-0> EntryNo:1, ulKeyId=1, ulEncAlg=4, ulUseDK=0 MacAddr <MAC ID removed>
[    4.076874] rtl8821ae: 
[    4.077514] rtl8821ae-0:rtl_cam_add_one_entry():<0-0> end 
[    4.111988] rtl8821ae-0:rtl_is_special_data():<200-1> dhcp Tx !!
[    5.782439] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> ratr_bitmap :ff000
[    5.782441] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> Rate_index:0, ratr_val:ff000, 0:81:0:0:f0:f:0
[    7.692340] rtl8821ae-0:rtl_is_special_data():<200-1> dhcp Tx !!
[   12.153014] rtl8821ae-0:rtl_is_special_data():<200-1> dhcp Tx !!
[   13.228116] rtl8821ae-0:rtl_tx_agg_start():<0-0> on ra = <MAC C-NA *Orchestra 1> tid = 0 seq:29
[   13.228147] rtl8821ae-0:rtl_action_proc():<200-1> Tx ACT_ADDBAREQ From :<MAC wlan0>
[   13.228148] rtl8821ae: 
[   13.229908] rtl8821ae-0:rtl_action_proc():<10000-1> Rx ACT_ADDBARSP From :<MAC C-NA *Orchestra 1>
[   13.229935] rtl8821ae-0:rtl_tx_agg_oper():<0-0> on ra = <MAC C-NA *Orchestra 1> tid = 0
[   17.796248] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off for 2 s
[   28.520428] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[   28.626808] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[   28.888310] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[   28.994690] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[   29.256165] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[   29.362532] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[   29.624040] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[   29.730428] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[   29.991912] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[   30.098306] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[   30.359775] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[   30.466154] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[   30.727647] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[   30.834036] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[   31.095496] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[   31.201901] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[   31.463380] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[   31.569783] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[   31.831245] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[   31.937645] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[   32.199133] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[   32.305522] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[   32.567008] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[   32.673394] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[   32.934878] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[   33.041269] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[   35.824352] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off for 2 s
[   37.827671] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off for 4 s
[   39.830947] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off for 6 s
[   41.834258] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off for 8 s
[   43.837566] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off for 10 s
[   43.837568] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off, try to reconnect now
[   43.837575] wlan0: Connection to AP <MAC C-NA *Orchestra 1> lost
[   43.841475] rtl8821ae-0:rtl_tx_agg_stop():<0-0> on ra = <MAC C-NA *Orchestra 1> tid = 0
[   43.841482] rtl8821ae-0:rtl_rx_agg_stop():<0-0> on ra = <MAC C-NA *Orchestra 1> tid = 0
[   43.853516] rtl8821ae-0:rtl_op_set_key():<0-0> Disabling hardware based encryption for keyidx: 0, mac: <MAC C-NA *Orchestra 1>
[   43.853531] rtl8821ae-0:rtl_op_set_key():<0-0> alg:CCMP
[   43.853532] rtl8821ae-0:rtl_op_set_key():<0-0> set enable_hw_sec, key_type:4(OPEN:0 WEP40:1 TKIP:2 AES:4 WEP104:5)
[   43.853534] rtl8821ae-0:rtl8821ae_enable_hw_security_config():<0-0> PairwiseEncAlgorithm = 4 GroupEncAlgorithm = 4
[   43.853540] rtl8821ae-0:rtl8821ae_enable_hw_security_config():<0-0> The SECR-value cc 
[   43.853543] rtl8821ae-0:rtl_op_set_key():<0-0> disable key delete one entry
[   43.853544] rtl8821ae-0:rtl_cam_delete_one_entry():<0-0> key_idx:0
[   43.853548] rtl8821ae-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A4: 0 
[   43.853549] rtl8821ae-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A0: 80010000 
[   43.853570] rtl8821ae-0:rtl_op_sta_remove():<0-0> Remove sta addr is <MAC C-NA *Orchestra 1>
[   43.853595] rtl8821ae-0:rtl_op_bss_info_changed():<0-0> BSS_CHANGED_UN_ASSOC
[   43.853623] rtl8821ae-0:rtl_op_bss_info_changed():<0-0> bssid: <MAC ID removed>
[   43.865496] rtl8821ae-0:rtl_op_set_key():<0-0> Disabling hardware based encryption for keyidx: 1, mac: <MAC ID removed>
[   43.865501] rtl8821ae-0:rtl_op_set_key():<0-0> alg:CCMP
[   43.865502] rtl8821ae-0:rtl_op_set_key():<0-0> disable key delete one entry
[   43.865503] rtl8821ae-0:rtl_cam_delete_one_entry():<0-0> key_idx:1
[   43.865509] rtl8821ae-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A4: 0 
[   43.865509] rtl8821ae-0:rtl_cam_delete_one_entry():<0-0> rtl_cam_delete_one_entry(): WRITE A0: 80010008 
[   44.569235] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[   45.972735] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[   45.972984] wlan0: authenticate with <MAC C-NA *Orchestra 1>
[   45.973435] rtl8821ae-0:rtl_op_bss_info_changed():<0-0> bssid: <MAC C-NA *Orchestra 1>
[   45.973507] wlan0: send auth to <MAC C-NA *Orchestra 1> (try 1/3)
[   45.973515] rtl8821ae-0:rtl_tx_mgmt_proc():<200-1> MAC80211_LINKING
[   45.979684] wlan0: authenticated
[   45.980751] wlan0: associate with <MAC C-NA *Orchestra 1> (try 1/3)
[   45.983852] wlan0: RX AssocResp from <MAC C-NA *Orchestra 1> (capab=0x411 status=0 aid=4)
[   45.983856] rtl8821ae-0:rtl_op_sta_add():<0-0> Add sta addr is <MAC C-NA *Orchestra 1>
[   45.983858] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> ratr_bitmap :ff005
[   45.983859] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> Rate_index:0, ratr_val:ff005, 0:81:0:5:f0:f:0
[   45.983895] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> ratr_bitmap :ff005
[   45.983896] rtl8821ae-0:rtl8821ae_update_hal_rate_mask():<0-0> Rate_index:0, ratr_val:ff005, 0:81:0:5:f0:f:0
[   45.983921] rtl8821ae-0:rtl_op_bss_info_changed():<0-0> BSS_CHANGED_ASSOC
[   45.983943] rtl8821ae-0:rtl8821ae_set_hw_reg():<0-0> switch case not process 5c
[   45.983967] rtl8821ae: 
[   45.983967] In process "kworker/u8:5" (pid 150):rtl8821ae_set_fw_rsvdpagepkt(): HW_VAR_SET_TX_CMD: ALL 
[   45.983974] rtl8821ae: 
[   45.984031] wlan0: associated
[   45.993063] rtl8821ae-0:rtl_action_proc():<10000-1> Rx ACT_ADDBAREQ From :<MAC C-NA *Orchestra 1>
[   45.993066] rtl8821ae: 
[   45.993107] rtl8821ae-0:rtl_rx_agg_start():<0-0> on ra = <MAC C-NA *Orchestra 1> tid = 0 seq:0
[   45.993114] rtl8821ae-0:rtl_action_proc():<200-1> Tx ACT_ADDBARSP From :<MAC wlan0>
[   45.996726] rtl8821ae-0:rtl_is_special_data():<10000-1> 802.1X Rx EAPOL pkt!!
[   45.997163] rtl8821ae-0:rtl_is_special_data():<200-1> 802.1X Tx EAPOL pkt!!
[   45.997195] rtl8821ae-0:rtl_is_special_data():<100-1> 802.1X Tx EAPOL pkt!!
[   46.005224] rtl8821ae-0:rtl_is_special_data():<10000-1> 802.1X Rx EAPOL pkt!!
[   46.005280] rtl8821ae-0:rtl_is_special_data():<200-1> 802.1X Tx EAPOL pkt!!
[   46.005324] rtl8821ae-0:rtl_is_special_data():<100-1> 802.1X Tx EAPOL pkt!!
[   46.005349] rtl8821ae-0:rtl_op_set_key():<0-0> Using hardware based encryption for keyidx: 0, mac: <MAC C-NA *Orchestra 1>
[   46.005351] rtl8821ae-0:rtl_op_set_key():<0-0> alg:CCMP
[   46.005352] rtl8821ae-0:rtl_op_set_key():<0-0> set enable_hw_sec, key_type:4(OPEN:0 WEP40:1 TKIP:2 AES:4 WEP104:5)
[   46.005353] rtl8821ae-0:rtl8821ae_enable_hw_security_config():<0-0> PairwiseEncAlgorithm = 4 GroupEncAlgorithm = 0
[   46.005359] rtl8821ae-0:rtl8821ae_enable_hw_security_config():<0-0> The SECR-value cc 
[   46.005362] rtl8821ae-0:rtl_op_set_key():<0-0> set pairwise key
[   46.005363] rtl8821ae-0:rtl8821ae_set_key():<0-0> add one entry
[   46.005364] rtl8821ae-0:rtl8821ae_set_key():<0-0> set Pairwiase key
[   46.005365] rtl8821ae-0:rtl_cam_add_one_entry():<0-0> EntryNo:4, ulKeyId=0, ulEncAlg=4, ulUseDK=0 MacAddr <MAC C-NA *Orchestra 1>
[   46.005366] rtl8821ae: 
[   46.006003] rtl8821ae-0:rtl_cam_add_one_entry():<0-0> end 
[   46.006066] rtl8821ae-0:rtl_op_set_key():<0-0> Using hardware based encryption for keyidx: 1, mac: <MAC ID removed>
[   46.006069] rtl8821ae-0:rtl_op_set_key():<0-0> alg:CCMP
[   46.006070] rtl8821ae-0:rtl_op_set_key():<0-0> set group key
[   46.006071] rtl8821ae-0:rtl8821ae_set_key():<0-0> add one entry
[   46.006073] rtl8821ae-0:rtl8821ae_set_key():<0-0> set group key
[   46.006074] rtl8821ae-0:rtl_cam_add_one_entry():<0-0> EntryNo:1, ulKeyId=1, ulEncAlg=4, ulUseDK=0 MacAddr <MAC ID removed>
[   46.006075] rtl8821ae: 
[   46.006715] rtl8821ae-0:rtl_cam_add_one_entry():<0-0> end 
[   52.298555] rtl8821ae-0:rtl_tx_agg_start():<0-0> on ra = <MAC C-NA *Orchestra 1> tid = 0 seq:116
[   52.298566] rtl8821ae-0:rtl_action_proc():<200-1> Tx ACT_ADDBAREQ From :<MAC wlan0>
[   52.298567] rtl8821ae: 
[   52.300487] rtl8821ae-0:rtl_action_proc():<10000-1> Rx ACT_ADDBARSP From :<MAC C-NA *Orchestra 1>
[   52.300518] rtl8821ae-0:rtl_tx_agg_oper():<0-0> on ra = <MAC C-NA *Orchestra 1> tid = 0
[   57.860670] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off for 2 s

    ======== Done ========
```

Thanks for any input!
Nick

---

### Post by varunendra on 2014-09-24
Welcome to the forums Nick!

You seem to have manually created a file "/etc/pm/power.d/wireless", were you having the "Power Management" setting to "on" problem in "iwconfig" output? Where did you get the idea (no bad though) to create that file, and why?

I'm asking because power management can be a reason for such problems (in fact it mostly is), and if it is still happening, we can put something in that file and make it executable to make it work better.

The only other thing that I can think of trying with this driver is to set your country code (US?) explicitly -
```
sudo sed -i 's/^REG.*=$/&US/' /etc/default/crda
sudo iw reg set US
```

As you can notice in the 'dmesg' part of the report, the driver itself doesn't promise much -
```
[    1.163546] rtl8821ae: module is from the staging directory, the quality is unknown, you have been warned.
```

..means perhaps the only other option is to try out a newer kernel, and hope it works better.

---

### Post by tachanchachi on 2015-01-26
Hi! Everybody! 

I have the same issue and the same Network controller. 
Attached you can find the output of my wireless-script run. 

I just got my new computer on Saturday, installed Ubuntu-Gnome 10.10 (Edited, i wrongly wrote 10.04, because that's what I wanted, but could not manage to install this distro with Gnome) alongside Windows 8 yesterday, and everything seemed to work, except the WiFi, which keeps disconnecting at random times. I can have network for few mins up to a couple of hours. I have to reboot the computer in order to have WiFi again, which is quite bad, because I need to have connection in order to work (I log in with ssh to a simulation-cluster, in particular). Right now I have no Ethernet cable which I could use either. So it's quite important to get a solution for this issue for me. 

Although I have use Ubuntu in the past, I was during the last 2 years using Mac-Os, and I didn't have to struggle with configuration issues in a long, long time. So there might be a lot of things I forgot how to use, so please... be quite explicit with how do I have to deal with the solution/commands. 

Every help will be appreciated. 
Thanks in Advance!

MCM.

[EDITED]: I was connected to the internet about 1 hour. When it failed I ran again the wireless-script. You can now find the output of the second run in the attachment. Again, I had to reboot the computer to be able to connect again to the wireless (highly annoying when you are trying to download and install a software). The second script is renamed as wireless-info-NoWifi.tar.gz. By the way! Now I see a question-mark sign where the WiFi sign should be... (!?) but it's connected...

---

### Post by tachanchachi on 2015-01-26
Really? Nobody can help me??? Please!!

---

### Post by brendonwp on 2015-01-27
@tachan - The OP was using 14.04 and you are using 10.04.  IMHO you should install 14.04 and get your system up-to-date following the sticky on "Before Posting in Networking & Wireless". 

I am not technical so have not looked at the files you attached.  If you really need 10.04, you could run it in a Virtual Machine.

---

### Post by pioterek01 on 2015-02-04
I have exactly the same issue... Asus R510JK-DM009H... Ubuntu 14.04, 14.10, kernels from 3.13.0 before "fixing" this bug and after, 3.16.0, 3.17.0 ... always the same situation

Tried installing windows drivers by ndiswrapper...
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

Tried lwfinger/rtlwifi_new repo...
[https://github.com/lwfinger/rtlwifi_new](https://github.com/lwfinger/rtlwifi_new)

Everything failed.
You are my last hope guys! :)

This is my output of wireless_script.txt

```



########## wireless info START ##########


Report from: 04 Feb 2015 20:23 CET +0100


Booted last: 04 Feb 2015 20:08 CET +0100


Script from: 20 Sep 2014 23:04 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 14.10
Release:    14.10
Codename:    utopic


##### kernel ############################


Linux 3.16.0-031600-generic #201408031935 SMP Sun Aug 3 23:36:11 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8821AE 802.11ac PCIe Wireless Network Adapter [10ec:8821]
    Subsystem: AzureWave Device [1a3b:2161]
    Kernel driver in use: rtl8821ae


04:00.1 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 12)
    Subsystem: ASUSTeK Computer Inc. Device [1043:200f]
    Kernel driver in use: r8169


##### lsusb #############################


Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0bda:57b4 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


1: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: asus-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


##### lsmod #############################


rtl8821ae             566837  0 
mac80211              687021  1 rtl8821ae
asus_nb_wmi            16990  0 
asus_wmi               24697  1 asus_nb_wmi
sparse_keymap          13890  1 asus_wmi
cfg80211              521225  2 mac80211,rtl8821ae
mxm_wmi                13021  1 nouveau
wmi                    19379  3 mxm_wmi,nouveau,asus_wmi
video                  20521  3 i915,nouveau,asus_wmi


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::6e71:d9ff:fef9:6c1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:54654 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28854 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:78258678 (78.2 MB)  TX bytes:2924129 (2.9 MB)


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11abgn  ESSID:"Meduza"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC 'Meduza' [AC1]>   
          Bit Rate=6.5 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-22 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0


##### resolv.conf #######################


nameserver 127.0.1.1


##### nm-tool ###########################


NetworkManager Tool


State: connected (global)


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth0' [IF]>


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off


- Device: wlan0  [Meduza] ------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8821ae
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>


  Capabilities:
    Speed:           6 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    NETIASPOT-CD79E0:Infra, <MAC 'NETIASPOT-CD79E0' [AC4]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    Fine_Media_51F334: Infra, <MAC 'Fine_Media_51F334' [AC2]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WPA2
    A7600-H:         Infra, <MAC 'A7600-H' [AC5]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 94 WPA2
    kermit:          Infra, <MAC 'kermit' [AC3]>, Freq 2427 MHz, Rate 54 Mb/s, Strength 77 WPA WPA2
    *Meduza:         Infra, <MAC 'Meduza' [AC1]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 98 WPA WPA2
    FAST3764-1664:   Infra, <MAC 'FAST3764-1664' [AC7]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 67 WPA WPA2
    miron:           Infra, <MAC 'miron' [AC6]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 64 WPA WPA2
    DIRECT-jj-BRAVIA:Infra, <MAC 'DIRECT-jj-BRAVIA' [AN8]>, Freq 2417 MHz, Rate 54 Mb/s, Strength 39 WPA2


  IPv4 Settings:
    Address:         192.168.0.100
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1


    DNS:             192.168.0.1


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


no-auto-default=<MAC 'eth0' [IF]>,


[ifupdown]
managed=false


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/Meduza]] (600 root)
[connection] id=Meduza | type=802-11-wireless
[802-11-wireless] ssid=Meduza | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: Europe/Warsaw (based on set time zone)


country 00: DFS-UNSET
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), NO-IR
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, NO-IR
    (5170 - 5250 @ 40), (3, 20), NO-IR
    (5735 - 5835 @ 40), (3, 20), NO-IR


##### iwlist channels ###################


eth0      no frequency information.


lo        no frequency information.


wlan0     24 channels in total; available frequencies :
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
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 149 : 5.745 GHz
          Channel 153 : 5.765 GHz
          Channel 157 : 5.785 GHz
          Channel 161 : 5.805 GHz
          Channel 165 : 5.825 GHz
          Current Frequency:2.462 GHz (Channel 11)


##### iwlist scan #######################


Channel occupancy:


      2   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.427 GHz (Channel 4)
      3   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.462 GHz (Channel 11)


eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


wlan0     Scan completed :
          Cell 01 - Address: <MAC 'Meduza' [AC1]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-16 dBm  
                    Encryption key:on
                    ESSID:"Meduza"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000162003fa28
                    Extra: Last beacon: 12ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'Fine_Media_51F334' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=68/70  Signal level=-42 dBm  
                    Encryption key:on
                    ESSID:"Fine_Media_51F334"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000b340e75be
                    Extra: Last beacon: 12ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'kermit' [AC3]>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:on
                    ESSID:"kermit"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000014a2a22a682
                    Extra: Last beacon: 12ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'NETIASPOT-CD79E0' [AC4]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-30 dBm  
                    Encryption key:on
                    ESSID:"NETIASPOT-CD79E0"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000005a619e2dfb1
                    Extra: Last beacon: 12ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'A7600-H' [AC5]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=56/70  Signal level=-54 dBm  
                    Encryption key:on
                    ESSID:"A7600-H"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000019c4f81d1a
                    Extra: Last beacon: 12ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'miron' [AC6]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"miron"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000028721a0648
                    Extra: Last beacon: 8000ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'FAST3764-1664' [AC7]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"FAST3764-1664"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s


##### module infos ######################


[rtl8821ae]
filename:       /lib/modules/3.16.0-031600-generic/kernel/drivers/staging/rtl8821ae/rtl8821ae.ko
firmware:       rtlwifi/rtl8821aefw.bin
description:    Realtek 8821ae 802.11ac PCI wireless
license:        GPL
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         Ping Yan<ping_yan@realsil.com.cn>
srcversion:     EA439BC895EA5691716AF12
depends:        mac80211,cfg80211
staging:        Y
intree:         Y
vermagic:       3.16.0-031600-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        22:1A:AC:02:5E:17:C8:E7:6D:81:97:A5:3A:A7:65:A4:61:7A:E7:DC
sig_hashalgo:   sha512
parm:           swlps:bool
parm:           swenc:using hardware crypto (default 0 [hardware])
 (bool)
parm:           ips:using no link power save (default 1 is open)
 (bool)
parm:           fwlps:using linked fw control power save (default 1 is open)
 (bool)


[mac80211]
filename:       /lib/modules/3.16.0-031600-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     E4D3FCB715C0CB33E42D11E
depends:        cfg80211
intree:         Y
vermagic:       3.16.0-031600-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        22:1A:AC:02:5E:17:C8:E7:6D:81:97:A5:3A:A7:65:A4:61:7A:E7:DC
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/3.16.0-031600-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     D86AFD97E7F71C59777C05F
depends:        
intree:         Y
vermagic:       3.16.0-031600-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        22:1A:AC:02:5E:17:C8:E7:6D:81:97:A5:3A:A7:65:A4:61:7A:E7:DC
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[rtl8821ae]
fwlps: N
ips: N
swenc: N
swlps: N


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


[/etc/modprobe.d/modesetting.conf]
options cirrus modeset=1
options mgag200 modeset=1


##### rc.local ##########################


exit 0


##### pm-utils ##########################


[/etc/pm/power.d/disable_wol] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0


[/etc/pm/power.d/laptop-mode] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0


[/etc/pm/power.d/pci_devices] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0


[/etc/pm/power.d/pcie_aspm] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0


[/etc/pm/power.d/sched-powersave] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0


[/etc/pm/power.d/usb_bluetooth] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0


[/etc/pm/power.d/wireless] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0


[/etc/pm/power.d/xfs_buffer] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x10ec:0x8821 (rtl8821ae)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


[  873.286697] rtl8821ae: 
[  873.286767] wlan0: associated
[  873.288527] rtl8821ae-0:rtl_is_special_data():<10000-1> 802.1X Rx EAPOL pkt!! (repeated 2 times)
[  873.294624] rtl8821ae-0:rtl_op_set_key():<0-0> Using hardware based encryption for keyidx: 0, mac: <MAC 'Meduza' [AC1]>
[  873.294628] rtl8821ae-0:rtl_op_set_key():<0-0> alg:CCMP
[  873.294629] rtl8821ae-0:rtl_op_set_key():<0-0> set enable_hw_sec, key_type:4(OPEN:0 WEP40:1 TKIP:2 AES:4 WEP104:5)
[  873.294631] rtl8821ae-0:rtl8821ae_enable_hw_security_config():<0-0> PairwiseEncAlgorithm = 4 GroupEncAlgorithm = 0
[  873.294638] rtl8821ae-0:rtl8821ae_enable_hw_security_config():<0-0> The SECR-value cc 
[  873.294642] rtl8821ae-0:rtl_op_set_key():<0-0> set pairwise key
[  873.294644] rtl8821ae-0:rtl8821ae_set_key():<0-0> add one entry
[  873.294646] rtl8821ae-0:rtl8821ae_set_key():<0-0> set Pairwiase key
[  873.294647] rtl8821ae-0:rtl_cam_add_one_entry():<0-0> EntryNo:4, ulKeyId=0, ulEncAlg=4, ulUseDK=0 MacAddr <MAC 'Meduza' [AC1]>
[  873.294649] rtl8821ae: 
[  873.295293] rtl8821ae-0:rtl_cam_add_one_entry():<0-0> end 
[  873.295391] rtl8821ae-0:rtl_op_set_key():<0-0> Using hardware based encryption for keyidx: 1, mac: <MAC address>
[  873.295393] rtl8821ae-0:rtl_op_set_key():<0-0> alg:CCMP
[  873.295395] rtl8821ae-0:rtl_op_set_key():<0-0> set group key
[  873.295396] rtl8821ae-0:rtl8821ae_set_key():<0-0> add one entry
[  873.295397] rtl8821ae-0:rtl8821ae_set_key():<0-0> set group key
[  873.295398] rtl8821ae-0:rtl_cam_add_one_entry():<0-0> EntryNo:1, ulKeyId=1, ulEncAlg=4, ulUseDK=0 MacAddr <MAC address>
[  873.295400] rtl8821ae: 
[  873.296042] rtl8821ae-0:rtl_cam_add_one_entry():<0-0> end 
[  874.822311] rtl8821ae-0:rtl_tx_agg_start():<0-0> on ra = <MAC 'Meduza' [AC1]> tid = 0 seq:2
[  874.822334] rtl8821ae-0:rtl_action_proc():<200-1> Tx ACT_ADDBAREQ From :<MAC 'wlan0' [IF]>
[  874.822336] rtl8821ae: 
[  874.824570] rtl8821ae-0:rtl_action_proc():<10000-1> Rx ACT_ADDBARSP From :<MAC 'Meduza' [AC1]>
[  874.824606] rtl8821ae-0:rtl_tx_agg_oper():<0-0> on ra = <MAC 'Meduza' [AC1]> tid = 0
[  874.844799] rtl8821ae-0:rtl_action_proc():<10000-1> Rx ACT_ADDBAREQ From :<MAC 'Meduza' [AC1]>
[  874.844804] rtl8821ae: 
[  874.844874] rtl8821ae-0:rtl_rx_agg_start():<0-0> on ra = <MAC 'Meduza' [AC1]> tid = 0 seq:2
[  874.844884] rtl8821ae-0:rtl_action_proc():<200-1> Tx ACT_ADDBARSP From :<MAC 'wlan0' [IF]>
[  877.567784] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off for 2 s
[  879.171127] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off for 4 s
[  881.177366] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off for 6 s
[  881.381588] rtl8821ae-0:rtl_tx_agg_stop():<0-0> on ra = <MAC 'Meduza' [AC1]> tid = 0
[  881.381628] rtl8821ae-0:rtl_action_proc():<400-1> ACT_ADDBADEL From :<MAC 'wlan0' [IF]>
[  881.846074] rtl8821ae-0:rtl_tx_agg_start():<0-0> on ra = <MAC 'Meduza' [AC1]> tid = 0 seq:18
[  881.846105] rtl8821ae-0:rtl_action_proc():<200-1> Tx ACT_ADDBAREQ From :<MAC 'wlan0' [IF]>
[  881.846109] rtl8821ae: 
[  881.848027] rtl8821ae-0:rtl_action_proc():<10000-1> Rx ACT_ADDBARSP From :<MAC 'Meduza' [AC1]>
[  881.848121] rtl8821ae-0:rtl_tx_agg_oper():<0-0> on ra = <MAC 'Meduza' [AC1]> tid = 0
[  883.183611] rtl8821ae-0:rtl_watchdog_wq_callback():<0-0> AP off for 8 s
[  890.719797] rtl8821ae-0:rtl_tx_agg_stop():<0-0> on ra = <MAC 'Meduza' [AC1]> tid = 0
[  892.247063] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  892.353575] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  892.615458] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  892.721939] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  892.983884] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  893.090396] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  893.352292] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  893.458786] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  893.720683] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  893.827195] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  894.089101] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  894.195612] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  894.457480] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  894.564006] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  894.825943] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  894.932374] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  895.194228] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  895.300728] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  895.562685] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  895.669193] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  895.931080] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  896.037604] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  896.299475] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  896.406001] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  896.667894] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  896.774413] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  896.774907] rtl8821ae-0:rtl_action_proc():<400-1> ACT_ADDBADEL From :<MAC 'wlan0' [IF]>


########## wireless info END ############



```


You make me so happy if you help me :)
Thanks in advance!

---

### Post by tachanchachi on 2015-02-06
Sorry, I installed Ubuntu-Gnome 14.10. I wanted to install 14.04 LTS but could not find a working image with Gnome and I wrote it wrong in my post (my bad). 
I did all possible updates and installed all kind of programs I need (most of them, actually), and the wireless still keeped on failing. 
I read the instructions of the forum, looked for a possible answer to my problem, tried some possibilities and at the end I decided to post in a similar thread with the same problem as mine, to avoid posting repeated questions. 
If that was not following the rules, I'm sorry, but I think I kind of did... 

Now, somebody has an answer to my question or I would really need to post a new topic in the forum? 

Thanks in advance. 
Tachan

P.S. Right now I'm connected to the internet using a cable, but I would like to solve the wireless problem, because the cable is way too short and has to cross from one room to another through two doors, which are slowly damaging it when opening an closing them.

---

### Post by jeremy31 on 2015-02-06
This should work for realtek cards, enter one line at a time into terminal
```
wget -N -t 5 -T 10 https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.18.1/backports-3.18.1-1.tar.xz
tar -xf backports-3.18.1-1.tar.xz
cd ~/backports-3.18.1-1
make defconfig-rtlwifi
make
sudo make install
```

After a kernel update you will need to
```
cd ~/backports-3.18.1-1
make clean
make defconfig-rtlwifi
make
sudo make install
```

---

### Post by tachanchachi on 2015-02-06
Hi, thanks for your fast answer. 

I never did a kernel update by myself. Could you explain me how should I do it? 

Thank you very much! 

Tachan

---

### Post by jeremy31 on 2015-02-06
> **tachanchachi said:**
> Hi, thanks for your fast answer. 

I never did a kernel update by myself. Could you explain me how should I do it? 

Thank you very much! 

Tachan

In Ubuntu, the kernel can update using the update manager program whenever a newer kernel is available, I think it tells you to reboot after an update to the kernel is installed and your wifi might not work unless the new kernel includes the needed changes to your wifi driver.

If you have errors when running the commands above, you will likely need ```
sudo apt-get install build-essential linux-headers-generic
```

---

### Post by tachanchachi on 2015-02-09
Thanks Jeremy31. 

I tried your solution and during 3 days I had no problem with the wifi. 
I think it worked. 

:-)

---

### Post by pioterek01 on 2015-02-16
Thank you [COLOR=#000000]Jeremy31! :)
[/COLOR]):P

---

### Post by mike176 on 2015-02-18
i found this for fixing the realtek issue. It worked for me.
Hope it helps others with the same problem.
Mike

[h=1]Installation[/h][COLOR=#333333][FONT=Helvetica Neue]Ensure you have the necessary prerequisites installed:[/FONT][/COLOR]
sudo apt-get install linux-headers-generic build-essential dkms
[COLOR=#333333][FONT=Helvetica Neue]Clone this repository:[/FONT][/COLOR]
git clone [https://github.com/pvaret/rtl8192cu-fixes.git](https://github.com/pvaret/rtl8192cu-fixes.git)
[COLOR=#333333][FONT=Helvetica Neue]Set it up as a DKMS module:[/FONT][/COLOR]
sudo dkms add ./rtl8192cu-fixes
[COLOR=#333333][FONT=Helvetica Neue]Build and install it:[/FONT][/COLOR]
sudo dkms install 8192cu/1.9
[COLOR=#333333][FONT=Helvetica Neue]Refresh the module list:[/FONT][/COLOR]
sudo depmod -a
[COLOR=#333333][FONT=Helvetica Neue]Ensure the native (and broken) kernel driver is blacklisted:[/FONT][/COLOR]
sudo cp ./rtl8192cu-fixes/blacklist-native-rtl8192.conf /etc/modprobe.d/
[COLOR=#333333][FONT=Helvetica Neue]And reboot. You're done.[/FONT][/COLOR]

---

### Post by boozelclark on 2015-04-08
Jeremy31's solution worked for me too on 14.10. Thank you very much! 
Ubuntu 14.10 was running on the Gigabyte brix pro (GB-BXi7-4770R) with the RealTek RTL8821AE wireless card.

My wireless AP had the 2.4Ghz and 5Ghz networks with the same SSID which Ubuntu seemed to have trouble connecting to after I installed the fix. As soon as the 5Ghz network was disabled (or renamed) it connected and hasn't disconnected since.

Thanks,

---

### Post by INF1 on 2015-09-09
Hello,

I've had  "wifi connection drops with rtl8821ae" for about 1 week. I followed your steps to fix it and all is working fine! At least no more drops while playing openarena:p

Thanx a bunch...

> **jeremy31 said:**
> This should work for realtek cards, enter one line at a time into terminal
```
wget -N -t 5 -T 10 https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.18.1/backports-3.18.1-1.tar.xz
tar -xf backports-3.18.1-1.tar.xz
cd ~/backports-3.18.1-1
make defconfig-rtlwifi
make
sudo make install
```

After a kernel update you will need to
```
cd ~/backports-3.18.1-1
make clean
make defconfig-rtlwifi
make
sudo make install
```

---

### Post by almirnb89 on 2016-05-15
Hi,

I am with this same issue. But when I try jeremy31 solution I get this error:

```
~/backports-3.18.1-1$ make defconfig-rtlwifi
Generating local configuration database from kernel ...Kernel version parse failed!
Makefile:40: recipe for target 'defconfig-rtlwifi' failed

```
Somebody could help me, please?

Thank you all!

---

### Post by jeremy31 on 2016-05-15
Time to close this old thread

---

