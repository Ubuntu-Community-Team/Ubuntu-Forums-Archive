---
title: "Problems with unstable wireless (Ralink RT5392)"
date: 2015-06-19
forum: Networking &amp; Wireless
---

### Post by christoff2 on 2015-06-19
Hi,


I am having trouble fixing an unusably slow wireless network on a new PC with Ubuntu 14.04 LTS installed.
After a while I have no network connection. It works if I restart my computer (still slow), but the connection usually becomes slower and later on I am unable to use it.


The wireless card I am using is a D-Link DWA-548 pci-express.


I came accross a couple of simular issues in my googling research, none of the suggestions helped me.


Here are some useful commands printing out information that may help. I have seen some of the gurus asked for this info (got it from one of varunendra's posts.):


```
====================================================================================
lsb_release -d
--------------
Description:    Ubuntu 14.04.2 LTS


====================================================================================
uname -mr
---------
3.13.0-55-generic x86_64


====================================================================================
lspci -nnk | grep -iA2 net
--------------------------
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
        Subsystem: Gigabyte Technology Co., Ltd Motherboard [1458:e000]
        Kernel driver in use: r8169
03:00.0 Network controller [0280]: Ralink corp. RT5392 PCIe Wireless Network Adapter [1814:5392]
        Subsystem: D-Link System Inc Device [1186:3c06]
        Kernel driver in use: rt2800pci


====================================================================================
lsmod
-----
Module                  Size  Used by
...
rt2800pci              13598  0 
rt2800mmio             20986  1 rt2800pci
rt2800lib              88867  2 rt2800pci,rt2800mmio
rt2x00pci              13287  1 rt2800pci
rt2x00mmio             13603  2 rt2800pci,rt2800mmio
rt2x00lib              55250  5 rt2x00pci,rt2800lib,rt2800pci,rt2800mmio,rt2x00mmio
mac80211              639514  3 rt2x00lib,rt2x00pci,rt2800lib
cfg80211              541326  2 mac80211,rt2x00lib
r8169                  67581  0
...


====================================================================================
iwconfig
--------
eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"Ex Mente"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <masked_address>  
          Bit Rate=27 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=47/70  Signal level=-63 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:37  Invalid misc:125   Missed beacon:0


====================================================================================
rfkill list all
---------------
0: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no


====================================================================================
iw reg get
----------
country 00:
        (2402 - 2472 @ 40), (3, 20)
        (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
        (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
        (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
        (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


====================================================================================
nm-tool
-------
NetworkManager Tool


State: connected (global)


- Device: wlan0  [Ex Mente] ----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2800pci
  State:             connected
  Default:           yes
  HW Address:        <masked_address>


  Capabilities:
    Speed:           14 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    *Ex Mente:       Infra, <masked_address>, Freq 2412 MHz, Rate 54 Mb/s, Strength 57 WPA2


  IPv4 Settings:
   .
   .
   .




- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <masked_address>


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off




====================================================================================
sudo iwlist scan
----------------
eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


wlan0     Scan completed :
          Cell 01 - Address: <masked_address>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=53/70  Signal level=-57 dBm  
                    Encryption key:on
                    ESSID:"Ex Mente"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 56ms ago
                    IE: Unknown: 00084578204D656E7465
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFE181BFFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D1601051700000000000000000000000000000000000000
                    IE: Unknown: DD7D0050F204104A00011010440001021041000100103B00010310470010550364D39CAC0C7C62E4DD6D11DFF2AD102100074E6574676561721023000944474E3232303076331024000944474E32323030763310420004313233341054000800060050F20400011011000944474E323230307633100800020084103C000101
                    IE: Unknown: DD090010180205F02C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00


====================================================================================
egrep '^(#.*device|[^#]|$)' /etc/udev/rules.d/70-persistent-net.rules
---------------------------------------------------------------------
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<masked_address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x1814:0x5392 (rt2800pci)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<masked_address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


====================================================================================
dmesg | grep 'wlan|rt2'
-----------------------




====================================================================================
/var/syslog
-----------
Jun 19 08:29:35 Vanadium NetworkManager[1226]: <info> caught signal 15, shutting down normally.
Jun 19 08:29:35 Vanadium NetworkManager[1226]: <info> (eth0): device state change: unavailable -> unmanaged (reason 'removed') [20 10 36]
Jun 19 08:29:35 Vanadium NetworkManager[1226]: <info> (eth0): cleaning up...
Jun 19 08:29:35 Vanadium NetworkManager[1226]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Jun 19 08:29:35 Vanadium NetworkManager[1226]: <info> (wlan0): device state change: activated -> unmanaged (reason 'removed') [100 10 36]
Jun 19 08:29:35 Vanadium NetworkManager[1226]: <info> (wlan0): deactivating device (reason 'removed') [36]
Jun 19 08:29:35 Vanadium kernel: [ 2895.755149] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Jun 19 08:29:35 Vanadium NetworkManager[1226]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 1429
Jun 19 08:29:35 Vanadium avahi-daemon[950]: Withdrawing address record for <masked_address> on wlan0.
Jun 19 08:29:35 Vanadium avahi-daemon[950]: Leaving mDNS multicast group on interface wlan0.IPv6 with address <masked_address>.
Jun 19 08:29:35 Vanadium avahi-daemon[950]: Interface wlan0.IPv6 no longer relevant for mDNS.
Jun 19 08:29:35 Vanadium kernel: [ 2895.956773] wlan0: deauthenticating from <masked_address> by local choice (Reason: 3=DEAUTH_LEAVING)
Jun 19 08:29:36 Vanadium kernel: [ 2896.113571] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
Jun 19 08:29:36 Vanadium kernel: [ 2896.273514] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
Jun 19 08:29:36 Vanadium kernel: [ 2896.433457] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
Jun 19 08:29:36 Vanadium kernel: [ 2896.593401] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
Jun 19 08:29:36 Vanadium wpa_supplicant[1308]: wlan0: CTRL-EVENT-DISCONNECTED bssid=<masked_address> reason=3 locally_generated=1
Jun 19 08:29:36 Vanadium avahi-daemon[950]: Withdrawing address record for <masked_address> on wlan0.
Jun 19 08:29:36 Vanadium avahi-daemon[950]: Leaving mDNS multicast group on interface wlan0.IPv4 with address <masked_address>.
Jun 19 08:29:36 Vanadium avahi-daemon[950]: Interface wlan0.IPv4 no longer relevant for mDNS.
Jun 19 08:29:36 Vanadium NetworkManager[1226]: <warn> DNS: plugin dnsmasq update failed
Jun 19 08:29:36 Vanadium NetworkManager[1226]: <info> Removing DNS information from /sbin/resolvconf
Jun 19 08:29:36 Vanadium dnsmasq[1728]: setting upstream servers from DBus
Jun 19 08:29:36 Vanadium kernel: [ 2896.795500] cfg80211: Calling CRDA to update world regulatory domain
Jun 19 08:29:36 Vanadium kernel: [ 2896.798942] cfg80211: World regulatory domain updated:
Jun 19 08:29:36 Vanadium kernel: [ 2896.798945] cfg80211:  DFS Master region: unset
Jun 19 08:29:36 Vanadium kernel: [ 2896.798946] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
Jun 19 08:29:36 Vanadium kernel: [ 2896.798947] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Jun 19 08:29:36 Vanadium kernel: [ 2896.798949] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Jun 19 08:29:36 Vanadium kernel: [ 2896.798949] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm), (N/A)
Jun 19 08:29:36 Vanadium kernel: [ 2896.798950] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Jun 19 08:29:36 Vanadium kernel: [ 2896.798951] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Jun 19 08:29:36 Vanadium NetworkManager[1226]: <info> (wlan0): cleaning up...
Jun 19 08:29:36 Vanadium NetworkManager[1226]: <info> (wlan0): taking down device.
Jun 19 08:29:36 Vanadium NetworkManager[1226]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Jun 19 08:29:36 Vanadium dbus[848]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Jun 19 08:29:36 Vanadium NetworkManager[1226]: <info> Removing DNS information from /sbin/resolvconf
Jun 19 08:29:36 Vanadium dnsmasq[1728]: exiting on receipt of SIGTERM
Jun 19 08:29:36 Vanadium kernel: [ 2896.854629] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun 19 08:29:36 Vanadium NetworkManager[1226]: <info> exiting (success)
Jun 19 08:29:36 Vanadium ModemManager[876]: <info>  Caught signal, shutting down...
Jun 19 08:29:36 Vanadium ModemManager[876]: <info>  ModemManager is shut down
Jun 19 08:29:36 Vanadium dbus[848]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Jun 19 08:29:36 Vanadium ModemManager[2869]: <info>  ModemManager (version 1.0.0) starting...
Jun 19 08:29:36 Vanadium NetworkManager[2875]: <info> NetworkManager (version 0.9.8.8) is starting...
Jun 19 08:29:36 Vanadium NetworkManager[2875]: <info> Read config file /etc/NetworkManager/NetworkManager.conf
Jun 19 08:29:36 Vanadium NetworkManager[2875]: <info> WEXT support is enabled
Jun 19 08:29:36 Vanadium NetworkManager[2875]: <info> VPN: loaded org.freedesktop.NetworkManager.pptp
Jun 19 08:29:36 Vanadium NetworkManager[2875]: <info> DNS: loaded plugin dnsmasq
Jun 19 08:29:36 Vanadium NetworkManager[2875]:    SCPlugin-Ifupdown: init!
Jun 19 08:29:36 Vanadium NetworkManager[2875]:    SCPlugin-Ifupdown: update_system_hostname
Jun 19 08:29:36 Vanadium NetworkManager[2875]:       interface-parser: parsing file /etc/network/interfaces
Jun 19 08:29:36 Vanadium NetworkManager[2875]:       interface-parser: finished parsing file /etc/network/interfaces
Jun 19 08:29:36 Vanadium NetworkManager[2875]:    SCPluginIfupdown: management mode: unmanaged
Jun 19 08:29:36 Vanadium NetworkManager[2875]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.2/0000:02:00.0/net/eth0, iface: eth0)
Jun 19 08:29:36 Vanadium NetworkManager[2875]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.2/0000:02:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
Jun 19 08:29:36 Vanadium NetworkManager[2875]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.5/0000:03:00.0/net/wlan0, iface: wlan0)
Jun 19 08:29:36 Vanadium NetworkManager[2875]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.5/0000:03:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Jun 19 08:29:36 Vanadium NetworkManager[2875]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Jun 19 08:29:36 Vanadium NetworkManager[2875]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Jun 19 08:29:36 Vanadium NetworkManager[2875]:    SCPlugin-Ifupdown: end _init.
Jun 19 08:29:36 Vanadium NetworkManager[2875]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Jun 19 08:29:36 Vanadium NetworkManager[2875]: <info> Loaded plugin keyfile: (c) 2007 - 2010 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Jun 19 08:29:36 Vanadium NetworkManager[2875]:    SCPlugin-Ofono: Acquired D-Bus service com.canonical.NMOfono
Jun 19 08:29:36 Vanadium NetworkManager[2875]:    SCPlugin-Ofono: init!
Jun 19 08:29:36 Vanadium NetworkManager[2875]:    SCPlugin-Ofono: end _init.
Jun 19 08:29:36 Vanadium NetworkManager[2875]: <info> Loaded plugin (null): (null)
Jun 19 08:29:36 Vanadium NetworkManager[2875]:    Ifupdown: get unmanaged devices count: 0
Jun 19 08:29:36 Vanadium NetworkManager[2875]:    SCPlugin-Ifupdown: (10735344) ... get_connections.
Jun 19 08:29:36 Vanadium NetworkManager[2875]:    SCPlugin-Ifupdown: (10735344) ... get_connections (managed=false): return empty list.
Jun 19 08:29:36 Vanadium NetworkManager[2875]:    keyfile: parsing Ex Mente ... 
Jun 19 08:29:36 Vanadium NetworkManager[2875]:    keyfile:     read connection 'Ex Mente'
Jun 19 08:29:36 Vanadium NetworkManager[2875]:    keyfile: parsing Wired connection 1 ... 
Jun 19 08:29:36 Vanadium NetworkManager[2875]:    keyfile:     read connection 'Wired connection 1'
Jun 19 08:29:36 Vanadium NetworkManager[2875]:    SCPlugin-Ofono: (1006649552) ... get_connections.
Jun 19 08:29:36 Vanadium NetworkManager[2875]:    SCPlugin-Ofono: (1006649552) connections count: 0
Jun 19 08:29:36 Vanadium NetworkManager[2875]:    Ifupdown: get unmanaged devices count: 0
Jun 19 08:29:36 Vanadium NetworkManager[2875]: <info> monitoring kernel firmware directory '/lib/firmware'.
Jun 19 08:29:36 Vanadium NetworkManager[2875]: <info> rfkill0: found WiFi radio killswitch (at /sys/devices/pci0000:00/0000:00:1c.5/0000:03:00.0/ieee80211/phy0/rfkill0) (driver rt2800pci)
Jun 19 08:29:36 Vanadium NetworkManager[2875]: <info> WiFi enabled by radio killswitch; enabled by state file
Jun 19 08:29:36 Vanadium NetworkManager[2875]: <info> WWAN enabled by radio killswitch; enabled by state file
Jun 19 08:29:36 Vanadium NetworkManager[2875]: <info> WiMAX enabled by radio killswitch; enabled by state file
Jun 19 08:29:36 Vanadium NetworkManager[2875]: <info> Networking is enabled by state file
Jun 19 08:29:36 Vanadium NetworkManager[2875]: <warn> failed to allocate link cache: (-12) Object not found
Jun 19 08:29:36 Vanadium NetworkManager[2875]: <info> (eth0): carrier is OFF
Jun 19 08:29:36 Vanadium NetworkManager[2875]: <info> (eth0): new Ethernet device (driver: 'r8169' ifindex: 2)
Jun 19 08:29:36 Vanadium NetworkManager[2875]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Jun 19 08:29:36 Vanadium NetworkManager[2875]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jun 19 08:29:36 Vanadium NetworkManager[2875]: <info> (eth0): bringing up device.
Jun 19 08:29:36 Vanadium NetworkManager[2875]: <info> (eth0): preparing device.
Jun 19 08:29:36 Vanadium NetworkManager[2875]: <info> (eth0): deactivating device (reason 'managed') [2]
Jun 19 08:29:36 Vanadium NetworkManager[2875]: <info> (wlan0): using nl80211 for WiFi device control
Jun 19 08:29:36 Vanadium NetworkManager[2875]: <info> (wlan0): driver supports Access Point (AP) mode
Jun 19 08:29:36 Vanadium NetworkManager[2875]: <info> (wlan0): new 802.11 WiFi device (driver: 'rt2800pci' ifindex: 3)
Jun 19 08:29:36 Vanadium NetworkManager[2875]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
Jun 19 08:29:36 Vanadium NetworkManager[2875]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jun 19 08:29:36 Vanadium NetworkManager[2875]: <info> (wlan0): bringing up device.
Jun 19 08:29:36 Vanadium kernel: [ 2896.971395] r8169 0000:02:00.0 eth0: link down
Jun 19 08:29:36 Vanadium kernel: [ 2896.971451] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Jun 19 08:29:36 Vanadium kernel: [ 2896.971679] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Jun 19 08:29:36 Vanadium NetworkManager[2875]: <info> (wlan0): preparing device.
Jun 19 08:29:36 Vanadium NetworkManager[2875]: <info> (wlan0): deactivating device (reason 'managed') [2]
Jun 19 08:29:36 Vanadium NetworkManager[2875]: <warn> /sys/devices/virtual/net/lo: couldn't determine device driver; ignoring...
Jun 19 08:29:36 Vanadium NetworkManager[2875]: <warn> /sys/devices/virtual/net/lo: couldn't determine device driver; ignoring...
Jun 19 08:29:36 Vanadium NetworkManager[2875]: <info> urfkill disappeared from the bus
Jun 19 08:29:36 Vanadium kernel: [ 2897.029391] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun 19 08:29:36 Vanadium kernel: [ 2897.029581] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun 19 08:29:36 Vanadium NetworkManager[2875]: <info> ModemManager available in the bus
Jun 19 08:29:37 Vanadium NetworkManager[2875]: <info> (wlan0) supports 4 scan SSIDs
Jun 19 08:29:37 Vanadium NetworkManager[2875]: <info> (wlan0): supplicant interface state: starting -> ready
Jun 19 08:29:37 Vanadium NetworkManager[2875]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Jun 19 08:29:37 Vanadium NetworkManager[2875]: <warn> Trying to remove a non-existant call id.
Jun 19 08:29:37 Vanadium wpa_supplicant[1308]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jun 19 08:29:37 Vanadium NetworkManager[2875]: <info> (wlan0): supplicant interface state: ready -> disconnected
Jun 19 08:29:37 Vanadium NetworkManager[2875]: <info> (wlan0) supports 4 scan SSIDs
Jun 19 08:29:38 Vanadium NetworkManager[2875]: <info> Auto-activating connection 'Ex Mente'.
Jun 19 08:29:38 Vanadium NetworkManager[2875]: <info> Activation (wlan0) starting connection 'Ex Mente'
Jun 19 08:29:38 Vanadium NetworkManager[2875]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Jun 19 08:29:38 Vanadium NetworkManager[2875]: <info> NetworkManager state is now CONNECTING
Jun 19 08:29:38 Vanadium NetworkManager[2875]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jun 19 08:29:38 Vanadium NetworkManager[2875]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jun 19 08:29:38 Vanadium NetworkManager[2875]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jun 19 08:29:38 Vanadium NetworkManager[2875]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jun 19 08:29:38 Vanadium NetworkManager[2875]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jun 19 08:29:38 Vanadium NetworkManager[2875]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Jun 19 08:29:38 Vanadium NetworkManager[2875]: <info> Activation (wlan0/wireless): connection 'Ex Mente' has security, and secrets exist.  No new secrets needed.
Jun 19 08:29:38 Vanadium NetworkManager[2875]: <info> Config: added 'ssid' value 'Ex Mente'
Jun 19 08:29:38 Vanadium NetworkManager[2875]: <info> Config: added 'scan_ssid' value '1'
Jun 19 08:29:38 Vanadium NetworkManager[2875]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Jun 19 08:29:38 Vanadium NetworkManager[2875]: <info> Config: added 'psk' value '<omitted>'
Jun 19 08:29:38 Vanadium NetworkManager[2875]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jun 19 08:29:38 Vanadium NetworkManager[2875]: <info> (wlan0): supplicant interface state: disconnected -> inactive
Jun 19 08:29:38 Vanadium NetworkManager[2875]: <info> Config: set interface ap_scan to 1
Jun 19 08:29:38 Vanadium ModemManager[2869]: <warn>  Couldn't find support for device at '/sys/devices/pci0000:00/0000:00:1c.2/0000:02:00.0': not supported by any plugin
Jun 19 08:29:38 Vanadium ModemManager[2869]: <warn>  Couldn't find support for device at '/sys/devices/pci0000:00/0000:00:1c.5/0000:03:00.0': not supported by any plugin
Jun 19 08:29:38 Vanadium wpa_supplicant[1308]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jun 19 08:29:39 Vanadium wpa_supplicant[1308]: wlan0: SME: Trying to authenticate with <masked_address> (SSID='Ex Mente' freq=2412 MHz)
Jun 19 08:29:39 Vanadium kernel: [ 2899.181261] wlan0: authenticate with <masked_address>
Jun 19 08:29:39 Vanadium NetworkManager[2875]: <info> (wlan0): supplicant interface state: inactive -> authenticating
Jun 19 08:29:39 Vanadium wpa_supplicant[1308]: wlan0: Trying to associate with <masked_address> (SSID='Ex Mente' freq=2412 MHz)
Jun 19 08:29:39 Vanadium kernel: [ 2899.196525] wlan0: send auth to <masked_address> (try 1/3)
Jun 19 08:29:39 Vanadium kernel: [ 2899.197983] wlan0: authenticated
Jun 19 08:29:39 Vanadium kernel: [ 2899.200461] wlan0: associate with <masked_address> (try 1/3)
Jun 19 08:29:39 Vanadium wpa_supplicant[1308]: wlan0: Associated with <masked_address>
Jun 19 08:29:39 Vanadium NetworkManager[2875]: <info> (wlan0): supplicant interface state: authenticating -> associating
Jun 19 08:29:39 Vanadium kernel: [ 2899.203440] wlan0: RX AssocResp from <masked_address> (capab=0x411 status=0 aid=4)
Jun 19 08:29:39 Vanadium kernel: [ 2899.203538] wlan0: associated
Jun 19 08:29:39 Vanadium kernel: [ 2899.203588] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Jun 19 08:29:39 Vanadium NetworkManager[2875]: <info> (wlan0): supplicant interface state: associating -> associated
Jun 19 08:29:39 Vanadium NetworkManager[2875]: <info> (wlan0): supplicant interface state: associated -> 4-way handshake
Jun 19 08:29:39 Vanadium wpa_supplicant[1308]: wlan0: WPA: Key negotiation completed with <masked_address> [PTK=CCMP GTK=CCMP]
Jun 19 08:29:39 Vanadium wpa_supplicant[1308]: wlan0: CTRL-EVENT-CONNECTED - Connection to <masked_address> completed [id=0 id_str=]
Jun 19 08:29:39 Vanadium wpa_supplicant[1308]: wlan0: SME: Trying to authenticate with <masked_address> (SSID='Ex Mente' freq=2412 MHz)
Jun 19 08:29:39 Vanadium kernel: [ 2899.220589] wlan0: deauthenticating from <masked_address> by local choice (Reason: 2=PREV_AUTH_NOT_VALID)
Jun 19 08:29:39 Vanadium kernel: [ 2899.260509] wlan0: authenticate with <masked_address>
Jun 19 08:29:39 Vanadium wpa_supplicant[1308]: wlan0: CTRL-EVENT-DISCONNECTED bssid=<masked_address> reason=2 locally_generated=1
Jun 19 08:29:39 Vanadium NetworkManager[2875]: <info> (wlan0): supplicant interface state: 4-way handshake -> authenticating
Jun 19 08:29:39 Vanadium wpa_supplicant[1308]: wlan0: Trying to associate with <masked_address> (SSID='Ex Mente' freq=2412 MHz)
Jun 19 08:29:39 Vanadium NetworkManager[2875]: <warn> Connection disconnected (reason -2)
Jun 19 08:29:39 Vanadium kernel: [ 2899.268499] wlan0: send auth to <masked_address> (try 1/3)
Jun 19 08:29:39 Vanadium kernel: [ 2899.268584] cfg80211: Calling CRDA to update world regulatory domain
Jun 19 08:29:39 Vanadium kernel: [ 2899.269983] wlan0: authenticated
Jun 19 08:29:39 Vanadium kernel: [ 2899.272407] wlan0: associate with <masked_address> (try 1/3)
Jun 19 08:29:39 Vanadium NetworkManager[2875]: <info> (wlan0): supplicant interface state: authenticating -> associating
Jun 19 08:29:39 Vanadium kernel: [ 2899.273352] cfg80211: World regulatory domain updated:
Jun 19 08:29:39 Vanadium kernel: [ 2899.273359] cfg80211:  DFS Master region: unset
Jun 19 08:29:39 Vanadium kernel: [ 2899.273362] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
Jun 19 08:29:39 Vanadium kernel: [ 2899.273368] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Jun 19 08:29:39 Vanadium kernel: [ 2899.273373] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Jun 19 08:29:39 Vanadium kernel: [ 2899.273377] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm), (N/A)
Jun 19 08:29:39 Vanadium kernel: [ 2899.273380] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Jun 19 08:29:39 Vanadium kernel: [ 2899.273384] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Jun 19 08:29:39 Vanadium wpa_supplicant[1308]: wlan0: Associated with <masked_address>
Jun 19 08:29:39 Vanadium kernel: [ 2899.277278] wlan0: RX AssocResp from <masked_address> (capab=0x411 status=0 aid=4)
Jun 19 08:29:39 Vanadium kernel: [ 2899.277375] wlan0: associated
Jun 19 08:29:39 Vanadium NetworkManager[2875]: <info> (wlan0): supplicant interface state: associating -> associated
Jun 19 08:29:39 Vanadium NetworkManager[2875]: <info> (wlan0): supplicant interface state: associated -> 4-way handshake
Jun 19 08:29:39 Vanadium wpa_supplicant[1308]: wlan0: WPA: Key negotiation completed with <masked_address> [PTK=CCMP GTK=CCMP]
Jun 19 08:29:39 Vanadium wpa_supplicant[1308]: wlan0: CTRL-EVENT-CONNECTED - Connection to <masked_address> completed [id=0 id_str=]
Jun 19 08:29:39 Vanadium NetworkManager[2875]: <info> (wlan0): supplicant interface state: 4-way handshake -> completed
Jun 19 08:29:39 Vanadium NetworkManager[2875]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'Ex Mente'.
Jun 19 08:29:39 Vanadium NetworkManager[2875]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Jun 19 08:29:39 Vanadium NetworkManager[2875]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Jun 19 08:29:39 Vanadium NetworkManager[2875]: <info> (wlan0): device state change: config -> ip-config (reason 'none') [50 70 0]
Jun 19 08:29:39 Vanadium NetworkManager[2875]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jun 19 08:29:39 Vanadium NetworkManager[2875]: <info> dhclient started with pid 2884
Jun 19 08:29:39 Vanadium NetworkManager[2875]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Jun 19 08:29:39 Vanadium dhclient: Internet Systems Consortium DHCP Client 4.2.4
Jun 19 08:29:39 Vanadium dhclient: Copyright 2004-2012 Internet Systems Consortium.
Jun 19 08:29:39 Vanadium dhclient: All rights reserved.
Jun 19 08:29:39 Vanadium dhclient: For info, please visit https://www.isc.org/software/dhcp/
Jun 19 08:29:39 Vanadium dhclient: 
Jun 19 08:29:39 Vanadium NetworkManager[2875]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Jun 19 08:29:39 Vanadium dhclient: Listening on LPF/wlan0/<masked_address>
Jun 19 08:29:39 Vanadium dhclient: Sending on   LPF/wlan0/<masked_address>
Jun 19 08:29:39 Vanadium dhclient: Sending on   Socket/fallback
Jun 19 08:29:39 Vanadium dhclient: DHCPREQUEST of <masked_address> on wlan0 to 255.255.255.255 port 67 (xid=0x614e4ac0)
Jun 19 08:29:39 Vanadium dhclient: DHCPACK of <masked_address> from <masked_address>
Jun 19 08:29:39 Vanadium dhclient: bound to <masked_address> -- renewal in 32515 seconds.
Jun 19 08:29:39 Vanadium NetworkManager[2875]: <info> (wlan0): DHCPv4 state changed preinit -> reboot
Jun 19 08:29:39 Vanadium NetworkManager[2875]: <info>   address <masked_address>
Jun 19 08:29:39 Vanadium NetworkManager[2875]: <info>   prefix 24 (255.255.255.0)
Jun 19 08:29:39 Vanadium NetworkManager[Jun 19 08:29:35 Vanadium NetworkManager[1226]: <info> caught signal 15, shutting down normally.
Jun 19 08:29:35 Vanadium NetworkManager[1226]: <info> (eth0): device state change: unavailable -> unmanaged (reason 'removed') [20 10 36]
Jun 19 08:29:35 Vanadium NetworkManager[1226]: <info> (eth0): cleaning up...
Jun 19 08:29:35 Vanadium NetworkManager[1226]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Jun 19 08:29:35 Vanadium NetworkManager[1226]: <info> (wlan0): device state change: activated -> unmanaged (reason 'removed') [100 10 36]
Jun 19 08:29:35 Vanadium NetworkManager[1226]: <info> (wlan0): deactivating device (reason 'removed') [36]
Jun 19 08:29:35 Vanadium kernel: [ 2895.755149] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Jun 19 08:29:35 Vanadium NetworkManager[1226]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 1429
Jun 19 08:29:35 Vanadium avahi-daemon[950]: Withdrawing address record for <masked_address> on wlan0.
Jun 19 08:29:35 Vanadium avahi-daemon[950]: Leaving mDNS multicast group on interface wlan0.IPv6 with address <masked_address>.
Jun 19 08:29:35 Vanadium avahi-daemon[950]: Interface wlan0.IPv6 no longer relevant for mDNS.
Jun 19 08:29:35 Vanadium kernel: [ 2895.956773] wlan0: deauthenticating from <masked_address> by local choice (Reason: 3=DEAUTH_LEAVING)
Jun 19 08:29:36 Vanadium kernel: [ 2896.113571] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
Jun 19 08:29:36 Vanadium kernel: [ 2896.273514] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
Jun 19 08:29:36 Vanadium kernel: [ 2896.433457] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
Jun 19 08:29:36 Vanadium kernel: [ 2896.593401] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
Jun 19 08:29:36 Vanadium wpa_supplicant[1308]: wlan0: CTRL-EVENT-DISCONNECTED bssid=<masked_address> reason=3 locally_generated=1
Jun 19 08:29:36 Vanadium avahi-daemon[950]: Withdrawing address record for <masked_address> on wlan0.
Jun 19 08:29:36 Vanadium avahi-daemon[950]: Leaving mDNS multicast group on interface wlan0.IPv4 with address <masked_address>.
Jun 19 08:29:36 Vanadium avahi-daemon[950]: Interface wlan0.IPv4 no longer relevant for mDNS.
Jun 19 08:29:36 Vanadium NetworkManager[1226]: <warn> DNS: plugin dnsmasq update failed
Jun 19 08:29:36 Vanadium NetworkManager[1226]: <info> Removing DNS information from /sbin/resolvconf
Jun 19 08:29:36 Vanadium dnsmasq[1728]: setting upstream servers from DBus
Jun 19 08:29:36 Vanadium kernel: [ 2896.795500] cfg80211: Calling CRDA to update world regulatory domain
Jun 19 08:29:36 Vanadium kernel: [ 2896.798942] cfg80211: World regulatory domain updated:
Jun 19 08:29:36 Vanadium kernel: [ 2896.798945] cfg80211:  DFS Master region: unset
Jun 19 08:29:36 Vanadium kernel: [ 2896.798946] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
Jun 19 08:29:36 Vanadium kernel: [ 2896.798947] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Jun 19 08:29:36 Vanadium kernel: [ 2896.798949] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Jun 19 08:29:36 Vanadium kernel: [ 2896.798949] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm), (N/A)
Jun 19 08:29:36 Vanadium kernel: [ 2896.798950] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Jun 19 08:29:36 Vanadium kernel: [ 2896.798951] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Jun 19 08:29:36 Vanadium NetworkManager[1226]: <info> (wlan0): cleaning up...
Jun 19 08:29:36 Vanadium NetworkManager[1226]: <info> (wlan0): taking down device.
Jun 19 08:29:36 Vanadium NetworkManager[1226]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Jun 19 08:29:36 Vanadium dbus[848]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Jun 19 08:29:36 Vanadium NetworkManager[1226]: <info> Removing DNS information from /sbin/resolvconf
Jun 19 08:29:36 Vanadium dnsmasq[1728]: exiting on receipt of SIGTERM
Jun 19 08:29:36 Vanadium kernel: [ 2896.854629] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun 19 08:29:36 Vanadium NetworkManager[1226]: <info> exiting (success)
Jun 19 08:29:36 Vanadium ModemManager[876]: <info>  Caught signal, shutting down...
Jun 19 08:29:36 Vanadium ModemManager[876]: <info>  ModemManager is shut down
Jun 19 08:29:36 Vanadium dbus[848]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Jun 19 08:29:36 Vanadium ModemManager[2869]: <info>  ModemManager (version 1.0.0) starting...
Jun 19 08:29:36 Vanadium NetworkManager[2875]: <info> NetworkManager (version 0.9.8.8) is starting...
Jun 19 08:29:36 Vanadium NetworkManager[2875]: <info> Read config file /etc/NetworkManager/NetworkManager.conf
Jun 19 08:29:36 Vanadium NetworkManager[2875]: <info> WEXT support is enabled
Jun 19 08:29:36 Vanadium NetworkManager[2875]: <info> VPN: loaded org.freedesktop.NetworkManager.pptp
Jun 19 08:29:36 Vanadium NetworkManager[2875]: <info> DNS: loaded plugin dnsmasq
Jun 19 08:29:36 Vanadium NetworkManager[2875]:    SCPlugin-Ifupdown: init!
Jun 19 08:29:36 Vanadium NetworkManager[2875]:    SCPlugin-Ifupdown: update_system_hostname
Jun 19 08:29:36 Vanadium NetworkManager[2875]:       interface-parser: parsing file /etc/network/interfaces
Jun 19 08:29:36 Vanadium NetworkManager[2875]:       interface-parser: finished parsing file /etc/network/interfaces
Jun 19 08:29:36 Vanadium NetworkManager[2875]:    SCPluginIfupdown: management mode: unmanaged
Jun 19 08:29:36 Vanadium NetworkManager[2875]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.2/0000:02:00.0/net/eth0, iface: eth0)
Jun 19 08:29:36 Vanadium NetworkManager[2875]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.2/0000:02:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
Jun 19 08:29:36 Vanadium NetworkManager[2875]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.5/0000:03:00.0/net/wlan0, iface: wlan0)
Jun 19 08:29:36 Vanadium NetworkManager[2875]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.5/0000:03:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Jun 19 08:29:36 Vanadium NetworkManager[2875]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Jun 19 08:29:36 Vanadium NetworkManager[2875]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Jun 19 08:29:36 Vanadium NetworkManager[2875]:    SCPlugin-Ifupdown: end _init.
Jun 19 08:29:36 Vanadium NetworkManager[2875]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Jun 19 08:29:36 Vanadium NetworkManager[2875]: <info> Loaded plugin keyfile: (c) 2007 - 2010 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Jun 19 08:29:36 Vanadium NetworkManager[2875]:    SCPlugin-Ofono: Acquired D-Bus service com.canonical.NMOfono
Jun 19 08:29:36 Vanadium NetworkManager[2875]:    SCPlugin-Ofono: init!
Jun 19 08:29:36 Vanadium NetworkManager[2875]:    SCPlugin-Ofono: end _init.
Jun 19 08:29:36 Vanadium NetworkManager[2875]: <info> Loaded plugin (null): (null)
Jun 19 08:29:36 Vanadium NetworkManager[2875]:    Ifupdown: get unmanaged devices count: 0
Jun 19 08:29:36 Vanadium NetworkManager[2875]:    SCPlugin-Ifupdown: (10735344) ... get_connections.
Jun 19 08:29:36 Vanadium NetworkManager[2875]:    SCPlugin-Ifupdown: (10735344) ... get_connections (managed=false): return empty list.
Jun 19 08:29:36 Vanadium NetworkManager[2875]:    keyfile: parsing Ex Mente ... 
Jun 19 08:29:36 Vanadium NetworkManager[2875]:    keyfile:     read connection 'Ex Mente'
Jun 19 08:29:36 Vanadium NetworkManager[2875]:    keyfile: parsing Wired connection 1 ... 
Jun 19 08:29:36 Vanadium NetworkManager[2875]:    keyfile:     read connection 'Wired connection 1'
Jun 19 08:29:36 Vanadium NetworkManager[2875]:    SCPlugin-Ofono: (1006649552) ... get_connections.
Jun 19 08:29:36 Vanadium NetworkManager[2875]:    SCPlugin-Ofono: (1006649552) connections count: 0
Jun 19 08:29:36 Vanadium NetworkManager[2875]:    Ifupdown: get unmanaged devices count: 0
Jun 19 08:29:36 Vanadium NetworkManager[2875]: <info> monitoring kernel firmware directory '/lib/firmware'.
Jun 19 08:29:36 Vanadium NetworkManager[2875]: <info> rfkill0: found WiFi radio killswitch (at /sys/devices/pci0000:00/0000:00:1c.5/0000:03:00.0/ieee80211/phy0/rfkill0) (driver rt2800pci)
Jun 19 08:29:36 Vanadium NetworkManager[2875]: <info> WiFi enabled by radio killswitch; enabled by state file
Jun 19 08:29:36 Vanadium NetworkManager[2875]: <info> WWAN enabled by radio killswitch; enabled by state file
Jun 19 08:29:36 Vanadium NetworkManager[2875]: <info> WiMAX enabled by radio killswitch; enabled by state file
Jun 19 08:29:36 Vanadium NetworkManager[2875]: <info> Networking is enabled by state file
Jun 19 08:29:36 Vanadium NetworkManager[2875]: <warn> failed to allocate link cache: (-12) Object not found
Jun 19 08:29:36 Vanadium NetworkManager[2875]: <info> (eth0): carrier is OFF
Jun 19 08:29:36 Vanadium NetworkManager[2875]: <info> (eth0): new Ethernet device (driver: 'r8169' ifindex: 2)
Jun 19 08:29:36 Vanadium NetworkManager[2875]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Jun 19 08:29:36 Vanadium NetworkManager[2875]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jun 19 08:29:36 Vanadium NetworkManager[2875]: <info> (eth0): bringing up device.
Jun 19 08:29:36 Vanadium NetworkManager[2875]: <info> (eth0): preparing device.
Jun 19 08:29:36 Vanadium NetworkManager[2875]: <info> (eth0): deactivating device (reason 'managed') [2]
Jun 19 08:29:36 Vanadium NetworkManager[2875]: <info> (wlan0): using nl80211 for WiFi device control
Jun 19 08:29:36 Vanadium NetworkManager[2875]: <info> (wlan0): driver supports Access Point (AP) mode
Jun 19 08:29:36 Vanadium NetworkManager[2875]: <info> (wlan0): new 802.11 WiFi device (driver: 'rt2800pci' ifindex: 3)
Jun 19 08:29:36 Vanadium NetworkManager[2875]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
Jun 19 08:29:36 Vanadium NetworkManager[2875]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jun 19 08:29:36 Vanadium NetworkManager[2875]: <info> (wlan0): bringing up device.
Jun 19 08:29:36 Vanadium kernel: [ 2896.971395] r8169 0000:02:00.0 eth0: link down
Jun 19 08:29:36 Vanadium kernel: [ 2896.971451] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Jun 19 08:29:36 Vanadium kernel: [ 2896.971679] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Jun 19 08:29:36 Vanadium NetworkManager[2875]: <info> (wlan0): preparing device.
Jun 19 08:29:36 Vanadium NetworkManager[2875]: <info> (wlan0): deactivating device (reason 'managed') [2]
Jun 19 08:29:36 Vanadium NetworkManager[2875]: <warn> /sys/devices/virtual/net/lo: couldn't determine device driver; ignoring...
Jun 19 08:29:36 Vanadium NetworkManager[2875]: <warn> /sys/devices/virtual/net/lo: couldn't determine device driver; ignoring...
Jun 19 08:29:36 Vanadium NetworkManager[2875]: <info> urfkill disappeared from the bus
Jun 19 08:29:36 Vanadium kernel: [ 2897.029391] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not readyJun 19 08:29:35 Vanadium NetworkManager[1226]: <info> caught signal 15, shutting down normally.
Jun 19 08:29:35 Vanadium NetworkManager[1226]: <info> (eth0): device state change: unavailable -> unmanaged (reason 'removed') [20 10 36]
Jun 19 08:29:35 Vanadium NetworkManager[1226]: <info> (eth0): cleaning up...
Jun 19 08:29:35 Vanadium NetworkManager[1226]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Jun 19 08:29:35 Vanadium NetworkManager[1226]: <info> (wlan0): device state change: activated -> unmanaged (reason 'removed') [100 10 36]
Jun 19 08:29:35 Vanadium NetworkManager[1226]: <info> (wlan0): deactivating device (reason 'removed') [36]
Jun 19 08:29:35 Vanadium kernel: [ 2895.755149] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Jun 19 08:29:35 Vanadium NetworkManager[1226]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 1429
Jun 19 08:29:35 Vanadium avahi-daemon[950]: Withdrawing address record for <masked_address> on wlan0.
Jun 19 08:29:35 Vanadium avahi-daemon[950]: Leaving mDNS multicast group on interface wlan0.IPv6 with address <masked_address>.
Jun 19 08:29:35 Vanadium avahi-daemon[950]: Interface wlan0.IPv6 no longer relevant for mDNS.
Jun 19 08:29:35 Vanadium kernel: [ 2895.956773] wlan0: deauthenticating from <masked_address> by local choice (Reason: 3=DEAUTH_LEAVING)
Jun 19 08:29:36 Vanadium kernel: [ 2896.113571] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
Jun 19 08:29:36 Vanadium kernel: [ 2896.273514] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
Jun 19 08:29:36 Vanadium kernel: [ 2896.433457] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
Jun 19 08:29:36 Vanadium kernel: [ 2896.593401] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
Jun 19 08:29:36 Vanadium wpa_supplicant[1308]: wlan0: CTRL-EVENT-DISCONNECTED bssid=<masked_address> reason=3 locally_generated=1
Jun 19 08:29:36 Vanadium avahi-daemon[950]: Withdrawing address record for <masked_address> on wlan0.
Jun 19 08:29:36 Vanadium avahi-daemon[950]: Leaving mDNS multicast group on interface wlan0.IPv4 with address <masked_address>.
Jun 19 08:29:36 Vanadium avahi-daemon[950]: Interface wlan0.IPv4 no longer relevant for mDNS.
Jun 19 08:29:36 Vanadium NetworkManager[1226]: <warn> DNS: plugin dnsmasq update failed
Jun 19 08:29:36 Vanadium NetworkManager[1226]: <info> Removing DNS information from /sbin/resolvconf
Jun 19 08:29:36 Vanadium dnsmasq[1728]: setting upstream servers from DBus
Jun 19 08:29:36 Vanadium kernel: [ 2896.795500] cfg80211: Calling CRDA to update world regulatory domain
Jun 19 08:29:36 Vanadium kernel: [ 2896.798942] cfg80211: World regulatory domain updated:
Jun 19 08:29:36 Vanadium kernel: [ 2896.798945] cfg80211:  DFS Master region: unset
Jun 19 08:29:36 Vanadium kernel: [ 2896.798946] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
Jun 19 08:29:36 Vanadium kernel: [ 2896.798947] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Jun 19 08:29:36 Vanadium kernel: [ 2896.798949] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Jun 19 08:29:36 Vanadium kernel: [ 2896.798949] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm), (N/A)
Jun 19 08:29:36 Vanadium kernel: [ 2896.798950] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Jun 19 08:29:36 Vanadium kernel: [ 2896.798951] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Jun 19 08:29:36 Vanadium NetworkManager[1226]: <info> (wlan0): cleaning up...
Jun 19 08:29:36 Vanadium NetworkManager[1226]: <info> (wlan0): taking down device.
Jun 19 08:29:36 Vanadium NetworkManager[1226]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Jun 19 08:29:36 Vanadium dbus[848]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Jun 19 08:29:36 Vanadium NetworkManager[1226]: <info> Removing DNS information from /sbin/resolvconf
Jun 19 08:29:36 Vanadium dnsmasq[1728]: exiting on receipt of SIGTERM
Jun 19 08:29:36 Vanadium kernel: [ 2896.854629] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun 19 08:29:36 Vanadium NetworkManager[1226]: <info> exiting (success)
Jun 19 08:29:36 Vanadium ModemManager[876]: <info>  Caught signal, shutting down...
Jun 19 08:29:36 Vanadium ModemManager[876]: <info>  ModemManager is shut down
Jun 19 08:29:36 Vanadium dbus[848]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Jun 19 08:29:36 Vanadium ModemManager[2869]: <info>  ModemManager (version 1.0.0) starting...
Jun 19 08:29:36 Vanadium NetworkManager[2875]: <info> NetworkManager (version 0.9.8.8) is starting...
Jun 19 08:29:36 Vanadium NetworkManager[2875]: <info> Read config file /etc/NetworkManager/NetworkManager.conf
Jun 19 08:29:36 Vanadium NetworkManager[2875]: <info> WEXT support is enabled
Jun 19 08:29:36 Vanadium NetworkManager[2875]: <info> VPN: loaded org.freedesktop.NetworkManager.pptp
Jun 19 08:29:36 Vanadium NetworkManager[2875]: <info> DNS: loaded plugin dnsmasq
Jun 19 08:29:36 Vanadium NetworkManager[2875]:    SCPlugin-Ifupdown: init!
Jun 19 08:29:36 Vanadium NetworkManager[2875]:    SCPlugin-Ifupdown: update_system_hostname
Jun 19 08:29:36 Vanadium NetworkManager[2875]:       interface-parser: parsing file /etc/network/interfaces
Jun 19 08:29:36 Vanadium NetworkManager[2875]:       interface-parser: finished parsing file /etc/network/interfaces
Jun 19 08:29:36 Vanadium NetworkManager[2875]:    SCPluginIfupdown: management mode: unmanaged
Jun 19 08:29:36 Vanadium NetworkManager[2875]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.2/0000:02:00.0/net/eth0, iface: eth0)
Jun 19 08:29:36 Vanadium NetworkManager[2875]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.2/0000:02:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
Jun 19 08:29:36 Vanadium NetworkManager[2875]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.5/0000:03:00.0/net/wlan0, iface: wlan0)
Jun 19 08:29:36 Vanadium NetworkManager[2875]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.5/0000:03:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Jun 19 08:29:36 Vanadium NetworkManager[2875]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Jun 19 08:29:36 Vanadium NetworkManager[2875]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Jun 19 08:29:36 Vanadium NetworkManager[2875]:    SCPlugin-Ifupdown: end _init.
Jun 19 08:29:36 Vanadium NetworkManager[2875]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Jun 19 08:29:36 Vanadium NetworkManager[2875]: <info> Loaded plugin keyfile: (c) 2007 - 2010 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Jun 19 08:29:36 Vanadium NetworkManager[2875]:    SCPlugin-Ofono: Acquired D-Bus service com.canonical.NMOfono
Jun 19 08:29:36 Vanadium NetworkManager[2875]:    SCPlugin-Ofono: init!
Jun 19 08:29:36 Vanadium NetworkManager[2875]:    SCPlugin-Ofono: end _init.
Jun 19 08:29:36 Vanadium NetworkManager[2875]: <info> Loaded plugin (null): (null)
Jun 19 08:29:36 Vanadium NetworkManager[2875]:    Ifupdown: get unmanaged devices count: 0
Jun 19 08:29:36 Vanadium NetworkManager[2875]:    SCPlugin-Ifupdown: (10735344) ... get_connections.
Jun 19 08:29:36 Vanadium NetworkManager[2875]:    SCPlugin-Ifupdown: (10735344) ... get_connections (managed=false): return empty list.
Jun 19 08:29:36 Vanadium NetworkManager[2875]:    keyfile: parsing Ex Mente ... 
Jun 19 08:29:36 Vanadium NetworkManager[2875]:    keyfile:     read connection 'Ex Mente'
Jun 19 08:29:36 Vanadium NetworkManager[2875]:    keyfile: parsing Wired connection 1 ... 
Jun 19 08:29:36 Vanadium NetworkManager[2875]:    keyfile:     read connection 'Wired connection 1'
Jun 19 08:29:36 Vanadium NetworkManager[2875]:    SCPlugin-Ofono: (1006649552) ... get_connections.
Jun 19 08:29:36 Vanadium NetworkManager[2875]:    SCPlugin-Ofono: (1006649552) connections count: 0
Jun 19 08:29:36 Vanadium NetworkManager[2875]:    Ifupdown: get unmanaged devices count: 0
Jun 19 08:29:36 Vanadium NetworkManager[2875]: <info> monitoring kernel firmware directory '/lib/firmware'.
Jun 19 08:29:36 Vanadium NetworkManager[2875]: <info> rfkill0: found WiFi radio killswitch (at /sys/devices/pci0000:00/0000:00:1c.5/0000:03:00.0/ieee80211/phy0/rfkill0) (driver rt2800pci)
Jun 19 08:29:36 Vanadium NetworkManager[2875]: <info> WiFi enabled by radio killswitch; enabled by state file
Jun 19 08:29:36 Vanadium NetworkManager[2875]: <info> WWAN enabled by radio killswitch; enabled by state file
Jun 19 08:29:36 Vanadium NetworkManager[2875]: <info> WiMAX enabled by radio killswitch; enabled by state file
Jun 19 08:29:36 Vanadium NetworkManager[2875]: <info> Networking is enabled by state file
Jun 19 08:29:36 Vanadium NetworkManager[2875]: <warn> failed to allocate link cache: (-12) Object not found
Jun 19 08:29:36 Vanadium NetworkManager[2875]: <info> (eth0): carrier is OFF
Jun 19 08:29:36 Vanadium NetworkManager[2875]: <info> (eth0): new Ethernet device (driver: 'r8169' ifindex: 2)
Jun 19 08:29:36 Vanadium NetworkManager[2875]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Jun 19 08:29:36 Vanadium NetworkManager[2875]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jun 19 08:29:36 Vanadium NetworkManager[2875]: <info> (eth0): bringing up device.
Jun 19 08:29:36 Vanadium NetworkManager[2875]: <info> (eth0): preparing device.
Jun 19 08:29:36 Vanadium NetworkManager[2875]: <info> (eth0): deactivating device (reason 'managed') [2]
Jun 19 08:29:36 Vanadium NetworkManager[2875]: <info> (wlan0): using nl80211 for WiFi device control
Jun 19 08:29:36 Vanadium NetworkManager[2875]: <info> (wlan0): driver supports Access Point (AP) mode
Jun 19 08:29:36 Vanadium NetworkManager[2875]: <info> (wlan0): new 802.11 WiFi device (driver: 'rt2800pci' ifindex: 3)
Jun 19 08:29:36 Vanadium NetworkManager[2875]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
Jun 19 08:29:36 Vanadium NetworkManager[2875]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jun 19 08:29:36 Vanadium NetworkManager[2875]: <info> (wlan0): bringing up device.
Jun 19 08:29:36 Vanadium kernel: [ 2896.971395] r8169 0000:02:00.0 eth0: link down
Jun 19 08:29:36 Vanadium kernel: [ 2896.971451] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Jun 19 08:29:36 Vanadium kernel: [ 2896.971679] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Jun 19 08:29:36 Vanadium NetworkManager[2875]: <info> (wlan0): preparing device.
Jun 19 08:29:36 Vanadium NetworkManager[2875]: <info> (wlan0): deactivating device (reason 'managed') [2]
Jun 19 08:29:36 Vanadium NetworkManager[2875]: <warn> /sys/devices/virtual/net/lo: couldn't determine device driver; ignoring...
Jun 19 08:29:36 Vanadium NetworkManager[2875]: <warn> /sys/devices/virtual/net/lo: couldn't determine device driver; ignoring...
Jun 19 08:29:36 Vanadium NetworkManager[2875]: <info> urfkill disappeared from the bus
Jun 19 08:29:36 Vanadium kernel: [ 2897.029391] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun 19 08:29:36 Vanadium kernel: [ 2897.029581] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun 19 08:29:36 Vanadium NetworkManager[2875]: <info> ModemManager available in the bus
Jun 19 08:29:37 Vanadium NetworkManager[2875]: <info> (wlan0) supports 4 scan SSIDs
Jun 19 08:29:37 Vanadium NetworkManager[2875]: <info> (wlan0): supplicant interface state: starting -> ready
Jun 19 08:29:37 Vanadium NetworkManager[2875]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Jun 19 08:29:37 Vanadium NetworkManager[2875]: <warn> Trying to remove a non-existant call id.
Jun 19 08:29:37 Vanadium wpa_supplicant[1308]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jun 19 08:29:37 Vanadium NetworkManager[2875]: <info> (wlan0): supplicant interface state: ready -> disconnected
Jun 19 08:29:37 Vanadium NetworkManager[2875]: <info> (wlan0) supports 4 scan SSIDs
Jun 19 08:29:38 Vanadium NetworkManager[2875]: <info> Auto-activating connection 'Ex Mente'.
Jun 19 08:29:38 Vanadium NetworkManager[2875]: <info> Activation (wlan0) starting connection 'Ex Mente'
Jun 19 08:29:38 Vanadium NetworkManager[2875]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Jun 19 08:29:38 Vanadium NetworkManager[2875]: <info> NetworkManager state is now CONNECTING
Jun 19 08:29:38 Vanadium NetworkManager[2875]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jun 19 08:29:38 Vanadium NetworkManager[2875]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jun 19 08:29:38 Vanadium NetworkManager[2875]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jun 19 08:29:38 Vanadium NetworkManager[2875]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jun 19 08:29:38 Vanadium NetworkManager[2875]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jun 19 08:29:38 Vanadium NetworkManager[2875]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Jun 19 08:29:38 Vanadium NetworkManager[2875]: <info> Activation (wlan0/wireless): connection 'Ex Mente' has security, and secrets exist.  No new secrets needed.
Jun 19 08:29:38 Vanadium NetworkManager[2875]: <info> Config: added 'ssid' value 'Ex Mente'
Jun 19 08:29:38 Vanadium NetworkManager[2875]: <info> Config: added 'scan_ssid' value '1'
Jun 19 08:29:38 Vanadium NetworkManager[2875]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Jun 19 08:29:38 Vanadium NetworkManager[2875]: <info> Config: added 'psk' value '<omitted>'
Jun 19 08:29:38 Vanadium NetworkManager[2875]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jun 19 08:29:38 Vanadium NetworkManager[2875]: <info> (wlan0): supplicant interface state: disconnected -> inactive
Jun 19 08:29:38 Vanadium NetworkManager[2875]: <info> Config: set interface ap_scan to 1
Jun 19 08:29:38 Vanadium ModemManager[2869]: <warn>  Couldn't find support for device at '/sys/devices/pci0000:00/0000:00:1c.2/0000:02:00.0': not supported by any plugin
Jun 19 08:29:38 Vanadium ModemManager[2869]: <warn>  Couldn't find support for device at '/sys/devices/pci0000:00/0000:00:1c.5/0000:03:00.0': not supported by any plugin
Jun 19 08:29:38 Vanadium wpa_supplicant[1308]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jun 19 08:29:39 Vanadium wpa_supplicant[1308]: wlan0: SME: Trying to authenticate with <masked_address> (SSID='Ex Mente' freq=2412 MHz)
Jun 19 08:29:39 Vanadium kernel: [ 2899.181261] wlan0: authenticate with <masked_address>
Jun 19 08:29:39 Vanadium NetworkManager[2875]: <info> (wlan0): supplicant interface state: inactive -> authenticating
Jun 19 08:29:39 Vanadium wpa_supplicant[1308]: wlan0: Trying to associate with <masked_address> (SSID='Ex Mente' freq=2412 MHz)
Jun 19 08:29:39 Vanadium kernel: [ 2899.196525] wlan0: send auth to <masked_address> (try 1/3)
Jun 19 08:29:39 Vanadium kernel: [ 2899.197983] wlan0: authenticated
Jun 19 08:29:39 Vanadium kernel: [ 2899.200461] wlan0: associate with <masked_address> (try 1/3)
Jun 19 08:29:39 Vanadium wpa_supplicant[1308]: wlan0: Associated with <masked_address>
Jun 19 08:29:39 Vanadium NetworkManager[2875]: <info> (wlan0): supplicant interface state: authenticating -> associating
Jun 19 08:29:39 Vanadium kernel: [ 2899.203440] wlan0: RX AssocResp from <masked_address> (capab=0x411 status=0 aid=4)
Jun 19 08:29:39 Vanadium kernel: [ 2899.203538] wlan0: associated
Jun 19 08:29:39 Vanadium kernel: [ 2899.203588] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Jun 19 08:29:39 Vanadium NetworkManager[2875]: <info> (wlan0): supplicant interface state: associating -> associated
Jun 19 08:29:39 Vanadium NetworkManager[2875]: <info> (wlan0): supplicant interface state: associated -> 4-way handshake
Jun 19 08:29:39 Vanadium wpa_supplicant[1308]: wlan0: WPA: Key negotiation completed with <masked_address> [PTK=CCMP GTK=CCMP]
Jun 19 08:29:39 Vanadium wpa_supplicant[1308]: wlan0: CTRL-EVENT-CONNECTED - Connection to <masked_address> completed [id=0 id_str=]
Jun 19 08:29:39 Vanadium wpa_supplicant[1308]: wlan0: SME: Trying to authenticate with <masked_address> (SSID='Ex Mente' freq=2412 MHz)
Jun 19 08:29:39 Vanadium kernel: [ 2899.220589] wlan0: deauthenticating from <masked_address> by local choice (Reason: 2=PREV_AUTH_NOT_VALID)
Jun 19 08:29:39 Vanadium kernel: [ 2899.260509] wlan0: authenticate with <masked_address>
Jun 19 08:29:39 Vanadium wpa_supplicant[1308]: wlan0: CTRL-EVENT-DISCONNECTED bssid=<masked_address> reason=2 locally_generated=1
Jun 19 08:29:39 Vanadium NetworkManager[2875]: <info> (wlan0): supplicant interface state: 4-way handshake -> authenticating
Jun 19 08:29:39 Vanadium wpa_supplicant[1308]: wlan0: Trying to associate with <masked_address> (SSID='Ex Mente' freq=2412 MHz)
Jun 19 08:29:39 Vanadium NetworkManager[2875]: <warn> Connection disconnected (reason -2)
Jun 19 08:29:39 Vanadium kernel: [ 2899.268499] wlan0: send auth to <masked_address> (try 1/3)
Jun 19 08:29:39 Vanadium kernel: [ 2899.268584] cfg80211: Calling CRDA to update world regulatory domain
Jun 19 08:29:39 Vanadium kernel: [ 2899.269983] wlan0: authenticated
Jun 19 08:29:39 Vanadium kernel: [ 2899.272407] wlan0: associate with <masked_address> (try 1/3)
Jun 19 08:29:39 Vanadium NetworkManager[2875]: <info> (wlan0): supplicant interface state: authenticating -> associating
Jun 19 08:29:39 Vanadium kernel: [ 2899.273352] cfg80211: World regulatory domain updated:
Jun 19 08:29:39 Vanadium kernel: [ 2899.273359] cfg80211:  DFS Master region: unset
Jun 19 08:29:39 Vanadium kernel: [ 2899.273362] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
Jun 19 08:29:39 Vanadium kernel: [ 2899.273368] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Jun 19 08:29:39 Vanadium kernel: [ 2899.273373] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Jun 19 08:29:39 Vanadium kernel: [ 2899.273377] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm), (N/A)
Jun 19 08:29:39 Vanadium kernel: [ 2899.273380] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Jun 19 08:29:39 Vanadium kernel: [ 2899.273384] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Jun 19 08:29:39 Vanadium wpa_supplicant[1308]: wlan0: Associated with <masked_address>
Jun 19 08:29:39 Vanadium kernel: [ 2899.277278] wlan0: RX AssocResp from <masked_address> (capab=0x411 status=0 aid=4)
Jun 19 08:29:39 Vanadium kernel: [ 2899.277375] wlan0: associated
Jun 19 08:29:39 Vanadium NetworkManager[2875]: <info> (wlan0): supplicant interface state: associating -> associated
Jun 19 08:29:39 Vanadium NetworkManager[2875]: <info> (wlan0): supplicant interface state: associated -> 4-way handshake
Jun 19 08:29:39 Vanadium wpa_supplicant[1308]: wlan0: WPA: Key negotiation completed with <masked_address> [PTK=CCMP GTK=CCMP]
Jun 19 08:29:39 Vanadium wpa_supplicant[1308]: wlan0: CTRL-EVENT-CONNECTED - Connection to <masked_address> completed [id=0 id_str=]
Jun 19 08:29:39 Vanadium NetworkManager[2875]: <info> (wlan0): supplicant interface state: 4-way handshake -> completed
Jun 19 08:29:39 Vanadium NetworkManager[2875]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'Ex Mente'.
Jun 19 08:29:39 Vanadium NetworkManager[2875]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Jun 19 08:29:39 Vanadium NetworkManager[2875]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Jun 19 08:29:39 Vanadium NetworkManager[2875]: <info> (wlan0): device state change: config -> ip-config (reason 'none') [50 70 0]
Jun 19 08:29:39 Vanadium NetworkManager[2875]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jun 19 08:29:39 Vanadium NetworkManager[2875]: <info> dhclient started with pid 2884
Jun 19 08:29:39 Vanadium NetworkManager[2875]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Jun 19 08:29:39 Vanadium dhclient: Internet Systems Consortium DHCP Client 4.2.4
Jun 19 08:29:39 Vanadium dhclient: Copyright 2004-2012 Internet Systems Consortium.
Jun 19 08:29:39 Vanadium dhclient: All rights reserved.
Jun 19 08:29:39 Vanadium dhclient: For info, please visit https://www.isc.org/software/dhcp/
Jun 19 08:29:39 Vanadium dhclient: 
Jun 19 08:29:39 Vanadium NetworkManager[2875]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Jun 19 08:29:39 Vanadium dhclient: Listening on LPF/wlan0/<masked_address>
Jun 19 08:29:39 Vanadium dhclient: Sending on   LPF/wlan0/<masked_address>
Jun 19 08:29:39 Vanadium dhclient: Sending on   Socket/fallback
Jun 19 08:29:39 Vanadium dhclient: DHCPREQUEST of <masked_address> on wlan0 to 255.255.255.255 port 67 (xid=0x614e4ac0)
Jun 19 08:29:39 Vanadium dhclient: DHCPACK of <masked_address> from <masked_address>
Jun 19 08:29:39 Vanadium dhclient: bound to <masked_address> -- renewal in 32515 seconds.
Jun 19 08:29:39 Vanadium NetworkManager[2875]: <info> (wlan0): DHCPv4 state changed preinit -> reboot
Jun 19 08:29:39 Vanadium NetworkManager[2875]: <info>   address <masked_address>
Jun 19 08:29:39 Vanadium NetworkManager[2875]: <info>   prefix 24 (255.255.255.0)
Jun 19 08:29:39 Vanadium NetworkManager[2875]: <info>   gateway <masked_address>
Jun 19 08:29:39 Vanadium NetworkManager[2875]: <info>   nameserver '<masked_address>'
Jun 19 08:29:39 Vanadium NetworkManager[2875]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Jun 19 08:29:39 Vanadium NetworkManager[2875]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) started...
Jun 19 08:29:39 Vanadium avahi-daemon[950]: Joining mDNS multicast group on interface wlan0.IPv4 with address <masked_address>.
Jun 19 08:29:39 Vanadium avahi-daemon[950]: New relevant interface wlan0.IPv4 for mDNS.
Jun 19 08:29:39 Vanadium avahi-daemon[950]: Registering new address record for <masked_address> on wlan0.IPv4.
Jun 19 08:29:40 Vanadium NetworkManager[2875]: <info> (wlan0): device state change: ip-config -> secondaries (reason 'none') [70 90 0]
Jun 19 08:29:40 Vanadium NetworkManager[2875]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) complete.
Jun 19 08:29:40 Vanadium NetworkManager[2875]: <info> (wlan0): device state change: secondaries -> activated (reason 'none') [90 100 0]
Jun 19 08:29:40 Vanadium NetworkManager[2875]: <info> NetworkManager state is now CONNECTED_GLOBAL
Jun 19 08:29:40 Vanadium NetworkManager[2875]: <info> Policy set 'Ex Mente' (wlan0) as default for IPv4 routing and DNS.
Jun 19 08:29:40 Vanadium NetworkManager[2875]: <info> DNS: starting dnsmasq...
Jun 19 08:29:40 Vanadium NetworkManager[2875]: <warn> dnsmasq not available on the bus, can't update servers.
Jun 19 08:29:40 Vanadium NetworkManager[2875]: <error> [1434695380.781783] [nm-dns-dnsmasq.c:396] update(): dnsmasq owner not found on bus: Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq': no such name
Jun 19 08:29:40 Vanadium NetworkManager[2875]: <warn> DNS: plugin dnsmasq update failed
Jun 19 08:29:40 Vanadium NetworkManager[2875]: <info> Writing DNS information to /sbin/resolvconf
Jun 19 08:29:40 Vanadium dnsmasq[2887]: started, version 2.68 cache disabled
Jun 19 08:29:40 Vanadium dnsmasq[2887]: compile time options: IPv6 GNU-getopt DBus i18n IDN DHCP DHCPv6 no-Lua TFTP conntrack ipset auth
Jun 19 08:29:40 Vanadium dnsmasq[2887]: DBus support enabled: connected to system bus
Jun 19 08:29:40 Vanadium dnsmasq[2887]: warning: no upstream servers configured
Jun 19 08:29:40 Vanadium avahi-daemon[950]: Got SIGTERM, quitting.
Jun 19 08:29:40 Vanadium avahi-daemon[950]: Leaving mDNS multicast group on interface wlan0.IPv4 with address <masked_address>.
Jun 19 08:29:40 Vanadium avahi-daemon[950]: avahi-daemon 0.6.31 exiting.
Jun 19 08:29:40 Vanadium avahi: Avahi detected that your currently configured local DNS server serves
Jun 19 08:29:40 Vanadium avahi: a domain .local. This is inherently incompatible with Avahi and thus
Jun 19 08:29:40 Vanadium avahi: Avahi disabled itself. If you want to use Avahi in this network, please
Jun 19 08:29:40 Vanadium avahi: contact your administrator and convince him to use a different DNS domain,
Jun 19 08:29:40 Vanadium avahi: since .local should be used exclusively for Zeroconf technology.
Jun 19 08:29:40 Vanadium avahi: For more information, see http://avahi.org/wiki/AvahiAndUnicastDotLocal
Jun 19 08:29:40 Vanadium NetworkManager[2875]: <info> Activation (wlan0) successful, device activated.
Jun 19 08:29:40 Vanadium NetworkManager[2875]: <warn> dnsmasq appeared on DBus: :1.118
Jun 19 08:29:40 Vanadium NetworkManager[2875]: <info> Writing DNS information to /sbin/resolvconf
Jun 19 08:29:40 Vanadium dnsmasq[2887]: setting upstream servers from DBus
Jun 19 08:29:40 Vanadium dnsmasq[2887]: using nameserver <masked_address>#53
Jun 19 08:29:40 Vanadium dnsmasq[2887]: using nameserver <masked_address>#53
Jun 19 08:29:40 Vanadium dnsmasq[2887]: using nameserver <masked_address>#53
Jun 19 08:29:51 Vanadium avahi-daemon[3101]: Found user 'avahi' (UID 111) and group 'avahi' (GID 117).
Jun 19 08:29:51 Vanadium avahi-daemon[3101]: Successfully dropped root privileges.
Jun 19 08:29:51 Vanadium avahi-daemon[3101]: avahi-daemon 0.6.31 starting up.
Jun 19 08:29:51 Vanadium dbus[848]: [system] Successfully activated service 'org.freedesktop.Avahi'
Jun 19 08:29:51 Vanadium avahi-daemon[3101]: Successfully called chroot().
Jun 19 08:29:51 Vanadium avahi-daemon[3101]: Successfully dropped remaining capabilities.
Jun 19 08:29:51 Vanadium avahi-daemon[3101]: No service file found in /etc/avahi/services.
Jun 19 08:29:51 Vanadium avahi-daemon[3101]: *** WARNING: Detected another IPv4 mDNS stack running on this host. This makes mDNS unreliable and is thus not recommended. ***
Jun 19 08:29:51 Vanadium avahi-daemon[3101]: Joining mDNS multicast group on interface wlan0.IPv6 with address <masked_address>.
Jun 19 08:29:51 Vanadium avahi-daemon[3101]: New relevant interface wlan0.IPv6 for mDNS.
Jun 19 08:29:51 Vanadium avahi-daemon[3101]: Joining mDNS multicast group on interface wlan0.IPv4 with address <masked_address>.
Jun 19 08:29:51 Vanadium avahi-daemon[3101]: New relevant interface wlan0.IPv4 for mDNS.
Jun 19 08:29:51 Vanadium avahi-daemon[3101]: Network interface enumeration completed.
Jun 19 08:29:51 Vanadium avahi-daemon[3101]: Registering new address record for <masked_address> on wlan0.*.
Jun 19 08:29:51 Vanadium avahi-daemon[3101]: Registering new address record for <masked_address> on wlan0.IPv4.
Jun 19 08:29:51 Vanadium avahi-daemon[3101]: Registering HINFO record with values 'X86_64'/'LINUX'.
Jun 19 08:29:51 Vanadium NetworkManager[2875]: <info> WiFi hardware radio set enabled
Jun 19 08:29:51 Vanadium avahi-daemon[3101]: Server startup complete. Host name is Vanadium.local. Local service cookie is 1245676608.
Jun 19 08:29:56 Vanadium whoopsie[1299]: offline
Jun 19 08:30:00 Vanadium kernel: [ 2920.116879] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
Jun 19 08:30:00 Vanadium kernel: [ 2920.276787] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
Jun 19 08:30:00 Vanadium kernel: [ 2920.436765] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
Jun 19 08:30:00 Vanadium wpa_supplicant[1308]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jun 19 08:30:00 Vanadium kernel: [ 2920.596674] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
Jun 19 08:30:03 Vanadium kernel: [ 2923.695581] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
Jun 19 08:30:36 Vanadium ntpdate[3011]: Can't find host ntp.ubuntu.com: Name or service not known (-2)
Jun 19 08:30:36 Vanadium ntpdate[3011]: no servers can be used, exiting
Jun 19 08:30:43 Vanadium kernel: [ 2963.101304] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
Jun 19 08:30:43 Vanadium kernel: [ 2963.261257] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
Jun 19 08:30:43 Vanadium kernel: [ 2963.421198] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
Jun 19 08:30:43 Vanadium kernel: [ 2963.581140] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
Jun 19 08:30:43 Vanadium kernel: [ 2963.949004] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
Jun 19 08:30:44 Vanadium kernel: [ 2964.108948] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
Jun 19 08:30:44 Vanadium kernel: [ 2964.268884] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
Jun 19 08:31:46 Vanadium kernel: [ 3026.074471] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
Jun 19 08:31:46 Vanadium kernel: [ 3026.234448] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
Jun 19 08:31:46 Vanadium kernel: [ 3026.394389] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
Jun 19 08:31:46 Vanadium kernel: [ 3026.554351] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
Jun 19 08:31:47 Vanadium kernel: [ 3027.561941] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
Jun 19 08:31:47 Vanadium kernel: [ 3027.721914] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
Jun 19 08:33:09 Vanadium kernel: [ 3109.048462] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
Jun 19 08:33:09 Vanadium kernel: [ 3109.208402] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
Jun 19 08:33:09 Vanadium kernel: [ 3109.368326] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
Jun 19 08:33:09 Vanadium kernel: [ 3109.528238] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
Jun 19 08:29:36 Vanadium kernel: [ 2897.029581] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun 19 08:29:36 Vanadium NetworkManager[2875]: <info> ModemManager available in the bus
Jun 19 08:29:37 Vanadium NetworkManager[2875]: <info> (wlan0) supports 4 scan SSIDs
Jun 19 08:29:37 Vanadium NetworkManager[2875]: <info> (wlan0): supplicant interface state: starting -> ready
Jun 19 08:29:37 Vanadium NetworkManager[2875]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Jun 19 08:29:37 Vanadium NetworkManager[2875]: <warn> Trying to remove a non-existant call id.
Jun 19 08:29:37 Vanadium wpa_supplicant[1308]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jun 19 08:29:37 Vanadium NetworkManager[2875]: <info> (wlan0): supplicant interface state: ready -> disconnected
Jun 19 08:29:37 Vanadium NetworkManager[2875]: <info> (wlan0) supports 4 scan SSIDs
Jun 19 08:29:38 Vanadium NetworkManager[2875]: <info> Auto-activating connection 'Ex Mente'.
Jun 19 08:29:38 Vanadium NetworkManager[2875]: <info> Activation (wlan0) starting connection 'Ex Mente'
Jun 19 08:29:38 Vanadium NetworkManager[2875]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Jun 19 08:29:38 Vanadium NetworkManager[2875]: <info> NetworkManager state is now CONNECTING
Jun 19 08:29:38 Vanadium NetworkManager[2875]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jun 19 08:29:38 Vanadium NetworkManager[2875]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jun 19 08:29:38 Vanadium NetworkManager[2875]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jun 19 08:29:38 Vanadium NetworkManager[2875]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jun 19 08:29:38 Vanadium NetworkManager[2875]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jun 19 08:29:38 Vanadium NetworkManager[2875]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Jun 19 08:29:38 Vanadium NetworkManager[2875]: <info> Activation (wlan0/wireless): connection 'Ex Mente' has security, and secrets exist.  No new secrets needed.
Jun 19 08:29:38 Vanadium NetworkManager[2875]: <info> Config: added 'ssid' value 'Ex Mente'
Jun 19 08:29:38 Vanadium NetworkManager[2875]: <info> Config: added 'scan_ssid' value '1'
Jun 19 08:29:38 Vanadium NetworkManager[2875]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Jun 19 08:29:38 Vanadium NetworkManager[2875]: <info> Config: added 'psk' value '<omitted>'
Jun 19 08:29:38 Vanadium NetworkManager[2875]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jun 19 08:29:38 Vanadium NetworkManager[2875]: <info> (wlan0): supplicant interface state: disconnected -> inactive
Jun 19 08:29:38 Vanadium NetworkManager[2875]: <info> Config: set interface ap_scan to 1
Jun 19 08:29:38 Vanadium ModemManager[2869]: <warn>  Couldn't find support for device at '/sys/devices/pci0000:00/0000:00:1c.2/0000:02:00.0': not supported by any plugin
Jun 19 08:29:38 Vanadium ModemManager[2869]: <warn>  Couldn't find support for device at '/sys/devices/pci0000:00/0000:00:1c.5/0000:03:00.0': not supported by any plugin
Jun 19 08:29:38 Vanadium wpa_supplicant[1308]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jun 19 08:29:39 Vanadium wpa_supplicant[1308]: wlan0: SME: Trying to authenticate with <masked_address> (SSID='Ex Mente' freq=2412 MHz)
Jun 19 08:29:39 Vanadium kernel: [ 2899.181261] wlan0: authenticate with <masked_address>
Jun 19 08:29:39 Vanadium NetworkManager[2875]: <info> (wlan0): supplicant interface state: inactive -> authenticating
Jun 19 08:29:39 Vanadium wpa_supplicant[1308]: wlan0: Trying to associate with <masked_address> (SSID='Ex Mente' freq=2412 MHz)
Jun 19 08:29:39 Vanadium kernel: [ 2899.196525] wlan0: send auth to <masked_address> (try 1/3)
Jun 19 08:29:39 Vanadium kernel: [ 2899.197983] wlan0: authenticated
Jun 19 08:29:39 Vanadium kernel: [ 2899.200461] wlan0: associate with <masked_address> (try 1/3)
Jun 19 08:29:39 Vanadium wpa_supplicant[1308]: wlan0: Associated with <masked_address>
Jun 19 08:29:39 Vanadium NetworkManager[2875]: <info> (wlan0): supplicant interface state: authenticating -> associating
Jun 19 08:29:39 Vanadium kernel: [ 2899.203440] wlan0: RX AssocResp from <masked_address> (capab=0x411 status=0 aid=4)
Jun 19 08:29:39 Vanadium kernel: [ 2899.203538] wlan0: associated
Jun 19 08:29:39 Vanadium kernel: [ 2899.203588] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Jun 19 08:29:39 Vanadium NetworkManager[2875]: <info> (wlan0): supplicant interface state: associating -> associated
Jun 19 08:29:39 Vanadium NetworkManager[2875]: <info> (wlan0): supplicant interface state: associated -> 4-way handshake
Jun 19 08:29:39 Vanadium wpa_supplicant[1308]: wlan0: WPA: Key negotiation completed with <masked_address> [PTK=CCMP GTK=CCMP]
Jun 19 08:29:39 Vanadium wpa_supplicant[1308]: wlan0: CTRL-EVENT-CONNECTED - Connection to <masked_address> completed [id=0 id_str=]
Jun 19 08:29:39 Vanadium wpa_supplicant[1308]: wlan0: SME: Trying to authenticate with <masked_address> (SSID='Ex Mente' freq=2412 MHz)
Jun 19 08:29:39 Vanadium kernel: [ 2899.220589] wlan0: deauthenticating from <masked_address> by local choice (Reason: 2=PREV_AUTH_NOT_VALID)
Jun 19 08:29:39 Vanadium kernel: [ 2899.260509] wlan0: authenticate with <masked_address>
Jun 19 08:29:39 Vanadium wpa_supplicant[1308]: wlan0: CTRL-EVENT-DISCONNECTED bssid=<masked_address> reason=2 locally_generated=1
Jun 19 08:29:39 Vanadium NetworkManager[2875]: <info> (wlan0): supplicant interface state: 4-way handshake -> authenticating
Jun 19 08:29:39 Vanadium wpa_supplicant[1308]: wlan0: Trying to associate with <masked_address> (SSID='Ex Mente' freq=2412 MHz)
Jun 19 08:29:39 Vanadium NetworkManager[2875]: <warn> Connection disconnected (reason -2)
Jun 19 08:29:39 Vanadium kernel: [ 2899.268499] wlan0: send auth to <masked_address> (try 1/3)
Jun 19 08:29:39 Vanadium kernel: [ 2899.268584] cfg80211: Calling CRDA to update world regulatory domain
Jun 19 08:29:39 Vanadium kernel: [ 2899.269983] wlan0: authenticated
Jun 19 08:29:39 Vanadium kernel: [ 2899.272407] wlan0: associate with <masked_address> (try 1/3)
Jun 19 08:29:39 Vanadium NetworkManager[2875]: <info> (wlan0): supplicant interface state: authenticating -> associating
Jun 19 08:29:39 Vanadium kernel: [ 2899.273352] cfg80211: World regulatory domain updated:
Jun 19 08:29:39 Vanadium kernel: [ 2899.273359] cfg80211:  DFS Master region: unset
Jun 19 08:29:39 Vanadium kernel: [ 2899.273362] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
Jun 19 08:29:39 Vanadium kernel: [ 2899.273368] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Jun 19 08:29:39 Vanadium kernel: [ 2899.273373] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Jun 19 08:29:39 Vanadium kernel: [ 2899.273377] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm), (N/A)
Jun 19 08:29:39 Vanadium kernel: [ 2899.273380] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Jun 19 08:29:39 Vanadium kernel: [ 2899.273384] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Jun 19 08:29:39 Vanadium wpa_supplicant[1308]: wlan0: Associated with <masked_address>
Jun 19 08:29:39 Vanadium kernel: [ 2899.277278] wlan0: RX AssocResp from <masked_address> (capab=0x411 status=0 aid=4)
Jun 19 08:29:39 Vanadium kernel: [ 2899.277375] wlan0: associated
Jun 19 08:29:39 Vanadium NetworkManager[2875]: <info> (wlan0): supplicant interface state: associating -> associated
Jun 19 08:29:39 Vanadium NetworkManager[2875]: <info> (wlan0): supplicant interface state: associated -> 4-way handshake
Jun 19 08:29:39 Vanadium wpa_supplicant[1308]: wlan0: WPA: Key negotiation completed with <masked_address> [PTK=CCMP GTK=CCMP]
Jun 19 08:29:39 Vanadium wpa_supplicant[1308]: wlan0: CTRL-EVENT-CONNECTED - Connection to <masked_address> completed [id=0 id_str=]
Jun 19 08:29:39 Vanadium NetworkManager[2875]: <info> (wlan0): supplicant interface state: 4-way handshake -> completed
Jun 19 08:29:39 Vanadium NetworkManager[2875]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'Ex Mente'.
Jun 19 08:29:39 Vanadium NetworkManager[2875]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Jun 19 08:29:39 Vanadium NetworkManager[2875]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Jun 19 08:29:39 Vanadium NetworkManager[2875]: <info> (wlan0): device state change: config -> ip-config (reason 'none') [50 70 0]
Jun 19 08:29:39 Vanadium NetworkManager[2875]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jun 19 08:29:39 Vanadium NetworkManager[2875]: <info> dhclient started with pid 2884
Jun 19 08:29:39 Vanadium NetworkManager[2875]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Jun 19 08:29:39 Vanadium dhclient: Internet Systems Consortium DHCP Client 4.2.4
Jun 19 08:29:39 Vanadium dhclient: Copyright 2004-2012 Internet Systems Consortium.
Jun 19 08:29:39 Vanadium dhclient: All rights reserved.
Jun 19 08:29:39 Vanadium dhclient: For info, please visit https://www.isc.org/software/dhcp/
Jun 19 08:29:39 Vanadium dhclient: 
Jun 19 08:29:39 Vanadium NetworkManager[2875]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Jun 19 08:29:39 Vanadium dhclient: Listening on LPF/wlan0/<masked_address>
Jun 19 08:29:39 Vanadium dhclient: Sending on   LPF/wlan0/<masked_address>
Jun 19 08:29:39 Vanadium dhclient: Sending on   Socket/fallback
Jun 19 08:29:39 Vanadium dhclient: DHCPREQUEST of <masked_address> on wlan0 to 255.255.255.255 port 67 (xid=0x614e4ac0)
Jun 19 08:29:39 Vanadium dhclient: DHCPACK of <masked_address> from <masked_address>
Jun 19 08:29:39 Vanadium dhclient: bound to <masked_address> -- renewal in 32515 seconds.
Jun 19 08:29:39 Vanadium NetworkManager[2875]: <info> (wlan0): DHCPv4 state changed preinit -> reboot
Jun 19 08:29:39 Vanadium NetworkManager[2875]: <info>   address <masked_address>
Jun 19 08:29:39 Vanadium NetworkManager[2875]: <info>   prefix 24 (255.255.255.0)
Jun 19 08:29:39 Vanadium NetworkManager[2875]: <info>   gateway <masked_address>
Jun 19 08:29:39 Vanadium NetworkManager[2875]: <info>   nameserver '<masked_address>'
Jun 19 08:29:39 Vanadium NetworkManager[2875]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Jun 19 08:29:39 Vanadium NetworkManager[2875]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) started...
Jun 19 08:29:39 Vanadium avahi-daemon[950]: Joining mDNS multicast group on interface wlan0.IPv4 with address <masked_address>.
Jun 19 08:29:39 Vanadium avahi-daemon[950]: New relevant interface wlan0.IPv4 for mDNS.
Jun 19 08:29:39 Vanadium avahi-daemon[950]: Registering new address record for <masked_address> on wlan0.IPv4.
Jun 19 08:29:40 Vanadium NetworkManager[2875]: <info> (wlan0): device state change: ip-config -> secondaries (reason 'none') [70 90 0]
Jun 19 08:29:40 Vanadium NetworkManager[2875]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) complete.
Jun 19 08:29:40 Vanadium NetworkManager[2875]: <info> (wlan0): device state change: secondaries -> activated (reason 'none') [90 100 0]
Jun 19 08:29:40 Vanadium NetworkManager[2875]: <info> NetworkManager state is now CONNECTED_GLOBAL
Jun 19 08:29:40 Vanadium NetworkManager[2875]: <info> Policy set 'Ex Mente' (wlan0) as default for IPv4 routing and DNS.
Jun 19 08:29:40 Vanadium NetworkManager[2875]: <info> DNS: starting dnsmasq...
Jun 19 08:29:40 Vanadium NetworkManager[2875]: <warn> dnsmasq not available on the bus, can't update servers.
Jun 19 08:29:40 Vanadium NetworkManager[2875]: <error> [1434695380.781783] [nm-dns-dnsmasq.c:396] update(): dnsmasq owner not found on bus: Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq': no such name
Jun 19 08:29:40 Vanadium NetworkManager[2875]: <warn> DNS: plugin dnsmasq update failed
Jun 19 08:29:40 Vanadium NetworkManager[2875]: <info> Writing DNS information to /sbin/resolvconf
Jun 19 08:29:40 Vanadium dnsmasq[2887]: started, version 2.68 cache disabled
Jun 19 08:29:40 Vanadium dnsmasq[2887]: compile time options: IPv6 GNU-getopt DBus i18n IDN DHCP DHCPv6 no-Lua TFTP conntrack ipset auth
Jun 19 08:29:40 Vanadium dnsmasq[2887]: DBus support enabled: connected to system bus
Jun 19 08:29:40 Vanadium dnsmasq[2887]: warning: no upstream servers configured
Jun 19 08:29:40 Vanadium avahi-daemon[950]: Got SIGTERM, quitting.
Jun 19 08:29:40 Vanadium avahi-daemon[950]: Leaving mDNS multicast group on interface wlan0.IPv4 with address <masked_address>.
Jun 19 08:29:40 Vanadium avahi-daemon[950]: avahi-daemon 0.6.31 exiting.
Jun 19 08:29:40 Vanadium avahi: Avahi detected that your currently configured local DNS server serves
Jun 19 08:29:40 Vanadium avahi: a domain .local. This is inherently incompatible with Avahi and thus
Jun 19 08:29:40 Vanadium avahi: Avahi disabled itself. If you want to use Avahi in this network, please
Jun 19 08:29:40 Vanadium avahi: contact your administrator and convince him to use a different DNS domain,
Jun 19 08:29:40 Vanadium avahi: since .local should be used exclusively for Zeroconf technology.
Jun 19 08:29:40 Vanadium avahi: For more information, see http://avahi.org/wiki/AvahiAndUnicastDotLocal
Jun 19 08:29:40 Vanadium NetworkManager[2875]: <info> Activation (wlan0) successful, device activated.
Jun 19 08:29:40 Vanadium NetworkManager[2875]: <warn> dnsmasq appeared on DBus: :1.118
Jun 19 08:29:40 Vanadium NetworkManager[2875]: <info> Writing DNS information to /sbin/resolvconf
Jun 19 08:29:40 Vanadium dnsmasq[2887]: setting upstream servers from DBus
Jun 19 08:29:40 Vanadium dnsmasq[2887]: using nameserver <masked_address>#53
Jun 19 08:29:40 Vanadium dnsmasq[2887]: using nameserver <masked_address>#53
Jun 19 08:29:40 Vanadium dnsmasq[2887]: using nameserver <masked_address>#53
Jun 19 08:29:51 Vanadium avahi-daemon[3101]: Found user 'avahi' (UID 111) and group 'avahi' (GID 117).
Jun 19 08:29:51 Vanadium avahi-daemon[3101]: Successfully dropped root privileges.
Jun 19 08:29:51 Vanadium avahi-daemon[3101]: avahi-daemon 0.6.31 starting up.
Jun 19 08:29:51 Vanadium dbus[848]: [system] Successfully activated service 'org.freedesktop.Avahi'
Jun 19 08:29:51 Vanadium avahi-daemon[3101]: Successfully called chroot().
Jun 19 08:29:51 Vanadium avahi-daemon[3101]: Successfully dropped remaining capabilities.
Jun 19 08:29:51 Vanadium avahi-daemon[3101]: No service file found in /etc/avahi/services.
Jun 19 08:29:51 Vanadium avahi-daemon[3101]: *** WARNING: Detected another IPv4 mDNS stack running on this host. This makes mDNS unreliable and is thus not recommended. ***
Jun 19 08:29:51 Vanadium avahi-daemon[3101]: Joining mDNS multicast group on interface wlan0.IPv6 with address <masked_address>.
Jun 19 08:29:51 Vanadium avahi-daemon[3101]: New relevant interface wlan0.IPv6 for mDNS.
Jun 19 08:29:51 Vanadium avahi-daemon[3101]: Joining mDNS multicast group on interface wlan0.IPv4 with address <masked_address>.
Jun 19 08:29:51 Vanadium avahi-daemon[3101]: New relevant interface wlan0.IPv4 for mDNS.
Jun 19 08:29:51 Vanadium avahi-daemon[3101]: Network interface enumeration completed.
Jun 19 08:29:51 Vanadium avahi-daemon[3101]: Registering new address record for <masked_address> on wlan0.*.
Jun 19 08:29:51 Vanadium avahi-daemon[3101]: Registering new address record for <masked_address> on wlan0.IPv4.
Jun 19 08:29:51 Vanadium avahi-daemon[3101]: Registering HINFO record with values 'X86_64'/'LINUX'.
Jun 19 08:29:51 Vanadium NetworkManager[2875]: <info> WiFi hardware radio set enabled
Jun 19 08:29:51 Vanadium avahi-daemon[3101]: Server startup complete. Host name is Vanadium.local. Local service cookie is 1245676608.
Jun 19 08:29:56 Vanadium whoopsie[1299]: offline
Jun 19 08:30:00 Vanadium kernel: [ 2920.116879] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
Jun 19 08:30:00 Vanadium kernel: [ 2920.276787] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
Jun 19 08:30:00 Vanadium kernel: [ 2920.436765] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
Jun 19 08:30:00 Vanadium wpa_supplicant[1308]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jun 19 08:30:00 Vanadium kernel: [ 2920.596674] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
Jun 19 08:30:03 Vanadium kernel: [ 2923.695581] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
Jun 19 08:30:36 Vanadium ntpdate[3011]: Can't find host ntp.ubuntu.com: Name or service not known (-2)
Jun 19 08:30:36 Vanadium ntpdate[3011]: no servers can be used, exiting
Jun 19 08:30:43 Vanadium kernel: [ 2963.101304] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
Jun 19 08:30:43 Vanadium kernel: [ 2963.261257] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
Jun 19 08:30:43 Vanadium kernel: [ 2963.421198] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
Jun 19 08:30:43 Vanadium kernel: [ 2963.581140] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
Jun 19 08:30:43 Vanadium kernel: [ 2963.949004] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
Jun 19 08:30:44 Vanadium kernel: [ 2964.108948] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
Jun 19 08:30:44 Vanadium kernel: [ 2964.268884] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
Jun 19 08:31:46 Vanadium kernel: [ 3026.074471] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
Jun 19 08:31:46 Vanadium kernel: [ 3026.234448] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
Jun 19 08:31:46 Vanadium kernel: [ 3026.394389] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
Jun 19 08:31:46 Vanadium kernel: [ 3026.554351] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
Jun 19 08:31:47 Vanadium kernel: [ 3027.561941] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
Jun 19 08:31:47 Vanadium kernel: [ 3027.721914] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
Jun 19 08:33:09 Vanadium kernel: [ 3109.048462] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
Jun 19 08:33:09 Vanadium kernel: [ 3109.208402] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
Jun 19 08:33:09 Vanadium kernel: [ 3109.368326] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
Jun 19 08:33:09 Vanadium kernel: [ 3109.528238] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush2875]: <info>   gateway <masked_address>
Jun 19 08:29:39 Vanadium NetworkManager[2875]: <info>   nameserver '<masked_address>'
Jun 19 08:29:39 Vanadium NetworkManager[2875]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Jun 19 08:29:39 Vanadium NetworkManager[2875]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) started...
Jun 19 08:29:39 Vanadium avahi-daemon[950]: Joining mDNS multicast group on interface wlan0.IPv4 with address <masked_address>.
Jun 19 08:29:39 Vanadium avahi-daemon[950]: New relevant interface wlan0.IPv4 for mDNS.
Jun 19 08:29:39 Vanadium avahi-daemon[950]: Registering new address record for <masked_address> on wlan0.IPv4.
Jun 19 08:29:40 Vanadium NetworkManager[2875]: <info> (wlan0): device state change: ip-config -> secondaries (reason 'none') [70 90 0]
Jun 19 08:29:40 Vanadium NetworkManager[2875]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) complete.
Jun 19 08:29:40 Vanadium NetworkManager[2875]: <info> (wlan0): device state change: secondaries -> activated (reason 'none') [90 100 0]
Jun 19 08:29:40 Vanadium NetworkManager[2875]: <info> NetworkManager state is now CONNECTED_GLOBAL
Jun 19 08:29:40 Vanadium NetworkManager[2875]: <info> Policy set 'Ex Mente' (wlan0) as default for IPv4 routing and DNS.
Jun 19 08:29:40 Vanadium NetworkManager[2875]: <info> DNS: starting dnsmasq...
Jun 19 08:29:40 Vanadium NetworkManager[2875]: <warn> dnsmasq not available on the bus, can't update servers.
Jun 19 08:29:40 Vanadium NetworkManager[2875]: <error> [1434695380.781783] [nm-dns-dnsmasq.c:396] update(): dnsmasq owner not found on bus: Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq': no such name
Jun 19 08:29:40 Vanadium NetworkManager[2875]: <warn> DNS: plugin dnsmasq update failed
Jun 19 08:29:40 Vanadium NetworkManager[2875]: <info> Writing DNS information to /sbin/resolvconf
Jun 19 08:29:40 Vanadium dnsmasq[2887]: started, version 2.68 cache disabled
Jun 19 08:29:40 Vanadium dnsmasq[2887]: compile time options: IPv6 GNU-getopt DBus i18n IDN DHCP DHCPv6 no-Lua TFTP conntrack ipset auth
Jun 19 08:29:40 Vanadium dnsmasq[2887]: DBus support enabled: connected to system bus
Jun 19 08:29:40 Vanadium dnsmasq[2887]: warning: no upstream servers configured
Jun 19 08:29:40 Vanadium avahi-daemon[950]: Got SIGTERM, quitting.
Jun 19 08:29:40 Vanadium avahi-daemon[950]: Leaving mDNS multicast group on interface wlan0.IPv4 with address <masked_address>.
Jun 19 08:29:40 Vanadium avahi-daemon[950]: avahi-daemon 0.6.31 exiting.
Jun 19 08:29:40 Vanadium avahi: Avahi detected that your currently configured local DNS server serves
Jun 19 08:29:40 Vanadium avahi: a domain .local. This is inherently incompatible with Avahi and thus
Jun 19 08:29:40 Vanadium avahi: Avahi disabled itself. If you want to use Avahi in this network, please
Jun 19 08:29:40 Vanadium avahi: contact your administrator and convince him to use a different DNS domain,
Jun 19 08:29:40 Vanadium avahi: since .local should be used exclusively for Zeroconf technology.
Jun 19 08:29:40 Vanadium avahi: For more information, see http://avahi.org/wiki/AvahiAndUnicastDotLocal
Jun 19 08:29:40 Vanadium NetworkManager[2875]: <info> Activation (wlan0) successful, device activated.
Jun 19 08:29:40 Vanadium NetworkManager[2875]: <warn> dnsmasq appeared on DBus: :1.118
Jun 19 08:29:40 Vanadium NetworkManager[2875]: <info> Writing DNS information to /sbin/resolvconf
Jun 19 08:29:40 Vanadium dnsmasq[2887]: setting upstream servers from DBus
Jun 19 08:29:40 Vanadium dnsmasq[2887]: using nameserver <masked_address>#53
Jun 19 08:29:40 Vanadium dnsmasq[2887]: using nameserver <masked_address>#53
Jun 19 08:29:40 Vanadium dnsmasq[2887]: using nameserver <masked_address>#53
Jun 19 08:29:51 Vanadium avahi-daemon[3101]: Found user 'avahi' (UID 111) and group 'avahi' (GID 117).
Jun 19 08:29:51 Vanadium avahi-daemon[3101]: Successfully dropped root privileges.
Jun 19 08:29:51 Vanadium avahi-daemon[3101]: avahi-daemon 0.6.31 starting up.
Jun 19 08:29:51 Vanadium dbus[848]: [system] Successfully activated service 'org.freedesktop.Avahi'
Jun 19 08:29:51 Vanadium avahi-daemon[3101]: Successfully called chroot().
Jun 19 08:29:51 Vanadium avahi-daemon[3101]: Successfully dropped remaining capabilities.
Jun 19 08:29:51 Vanadium avahi-daemon[3101]: No service file found in /etc/avahi/services.
Jun 19 08:29:51 Vanadium avahi-daemon[3101]: *** WARNING: Detected another IPv4 mDNS stack running on this host. This makes mDNS unreliable and is thus not recommended. ***
Jun 19 08:29:51 Vanadium avahi-daemon[3101]: Joining mDNS multicast group on interface wlan0.IPv6 with address <masked_address>.
Jun 19 08:29:51 Vanadium avahi-daemon[3101]: New relevant interface wlan0.IPv6 for mDNS.
Jun 19 08:29:51 Vanadium avahi-daemon[3101]: Joining mDNS multicast group on interface wlan0.IPv4 with address <masked_address>.
Jun 19 08:29:51 Vanadium avahi-daemon[3101]: New relevant interface wlan0.IPv4 for mDNS.
Jun 19 08:29:51 Vanadium avahi-daemon[3101]: Network interface enumeration completed.
Jun 19 08:29:51 Vanadium avahi-daemon[3101]: Registering new address record for <masked_address> on wlan0.*.
Jun 19 08:29:51 Vanadium avahi-daemon[3101]: Registering new address record for <masked_address> on wlan0.IPv4.
Jun 19 08:29:51 Vanadium avahi-daemon[3101]: Registering HINFO record with values 'X86_64'/'LINUX'.
Jun 19 08:29:51 Vanadium NetworkManager[2875]: <info> WiFi hardware radio set enabled
Jun 19 08:29:51 Vanadium avahi-daemon[3101]: Server startup complete. Host name is Vanadium.local. Local service cookie is 1245676608.
Jun 19 08:29:56 Vanadium whoopsie[1299]: offline
Jun 19 08:30:00 Vanadium kernel: [ 2920.116879] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
Jun 19 08:30:00 Vanadium kernel: [ 2920.276787] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
Jun 19 08:30:00 Vanadium kernel: [ 2920.436765] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
Jun 19 08:30:00 Vanadium wpa_supplicant[1308]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jun 19 08:30:00 Vanadium kernel: [ 2920.596674] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
Jun 19 08:30:03 Vanadium kernel: [ 2923.695581] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
Jun 19 08:30:36 Vanadium ntpdate[3011]: Can't find host ntp.ubuntu.com: Name or service not known (-2)
Jun 19 08:30:36 Vanadium ntpdate[3011]: no servers can be used, exiting
Jun 19 08:30:43 Vanadium kernel: [ 2963.101304] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
Jun 19 08:30:43 Vanadium kernel: [ 2963.261257] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
Jun 19 08:30:43 Vanadium kernel: [ 2963.421198] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
Jun 19 08:30:43 Vanadium kernel: [ 2963.581140] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
Jun 19 08:30:43 Vanadium kernel: [ 2963.949004] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
Jun 19 08:30:44 Vanadium kernel: [ 2964.108948] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
Jun 19 08:30:44 Vanadium kernel: [ 2964.268884] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
Jun 19 08:31:46 Vanadium kernel: [ 3026.074471] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
Jun 19 08:31:46 Vanadium kernel: [ 3026.234448] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
Jun 19 08:31:46 Vanadium kernel: [ 3026.394389] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
Jun 19 08:31:46 Vanadium kernel: [ 3026.554351] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
Jun 19 08:31:47 Vanadium kernel: [ 3027.561941] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
Jun 19 08:31:47 Vanadium kernel: [ 3027.721914] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
Jun 19 08:33:09 Vanadium kernel: [ 3109.048462] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
Jun 19 08:33:09 Vanadium kernel: [ 3109.208402] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
Jun 19 08:33:09 Vanadium kernel: [ 3109.368326] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
Jun 19 08:33:09 Vanadium kernel: [ 3109.528238] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush

```



I tried to set the nohwcrypt as well, but had no success:


```
sudo modprobe -rv rt2800pci
sudo modprobe -v rt2800pci nohwcrypt=Y

```

It leaves my wireless unable to connect.

---

