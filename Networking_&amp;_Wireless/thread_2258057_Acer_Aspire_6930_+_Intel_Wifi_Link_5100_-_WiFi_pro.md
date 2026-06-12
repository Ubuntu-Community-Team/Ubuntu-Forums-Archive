---
title: "Acer Aspire 6930 + Intel Wifi Link 5100 - WiFi problems"
date: 2014-12-24
forum: Networking &amp; Wireless
---

### Post by metamorph2 on 2014-12-24
Hello,

it's my first post in this forum, since a few weeks ago my wireless connection on my laptop with Ubuntu 14.04.1 is very slow, or doesn't work at all. I don't think to have changed any particular software or hardware (except for system updates, downloaded every time I managed to connect), and the crazy thing is that when my laptop is turned on with Ubuntu all the devices connected to the same network suffer from the same issue.

(This never happened when my laptop is shut down, or rebooted with Windows: that's why I think it's an Ubuntu issue)

Before posting, I tried some different approaches like:
- [disabling N mode in my wireless card]("http://askubuntu.com/questions/457986/very-slow-intermittent-wifi-speeds-with-14-04-and-intel-pro-wireless-5100-agn")
- blacklisting the acer_wmi drivers
- [setting the router in WPA2-AES mode and disabling the IPv6 protocol in Network Manager]("http://ubuntuforums.org/showthread.php?t=2255399&p=13180837#post13180837")
but none of them worked.

Here's the output of the [Wireless Script]("http://ubuntuforums.org/showthread.php?t=2224209&p=13024222#post13024222"):

