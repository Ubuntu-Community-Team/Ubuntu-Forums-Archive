---
title: "wifi not working on ubuntu 14.04 LTS"
date: 2014-08-02
forum: Networking &amp; Wireless
---

### Post by Mohamed_EL_MOUDDEN on 2014-08-02
**can't get my Qualcomm Atheros AR956x Wirele[SIZE=2][/SIZE]ss Network Adapter to work on Ubuntu 14.04 LTS, help me please!**

---

### Post by varunendra on 2014-08-04
Please follow the instructions in this post to download and run 'wireless_script' (experimental version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

### Post by Mohamed_EL_MOUDDEN on 2014-08-04
Here it is. 
**NB**: I have installed Ubuntu in VMware & I've used a wireless usb to connect (Ralink).
```


    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

ubuntu 3.13.0-24-generic i686,  Ubuntu 14.04 LTS, trusty

CPU    : Intel(R) Core(TM) i5-4200M CPU @ 2.50GHz
Memory : 1001 MB
Uptime : 12:38:01 up 21 min,  2 users,  load average: 0.73, 0.59, 0.48


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

02:01.0 Ethernet controller [0200]: Advanced Micro Devices, Inc. [AMD] 79c970 [PCnet32 LANCE] [1022:2000] (rev 10)
    Subsystem: Advanced Micro Devices, Inc. [AMD] PCnet - Fast 79C971 [1022:2000]
    Kernel driver in use: pcnet32
02:02.0 Multimedia audio controller [0401]: Ensoniq ES1371 / Creative Labs CT2518 [AudioPCI-97] [1274:1371] (rev 02)
    Subsystem: Ensoniq AudioPCI 64V/128 / Creative Sound Blaster CT4810 [1274:1371]


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 004: ID 0e0f:0008 VMware, Inc. 
Bus 002 Device 003: ID 0e0f:0002 VMware, Inc. Virtual USB Hub
Bus 002 Device 002: ID 0e0f:0003 VMware, Inc. Virtual Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~



rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface     Soft blocked  Hard blocked
0: hci0: Bluetooth      no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

rt2800usb              26581  0 
rt2x00usb              20041  1 rt2800usb
rt2800lib              83150  1 rt2800usb
rt2x00lib              48886  3 rt2x00usb,rt2800lib,rt2800usb
mac80211              545990  3 rt2x00lib,rt2x00usb,rt2800lib
cfg80211              409394  2 mac80211,rt2x00lib
crc_ccitt              12627  1 rt2800lib


module parameters ~~~~~~~~~~~~~~~~~~

cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
rt2800usb     (1): nohwcrypt=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: disconnected
================o=======o=========o=============o=========o===========o==============o===========
 Interface & ID | Type  | Driver  | State       | Default | Speed     | Support      | HW Addr   
================o=======o=========o=============o=========o===========o==============o===========
 eth0           | Wired | pcnet32 | unavailable | no      |           |              | <MAC ID removed>
----------------+-------+---------+-------------+---------+-----------+--------------+-----------


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

MEDITEL WIFI         : ssid=MEDITEL WIFI | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~



Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "en_US.UTF-8")
country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

           - 


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~



blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[rt2800usb]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/rt2x00/rt2800usb.ko
firmware:       rt2870.bin
version:        2.3.0
srcversion:     D6F814DAF78F2BEA3DA12CB
depends:        rt2x00lib,rt2800lib,rt2x00usb
parm:           nohwcrypt:Disable hardware encryption. (bool)

[rt2x00usb]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/rt2x00/rt2x00usb.ko
version:        2.3.0
srcversion:     44768071492503F8EFE1EED
depends:        rt2x00lib,mac80211

[rt2800lib]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/rt2x00/rt2800lib.ko
version:        2.3.0
srcversion:     9BD0087B6943A41E7FD8EDA
depends:        rt2x00lib,mac80211,crc-ccitt

[rt2x00lib]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
version:        2.3.0
srcversion:     C57F87A3569F5363E79FD42
depends:        mac80211,cfg80211

[mac80211]
filename:       /lib/modules/3.13.0-24-generic/kernel/net/mac80211/mac80211.ko
srcversion:     C0F95BBF832E05DEFD722F4
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-24-generic/kernel/net/wireless/cfg80211.ko
srcversion:     8B3D642D1F2E6406EF33F74
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[crc_ccitt]
filename:       /lib/modules/3.13.0-24-generic/kernel/lib/crc-ccitt.ko
srcversion:     2294FCAD06D727386004EEB
depends:        


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# USB device 0x:0x (rt2800usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


Custom files/entries ~~~~~~~~~~~~~~~

/etc/modules        : Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Default

[/etc/modprobe.d]
asus_nb_wmi.conf  : options asus_nb_wmi wapf=4
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
mlx4.conf         : softdep mlx4_core post: mlx4_en


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/boot/vmlinuz-3.13.0-24-generic root=UUID=7d644718-221a-4a6d-bb41-15f86219aecd ro find_preseed=/preseed.cfg auto noprompt priority=critical locale=en_US quiet


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    0.815968] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.816202] audit: initializing netlink socket (disabled)
[    1.336350] VMware vmxnet3 virtual NIC driver - version 1.2.0.0-k-NAPI
[    1.368377] pcnet32: pcnet32.c:v1.35 21.Apr.2008 tsbogend@alpha.franken.de
[    1.368439] pcnet32: PCnet/PCI II 79C970A at 0x2000, <MAC ID removed> assigned IRQ 19
[    1.368564] pcnet32: eth0: registered as PCnet/PCI II 79C970A
[    1.369560] pcnet32: 1 cards_found
[   54.872986] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   62.742134] pcnet32 0000:02:01.0 eth0: link down
[  203.060594] ieee80211 phy0: rt2x00_set_rt: Info - RT chipset 3070, rev 0201 detected
[  203.951981] ieee80211 phy0: rt2x00_set_rf: Info - RF chipset 0005 detected
[  204.169398] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[  204.215641] ieee80211 phy0: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
[  209.606386] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  209.607121] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  226.074015] wlan0: authenticate with <MAC ID removed>
[  226.916266] wlan0: send auth to <MAC ID removed> (try 1/3)
[  226.922195] wlan0: authenticated
[  226.922528] rt2800usb 1-1:1.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[  226.922536] rt2800usb 1-1:1.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  226.922543] rt2800usb 1-1:1.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  226.925720] wlan0: associate with <MAC ID removed> (try 1/3)
[  226.932113] wlan0: RX AssocResp from <MAC ID removed> (capab=0x411 status=0 aid=4)
[  227.114881] wlan0: associated
[  227.114921] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  227.199630] wlan0: deauthenticating from <MAC ID removed> by local choice (reason=2)
[  227.524797] wlan0: authenticate with <MAC ID removed>
[  227.616175] wlan0: send auth to <MAC ID removed> (try 1/3)
[  227.710750] wlan0: authenticated
[  227.711111] rt2800usb 1-1:1.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[  227.711119] rt2800usb 1-1:1.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  227.711123] rt2800usb 1-1:1.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  227.713789] wlan0: associate with <MAC ID removed> (try 1/3)
[  227.719899] wlan0: RX AssocResp from <MAC ID removed> (capab=0x411 status=0 aid=4)
[  227.903510] wlan0: associated
[  237.924111] wlan0: deauthenticating from <MAC ID removed> by local choice (reason=3)
[  240.763022] wlan0: authenticate with <MAC ID removed>
[  241.083844] wlan0: send auth to <MAC ID removed> (try 1/3)
[  241.088691] wlan0: authenticated
[  241.089081] rt2800usb 1-1:1.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[  241.089091] rt2800usb 1-1:1.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  241.089098] rt2800usb 1-1:1.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  241.094471] wlan0: associate with <MAC ID removed> (try 1/3)
[  241.099094] wlan0: RX AssocResp from <MAC ID removed> (capab=0x411 status=0 aid=2)
[  241.251158] wlan0: associated
[  359.535246] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 12 in queue 0
[  359.536381] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 12 in queue 0
[  359.536390] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 12 in queue 0
[  360.023759] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 0, dropping
[  391.153869] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 5 in queue 0
[  391.153885] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 5 in queue 0
[  391.154223] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 0, dropping
[  401.037525] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 14 in queue 2
[  401.037565] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 14 in queue 2
[  401.037570] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 14 in queue 2
[  401.140456] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  416.812489] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 8 in queue 2
[  416.812520] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 8 in queue 2
[  416.812522] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 8 in queue 2
[  416.812532] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 9 in queue 2
[  416.869785] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 10 in queue 2
[  416.869854] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 10 in queue 2
[  416.869860] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 10 in queue 2
[  416.884823] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 11 in queue 2
[  416.884896] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 11 in queue 2
[  416.884904] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 11 in queue 2
[  416.884926] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 12 in queue 2
[  416.892198] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 13 in queue 2
[  416.892272] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 13 in queue 2
[  416.892280] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 13 in queue 2
[  416.899557] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 14 in queue 2
[  416.899602] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 14 in queue 2
[  416.899606] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 14 in queue 2
[  416.904523] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 15 in queue 2
[  416.904564] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 15 in queue 2
[  416.904568] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 15 in queue 2
[  416.906987] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 2
[  416.907012] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 2
[  416.907015] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 2
[  416.911979] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 1 in queue 2
[  416.912006] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 1 in queue 2
[  416.912008] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 1 in queue 2
[  416.934331] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 2 in queue 2
[  416.934357] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 2 in queue 2
[  416.934359] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 2 in queue 2
[  416.954231] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 3 in queue 2
[  416.954252] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 3 in queue 2
[  416.954253] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 3 in queue 2
[  417.078748] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 4 in queue 2
[  417.078772] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 4 in queue 2
[  417.078774] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 4 in queue 2
[  417.078785] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 5 in queue 2
[  417.078787] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 6 in queue 2
[  417.078790] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 7 in queue 2
[  417.175920] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  417.178370] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  417.180860] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  417.183363] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  417.185832] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  417.188328] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  417.190927] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  417.193322] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  417.195757] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  417.198309] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  417.200854] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  417.203294] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  417.205787] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  417.208273] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  417.210784] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  417.213228] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  417.275487] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 14 in queue 0
[  417.275509] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 14 in queue 0
[  417.275511] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 14 in queue 0
[  417.625161] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 13 in queue 2
[  417.625184] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 13 in queue 2
[  417.625186] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 13 in queue 2
[  417.736062] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  417.736067] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  417.885618] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  417.888074] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 0, dropping
[  418.134960] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 15 in queue 2
[  418.135186] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 15 in queue 2
[  418.135191] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 15 in queue 2
[  418.135207] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 2
[  418.135213] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 1 in queue 2
[  418.172237] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 2 in queue 0
[  418.172410] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 2 in queue 0
[  418.172413] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 2 in queue 0
[  418.182256] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  418.184692] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  418.187432] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  418.597918] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 0, dropping
[  419.845884] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 14 in queue 2
[  419.846169] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 14 in queue 2
[  419.846175] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 14 in queue 2
[  419.850848] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 15 in queue 2
[  419.850884] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 15 in queue 2
[  419.850892] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 15 in queue 2
[  419.947806] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  419.950216] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  423.212884] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 6 in queue 2
[  423.213065] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 6 in queue 2
[  423.213067] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 6 in queue 2
[  423.240497] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  439.503632] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 14 in queue 2
[  439.504064] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 14 in queue 2
[  439.504072] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 14 in queue 2
[  439.558573] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  450.526663] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 12 in queue 2
[  450.526883] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 12 in queue 2
[  450.526886] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 12 in queue 2
[  450.534531] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 13 in queue 2
[  450.534666] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 13 in queue 2
[  450.534669] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 13 in queue 2
[  450.534682] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 14 in queue 2
[  450.538941] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 15 in queue 2
[  450.539137] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 15 in queue 2
[  450.539140] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 15 in queue 2
[  450.543507] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 2
[  450.543543] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 2
[  450.543547] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 2
[  450.636576] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 7 in queue 2
[  450.636583] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 8 in queue 2
[  450.651845] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 10 in queue 2
[  450.651850] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 11 in queue 2
[  450.651852] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 12 in queue 2
[  450.667184] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  450.683210] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  450.698690] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  450.714355] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  450.730152] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  450.745802] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  450.755999] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  450.756319] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  450.761344] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  450.765244] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  451.701263] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 2
[  451.701609] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 2
[  451.701616] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 2
[  451.705177] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 1 in queue 2
[  451.705206] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 1 in queue 2
[  451.705211] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 1 in queue 2
[  451.717124] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 2 in queue 2
[  451.717234] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 2 in queue 2
[  451.717244] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 2 in queue 2
[  451.717303] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 3 in queue 2
[  451.724981] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 4 in queue 2
[  451.725023] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 4 in queue 2
[  451.725029] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 4 in queue 2
[  451.725050] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 5 in queue 2
[  451.725056] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 6 in queue 2
[  451.728731] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 7 in queue 2
[  451.729036] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 7 in queue 2
[  451.729043] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 7 in queue 2
[  451.729064] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 8 in queue 2
[  451.737244] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 9 in queue 2
[  451.737328] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 9 in queue 2
[  451.737334] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 9 in queue 2
[  451.752133] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 10 in queue 2
[  451.752190] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 10 in queue 2
[  451.752196] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 10 in queue 2
[  451.752216] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 11 in queue 2
[  451.752222] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 12 in queue 2
[  451.779677] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  451.783590] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  451.790560] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  451.795188] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  451.799328] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  451.802914] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  451.807095] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  451.810809] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  451.814851] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  451.818535] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  451.822476] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  451.826319] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  451.830114] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  495.678548] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 2 in queue 2
[  495.678576] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 2 in queue 2
[  495.678578] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 2 in queue 2
[  495.683184] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 3 in queue 2
[  495.683274] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 3 in queue 2
[  495.683276] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 3 in queue 2
[  495.683293] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 4 in queue 2
[  495.691903] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 5 in queue 2
[  495.691916] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 5 in queue 2
[  495.691917] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 5 in queue 2
[  495.696781] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 6 in queue 2
[  495.696801] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 6 in queue 2
[  495.696803] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 6 in queue 2
[  495.696890] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 7 in queue 2
[  495.696897] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 8 in queue 2
[  495.696900] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 9 in queue 2
[  495.696904] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 10 in queue 2
[  495.703552] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 11 in queue 2
[  495.703924] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 11 in queue 2
[  495.703927] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 11 in queue 2
[  495.719784] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 12 in queue 2
[  495.719816] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 12 in queue 2
[  495.719819] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 12 in queue 2
[  495.722588] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 13 in queue 2
[  495.723247] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 13 in queue 2
[  495.723253] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 13 in queue 2
[  495.726744] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 14 in queue 2
[  495.727324] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 14 in queue 2
[  495.727328] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 14 in queue 2
[  495.730464] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 15 in queue 2
[  495.730806] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 15 in queue 2
[  495.730809] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 15 in queue 2
[  495.926018] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  495.927083] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  496.809331] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 11 in queue 2
[  496.809387] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 11 in queue 2
[  496.809389] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 11 in queue 2
[  496.813334] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 12 in queue 2
[  496.813360] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 12 in queue 2
[  496.813362] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 12 in queue 2
[  496.891030] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  496.891545] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  574.381328] wlan0: deauthenticated from <MAC ID removed> (Reason: 7)
[  574.585821] wlan0: authenticate with <MAC ID removed>
[  574.650430] wlan0: send auth to <MAC ID removed> (try 1/3)
[  574.654715] wlan0: authenticated
[  574.655977] rt2800usb 1-1:1.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[  574.655979] rt2800usb 1-1:1.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  574.655980] rt2800usb 1-1:1.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  574.660148] wlan0: associate with <MAC ID removed> (try 1/3)
[  574.662268] wlan0: RX AssocResp from <MAC ID removed> (capab=0x411 status=0 aid=2)
[  574.792562] wlan0: associated
[  754.458969] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 14 in queue 2
[  754.458989] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 14 in queue 2
[  754.458992] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 14 in queue 2
[  754.459006] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 15 in queue 2
[  754.459011] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 2
[  754.471766] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 1 in queue 2
[  754.472445] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 1 in queue 2
[  754.472448] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 1 in queue 2
[  754.472459] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 2 in queue 2
[  754.472462] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 3 in queue 2
[  754.472465] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 4 in queue 2
[  754.474179] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 5 in queue 2
[  754.474195] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 5 in queue 2
[  754.474197] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 5 in queue 2
[  754.474207] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 6 in queue 2
[  754.525656] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  754.525660] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  754.529443] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  754.533951] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  754.537261] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  754.539908] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  754.544014] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  754.547285] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  754.550765] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  762.863141] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 2 in queue 0
[  762.863165] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 2 in queue 0
[  762.863166] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 2 in queue 0
[  762.929142] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 0, dropping
[  763.341786] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 13 in queue 2
[  763.341845] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 13 in queue 2
[  763.341847] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 13 in queue 2
[  763.439987] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  763.439991] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 5 in queue 0
[  763.895649] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 0, dropping
[ 1179.025652] wlan0: deauthenticated from <MAC ID removed> (Reason: 7)
[ 1179.323957] wlan0: authenticate with <MAC ID removed>
[ 1179.408242] wlan0: send auth to <MAC ID removed> (try 1/3)
[ 1179.412714] wlan0: authenticated
[ 1179.413468] rt2800usb 1-1:1.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 1179.413477] rt2800usb 1-1:1.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 1179.413481] rt2800usb 1-1:1.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 1179.413865] wlan0: associate with <MAC ID removed> (try 1/3)
[ 1179.416749] wlan0: RX AssocResp from <MAC ID removed> (capab=0x411 status=0 aid=2)
[ 1179.594145] wlan0: associated
[ 1298.353130] wlan0: deauthenticated from <MAC ID removed> (Reason: 7)
[ 1298.627405] wlan0: authenticate with <MAC ID removed>
[ 1298.712183] wlan0: send auth to <MAC ID removed> (try 1/3)
[ 1298.717815] wlan0: authenticated
[ 1298.718268] rt2800usb 1-1:1.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 1298.718275] rt2800usb 1-1:1.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 1298.718279] rt2800usb 1-1:1.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 1298.721289] wlan0: associate with <MAC ID removed> (try 1/3)
[ 1298.727234] wlan0: RX AssocResp from <MAC ID removed> (capab=0x411 status=0 aid=2)
[ 1298.906156] wlan0: associated
[ 1305.772345] wlan0: deauthenticating from <MAC ID removed> by local choice (reason=3)
[ 1312.045417] ieee80211 phy0: rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x0500 with error -19

    ======== Done ========
```

---

### Post by varunendra on 2014-08-04
The device being troubleshooted is supposed to be present when troubleshooting it.

I can't find your USB adapter in the report. Obviously it was disconnected before running the script, so nothing to troubleshoot here.

---

### Post by Mohamed_EL_MOUDDEN on 2014-08-05
Firstly, thanks for your help. Yes you're right, I've disconnected it because it doesn't need troubleshooting, my problem is with my PC wifi adapter.

---

### Post by varunendra on 2014-08-08
If you mean the internal (PCI) wireless adapter in your PC/laptop, then you are on a wild-goose chase. It's simply not possible, at least not in today's world.

As far as I know, the internal devices located on a PCI bus can't be directly accessed from a Virtual Machine. I added "as far as I know" only because things keep developing, and some day we may see such capability in VMs. But at the moment, I don't think any VM platform has that capability.

A virtual machine only sees virtualized hardware (with the exception of a few devices like optical drives and USB devices), not the real one in your physical machine.

---

### Post by Mohamed_EL_MOUDDEN on 2014-08-10
Hope to see that possible in the near future, but thank God there are other alternatives, like using wifi USB adapter...
Many thanks [**[COLOR=#DD4814][B]varunendra**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=1043629").
With all my respect.

---

