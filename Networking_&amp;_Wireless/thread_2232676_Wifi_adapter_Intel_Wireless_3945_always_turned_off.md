---
title: "Wifi adapter Intel Wireless 3945 always turned off. LED light turned off"
date: 2014-07-03
forum: Networking &amp; Wireless
---

### Post by srinig82 on 2014-07-03
Hi,
I tried all existing forums on ubuntuforums.org but I could not find a solution. My PC is a Toshiba Satellite M105-S3041 and its wireless adapter is Intel Wireless 3945abg adapter. My issue is that the wireless LED never turns ON. It is always off. lshw and ifconfig do not list my adapter in hardware. Please I need help. I had ubuntu 12 installed it a while and that detected the wireless adapter fine but that OS is too slow. The OS is Linux Lite. 

The LED light was ON when I had windows xp and when I opened the OS through USB disk but as soon as I formatted and installed Linux Lite the LED light turned off and the wifi is not detected.

I ran wireless script from the sticky thread and this is the result
```

########## wireless info START ##########

##### release #####

Distributor ID:    Ubuntu
Description:    Linux Lite 2.0
Release:    14.04
Codename:    trusty

##### kernel #####

Linux srini-home 3.13.0-24-generic #47-Ubuntu SMP Fri May 2 23:31:42 UTC 2014 i686 i686 i686 GNU/Linux

##### lspci #####

05:08.0 Ethernet controller [0200]: Intel Corporation PRO/100 VM Network Connection [8086:1093] (rev 02)
    Subsystem: Toshiba America Info Systems Device [1179:ff00]
    Kernel driver in use: e100

##### lsusb #####

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA Card Info #####

##### rfkill #####

##### lsmod #####

iwlegacy               88016  0 
mac80211              545990  1 iwlegacy
cfg80211              409394  2 iwlegacy,mac80211

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

##### route #####

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 eth0
192.168.2.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0

##### resolv.conf #####

nameserver 127.0.0.1

nameserver 192.168.2.1

##### nm-tool #####

##### NetworkManager.state #####

##### NetworkManager.conf #####

##### iwlist #####

##### iwlist channel #####

##### modinfo #####

filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/iwlegacy/iwlegacy.ko
license:        GPL
author:         Copyright(c) 2003-2011 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    iwl-legacy: common functions for 3945 and 4965
srcversion:     400F302BE5C25B3C98A6CE8
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-24-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:A1:7E:EF:58:C6:AC:5E:9A:85:71:2C:92:08:DF
sig_hashalgo:   sha512
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking (int)
parm:           bt_coex_active:enable wifi/bluetooth co-exist (bool)

##### modules #####

lp
lp
iwlegacy

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
blacklist iwlegacy

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

# PCI device 0x8086:0x1093 (e100)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

##### dmesg #####

########## wireless info END ############


```

Thanks in advance,
Srini

---

### Post by praseodym on 2014-07-03
Tried to reset the BIOS to default settings?

---

### Post by srinig82 on 2014-07-04
BIOS is in default setting only. lspci doesn't show the wireless device. also i am absolutely unable to turn on the wifi LED light. it is always off. it was ON when I used the live usb when the system still had windows. now i have erased the windows os and only runs linux lite and LED light never turns on

---