```

    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

dade-notebook 3.13.0-43-generic x86_64,  Ubuntu 14.04.1 LTS, trusty

CPU    : Intel(R) Core(TM)2 Duo CPU     P8400  @ 2.26GHz
Memory : 3948 MB
Uptime : 15:34:22 up 10 min,  2 users,  load average: 1,82, 1,31, 0,87


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

07:00.0 Network controller [0280]: Intel Corporation WiFi Link 5100 [8086:4232]
    Subsystem: Intel Corporation WiFi Link 5100 AGN [8086:1201]
    Kernel driver in use: iwlwifi
09:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8121/AR8113/AR8114 Gigabit or Fast Ethernet [1969:1026] (rev b0)
    Subsystem: Acer Incorporated [ALI] Device [1025:015e]
    Kernel driver in use: ATL1E


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 002 Device 005: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 002 Device 004: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 002 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 002: ID 046d:c05a Logitech, Inc. M90/M100 Optical Mouse
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 5986:0105 Acer, Inc 
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 147e:1000 Upek Biometric Touchchip/Touchstrip Fingerprint Sensor
Bus 004 Device 002: ID 0a5c:2101 Broadcom Corp. BCM2045 Bluetooth
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11abg  ESSID:"Sitecom59383F"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC C-01 Sitecom59383F>   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=54/70  Signal level=-56 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:2  Invalid misc:190   Missed beacon:0



rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface                 Soft blocked  Hard blocked
0: hci0: Bluetooth                  no            no
1: phy0: Wireless LAN               no            no
2: acer-wireless: Wireless LAN      no            no
3: acer-bluetooth: Bluetooth        no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

mxm_wmi                13021  0 
acer_wmi               32522  0 
sparse_keymap          13948  1 acer_wmi
iwldvm                232285  0 
mac80211              630653  1 iwldvm
iwlwifi               169932  1 iwldvm
cfg80211              484040  3 iwlwifi,mac80211,iwldvm
video                  19476  1 acer_wmi
wmi                    19177  2 acer_wmi,mxm_wmi


module parameters ~~~~~~~~~~~~~~~~~~

acer_wmi      (5): brightness=-1 | ec_raw_mode=N | force_series=0 | mailled=-1 | threeg=-1
cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
iwlwifi      (11): 11n_disable=1 | amsdu_size_8K=0 | antenna_coupling=0 | bt_coex_active=Y | fw_restart=Y | led_mode=0 | nvm_file=(null) | power_level=0 | power_save=N | swcrypto=0 | wd_disable=1
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
video         (3): allow_duplicates=N | brightness_switch_enabled=Y | use_native_backlight=-1
wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
======================================o===========  ==o=========o==============o=========o===========o  ==============o===========
 Interface & ID                       | Type        | Driver  | State        | Default | Speed     | Support      | HW Addr   
======================================o===========  ==o=========o==============o=========o===========o  ==============o===========
 <BT Device>                          | Bluetooth   | bluez   | disconnected | no      |           |              |           
--------------------------------------+-------------+---------+--------------+---------+-----------+--------------+-----------
 eth0                                 | Wired       | ATL1E   | unavailable  | no      |           |              | <MAC eth0>
--------------------------------------+-------------+---------+--------------+---------+-----------+--------------+-----------
 wlan0  [Sitecom59383F (Telecom DNS)] | 802.11 WiFi | iwlwifi | connected    | yes     | 1 Mb/s    | WEP/WPA/WPA2 | <MAC wlan0>

    TP-LINK_6C11D0:  Infra, <MAC C-02 TP-LINK_6C11D0>, Freq 2412 MHz, Rate 54 Mb/s, Strength 29 WEP
    *Sitecom59383F:  Infra, <MAC C-01 Sitecom59383F>, Freq 2437 MHz, Rate 54 Mb/s, Strength 63 WPA2

    Address:         192.168.0.103
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.101
    DNS:             62.211.69.170
    DNS:             212.48.4.30
--------------------------------------+-------------+---------+--------------+---------+-----------+--------------+-----------


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

Sitecom59383F (Google DNS) : ssid=Sitecom59383F | mac-address=<MAC wlan0> | ipv4=manual | ipv6=ignore 
Sitecom59383F (OpenDNS) : ssid=Sitecom59383F | mac-address=<MAC wlan0> | ipv4=manual | ipv6=ignore 
Sitecom59383F (Telecom DNS) : ssid=Sitecom59383F | mac-address=<MAC wlan0> | ipv4=manual | ipv6=ignore 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

auto lo
iface lo inet loopback


resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 127.0.1.1


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Tabella di routing IP del kernel
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.101   0.0.0.0         UG    0      0        0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

--- 192.168.0.101 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.580/0.667/0.754/0.087 ms

--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1000ms
rtt min/avg/max/mdev = 0.024/0.030/0.037/0.008 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "it_IT.UTF-8")
country US:
    (2402 - 2472 @ 40), (3, 27)
    (5170 - 5250 @ 40), (3, 17)
    (5250 - 5330 @ 40), (3, 20), DFS
    (5490 - 5600 @ 40), (3, 20), DFS
    (5650 - 5710 @ 40), (3, 20), DFS
    (5735 - 5835 @ 40), (3, 30)
    (57240 - 63720 @ 2160), (N/A, 40)


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     32 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 11 (2.462 GHz)
          Channel 36 (5.18 GHz)
          Channel 40 (5.2 GHz)
          Channel 44 (5.22 GHz)
          Channel 48 (5.24 GHz)
          Channel 52 (5.26 GHz)
          Channel 56 (5.28 GHz)
          Channel 60 (5.3 GHz)
          Channel 64 (5.32 GHz)
          Channel 100 (5.5 GHz)
          Channel 104 (5.52 GHz)
          Channel 108 (5.54 GHz)
          Channel 112 (5.56 GHz)
          Channel 116 (5.58 GHz)
          Channel 132 (5.66 GHz)
          Channel 136 (5.68 GHz)
          Channel 140 (5.7 GHz)
          Channel 149 (5.745 GHz)
          Channel 153 (5.765 GHz)
          Channel 157 (5.785 GHz)
          Channel 161 (5.805 GHz)
          Channel 165 (5.825 GHz)

          Current Frequency:2.437 GHz (Channel 6)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 Sitecom59383F>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:"Sitecom59383F"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000004bbe8b2ed
                    Extra: Last beacon: 48ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC C-02 TP-LINK_6C11D0>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"TP-LINK_6C11D0"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000028a6ee9c183
                    Extra: Last beacon: 4752ms ago


blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist acer_wmiblacklist acer_wmi

[/etc/modprobe.d/osspd.conf]
blacklist snd-pcm-oss
blacklist snd-mixer-oss
blacklist snd-seq-oss


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[mxm_wmi]
filename:       /lib/modules/3.13.0-43-generic/kernel/drivers/platform/x86/mxm-wmi.ko
srcversion:     62CBD37DE87DF0C4CD7FBA3
depends:        wmi

[acer_wmi]
filename:       /lib/modules/3.13.0-43-generic/kernel/drivers/platform/x86/acer-wmi.ko
srcversion:     15371DC0E403E93954B38E5
depends:        wmi,sparse-keymap,video
parm:           mailled:Set initial state of Mail LED (int)
parm:           brightness:Set initial LCD backlight brightness (int)
parm:           threeg:Set initial state of 3G hardware (int)
parm:           force_series:Force a different laptop series (int)
parm:           ec_raw_mode:Enable EC raw mode (bool)

[iwldvm]
filename:       /lib/modules/3.13.0-43-generic/kernel/drivers/net/wireless/iwlwifi/dvm/iwldvm.ko
version:        in-tree:
srcversion:     9ABCB275EC05F363D958754
depends:        iwlwifi,mac80211,cfg80211

[mac80211]
filename:       /lib/modules/3.13.0-43-generic/kernel/net/mac80211/mac80211.ko
srcversion:     446B3604A9C5461044DD691
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[iwlwifi]
filename:       /lib/modules/3.13.0-43-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
version:        in-tree:
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
srcversion:     72E4ECE7C2CBAA62E552DCE
depends:        cfg80211
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

[cfg80211]
filename:       /lib/modules/3.13.0-43-generic/kernel/net/wireless/cfg80211.ko
srcversion:     C2478077E22138832B71659
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[video]
filename:       /lib/modules/3.13.0-43-generic/kernel/drivers/acpi/video.ko
srcversion:     FBDB15F61F4F35FB6EE9AC8
depends:        
parm:           brightness_switch_enabled:bool
parm:           allow_duplicates:bool
parm:           use_native_backlight:int

[wmi]
filename:       /lib/modules/3.13.0-43-generic/kernel/drivers/platform/x86/wmi.ko
srcversion:     CED5410F008DC70DF5F064B
depends:        
parm:           debug_event:Log WMI Events [0/1] (bool)
parm:           debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x1969:/sys/devices/pci0000:00/0000:00:1c.5/0000:09:00.0 (ATL1E)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:1c.3/0000:07:00.0 (iwlwifi)
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
                    options iwlwifi 11n_disable=1
iwlwifi.conf~     : options iwlwifi 11n_disable=1
iwlwifi.conf.dpkg-old: options iwlwifi 11n_disable=1
mlx4.conf         : softdep mlx4_core post: mlx4_en


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/boot/vmlinuz-3.13.0-43-generic root=UUID=7c49dd9f-f330-4eaa-9083-c8b5a8258945 ro quiet splash


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    0.599001] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.599327] audit: initializing netlink socket (disabled)
[   26.627060] wmi: Mapper loaded
[   26.743721] iwlwifi 0000:07:00.0: enabling device (0000 -> 0002)
[   26.743789] iwlwifi 0000:07:00.0: can't disable ASPM; OS doesn't have ASPM control
[   26.743847] iwlwifi 0000:07:00.0: irq 45 for MSI/MSI-X
[   27.006225] iwlwifi 0000:07:00.0: loaded firmware version 8.83.5.1 build 33692 op_mode iwldvm
[   27.024624] iwlwifi 0000:07:00.0: CONFIG_IWLWIFI_DEBUG disabled
[   27.024629] iwlwifi 0000:07:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[   27.024631] iwlwifi 0000:07:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[   27.024634] iwlwifi 0000:07:00.0: Detected Intel(R) WiFi Link 5100 AGN, REV=0x54
[   27.024685] iwlwifi 0000:07:00.0: L1 Enabled - LTR Disabled
[   27.053204] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   27.230490] acer_wmi: Acer Laptop ACPI-WMI Extras
[   27.230949] acer_wmi: Function bitmap for Communication Device: 0x17
[   27.230953] acer_wmi: Brightness must be controlled by acpi video driver
[   28.411729] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   31.143652] iwlwifi 0000:07:00.0: L1 Enabled - LTR Disabled
[   31.146689] iwlwifi 0000:07:00.0: Radio type=0x1-0x2-0x0
[   31.243106] iwlwifi 0000:07:00.0: L1 Enabled - LTR Disabled
[   31.246130] iwlwifi 0000:07:00.0: Radio type=0x1-0x2-0x0
[   31.276447] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   31.276746] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   37.701816] wlan0: authenticate with <MAC C-01 Sitecom59383F>
[   37.705972] wlan0: send auth to <MAC C-01 Sitecom59383F> (try 1/3)
[   37.708731] wlan0: authenticated
[   37.708914] wlan0: waiting for beacon from <MAC C-01 Sitecom59383F>
[   37.764035] wlan0: associate with <MAC C-01 Sitecom59383F> (try 1/3)
[   37.766783] wlan0: RX AssocResp from <MAC C-01 Sitecom59383F> (capab=0x411 status=0 aid=2)
[   37.769611] wlan0: associated
[   37.769958] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   37.831008] wlan0: deauthenticating from <MAC C-01 Sitecom59383F> by local choice (reason=2)
[   37.844431] wlan0: authenticate with <MAC C-01 Sitecom59383F>
[   37.845523] wlan0: send auth to <MAC C-01 Sitecom59383F> (try 1/3)
[   37.847871] wlan0: authenticated
[   37.852064] wlan0: associate with <MAC C-01 Sitecom59383F> (try 1/3)
[   37.855139] wlan0: RX AssocResp from <MAC C-01 Sitecom59383F> (capab=0x411 status=0 aid=2)
[   37.857907] wlan0: associated

    ======== Done ========


```

