---
title: "Wireless too slow and disconnecting itself"
date: 2014-12-13
forum: Networking &amp; Wireless
---

### Post by katenoox on 2014-12-13
Hello community,

I have recently bought Lenovo Yoga 2 (not Pro) laptop and I am dealing with probably all issues one can experience using its Intel wireless card.
Firstly I had to modify kernel following [this thread]("http://ubuntuforums.org/showthread.php?t=2215044&page=3"), because the wifi was hardblocked after the fresh installation.
Wlan is thanks to that not blocked anymore but its functionality is far from perfect. It is disconnecting every ~10 minutes and if it is not disconnected the speed is many times slower than on other notebooks in the house.

I was googling around and tried:

```
modprobe -r iwlwifi
modprobe iwlwifi 11n_disable=1
```

and

```
echo "options iwlwifi bt_coex_active=N swcrypto=1 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
```

but it did not work.
Could you please help me to fix this issue?

Here is the output of wireless-info script:

```


    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

kxb 3.13.0-37-generic x86_64, Linux Mint 17.1 Rebecca (Ubuntu 14.04.1 LTS)

CPU    : Intel(R) Core(TM) i7-4510U CPU @ 2.00GHz
Memory : 7913 MB
Uptime : 15:58:55 up 7 min,  3 users,  load average: 0,14, 0,19, 0,10


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

01:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b2] (rev 6b)
    Subsystem: Intel Corporation Wireless-N 7260 [8086:c262]
    Kernel driver in use: iwlwifi


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 001 Device 002: ID 8087:8000 Intel Corp.
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 007: ID 048d:8350 Integrated Technology Express, Inc.
Bus 002 Device 006: ID 8087:07dc Intel Corp.
Bus 002 Device 005: ID 04f2:b40f Chicony Electronics Co., Ltd
Bus 002 Device 004: ID 04f3:0304 Elan Microelectronics Corp.
Bus 002 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 002 Device 002: ID 18d1:4e21 Google Inc. Nexus S
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11bgn  ESSID:"blesmrt"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC C-01 blesmrt>   
          Bit Rate=1 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=38/70  Signal level=-72 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:3   Missed beacon:0



rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface        Soft blocked  Hard blocked
0: hci0: Bluetooth         no            no
1: phy0: Wireless LAN      no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

iwlmvm                189813  0
mac80211              630653  1 iwlmvm
iwlwifi               169932  1 iwlmvm
cfg80211              484040  3 iwlwifi,mac80211,iwlmvm


module parameters ~~~~~~~~~~~~~~~~~~

cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
iwlmvm        (2): init_dbg=N | power_scheme=2
iwlwifi      (11): amsdu_size_8K=0 | antenna_coupling=0 | bt_coex_active=Y | fw_restart=Y | led_mode=0 | nvm_file=(null) | power_level=0 | power_save=N | swcrypto=0 | wd_disable=1 | 11n_disable=0
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
==============================o=============o=========o===========o=========o===========o==============o===========
 Interface & ID               | Type        | Driver  | State     | Default | Speed     | Support      | HW Addr   
==============================o=============o=========o===========o=========o===========o==============o===========
 wlan0  [Automaticky blesmrt] | 802.11 WiFi | iwlwifi | connected | yes     | 1 Mb/s    | WEP/WPA/WPA2 | <MAC wlan0>

    *blesmrt:        Infra, <MAC C-01 blesmrt>, Freq 2437 MHz, Rate 54 Mb/s, Strength 50

    Address:         10.0.0.3
    Prefix:          24 (255.255.255.0)
    Gateway:         10.0.0.138
    DNS:             10.0.0.138
------------------------------+-------------+---------+-----------+---------+-----------+--------------+-----------


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

Automaticky blesmrt  : ssid=blesmrt | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto
Hotspot              : ssid=kxb | autoconnect=false | mac-address=<MAC wlan0> | ipv4=shared | ipv6=auto


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 127.0.1.1


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.0.0.138      0.0.0.0         UG    0      0        0 wlan0
10.0.0.0        0.0.0.0         255.255.255.0   U     9      0        0 wlan0

--- 10.0.0.138 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 34.818/35.567/36.316/0.749 ms

--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.030/0.041/0.052/0.011 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "cs_CZ.UTF-8")
country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     13 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 13 (2.472 GHz)

          Current Frequency:2.437 GHz (Channel 6)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 blesmrt>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:off
                    ESSID:"blesmrt"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000024448ac48d
                    Extra: Last beacon: 16ms ago


blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist ideapad-laptop

[/etc/modprobe.d/blacklist-ideapad.conf]
blacklist ideapad-laptop


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[iwlmvm]
filename:       /lib/modules/3.13.0-37-generic/kernel/drivers/net/wireless/iwlwifi/mvm/iwlmvm.ko
version:        in-tree:
srcversion:     D8BB21196A865641A4A81D0
depends:        iwlwifi,mac80211,cfg80211
parm:           init_dbg:set to true to debug an ASSERT in INIT fw (default: false (bool)
parm:           power_scheme:power management scheme: 1-active, 2-balanced, 3-low power, default: 2 (int)

[mac80211]
filename:       /lib/modules/3.13.0-37-generic/kernel/net/mac80211/mac80211.ko
srcversion:     B822641624778B987844F6F
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[iwlwifi]
filename:       /lib/modules/3.13.0-37-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
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
srcversion:     C2D0F3DFCA289585C100E36
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
filename:       /lib/modules/3.13.0-37-generic/kernel/net/wireless/cfg80211.ko
srcversion:     C2478077E22138832B71659
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x8086:0x08b2 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

# USB device 0x:0x (cdc_ether)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


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

BOOT_IMAGE=/boot/vmlinuz-3.13.0-37-generic root=UUID=67d54590-9f40-4920-b2eb-642508881a74 ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    1.363146] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    1.363466] audit: initializing netlink socket (disabled)
[    4.125494] iwlwifi 0000:01:00.0: irq 62 for MSI/MSI-X
[    4.140410] iwlwifi 0000:01:00.0: loaded firmware version 22.24.8.0 op_mode iwlmvm
[    4.165601] iwlwifi 0000:01:00.0: Detected Intel(R) Wireless N 7260, REV=0x144
[    4.165653] iwlwifi 0000:01:00.0: L1 Disabled; Enabling L0S
[    4.165871] iwlwifi 0000:01:00.0: L1 Disabled; Enabling L0S
[    4.175501] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    4.372475] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[    4.872743] iwlwifi 0000:01:00.0: L1 Disabled; Enabling L0S
[    4.872960] iwlwifi 0000:01:00.0: L1 Disabled; Enabling L0S
[    4.884027] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    4.884311] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    5.631040] wlan0: authenticate with <MAC C-01 blesmrt>
[    5.632962] wlan0: direct probe to <MAC C-01 blesmrt> (try 1/3)
[    5.835062] wlan0: direct probe to <MAC C-01 blesmrt> (try 2/3)
[    6.039405] wlan0: send auth to <MAC C-01 blesmrt> (try 3/3)
[    6.040937] wlan0: authenticated
[    6.041165] iwlwifi 0000:01:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[    6.041169] iwlwifi 0000:01:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[    6.042626] wlan0: associate with <MAC C-01 blesmrt> (try 1/3)
[    6.044482] wlan0: RX AssocResp from <MAC C-01 blesmrt> (capab=0x1 status=0 aid=2)
[    6.045292] wlan0: associated
[    6.045312] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   35.514664] wlan0: authenticate with <MAC C-01 blesmrt>
[   35.516323] wlan0: send auth to <MAC C-01 blesmrt> (try 1/3)
[   35.521033] wlan0: authenticated
[   35.521442] iwlwifi 0000:01:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   35.521452] iwlwifi 0000:01:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   35.524716] wlan0: associate with <MAC C-01 blesmrt> (try 1/3)
[   35.529222] wlan0: RX AssocResp from <MAC C-01 blesmrt> (capab=0x1 status=0 aid=2)
[   35.530259] wlan0: associated
[  218.811728] wlan0: authenticate with <MAC C-01 blesmrt>
[  218.813372] wlan0: send auth to <MAC C-01 blesmrt> (try 1/3)
[  218.983563] wlan0: send auth to <MAC C-01 blesmrt> (try 2/3)
[  218.989826] wlan0: authenticated
[  218.990161] iwlwifi 0000:01:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  218.990174] iwlwifi 0000:01:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  218.990720] wlan0: associate with <MAC C-01 blesmrt> (try 1/3)
[  218.999034] wlan0: RX AssocResp from <MAC C-01 blesmrt> (capab=0x1 status=0 aid=2)
[  219.000054] wlan0: associated

    ======== Done ========


```