### Post by srinig82 on 2014-07-04
This is the output after I use the latest wireless script. RIght now I am using ralink usb wireless adapter to connect to the net.```

	======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

localhost.localdomain 3.14.9-200.fc20.i686 i686,  

CPU    : Genuine Intel(R) CPU           T1350  @ 1.86GHz
Memory : 1500 MB
Uptime : 18:35:00 up  1:00,  1 user,  load average: 0.73, 0.58, 0.45


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

05:08.0 Ethernet controller [0200]: Intel Corporation PRO/100 VM Network Connection [8086:1093] (rev 02)
	Subsystem: Toshiba America Info Systems Device [1179:ff00]
	Kernel driver in use: e100


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 001 Device 002: ID 148f:2573 Ralink Technology, Corp. RT2501/RT2573 Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~

PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255


iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlp0s29f7u6  IEEE 802.11bg  ESSID:"artvandalay"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC C-01 artvandalay>   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on
          Link Quality=64/70  Signal level=-46 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1103   Missed beacon:0



rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface        Soft blocked  Hard blocked
0: phy0: Wireless LAN      no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

iwl3945                98585  0 
iwlegacy              110164  1 iwl3945
iwlwifi               108894  0 
rt73usb                31157  0 
rt2x00usb              19262  1 rt73usb
rt2x00lib              56555  2 rt73usb,rt2x00usb
mac80211              536316  4 iwl3945,iwlegacy,rt2x00lib,rt2x00usb
cfg80211              435060  5 iwl3945,iwlwifi,iwlegacy,mac80211,rt2x00lib
crc_itu_t              12549  2 rt73usb,firewire_core


module parameters ~~~~~~~~~~~~~~~~~~

cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
iwl3945       (5): antenna=0 | debug=0 | disable_hw_scan=1 | fw_restart=1 | swcrypto=1
iwlegacy      (2): bt_coex_active=N | led_mode=0
iwlwifi      (12): 11n_disable=0 | amsdu_size_8K=0 | antenna_coupling=0 | bt_coex_active=Y | debug=0 | fw_restart=Y | led_mode=0 | nvm_file=(null) | power_level=0 | power_save=N | swcrypto=0 | wd_disable=1
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
rt73usb       (1): nohwcrypt=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


================o======o========o==============o=========o===========o==============o===========
 Interface & ID | Type | Driver | State        | Default | Speed     | Support      | HW Addr   
================o======o========o==============o=========o===========o==============o===========
                |      |        |              |         |           |              |           
----------------+------+--------+--------------+---------+-----------+--------------+-----------


NetworkManager.state ~~~~~~~~~~~~~~~
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


NetworkManager.conf ~~~~~~~~~~~~~~~~

[main]
plugins=ifcfg-rh


NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~
 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~


resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 192.168.2.1


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.2.1     0.0.0.0         UG    1024   0        0 wlp0s29f7u6
192.168.2.0     0.0.0.0         255.255.255.0   U     0      0        0 wlp0s29f7u6

--- 192.168.2.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 12.941/13.431/13.921/0.490 ms

--- 192.168.2.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 1.738/7.773/13.809/6.036 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "en_US.UTF-8")
country IN: DFS-UNSET
	(2402 - 2482 @ 40), (N/A, 20)
	(5170 - 5250 @ 80), (N/A, 20)
	(5250 - 5330 @ 80), (N/A, 20), DFS
	(5735 - 5835 @ 80), (N/A, 20)


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

wlp0s29f7u6  13 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 13 (2.472 GHz)

          Current Frequency:2.462 GHz (Channel 11)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

wlp0s29f7u6  Scan completed :
          Cell 01 - Address: <MAC C-01 artvandalay>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=68/70  Signal level=-42 dBm  
                    Encryption key:off
                    ESSID:"artvandalay"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000005d8849d3f
                    Extra: Last beacon: 51ms ago
          Cell 02 - Address: <MAC C-02 OMNAMASIVA>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:on
                    ESSID:"OMNAMASIVA"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000002ff6e18385
                    Extra: Last beacon: 53ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC C-03 >
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=56/70  Signal level=-54 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000002ff6e1c98c
                    Extra: Last beacon: 3985ms ago
          Cell 04 - Address: <MAC C-04 Sony Xperiaâ&#132;¢ tipo_4110>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"Sony Xperiaâ&#132;¢ tipo_4110"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000004f5389b47
                    Extra: Last beacon: 53ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK


blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist.conf]
blacklist b43


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[iwl3945]
filename:       /lib/modules/3.14.9-200.fc20.i686/kernel/drivers/net/wireless/iwlegacy/iwl3945.ko
firmware:       iwlwifi-3945-2.ucode
version:        in-tree:ds
srcversion:     4E926C85C8DB36AABFD0900
depends:        iwlegacy,cfg80211,mac80211
parm:           antenna:select antenna (1=Main, 2=Aux, default 0 [both]) (int)
parm:           swcrypto:using software crypto (default 1 [software]) (int)
parm:           disable_hw_scan:disable hardware scanning (default 1) (int)
parm:           debug:debug output mask (uint)
parm:           fw_restart:restart firmware in case of error (int)

[iwlegacy]
filename:       /lib/modules/3.14.9-200.fc20.i686/kernel/drivers/net/wireless/iwlegacy/iwlegacy.ko
version:        in-tree:
srcversion:     955170B59A7606EF9485575
depends:        mac80211,cfg80211
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking (int)
parm:           bt_coex_active:enable wifi/bluetooth co-exist (bool)

[iwlwifi]
filename:       /lib/modules/3.14.9-200.fc20.i686/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
version:        in-tree:d
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
firmware:       iwlwifi-7265-7.ucode
firmware:       iwlwifi-3160-7.ucode
firmware:       iwlwifi-7260-7.ucode
srcversion:     F5EF6CB9BD0F7C82F795640
depends:        cfg80211
parm:           debug:debug output mask (uint)
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (defualt: 0 dB) (int)
parm:           wd_disable:Disable stuck queue watchdog timer 0=system default, 1=disable, 2=enable (default: 0) (int)
parm:           nvm_file:NVM file name (charp)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)

[rt73usb]
filename:       /lib/modules/3.14.9-200.fc20.i686/kernel/drivers/net/wireless/rt2x00/rt73usb.ko
firmware:       rt73.bin
version:        2.3.0
srcversion:     2895B54E117EB0356D1E95D
depends:        rt2x00lib,rt2x00usb,crc-itu-t
parm:           nohwcrypt:Disable hardware encryption. (bool)

[rt2x00usb]
filename:       /lib/modules/3.14.9-200.fc20.i686/kernel/drivers/net/wireless/rt2x00/rt2x00usb.ko
version:        2.3.0
srcversion:     44768071492503F8EFE1EED
depends:        rt2x00lib,mac80211

[rt2x00lib]
filename:       /lib/modules/3.14.9-200.fc20.i686/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
version:        2.3.0
srcversion:     5175D5F88811224E27FB78F
depends:        mac80211,cfg80211

[mac80211]
filename:       /lib/modules/3.14.9-200.fc20.i686/kernel/net/mac80211/mac80211.ko
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.14.9-200.fc20.i686/kernel/net/wireless/cfg80211.ko
depends:        rfkill
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[crc_itu_t]
filename:       /lib/modules/3.14.9-200.fc20.i686/kernel/lib/crc-itu-t.ko
depends:        


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~


Custom files/entries ~~~~~~~~~~~~~~~

/etc/modules        : Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Default

[/etc/modprobe.d]
openfwwf.conf     : options b43 nohwcrypt=1 qos=0


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/vmlinuz-3.14.9-200.fc20.i686 root=/dev/mapper/fedora-root ro rd.lvm.lv=fedora/swap vconsole.font=latarcyrheb-sun16 rd.lvm.lv=fedora/root rhgb quiet


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    0.008068] Initializing cgroup subsys net_cls
[    0.698065] audit: initializing netlink subsys (disabled)
[    0.728945] SELinux:  Registering netfilter hooks
[    0.902116] drop_monitor: Initializing network drop monitor service
[    0.902243] Initializing XFRM netlink socket
[    2.033700] systemd-udevd[223]: renamed network interface eth0 to em1
[   12.156388] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[   16.875637] ieee80211 phy0: rt2x00_set_chip: Info - Chipset detected - rt: 2573, rf: 0002, rev: 000a
[   17.502200] systemd-udevd[467]: renamed network interface wlan0 to wlp0s29f7u6
[   31.218210] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file 'rt73.bin'
[   31.280579] ieee80211 phy0: rt2x00lib_request_firmware: Info - Firmware detected - version: 1.7
[   31.382454] IPv6: ADDRCONF(NETDEV_UP): wlp0s29f7u6: link is not ready
[   31.832646] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   79.272719] wlp0s29f7u6: authenticate with <MAC C-01 artvandalay>
[   79.339567] wlp0s29f7u6: send auth to <MAC C-01 artvandalay> (try 1/3)
[   79.345665] wlp0s29f7u6: authenticated
[   79.346668] rt73usb 1-6:1.0 wlp0s29f7u6: disabling HT as WMM/QoS is not supported by the AP
[   79.346678] rt73usb 1-6:1.0 wlp0s29f7u6: disabling VHT as WMM/QoS is not supported by the AP
[   79.349449] wlp0s29f7u6: associate with <MAC C-01 artvandalay> (try 1/3)
[   79.352488] wlp0s29f7u6: RX AssocResp from <MAC C-01 artvandalay> (capab=0x401 status=0 aid=2)
[   79.352492] wlp0s29f7u6: invalid AID value 0x2; bits 15:14 not set
[   79.364690] wlp0s29f7u6: associated
[   79.364725] IPv6: ADDRCONF(NETDEV_CHANGE): wlp0s29f7u6: link becomes ready
[ 1447.687985] Loading kernel module for a network device with CAP_SYS_MODULE (deprecated).  Use CAP_NET_ADMIN and alias netdev-iwlwifi instead.
[ 2937.324698] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:ds
[ 2937.324704] iwl3945: Copyright(c) 2003-2011 Intel Corporation
[ 3004.991648] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:ds
[ 3004.991654] iwl3945: Copyright(c) 2003-2011 Intel Corporation

	======== Done ========

```