If any other information is needed, just tell me... thanks in advance for answering (and really sorry if my English is not so good...).

---

### Post by jeremy31 on 2014-12-24
I would do this ```
sudo iw reg set IT
``````
sudo rm /etc/modprobe.d/iwlwifi.conf~
``````
sudo rm /etc/modprobe.d/iwlwifi.conf.dpkg-old
```
Then```
gksudo gedit /etc/modprobe.d/iwlwifi.conf
``` and change the line ```
options iwlwifi 11n_disable=1
``` to ```
options iwlwifi 11n_disable=8
``` save, exit program and reboot

---

### Post by metamorph2 on 2014-12-26
Ok, here are some updates: yesterday, after launching the commands above and rebooting, I managed to connect to the Internet.

Today I couldn't connect, I checked the changes made yesterday and I noticed that the output of **iw reg get** was reverted back to
```
country US:
    (2402 - 2472 @ 40), (3, 27)
    (5170 - 5250 @ 40), (3, 17)
    (5250 - 5330 @ 40), (3, 20), DFS
    (5490 - 5600 @ 40), (3, 20), DFS
    (5650 - 5710 @ 40), (3, 20), DFS
    (5735 - 5835 @ 40), (3, 30)
    (57240 - 63720 @ 2160), (N/A, 40)

```
instead of
```
country 98:
    (2402 - 2472 @ 40), (N/A, 20)
    (5170 - 5250 @ 40), (N/A, 17)
    (5250 - 5330 @ 40), (N/A, 20), DFS
    (5490 - 5600 @ 40), (N/A, 20), DFS
    (5650 - 5710 @ 40), (N/A, 20), DFS
    (57240 - 63720 @ 2160), (N/A, 40), NO-OUTDOOR

```
May this missing change be the cause? How can I make it permanent?

