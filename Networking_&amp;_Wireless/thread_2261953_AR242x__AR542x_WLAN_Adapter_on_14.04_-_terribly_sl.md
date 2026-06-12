---
title: "AR242x / AR542x WLAN Adapter on 14.04 - terribly slow, high ping, dropping bitrate"
date: 2015-01-22
forum: Networking &amp; Wireless
---

### Post by wripet on 2015-01-22
Hi everybody,

I am using the Qualcomm Atheros AR242x / AR542x Wireless Network Adapter on Ubuntu 14.04, and after the last dist-upgrade including a kernel upgrade, WLAN still works, but painfully slow, the ping is unbearably high - even when pinging the WLAN router. I recognized that the bitrate is at 54M at first, but keeps constantly dropping until it reaches something around 8M.

Here is all the information about setup:

```



    ======== Wireless-Info START ========


System-Info ~~~~~~~~~~~~~~~~~~~~~~~~


htpc 3.13.0-44-generic x86_64,  Ubuntu 14.04.1 LTS, trusty


CPU    : Intel(R) Atom(TM) CPU  330   @ 1.60GHz
Memory : 1749 MB
Uptime : 12:07:02 up 9 min,  2 users,  load average: 0.50, 0.79, 0.54




lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


00:0a.0 Ethernet controller [0200]: NVIDIA Corporation MCP79 Ethernet [10de:0ab0] (rev b1)
    Subsystem: Acer Incorporated [ALI] Device [1025:0222]
    Kernel driver in use: forcedeth
--
05:00.0 Ethernet controller [0200]: Qualcomm Atheros AR242x / AR542x Wireless Network Adapter (PCI-Express) [168c:001c] (rev 01)
    Subsystem: Foxconn International, Inc. Device [105b:e008]
    Kernel driver in use: ath5k




lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


Bus 001 Device 004: ID 0ccd:00ab TerraTec Electronic GmbH 
Bus 001 Device 003: ID 1058:1021 Western Digital Technologies, Inc. Elements 2TB
Bus 001 Device 002: ID 1058:1021 Western Digital Technologies, Inc. Elements 2TB
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub




PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~






iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     IEEE 802.11bg  ESSID:"fritz.box"  
          Mode:Managed  Frequency:2.447 GHz  Access Point: <MAC C-01 fritz.box>   
          Bit Rate=48 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=35/70  Signal level=-75 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:36  Invalid misc:155   Missed beacon:0






rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~








lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


ath5k                 149924  0 
ath                    28698  1 ath5k
mac80211              630669  1 ath5k
cfg80211              484040  3 ath,ath5k,mac80211
wmi                    19177  0 




module parameters ~~~~~~~~~~~~~~~~~~


ath5k         (3): fastchanswitch=N | nohwcrypt=Y | no_hw_rfkill_switch=N
cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
wmi           (2): debug_dump_wdg=N | debug_event=N




nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~




================o======o========o========o=========o===========o==============o===========
 Interface & ID | Type | Driver | State  | Default | Speed     | Support      | HW Addr   
================o======o========o========o=========o===========o==============o===========
                |      |        |        |         |           |              |           
----------------+------+--------+--------+---------+-----------+--------------+-----------




NetworkManager.state ~~~~~~~~~~~~~~~




NetworkManager.conf ~~~~~~~~~~~~~~~~






NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~
 




interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~


# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).


# The loopback network interface
auto lo
iface lo inet loopback


auto eth0
iface eth0 inet static
    address 192.168.2.1


auto wlan0
iface wlan0 inet static
    address 192.168.178.2
    gateway 192.168.178.1
    netmask 255.255.255.0
    wpa-conf /etc/wpa_supplicant/wpa_supplicant.conf


resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~


nameserver 127.0.0.1
nameserver 192.168.178.1




Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.178.1   0.0.0.0         UG    0      0        0 wlan0
192.168.2.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.178.0   0.0.0.0         255.255.255.0   U     0      0        0 wlan0


--- 192.168.178.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 2.076/6.236/10.397/4.161 ms


--- 127.0.0.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.067/0.067/0.067/0.000 ms


--- 192.168.178.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1002ms
rtt min/avg/max/mdev = 1.020/3.927/6.835/2.908 ms




iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~


(Region : "en_US.UTF-8")
country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS




iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     13 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 13 (2.472 GHz)


          Current Frequency:2.447 GHz (Channel 8)




iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 fritz.box>
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"fritz.box"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000029b191e3f
                    Extra: Last beacon: 4ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC C-02 suppafunk>
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"suppafunk"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001c92a1ff183
                    Extra: Last beacon: 88ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK




blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci




modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


[ath5k]
filename:       /lib/modules/3.13.0-44-generic/kernel/drivers/net/wireless/ath/ath5k/ath5k.ko
srcversion:     F36818A2F0BCB2B0CC9BB8C
depends:        mac80211,cfg80211,ath
parm:           nohwcrypt:Disable hardware encryption. (bool)
parm:           fastchanswitch:Enable fast channel switching for AR2413/AR5413 radios. (bool)
parm:           no_hw_rfkill_switch:Ignore the GPIO RFKill switch state (bool)


[ath]
filename:       /lib/modules/3.13.0-44-generic/kernel/drivers/net/wireless/ath/ath.ko
srcversion:     88A67C5359B02C5A710AFCF
depends:        cfg80211


[mac80211]
filename:       /lib/modules/3.13.0-44-generic/kernel/net/mac80211/mac80211.ko
srcversion:     385697223F8285F67C93A06
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/3.13.0-44-generic/kernel/net/wireless/cfg80211.ko
srcversion:     C2478077E22138832B71659
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


[wmi]
filename:       /lib/modules/3.13.0-44-generic/kernel/drivers/platform/x86/wmi.ko
srcversion:     CED5410F008DC70DF5F064B
depends:        
parm:           debug_event:Log WMI Events [0/1] (bool)
parm:           debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)




udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~


# PCI device 0x10de:0x0ab0 (forcedeth)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x168c:0x001c (ath5k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"




Custom files/entries ~~~~~~~~~~~~~~~


/etc/modules        : Default
/etc/rc.local       : Not Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Default


[/etc/rc.local]
fstrim -v /
exit 0


[/etc/modprobe.d]
ath5k.conf        : options ath5k nohwcrypt=1
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
                    options iwlwifi 11n_disable=1
mlx4.conf         : softdep mlx4_core post: mlx4_en




Kernel boot line ~~~~~~~~~~~~~~~~~~~


BOOT_IMAGE=/boot/vmlinuz-3.13.0-44-generic root=UUID=912f5f8b-227f-4cdf-b467-427c016b0d95 ro noplymouth




dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


[    0.534523] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.535637] audit: initializing netlink socket (disabled)
[    2.888986] wmi: Mapper loaded
[    3.103355] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    3.381999] ath5k 0000:05:00.0: can't disable ASPM; OS doesn't have ASPM control
[    3.393367] ath5k 0000:05:00.0: registered as 'phy0'
[    4.373812] ath: EEPROM regdomain: 0x65
[    4.373821] ath: EEPROM indicates we should expect a direct regpair map
[    4.373828] ath: Country alpha2 being used: 00
[    4.373832] ath: Regpair used: 0x65
[    4.391750] ath5k: phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[    4.525190] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    5.513190] wlan0: authenticate with <MAC C-01 fritz.box>
[    5.520700] wlan0: send auth to <MAC C-01 fritz.box> (try 1/3)
[    5.522559] wlan0: authenticated
[    5.524082] wlan0: associate with <MAC C-01 fritz.box> (try 1/3)
[    5.526794] wlan0: RX AssocResp from <MAC C-01 fritz.box> (capab=0x431 status=0 aid=1)
[    5.527409] wlan0: associated
[    5.527440] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready


    ======== Done ========



```

---