---

### Post by varunendra on 2014-07-04
> **srinig82 said:**
> BIOS is in default setting only. lspci doesn't show the wireless device. also i am absolutely unable to turn on the wifi LED light. it is always off. it was ON when I used the live usb when the system still had windows. now i have erased the windows os and only runs linux lite and LED light never turns on

The advice to reset BIOS does not assume that you might have misconfigured something in it. Sometimes when everything is okay, the BIOS or wireless card firmware may get 'stuck' in a stage that only a full reset can fix.

So if you haven't already tried a BIOS reset, please try that now and see if "lspci" or "lshw" can see the wireless card. Except in some very exceptional cases, a pci card not appearing in "lspci" even after a BIOS reset means either a lose card (open it > clean contacts > re-seat it properly) or that the card is dead. We don't want to jump to that conclusion so easily.

---

### Post by srinig82 on 2014-07-04
I have reset the BIOS and the wifi led key still does not turn on. its a laptop. i am very very sure the wifi card is working fine. i installed windows and wasted 2 hours to check if the wifi card is dead and it certainly is not. like i said live CD showed the LED light ON but as soon as i formatted and installed linux it went OFF.

---

### Post by varunendra on 2014-07-04
> **srinig82 said:**
> I have reset the BIOS and the wifi led key still does not turn on. its a laptop. i am very very sure the wifi card is working fine. i installed windows and wasted 2 hours to check if the wifi card is dead and it certainly is not. like i said live CD showed the LED light ON but as soon as i formatted and installed linux it went OFF.

So do you have windows installed on it now and it works okay there?

Does the output of "lspci" still not show the card?

Can you please check the Live DVD/USB again and see if it works there? If yes, please post the wireless_script report from there.

If the card still doesn't show up in the output of "lspci" or "lshw" (sudo lshw -C network), please post back the outputs of -
```
lspci -nn
lsmod
egrep '3945|iwl' /var/log/syslog
```

---

### Post by praseodym on 2014-07-04
Please show
```

lsmod
```

completely and run
```

dmesg >> dmesg.txt
```
Upload this file (in your home folder)

---

### Post by srinig82 on 2014-07-05
Varun was right. The wireless adapter was loose. I fixed it and now it is detecting. There are still problems with the wireless dropping typical with 3945abg but that should be easily solvable with the rest of the threads.

Thanks a lot
Srini

---

### Post by varunendra on 2014-07-05
You're welcome!

> **srinig82 said:**
> but that should be easily solvable with the rest of the threads.
..if not, feel free to remove the [SOLVED] prefix and post back a report generated by wireless_script discussed here : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

We can take it from there. :)

---

### Post by srinig82 on 2014-07-05
Varun,

Sorry I am unable to solve the puzzle. I can see what the problem is but not solve it.  I can see that the wireless adapter does not have a driver in use. I can't seem to fix it.

Here is the wireless script output