---

### Post by jeremy31 on 2014-12-13
Try ```
echo "options iwlwifi 11n_disable=8" | sudo tee -a /etc/modprobe.d/iwlwifi.conf
``````
sudo modprobe -r iwlwifi
``````
sudo modprobe iwlwifi
```

---

### Post by katenoox on 2014-12-14
Thank you for your fast reply, I have tested it from the time you posted your answer.
Parameter 11n_disable=8 improved disconnecting issue to once every ~3 hours. But the terrible slow speed did not change. At the moment I am downloading 3KB/s and pages, which I try to load most of the time timeout.

I have also tried to combine parameters like:

```
options iwlwifi swcrypto=1 11n_disable=8
```
or even
```
options iwlwifi swcrypto=1
```
which behaves faster but still not as fast as other computers in the house and still disconnects every ~3 hours.

Have you got any other suggestions/improvements worth to try?

---

### Post by David_OConnor on 2015-04-14
Same issue. This is really frustrating.

---

### Post by Mahendra_Sahasrabu on 2015-04-15
I had same issue on intel nuc with 7260 card and Mint 17.1. I have read that this is fixed kernel version 3.17. However following worked for me with existing kernel 3.13.0-37-generic #64
Download 
[https://launchpad.net/ubuntu/+source/linux-firmware/1.143](https://launchpad.net/ubuntu/+source/linux-firmware/1.143)
**copy iwlwifi-7260-9.ucode from extracted to /lib/firmware**
**remove iwlwifi-7260-8.ucode from  /lib/firmware**
/lib/firmware has **iwlwifi-7260-7.ucode **and **iwlwifi-7260-9.ucode **only. not 8
---
update :
Sorry  I may have been wrong.. My problem still persists.  This is really frustrating. This is supposed to be intel's latest wifi card behaves extremely poorly in terms of speed and has several disconnects and at times it fails to find my wifi router. My 5 year old netbook's old wifi card connects flawlessly to same router and  from the same physical location.

---

### Post by jeremy31 on 2015-04-26
You could try the latest firmware version for the 7260
```
wget https://wireless.wiki.kernel.org/_media/en/users/drivers/iwlwifi-7260-ucode-25.16.12.0.tgz
```
```
tar zxvf iwlwifi-7260-ucode-25.16.12.0.tgz
```

Then you may be able to get it to load by changing the name 
```
mkdir iwlwifi-back
```
```
cp /lib/firmware/iwlwifi-7260-*.ucode ~/iwlwifi-back/
```
```
cd iwlwifi-7260-ucode-25.16.12.0
```
```
sudo cp iwlwifi-7260-12.ucode /lib/firmware/iwlwifi-7260-9.ucode
``` and reboot

Depending on your kernel version you may need to change iwlwifi-7260-9.ucode to iwlwifi-7260-8.ucode in the last command for it to load

If it fails to work, you can restore the old ucode with
```
sudo cp /iwlwifi-back/iwlwifi-7260-*.ucode /lib/firmware/
```

---

### Post by ecborder on 2015-04-27
I have the same issue, just had to switch from windows where the card worked really well.

---