---

### Post by jeremy31 on 2014-12-26
This might be a battle but there is a couple other places to set it ```
gksudo gedit /etc/default/crda
```
Make the last line will say```
REGDOMAIN=IT
``` save and exit program
And for good measure ```
echo "options cfg80211 ieee80211_regdom=IT" | sudo tee /etc/modprobe.d/cfg80211.conf
```
Reboot

---

### Post by metamorph2 on 2014-12-27
Well... guess what? Problems are still alive... ;(

This is what happened in detail yesterday:
- I powered down the laptop (booted with Windows). After a while I rebooted into Ubuntu and Wi-Fi **worked** even before changing the configuration files (as suggested in post #4)
- I made the changes anyway, rebooted the PC and Wi-Fi **still worked**: I could connect to the Internet during all the afternoon
- Yesterday evening I powered down the PC and unplugged it from AC. This morning I replugged and power it up and Wi-Fi **didn't work**.

I checked if the configuration files were reverted some way, this time they are correctly saved.

I don't know if unplugging the PC from AC can be of any significance: it seems that the Wi-Fi card resets itself each night (without any power supply, the battery in my laptop is failed), and can realign only if I start the PC with Windows the first time... by the way, even Windows for a few seconds boots with "No Internet access" on the Wi-Fi connection (after that, anyway, it becomes stable).

Any other idea? Thanks for answering...

---

### Post by praseodym on 2014-12-27
Check the deactivation of the queue, too:
```

echo "options iwlwifi 11n_disable=1 wd_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
```

---

### Post by metamorph2 on 2014-12-31
Sorry if I post just today: I made some tests on these days just to make sure the issue was "solved"...

Unfortunately even the changes in post #6 didn't make the job: I had still problems in connecting to the Internet.

Then I rebooted with Windows... and the AC charger broke down completely (blocking all the AC-working stuff in my house... thanks lifesaver). I had to replace it and, since then, no more connection problems...

I don't know why this solved the issue. Expecially, why the same wireless card and the same charger worked for a while with a different OS?

Anyway, thanks you all for your help. By the way, happy new year...

---

