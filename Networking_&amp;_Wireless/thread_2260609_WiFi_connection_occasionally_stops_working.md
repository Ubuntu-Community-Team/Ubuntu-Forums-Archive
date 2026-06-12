---
title: "WiFi connection occasionally stops working"
date: 2015-01-13
forum: Networking &amp; Wireless
---

### Post by Ratatwisker on 2015-01-13
Hi,

for a long time now the WiFi adapter of my TinkPad E525 is giving me connectioon problems using Xubuntu & friends (didn't check any other operating system). I cannot say for sure if the problem was there from the beginning or started to show up at some point. Usually there is no problem connecting to different wireless networks (I use three different ones), but from time to time there is no data transfer possible for about a minute or so. During this time no connection loss is displayed. However, I sometimes notice the signal quality is very unsteady, so maybe the antenna is not in order?

Until recently I blamed the networks itself, i.e. the routers being too far away, buggy or whatever, but eventually I figured out my computer is the culprit here. So during my research to resolve the problem I found [this post]("http://ubuntuforums.org/showthread.php?p=12815912#post12815912") and tried the suggestions found there. However, all it does is that I cannot connect to the network at all, no matter which of the combinations of module parameters I use. Even resetting the parameters to the default values does not help. I can see via the network manager that the network is available, but after some time trying to connect the network manager gives up. Only way to get the WiFi working again I found so far is rebooting.

Here is the output of the wireless_script with some names and other sensitive information edited out by me:
```

    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

3.16.0-29-generic x86_64,  Ubuntu 14.10, utopic

CPU    : AMD A8-3500M APU with Radeon(tm) HD Graphics
Memory : 7453 MB
Uptime : 14:52:42 up 6 min,  2 users,  load average: 0,08, 0,23, 0,14


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
    Subsystem: Lenovo Device [17aa:21ea]
    Kernel driver in use: r8169
--
05:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:8195]
    Kernel driver in use: rtl8192ce


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 046d:c05a Logitech, Inc. M90/M100 Optical Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11bgn  ESSID: <cut>
          Mode:Managed  Frequency:2.462 GHz  Access Point: <cut>
          Bit Rate=18 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=57/70  Signal level=-53 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:4   Missed beacon:0



rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface                    Soft blocked  Hard blocked
0: tpacpi_bluetooth_sw: Bluetooth      yes           no
1: phy0: Wireless LAN                  no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

rtl8192ce              53509  0 
rtl_pci                26674  1 rtl8192ce
rtlwifi                64237  2 rtl_pci,rtl8192ce
rtl8192c_common        53170  1 rtl8192ce
mac80211              660592  3 rtl_pci,rtlwifi,rtl8192ce
cfg80211              510218  2 mac80211,rtlwifi


module parameters ~~~~~~~~~~~~~~~~~~

cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
rtl8192ce     (5): debug=0 | fwlps=Y | ips=Y | swenc=N | swlps=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
=================o=============o===========o=============o=========o===========o==============o===========
 Interface & ID  | Type        | Driver    | State       | Default | Speed     | Support      | HW Addr   
=================o=============o===========o=============o=========o===========o==============o===========
 wlan0  [xxxxxx] | 802.11 WiFi | rtl8192ce | connected   | yes     | 18 Mb/s   | WEP/WPA/WPA2 | <MAC wlan0>

    <cut>

-----------------+-------------+-----------+-------------+---------+-----------+--------------+-----------
 eth0            | Wired       | r8169     | unavailable | no      |           |              | <MAC eth0>
-----------------+-------------+-----------+-------------+---------+-----------+--------------+-----------


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

no-auto-default=<MAC eth0>,

[ifupdown]
managed=false


NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~

<cut>

interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 127.0.1.1
search <cut>


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

<cut>

iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "de_DE.UTF-8")
country DE: DFS-UNSET
    (2400 - 2483 @ 40), (N/A, 20)
    (5150 - 5250 @ 40), (N/A, 20), NO-OUTDOOR
    (5250 - 5350 @ 40), (N/A, 20), NO-OUTDOOR, DFS
    (5470 - 5725 @ 40), (N/A, 26), DFS
    (57240 - 65880 @ 2160), (N/A, 40), NO-OUTDOOR


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     13 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 13 (2.472 GHz)

          Current Frequency:2.462 GHz (Channel 11)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

<cut>

blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[rtl8192ce]
filename:       /lib/modules/3.16.0-29-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko
firmware:       rtlwifi/rtl8192cfwU_B.bin
firmware:       rtlwifi/rtl8192cfwU.bin
firmware:       rtlwifi/rtl8192cfw.bin
srcversion:     BE372FB24A1F38A5218DAA0
depends:        rtlwifi,rtl_pci,rtl8192c-common,mac80211
parm:           swenc:Set to 1 for software crypto (default 0)
parm:           ips:Set to 0 to not use link power save (default 1)
parm:           swlps:Set to 1 to use SW control power save (default 0)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
parm:           debug:Set debug level (0-5) (default 0) (int)

[rtl_pci]
filename:       /lib/modules/3.16.0-29-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
srcversion:     3273ECD6028617EFD27E4F4
depends:        mac80211,rtlwifi

[rtlwifi]
filename:       /lib/modules/3.16.0-29-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
srcversion:     8362106E96F806A9DBAE565
depends:        mac80211,cfg80211

[rtl8192c_common]
filename:       /lib/modules/3.16.0-29-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192c/rtl8192c-common.ko
srcversion:     A279C50E29ED7F277EAF738
depends:        

[mac80211]
filename:       /lib/modules/3.16.0-29-generic/kernel/net/mac80211/mac80211.ko
srcversion:     B3A65EB1DAE59CB6B5FD971
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.16.0-29-generic/kernel/net/wireless/cfg80211.ko
srcversion:     DEE8EAA48495E392CD51C2D
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x10ec:0x8176 (rtl8192ce)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

# USB device 0x:0x (rtl8192cu)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan1>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"


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


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/boot/vmlinuz-3.16.0-29-generic root=UUID=<cut> ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    0.026544] Initializing cgroup subsys net_cls
[    0.026562] Initializing cgroup subsys net_prio
[    1.027052] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    1.027721] audit: initializing netlink subsys (disabled)
[    1.357162] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    7.735718] thinkpad_acpi: http://ibm-acpi.sf.net/
[    7.739003] thinkpad_acpi: Unsupported brightness interface, please contact ibm-acpi-devel@lists.sourceforge.net
[    8.042778] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    8.042940] rtl8192ce: Using firmware rtlwifi/rtl8192cfw.bin
[    8.065643] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[    8.066069] rtlwifi: wireless switch is on
[    8.869586] psmouse serio2: trackpoint: IBM TrackPoint firmware: 0x0e, buttons: 3/3
[    9.543453] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   18.192786] wlan0: authenticate with <cut>
[   18.203025] wlan0: send auth to <cut> (try 1/3)
[   18.204946] wlan0: authenticated
[   18.205244] rtl8192ce 0000:05:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   18.205249] rtl8192ce 0000:05:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   18.208060] wlan0: associate with <cut> (try 1/3)
[   18.210970] wlan0: RX AssocResp from <cut> (capab=0x431 status=0 aid=1)
[   18.211110] wlan0: associated
[   18.211150] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   62.376835] wlan0: authenticate with <cut>
[   62.387049] wlan0: send auth to <cut> (try 1/3)
[   62.488112] wlan0: send auth to <cut> (try 2/3)
[   62.592034] wlan0: send auth to <cut> (try 3/3)
[   62.594328] wlan0: authenticated
[   62.594672] rtl8192ce 0000:05:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   62.594682] rtl8192ce 0000:05:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   62.596104] wlan0: associate with <cut> (try 1/3)
[   62.599395] wlan0: RX AssocResp from <cut> (capab=0x431 status=0 aid=49)
[   62.599538] wlan0: associated
[   79.683351] wlan0: Connection to AP <cut> lost
[   80.228965] wlan0: authenticate with <cut>
[   80.248705] wlan0: send auth to <cut> (try 1/3)
[   80.250126] wlan0: authenticated
[   80.250312] rtl8192ce 0000:05:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   80.250316] rtl8192ce 0000:05:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   80.252100] wlan0: associate with <cut> (try 1/3)
[   80.255178] wlan0: RX AssocResp from <cut> (capab=0x431 status=0 aid=1)
[   80.255327] wlan0: associated

    ======== Done ========
```

I visited the Realtek site to see the driver posted there is a little dated, so I don't know if that could improve my connection's durability. Any suggestions? Any information missing?

---