```

########## wireless info START ##########

##### release #####

##### kernel #####

Linux localhost.localdomain 3.14.9-200.fc20.i686 #1 SMP Thu Jun 26 22:19:04 UTC 2014 i686 i686 i386 GNU/Linux

##### lspci #####

03:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev ff)
	Kernel modules: iwl3945
05:06.0 CardBus bridge [0607]: Texas Instruments PCIxx12 Cardbus Controller [104c:8039]

05:08.0 Ethernet controller [0200]: Intel Corporation PRO/100 VM Network Connection [8086:1093] (rev 02)
	Subsystem: Toshiba America Info Systems Device [1179:ff00]
	Kernel driver in use: e100

##### lsusb #####

Bus 001 Device 002: ID 148f:2573 Ralink Technology, Corp. RT2501/RT2573 Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA Card Info #####

PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255

##### rfkill #####

0: phy1: Wireless LAN
	Soft blocked: no
	Hard blocked: no

##### lsmod #####

rt73usb                31157  0 
rt2x00usb              19262  1 rt73usb
rt2x00lib              56555  2 rt73usb,rt2x00usb
iwl3945                98585  0 
iwlegacy              110164  1 iwl3945
mac80211              536316  4 iwl3945,iwlegacy,rt2x00lib,rt2x00usb
cfg80211              435060  4 iwl3945,iwlegacy,mac80211,rt2x00lib
crc_itu_t              12549  2 rt73usb,firewire_core

##### iw reg get #####

country LK: DFS-UNSET
	(2402 - 2482 @ 40), (N/A, 20)
	(5170 - 5250 @ 80), (N/A, 17)
	(5250 - 5330 @ 80), (N/A, 24), DFS
	(5490 - 5730 @ 80), (N/A, 24), DFS
	(5735 - 5835 @ 80), (N/A, 30)

##### interfaces #####

##### iwconfig #####

wlp0s29f7u6  IEEE 802.11bg  ESSID:"artvandalay"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC address removed>   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on
          Link Quality=70/70  Signal level=-36 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:126   Missed beacon:0

##### route #####

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.2.1     0.0.0.0         UG    1024   0        0 wlp0s29f7u6
192.168.2.0     0.0.0.0         255.255.255.0   U     0      0        0 wlp0s29f7u6

##### resolv.conf #####

nameserver 192.168.2.1

##### nm-tool #####

##### NetworkManager.state #####

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf #####

[main]
plugins=ifcfg-rh

##### iwlist #####

wlp0s29f7u6  Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-38 dBm  
                    Encryption key:off
                    ESSID:"artvandalay"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000024f829b49
                    Extra: Last beacon: 710ms ago
                    IE: Unknown: 000B61727476616E64616C6179
                    IE: Unknown: 010882840B160C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
          Cell 02 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000004312bd6997
                    Extra: Last beacon: 4119ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 32040C183060
                    IE: Unknown: 07064D5800010B14
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD07000C4304000000
          Cell 03 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:"OMNAMASIVA"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000004312bdbedc
                    Extra: Last beacon: 4096ms ago
                    IE: Unknown: 000A4F4D4E414D4153495641
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A6E1117FF000000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1601050000000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: DD07000C4304000000
                    IE: Unknown: 07064D5800010B10
          Cell 04 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"Sony Xperiaâ&#132;¢ tipo_4110"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000066bb4787d
                    Extra: Last beacon: 2409ms ago
                    IE: Unknown: 0018536F6E7920587065726961E284A2207469706F5F34313130
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A0C1019FF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606080400000000000000000000000000000000000000
                    IE: Unknown: DD09001018020200040000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00

##### iwlist channel #####

wlp0s29f7u6  13 channels in total; available frequencies :
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
          Current Frequency:2.462 GHz (Channel 11)

##### modinfo #####

filename:       /lib/modules/3.14.9-200.fc20.i686/kernel/drivers/net/wireless/rt2x00/rt73usb.ko
license:        GPL
firmware:       rt73.bin
description:    Ralink RT73 USB Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     2895B54E117EB0356D1E95D
alias:          usb:v0586p3415d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CDEp001Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v7167p3840d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019pAB50d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019pAB01d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0471p200Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v6933p5001d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0769p31F3d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p9712d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p90ACd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p002Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0027d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0024d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1740p7100d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04E8p4471d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v18E8p6238d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v18E8p6229d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v18E8p6196d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0812p3101d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp2671d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp2573d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04BBp093Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B75p7318d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DB0pA874d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DB0pA861d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DB0p6874d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DB0p6877d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DB0p4600d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13B1p0028d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13B1p0023d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13B1p0020d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v06F8pE020d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v06F8pE010d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v06F8pE002d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1472p0009d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1044p800Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1044p8008d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v15A9p0004d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1740p3701d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v7392p7618d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v7392p7318d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07D1p3C07d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07D1p3C06d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07D1p3C04d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07D1p3C03d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07AAp002Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v14B2p3C22d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1371p9032d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1371p9022d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v178Dp02BEd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0411p0137d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0411p0119d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0411p0116d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0411p00F4d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0411p00E6d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0411p00D9d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0411p00D8d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v08DDp0120d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1631pC019d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp905Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp905Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp705Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp7050d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p1724d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p1723d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1690p0722d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v18C5p0002d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0EB0p9021d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp9021d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v14B2p3C10d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07B8pB21Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07B8pB21Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07B8pB21Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07B8pB21Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07B8pB21Bd*dc*dsc*dp*ic*isc*ip*in*
depends:        rt2x00lib,rt2x00usb,crc-itu-t
intree:         Y
vermagic:       3.14.9-200.fc20.i686 SMP mod_unload 686 
signer:         Fedora kernel signing key
sig_key:        <MAC address removed>:6F:C5:88:DF:61:96:54:6B:8A:B6:76:0F:87:E4
sig_hashalgo:   sha256
parm:           nohwcrypt:Disable hardware encryption. (bool)

filename:       /lib/modules/3.14.9-200.fc20.i686/kernel/drivers/net/wireless/rt2x00/rt2x00usb.ko
license:        GPL
description:    rt2x00 usb library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     44768071492503F8EFE1EED
depends:        rt2x00lib,mac80211
intree:         Y
vermagic:       3.14.9-200.fc20.i686 SMP mod_unload 686 
signer:         Fedora kernel signing key
sig_key:        <MAC address removed>:6F:C5:88:DF:61:96:54:6B:8A:B6:76:0F:87:E4
sig_hashalgo:   sha256

filename:       /lib/modules/3.14.9-200.fc20.i686/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
license:        GPL
description:    rt2x00 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     5175D5F88811224E27FB78F
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.14.9-200.fc20.i686 SMP mod_unload 686 
signer:         Fedora kernel signing key
sig_key:        <MAC address removed>:6F:C5:88:DF:61:96:54:6B:8A:B6:76:0F:87:E4
sig_hashalgo:   sha256

filename:       /lib/modules/3.14.9-200.fc20.i686/kernel/drivers/net/wireless/iwlegacy/iwl3945.ko
firmware:       iwlwifi-3945-2.ucode
license:        GPL
author:         Copyright(c) 2003-2011 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:ds
description:    Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux
srcversion:     4E926C85C8DB36AABFD0900
alias:          pci:v00008086d00004227sv*sd*bc*sc*i*
alias:          pci:v00008086d00004222sv*sd*bc*sc*i*
alias:          pci:v00008086d00004227sv*sd00001014bc*sc*i*
alias:          pci:v00008086d00004222sv*sd00001044bc*sc*i*
alias:          pci:v00008086d00004222sv*sd00001034bc*sc*i*
alias:          pci:v00008086d00004222sv*sd00001005bc*sc*i*
depends:        iwlegacy,cfg80211,mac80211
intree:         Y
vermagic:       3.14.9-200.fc20.i686 SMP mod_unload 686 
signer:         Fedora kernel signing key
sig_key:        <MAC address removed>:6F:C5:88:DF:61:96:54:6B:8A:B6:76:0F:87:E4
sig_hashalgo:   sha256
parm:           antenna:select antenna (1=Main, 2=Aux, default 0 [both]) (int)
parm:           swcrypto:using software crypto (default 1 [software]) (int)
parm:           disable_hw_scan:disable hardware scanning (default 1) (int)
parm:           debug:debug output mask (uint)
parm:           fw_restart:restart firmware in case of error (int)

filename:       /lib/modules/3.14.9-200.fc20.i686/kernel/drivers/net/wireless/iwlegacy/iwlegacy.ko
license:        GPL
author:         Copyright(c) 2003-2011 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    iwl-legacy: common functions for 3945 and 4965
srcversion:     955170B59A7606EF9485575
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.14.9-200.fc20.i686 SMP mod_unload 686 
signer:         Fedora kernel signing key
sig_key:        <MAC address removed>:6F:C5:88:DF:61:96:54:6B:8A:B6:76:0F:87:E4
sig_hashalgo:   sha256
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking (int)
parm:           bt_coex_active:enable wifi/bluetooth co-exist (bool)

##### modules #####

##### blacklist #####

##### udev rules #####

##### dmesg #####

[   17.695972] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:ds
[   17.695978] iwl3945: Copyright(c) 2003-2011 Intel Corporation
[   17.696189] iwl3945 0000:03:00.0: can't disable ASPM; OS doesn't have ASPM control
[   17.754191] WARNING: CPU: 0 PID: 494 at drivers/net/wireless/iwlegacy/common.c:116 _il_grab_nic_access+0xa0/0xb0 [iwlegacy]()
[   17.754191] Modules linked in: iwl3945(+) snd_hda_codec_si3054 iwlegacy snd_hda_codec_realtek snd_hda_codec_generic iTCO_wdt iTCO_vendor_support joydev mac80211 ppdev snd_hda_intel serio_raw snd_hda_codec coretemp snd_hwdep snd_seq cfg80211 microcode sdhci_pci snd_seq_device i2c_i801 snd_pcm sdhci toshiba_bluetooth parport_pc mmc_core tifm_7xx1 tifm_core lpc_ich snd_timer rfkill irda parport snd crc_ccitt soundcore tpm_tis tpm_infineon tpm acpi_cpufreq nfsd auth_rpcgss nfs_acl lockd sunrpc i915 i2c_algo_bit drm_kms_helper e100 mii drm i2c_core ata_generic yenta_socket firewire_ohci pata_acpi firewire_core crc_itu_t video
[   17.754191]  [<f854a1b0>] ? _il_grab_nic_access+0xa0/0xb0 [iwlegacy]
[   17.754191]  [<f854a1b0>] ? _il_grab_nic_access+0xa0/0xb0 [iwlegacy]
[   17.754191]  [<f854a1b0>] _il_grab_nic_access+0xa0/0xb0 [iwlegacy]
[   17.754191]  [<f85eb0a4>] il3945_apm_init+0xc4/0x130 [iwl3945]
[   17.754191]  [<f854dede>] il_eeprom_init+0x9e/0x2e0 [iwlegacy]
[   17.754191]  [<f85e5b97>] il3945_pci_probe+0x317/0xad0 [iwl3945]
[   17.754191]  [<f80d5052>] il3945_init+0x52/0x1000 [iwl3945]
[   17.802874] iwl3945 0000:03:00.0: bad EEPROM signature,EEPROM_GP=0x00000007
[   17.802879] iwl3945 0000:03:00.0: EEPROM not found, EEPROM_GP=0x10000004
[   17.802896] iwl3945 0000:03:00.0: Unable to init EEPROM
[   17.803623] iwl3945: probe of 0000:03:00.0 failed with error -2
[   79.668652] ieee80211 phy1: rt2x00_set_chip: Info - Chipset detected - rt: 2573, rf: 0002, rev: 000a
[   79.785822] systemd-udevd[1455]: renamed network interface wlan0 to wlp0s29f7u6
[   79.823936] ieee80211 phy1: rt2x00lib_request_firmware: Info - Loading firmware file 'rt73.bin'
[   79.868548] ieee80211 phy1: rt2x00lib_request_firmware: Info - Firmware detected - version: 1.7
[   79.966892] IPv6: ADDRCONF(NETDEV_UP): wlp0s29f7u6: link is not ready
[   82.252830] wlp0s29f7u6: authenticate with <MAC address removed>
[   82.319768] wlp0s29f7u6: send auth to <MAC address removed> (try 1/3)
[   82.322185] wlp0s29f7u6: authenticated
[   82.325409] rt73usb 1-6:1.0 wlp0s29f7u6: disabling HT as WMM/QoS is not supported by the AP
[   82.325417] rt73usb 1-6:1.0 wlp0s29f7u6: disabling VHT as WMM/QoS is not supported by the AP
[   82.326041] wlp0s29f7u6: associate with <MAC address removed> (try 1/3)
[   82.337735] wlp0s29f7u6: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=2)
[   82.337741] wlp0s29f7u6: invalid AID value 0x2; bits 15:14 not set
[   82.348073] wlp0s29f7u6: associated
[   82.348111] IPv6: ADDRCONF(NETDEV_CHANGE): wlp0s29f7u6: link becomes ready

########## wireless info END ############

```

