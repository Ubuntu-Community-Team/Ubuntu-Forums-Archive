---
title: "Unstable wifi on Ubuntu 14.04"
date: 2014-09-30
forum: Networking &amp; Wireless
---

### Post by saulspatz on 2014-09-30
I installed Ubuntu 14.04 yesterday, and the Wifi connection is unstable.  It shows as connected, but I can't access the internet.  This happens every few minutes.  The fix I have found is to manually disconnect the wifi, and then connect it again.  I have found various suggestions in the forums, but I know nothing at all about wifi, and I'm afraid of screwing things up worse.  The output from the wireless script is given below.  I would really appreciate your help.


```


    ======== Wireless-Info START ========


System-Info ~~~~~~~~~~~~~~~~~~~~~~~~


Banach 3.13.0-36-generic x86_64,  Ubuntu 14.04.1 LTS, trusty


CPU    : Intel(R) Core(TM) i3 CPU       M 380  @ 2.53GHz
Memory : 3753 MB
Uptime : 11:09:52 up 17:40,  2 users,  load average: 0.29, 0.27, 0.29




lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


05:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
    Subsystem: Broadcom Corporation Device [14e4:0510]
    Kernel driver in use: wl
06:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
    Subsystem: Lenovo Device [17aa:392e]
    Kernel driver in use: r8169




lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


Bus 002 Device 004: ID 046d:c534 Logitech, Inc. 
Bus 002 Device 003: ID 04f2:b1c1 Chicony Electronics Co., Ltd 
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0489:e00d Foxconn / Hon Hai Broadcom Bluetooth 2.1 Device
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub




PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~






iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     IEEE 802.11abg  ESSID:"Yenta"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC C-01 Yenta>   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          




rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


      Interface                  Soft blocked  Hard blocked
0: ideapad_wlan: Wireless LAN        no            no
1: phy0: Wireless LAN                no            no
2: ideapad_bluetooth: Bluetooth      no            no
3: brcmwl-0: Wireless LAN            no            no
4: hci0: Bluetooth                   no            no




lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


wl                   4207846  0 
lib80211               14381  2 wl,lib80211_crypt_tkip
cfg80211              484040  1 wl
wmi                    19177  0 




module parameters ~~~~~~~~~~~~~~~~~~


cfg80211      (2): 
wmi           (2): 




nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


State: connected (global)
================o=============o========o=============o=========o===========o==============o===========
 Interface & ID | Type        | Driver | State       | Default | Speed     | Support      | HW Addr   
================o=============o========o=============o=========o===========o==============o===========
 eth0           | Wired       | r8169  | unavailable | no      |           |              | <MAC eth0>
----------------+-------------+--------+-------------+---------+-----------+--------------+-----------
 wlan0  [Yenta] | 802.11 WiFi | wl     | connected   | yes     | 54 Mb/s   | WEP/WPA/WPA2 | <MAC wlan0>


    Pearliehayes1:   Infra, <MAC C-05 Pearliehayes1>, Freq 2452 MHz, Rate 54 Mb/s, Strength 92 WPA2
    bissodrekc:      Infra, <MAC C-08 bissodrekc>, Freq 2412 MHz, Rate 54 Mb/s, Strength 70 WPA2
    *Yenta:          Infra, <MAC C-01 Yenta>, Freq 2437 MHz, Rate 54 Mb/s, Strength 96 WPA
    DG860A02:        Infra, <MAC C-09 DG860A02>, Freq 2412 MHz, Rate 54 Mb/s, Strength 15 WPA2
    dlink:           Infra, <MAC C-06 dlink>, Freq 2452 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2
    rosses2:         Infra, <MAC C-03 rosses2>, Freq 2437 MHz, Rate 54 Mb/s, Strength 57 WPA2
    Alberto's Wi-Fi Network: Infra, <MAC C-NA Alberto's Wi-Fi Network 1>, Freq 2437 MHz, Rate 54 Mb/s, Strength 35 WPA2
    DG860A22:        Infra, <MAC C-07 DG860A22>, Freq 2462 MHz, Rate 54 Mb/s, Strength 32 WPA2
    ATT942:          Infra, <MAC C-NA ATT942 1>, Freq 2462 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2


    Address:         192.168.0.100
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1
    DNS:             209.18.47.61
    DNS:             209.18.47.62
----------------+-------------+--------+-------------+---------+-----------+--------------+-----------




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


2WIRE526             : ssid=2WIRE526 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Apple Network c1d0c0 : ssid=Apple Network c1d0c0 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
attwifi              : ssid=attwifi | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
Beta                 : ssid=Beta | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Beta 1               : ssid=Beta | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
EV_2_4_Guest         : ssid=EV_2_4_Guest | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Ingenology           : ssid=Ingenology | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
MJshop               : ssid=MJshop | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Scooter's Coffee & Yogurt : ssid=Scooter's Coffee & Yogurt | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
TBP-4                : ssid=TBP-4 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
UMKClegacy           : ssid=UMKClegacy | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
Yenta                : ssid=Yenta | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 




interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~


auto lo
iface lo inet loopback




resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~


nameserver 127.0.1.1




Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0


--- 192.168.0.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 1.012/1.344/1.676/0.332 ms


--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.040/0.042/0.044/0.002 ms




iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~


(Region : "en_US.UTF-8")
country CN:
    (2402 - 2482 @ 40), (N/A, 20)
    (5735 - 5835 @ 40), (N/A, 30)
    (57240 - 59400 @ 2160), (N/A, 28)
    (59400 - 63720 @ 2160), (N/A, 44)
    (63720 - 65880 @ 2160), (N/A, 28)




iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     18 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 13 (2.472 GHz)
          Channel 149 (5.745 GHz)
          Channel 153 (5.765 GHz)
          Channel 157 (5.785 GHz)
          Channel 161 (5.805 GHz)
          Channel 165 (5.825 GHz)


          Current Frequency:2.437 GHz (Channel 6)




iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 Yenta>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-24 dBm  
                    Encryption key:on
                    ESSID:"Yenta"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 60ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC C-02 rosses2>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=49/70  Signal level=-61 dBm  
                    Encryption key:on
                    ESSID:"rosses2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 60ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC C-03 rosses2>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"rosses2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 60ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC C-04 ATT077>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"ATT077"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 60ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC C-05 Pearliehayes1>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=59/70  Signal level=-51 dBm  
                    Encryption key:on
                    ESSID:"Pearliehayes1"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 60ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC C-06 dlink>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"dlink"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 60ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC C-07 DG860A22>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"DG860A22"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 60ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC C-08 bissodrekc>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:"bissodrekc"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 60ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC C-09 DG860A02>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"DG860A02"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 60ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK




blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


[/etc/modprobe.d/blacklist-bcm43.conf]
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist brcm80211
blacklist brcmfmac
blacklist brcmsmac
blacklist bcma


[/etc/modprobe.d/osspd.conf]
blacklist snd-pcm-oss
blacklist snd-mixer-oss
blacklist snd-seq-oss




modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


[wl]
filename:       /lib/modules/3.13.0-36-generic/updates/dkms/wl.ko
srcversion:     FF25FE784DC6BDFF69DAFCB
depends:        cfg80211,lib80211
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string


[lib80211]
filename:       /lib/modules/3.13.0-36-generic/kernel/net/wireless/lib80211.ko
srcversion:     84DEF767F03D28E373F18E5
depends:        


[cfg80211]
filename:       /lib/modules/3.13.0-36-generic/kernel/net/wireless/cfg80211.ko
srcversion:     C2478077E22138832B71659
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


[wmi]
filename:       /lib/modules/3.13.0-36-generic/kernel/drivers/platform/x86/wmi.ko
srcversion:     CED5410F008DC70DF5F064B
depends:        
parm:           debug_event:Log WMI Events [0/1] (bool)
parm:           debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)




udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~


# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.2/0000:06:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.1/0000:05:00.0/bcma0:0 (bcma-pci-bridge)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.1/0000:05:00.0 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"


# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.1/0000:05:00.0 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth2"




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


BOOT_IMAGE=/boot/vmlinuz-3.13.0-36-generic root=UUID=70fb2985-655c-4463-8a29-9fee5bb1ec1f ro quiet splash vt.handoff=7




dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


[    0.941592] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.941998] audit: initializing netlink socket (disabled)
[    1.466107] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    2.618971] psmouse serio1: elantech: assuming hardware version 2 (with firmware version 0x140000)
[   23.266634] wmi: Mapper loaded
[   23.327940] wl: module license 'MIXED/Proprietary' taints kernel.
[   23.331089] wl: module verification failed: signature and/or  required key missing - tainting kernel
[   23.373271] INFO @wl_cfg80211_attach : Registered CFG80211 phy
[   23.458238] wlan0: Broadcom BCM4727 802.11 Hybrid Wireless Controller 6.30.223.141 (r415941)
[   32.461073] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[60932.277259] ERROR @wl_dev_intvar_get : error (-1)
[60932.277269] ERROR @wl_cfg80211_get_tx_power : error (-1)
[63607.177708] ERROR @wl_dev_intvar_get : error (-1)
[63607.177714] ERROR @wl_cfg80211_get_tx_power : error (-1)


    ======== Done ========

```

---

### Post by varunendra on 2014-10-01
Please always use 'Code' tags to post terminal outputs or codes whose formatting is important. Please follow the "Use Code Tags" link in my signature to see how. You can then edit your above post to check out the difference yourself.

Regarding the problem, please purge the proprietary driver by running the following command in terminal (can be opened with Ctrl-Alt-T) -
```
sudo apt-get purge bcmwl-kernel-source
```
..followed by a reboot. Better now?

---

### Post by saulspatz on 2014-10-01
That seems to have fixed it.  It's been running for an hour without dropping the WiFi.  Thanks so much.

---

### Post by varunendra on 2014-10-01
You're welcome!

Be sure to NOT install the driver that the "Additional Driver" program may offer you for your wireless card (or 'Any' other driver for that matter). It is supposed to work with your card, but as you saw yourself, it doesn't do it as well as the native one (brcmsmac) that is already available in the kernel and doesn't require you to install anything.

---