---

### Post by varunendra on 2014-07-05
I'm not sure what to do about this -
> **srinig82 said:**
> ```
[   17.802874] iwl3945 0000:03:00.0: bad EEPROM signature,EEPROM_GP=0x00000007
[   17.802879] iwl3945 0000:03:00.0: EEPROM not found, EEPROM_GP=0x10000004
[   17.802896] iwl3945 0000:03:00.0: Unable to init EEPROM
[   17.803623] **iwl3945: probe of 0000:03:00.0 [COLOR="#FF0000"]failed with error -2[/COLOR]**

```

It seems either the card is still loose or indeed broken. Please make sure the connections are clean and firm (that is, the card is tightly seated in its socket), then generate a fresh wireless_script report without the USB adapter this time. Please use the newer version of the script which you can find in the link I gave in my previous post. That one generates a lot more info which may sometimes be useful.

And do you still have a Live DVD/USB of Ubuntu? If yes, please also try that in live session. If Ubuntu is too heavy for your system, you may try Xubuntu or Lubuntu which are lighter variants of Ubuntu. Lubuntu is lightest, Xubuntu is heavier that Lubuntu, but a good balance between performance and functionality.

---

### Post by praseodym on 2014-07-06
Are you familiar with boot options? If yes, please try these right above the ```
bold
``` entries

[http://forum.ubuntuusers.de/topic/wlan-hardware-geht-nicht-notebook/2/#post-6231507](http://forum.ubuntuusers.de/topic/wlan-hardware-geht-nicht-notebook/2/#post-6231507)

---

### Post by varunendra on 2014-07-06
A good explanation of Boot Options : [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

Common boot options (there are many more) : [https://help.ubuntu.com/community/BootOptions#Common_Kernel_Options](https://help.ubuntu.com/community/BootOptions#Common_Kernel_Options)

---

### Post by srinig82 on 2014-07-07
Sorry Varun was travelling. I haven't tried boot options. tbh i don't understand it at all. Anyway here is the latest run without the usb wireless adapter.

```

	======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

srinig-Satellite-M105 3.13.0-30-generic i686,  Ubuntu 14.04 LTS, trusty

CPU    : Genuine Intel(R) CPU           T1350  @ 1.86GHz
Memory : 1499 MB
Uptime : 15:45:01 up 26 min,  2 users,  load average: 0.19, 0.22, 0.28


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

03:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)
	Subsystem: Intel Corporation Device [8086:1040]
	Kernel driver in use: iwl3945
--
05:08.0 Ethernet controller [0200]: Intel Corporation PRO/100 VM Network Connection [8086:1093] (rev 02)
	Subsystem: Toshiba America Info Systems Device [1179:ff00]
	Kernel driver in use: e100


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface        Soft blocked  Hard blocked
1: phy1: Wireless LAN      no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

iwl3945                63619  0 
iwlegacy               88016  1 iwl3945
ar5523                 32857  0 
mac80211              546051  3 iwl3945,iwlegacy,ar5523
cfg80211              409394  4 iwl3945,iwlegacy,mac80211,ar5523


module parameters ~~~~~~~~~~~~~~~~~~

cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
iwl3945       (4): antenna=0 | disable_hw_scan=1 | fw_restart=1 | swcrypto=1
iwlegacy      (2): bt_coex_active=Y | led_mode=0
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: disconnected
================o=============o=========o==============o=========o===========o==============o===========
 Interface & ID | Type        | Driver  | State        | Default | Speed     | Support      | HW Addr   
================o=============o=========o==============o=========o===========o==============o===========
 eth0           | Wired       | e100    | unavailable  | no      |           |              | <MAC eth0>
----------------+-------------+---------+--------------+---------+-----------+--------------+-----------
 wlan0          | 802.11 WiFi | iwl3945 | disconnected | no      |           | WEP/WPA/WPA2 | <MAC wlan0>
----------------+-------------+---------+--------------+---------+-----------+--------------+-----------


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
          Channel 165 (5.825 GHz) - 11 (2.462 GHz)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     No scan results


blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/libpisock9.conf]
blacklist visor


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[iwl3945]
filename:       /lib/modules/3.13.0-30-generic/kernel/drivers/net/wireless/iwlegacy/iwl3945.ko
firmware:       iwlwifi-3945-2.ucode
version:        in-tree:s
srcversion:     C93C31FCEBBAE1F376E495F
depends:        iwlegacy,cfg80211,mac80211
parm:           antenna:select antenna (1=Main, 2=Aux, default 0 [both]) (int)
parm:           swcrypto:using software crypto (default 1 [software]) (int)
parm:           disable_hw_scan:disable hardware scanning (default 1) (int)
parm:           fw_restart:restart firmware in case of error (int)

[iwlegacy]
filename:       /lib/modules/3.13.0-30-generic/kernel/drivers/net/wireless/iwlegacy/iwlegacy.ko
version:        in-tree:
srcversion:     400F302BE5C25B3C98A6CE8
depends:        mac80211,cfg80211
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking (int)
parm:           bt_coex_active:enable wifi/bluetooth co-exist (bool)

[ar5523]
filename:       /lib/modules/3.13.0-30-generic/kernel/drivers/net/wireless/ath/ar5523/ar5523.ko
firmware:       ar5523.bin
srcversion:     06242D88E1FBF80DD4380BC
depends:        mac80211,cfg80211

[mac80211]
filename:       /lib/modules/3.13.0-30-generic/kernel/net/mac80211/mac80211.ko
srcversion:     6F23437712851B1B0563BCB
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-30-generic/kernel/net/wireless/cfg80211.ko
srcversion:     8B3D642D1F2E6406EF33F74
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x8086:0x1093 (e100)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x8086:0x4222 (iwl3945)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

# USB device 0x:0x (rt73usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan1>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"

# USB device 0x:0x (ar5523)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan2>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan2"


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

BOOT_IMAGE=/boot/vmlinuz-3.13.0-30-generic root=UUID=70de5c81-fccf-4088-9e1b-6acd3b14474f ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    0.777220] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.777637] audit: initializing netlink socket (disabled)
[   12.045275] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[   12.045281] iwl3945: Copyright(c) 2003-2011 Intel Corporation
[   12.045342] iwl3945 0000:03:00.0: can't disable ASPM; OS doesn't have ASPM control
[   12.105767] iwl3945 0000:03:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[   12.105772] iwl3945 0000:03:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   12.105848] iwl3945 0000:03:00.0: irq 42 for MSI/MSI-X
[   12.269409] ieee80211 phy1: Selected rate control algorithm 'iwl-3945-rs'
[   12.288373] systemd-udevd[311]: renamed network interface wlan1 to wlan2
[   17.662587] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   21.497930] iwl3945 0000:03:00.0: loaded firmware version 15.32.2.9
[   21.566263] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   21.566747] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   21.684442] IPv6: ADDRCONF(NETDEV_UP): wlan2: link is not ready
[   21.684946] IPv6: ADDRCONF(NETDEV_UP): wlan2: link is not ready
[   89.689194] wlan0: authenticate with <MAC ID removed>
[   89.694312] wlan0: send auth to <MAC ID removed> (try 1/3)
[   89.696312] wlan0: authenticated
[   89.697528] iwl3945 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   89.697538] iwl3945 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   89.700262] wlan0: associate with <MAC ID removed> (try 1/3)
[   89.704220] wlan0: RX AssocResp from <MAC ID removed> (capab=0x401 status=0 aid=2)
[   89.704225] wlan0: invalid AID value 0x2; bits 15:14 not set
[   89.705623] wlan0: associated
[   89.705673] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  125.264235] iwl3945 0000:03:00.0: Error sending C_RXON: time out after 500ms.
[  125.264252] iwl3945 0000:03:00.0: Error clearing ASSOC_MSK on current configuration (-110).
[  126.012137] iwl3945 0000:03:00.0: Error sending C_RXON: time out after 500ms.
[  126.012155] iwl3945 0000:03:00.0: Error clearing ASSOC_MSK on current configuration (-110).
[  126.620175] iwl3945 0000:03:00.0: Error sending C_RXON: time out after 500ms.
[  126.620191] iwl3945 0000:03:00.0: Error clearing ASSOC_MSK on current configuration (-110).
[  127.060181] iwl3945 0000:03:00.0: Queue 4 stuck for 2404 ms.
[  127.060206] iwl3945 0000:03:00.0: On demand firmware reload
[  127.368300] iwl3945 0000:03:00.0: Error sending C_RXON: time out after 500ms.
[  127.368316] iwl3945 0000:03:00.0: Error clearing ASSOC_MSK on current configuration (-110).
[  127.372204] WARNING: CPU: 0 PID: 69 at /build/buildd/linux-3.13.0/drivers/net/wireless/iwlegacy/common.c:117 _il_grab_nic_access+0xa0/0xb0 [iwlegacy]()
[  127.372204] Modules linked in: bnep rfcomm bluetooth snd_hda_codec_si3054 snd_hda_codec_realtek snd_hda_intel arc4 snd_hda_codec snd_hwdep iwl3945 snd_pcm iwlegacy ar5523 i915 mac80211 snd_page_alloc snd_seq_midi pcmcia snd_seq_midi_event snd_rawmidi snd_seq coretemp drm_kms_helper cfg80211 yenta_socket snd_seq_device drm pcmcia_rsrc snd_timer joydev tifm_7xx1 pcmcia_core serio_raw snd i2c_algo_bit tifm_core lpc_ich soundcore video mac_hid parport_pc ppdev lp parport e100 firewire_ohci sdhci_pci firewire_core psmouse sdhci crc_itu_t mii
[  127.372204]  [<f847f860>] ? _il_grab_nic_access+0xa0/0xb0 [iwlegacy]
[  127.372204]  [<f847f860>] ? _il_grab_nic_access+0xa0/0xb0 [iwlegacy]
[  127.372204]  [<f847f860>] _il_grab_nic_access+0xa0/0xb0 [iwlegacy]
[  127.372204]  [<f847f9ac>] il_wr_prph+0x2c/0x80 [iwlegacy]
[  127.372204]  [<f8480f41>] il_apm_init+0x161/0x1d0 [iwlegacy]
[  127.372204]  [<f84eeee5>] il3945_apm_init+0x15/0x140 [iwl3945]
[  127.372204]  [<f84efe82>] il3945_hw_nic_init+0x32/0x540 [iwl3945]
[  127.372204]  [<f84ebd72>] __il3945_up+0xb2/0x2a0 [iwl3945]
[  127.372204]  [<f84ec9cf>] il3945_mac_start+0x29f/0x640 [iwl3945]
[  128.317599] iwl3945 0000:03:00.0: BSM uCode verification failed at addr 0x00003800+0 (of 900), is 0xffffffff, s/b 0xf802020
[  128.317612] iwl3945 0000:03:00.0: Unable to set up bootstrap uCode: -5
[  128.446305] iwl3945 0000:03:00.0: BSM uCode verification failed at addr 0x00003800+0 (of 900), is 0xffffffff, s/b 0xf802020
[  128.446313] iwl3945 0000:03:00.0: Unable to set up bootstrap uCode: -5
[  128.575019] iwl3945 0000:03:00.0: BSM uCode verification failed at addr 0x00003800+0 (of 900), is 0xffffffff, s/b 0xf802020
[  128.575027] iwl3945 0000:03:00.0: Unable to set up bootstrap uCode: -5
[  128.703730] iwl3945 0000:03:00.0: BSM uCode verification failed at addr 0x00003800+0 (of 900), is 0xffffffff, s/b 0xf802020
[  128.703737] iwl3945 0000:03:00.0: Unable to set up bootstrap uCode: -5
[  128.832453] iwl3945 0000:03:00.0: BSM uCode verification failed at addr 0x00003800+0 (of 900), is 0xffffffff, s/b 0xf802020
[  128.832461] iwl3945 0000:03:00.0: Unable to set up bootstrap uCode: -5
[  128.832720] iwl3945 0000:03:00.0: Unable to initialize device after 5 attempts.
[  131.336306] ieee80211 phy1: wlan0: No probe response from AP <MAC ID removed> after 500ms, disconnecting.
[  133.459857] wlan0: authenticate with <MAC ID removed>
[  133.460958] wlan0: send auth to <MAC ID removed> (try 1/3)
[  133.664064] wlan0: send auth to <MAC ID removed> (try 2/3)
[  133.868120] wlan0: send auth to <MAC ID removed> (try 3/3)
[  134.072122] wlan0: authentication with <MAC ID removed> timed out
[  147.108346] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  163.873334] wlan2: authenticate with <MAC ID removed>
[  163.882788] wlan2: send auth to <MAC ID removed> (try 1/3)
[  163.884704] wlan2: authenticated
[  163.887282] ar5523 1-5:1.0 wlan2: disabling HT as WMM/QoS is not supported by the AP
[  163.887291] ar5523 1-5:1.0 wlan2: disabling VHT as WMM/QoS is not supported by the AP
[  163.888233] wlan2: associate with <MAC ID removed> (try 1/3)
[  163.892181] wlan2: RX AssocResp from <MAC ID removed> (capab=0x401 status=0 aid=3)
[  163.892189] wlan2: invalid AID value 0x3; bits 15:14 not set
[  163.893200] wlan2: associated
[  163.893240] IPv6: ADDRCONF(NETDEV_CHANGE): wlan2: link becomes ready
[  920.033526] wlan2: deauthenticating from <MAC ID removed> by local choice (reason=3)
[  951.464098] systemd-udevd[3526]: renamed network interface wlan1 to wlan2
[  951.583499] IPv6: ADDRCONF(NETDEV_UP): wlan2: link is not ready
[  951.583999] IPv6: ADDRCONF(NETDEV_UP): wlan2: link is not ready
[  952.598217] wlan2: authenticate with <MAC ID removed>
[  952.603502] wlan2: send auth to <MAC ID removed> (try 1/3)
[  952.605427] wlan2: authenticated
[  952.605608] ar5523 1-5:1.0 wlan2: disabling HT as WMM/QoS is not supported by the AP
[  952.605612] ar5523 1-5:1.0 wlan2: disabling VHT as WMM/QoS is not supported by the AP
[  952.608159] wlan2: associate with <MAC ID removed> (try 1/3)
[  952.610552] wlan2: RX AssocResp from <MAC ID removed> (capab=0x401 status=0 aid=3)
[  952.610557] wlan2: invalid AID value 0x3; bits 15:14 not set
[  952.611681] wlan2: associated
[  952.611711] IPv6: ADDRCONF(NETDEV_CHANGE): wlan2: link becomes ready
[ 1585.972992] wlan2: deauthenticating from <MAC ID removed> by local choice (reason=3)

	======== Done ========
  
```

---

### Post by varunendra on 2014-07-07
> **srinig82 said:**
> ```
[  128.832453] iwl3945 0000:03:00.0: [COLOR="#FF0000"]BSM uCode verification failed[/COLOR] at addr 0x00003800+0 (of 900), is 0xffffffff, s/b 0xf802020
[  128.832461] iwl3945 0000:03:00.0: Unable to set up bootstrap uCode: -5
[  128.832720] iwl3945 0000:03:00.0: Unable to initialize device after 5 attempts.
[  131.336306] ieee80211 phy1: wlan0: **No probe response from AP <MAC ID removed> after 500ms, disconnecting**.
  
```

A different error, but again firmware related it seems.

With a wired (or USB) connection, please try upgrading your firmware package -
```
sudo apt-get clean
sudo apt-get update
sudo apt-get install --reinstall linux-firmware
```
Followed by a reboot.

Based on the last line I quoted above, you may also try extending the time that the driver waits for to get a response from the AP. To do so, run the following command that will create a conf file with with a driver parameter that defines the time. 
```
echo "options mac80211 probe_wait_ms=2000" | sudo tee /etc/modprobe.d/mac80211.conf
```
Reboot, try to connect and post back the outputs of -
```
iwconfig
dmesg | egrep 'iwl|wlan0'
```
Oh, and keep the USB adapter disconnected while rebooting or trying the internal wifi.

The 'Tx power' on your wifi interface is also very low (only 14 dBm) which I thing we can increase upto 20 dBm, but I believe we must first get rid of the firmware related issues, only then tricks like increasing tx power (if possible) would make sense.

---

### Post by srinig82 on 2014-07-07
Hi Varun,

Things slight look ok. It hasn't failed so far.

```
  wlan0     IEEE 802.11abg  ESSID:"artvandalay"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:0E:2E:7A:C6:8C   
          Bit Rate=54 Mb/s   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-34 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:169   Missed beacon:0

lo        no wireless extensions.

eth0      no wireless extensions.
   
```


```
 [   16.458573] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[   16.458579] iwl3945: Copyright(c) 2003-2011 Intel Corporation
[   16.458641] iwl3945 0000:03:00.0: can't disable ASPM; OS doesn't have ASPM control
[   16.664701] iwl3945 0000:03:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[   16.664708] iwl3945 0000:03:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   16.664786] iwl3945 0000:03:00.0: irq 42 for MSI/MSI-X
[   16.747716] ieee80211 phy0: Selected rate control algorithm 'iwl-3945-rs'
[   20.329299] iwl3945 0000:03:00.0: loaded firmware version 15.32.2.9
[   20.398339] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   20.398908] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   23.841104] wlan0: authenticate with 00:0e:2e:7a:c6:8c
[   23.842986] wlan0: send auth to 00:0e:2e:7a:c6:8c (try 1/3)
[   23.844788] wlan0: authenticated
[   23.845094] iwl3945 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   23.845103] iwl3945 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   23.848115] wlan0: associate with 00:0e:2e:7a:c6:8c (try 1/3)
[   23.850669] wlan0: RX AssocResp from 00:0e:2e:7a:c6:8c (capab=0x401 status=0 aid=3)
[   23.850674] wlan0: invalid AID value 0x3; bits 15:14 not set
[   23.853121] wlan0: associated
[   23.853151] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
    
```

I think the problem is solved. I am guessing a bunch of reboots and updates did the trick. Not sure exactly which procedure to follow. I will close this link if I am problem free for the next couple of days.

Thanks a lot!!!!!!! ;-)

---

### Post by srinig82 on 2014-07-08
Hi Varun,

Nope same problem. Updated everything I think. Still disconnects 4-5 minutes after rebooting. Getting that BSM code verification error again. Any other suggestions????

Cheers,
Srini

---

### Post by varunendra on 2014-07-10
Ignoring the BSM ucode error for a moment, please try increasing Tx power on your wifi card and see if it accepts the increased value (not all cards can accept a forced value) -
```
sudo iwconfig wlan0 txpower 20
```

Then check -
```
iwconfig
```
..and see if "Tx-Power" value becomes 20 dBm. If the '...txpower 20' command returns any errors, please post it here.

If the value is accepted, but the problem persists, please post a fresh report of the new wireless_script. I don't know yet if we can do something about the "BSM ucode.." error or not, or even if it is really harmful or just a red herring, but it seems to be power management related. Just post back the fresh report if the txpower trick doesn't do any magic, and we'll see if there is something more we can try.

---

