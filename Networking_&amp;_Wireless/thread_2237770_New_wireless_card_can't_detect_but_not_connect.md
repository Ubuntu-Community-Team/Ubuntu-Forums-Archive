---
title: "New wireless card can't detect but not connect"
date: 2014-08-03
forum: Networking &amp; Wireless
---

### Post by PenguinLust on 2014-08-03
Yesterday I posted a problem w/my old wireless card ([http://ubuntuforums.org/showthread.php?t=2237588](http://ubuntuforums.org/showthread.php?t=2237588)), which I suspected broken. Before I could get any responses, I bought a new one. Unfortunately, it's behaving in exactly the same way. I can detect my access point, but I can't use it. Here's what I see in dmesg:
```
[   78.415659] wlan1: send auth to 00:14:6c:a2:0d:02 (try 1/3)
[   78.417991] wlan1: authenticated
[   78.418295] ath9k 0000:03:00.0 wlan1: disabling HT as WMM/QoS is not supported by the AP
[   78.418306] ath9k 0000:03:00.0 wlan1: disabling VHT as WMM/QoS is not supported by the AP
[   78.419903] wlan1: associate with 00:14:6c:a2:0d:02 (try 1/3)
[   78.523897] wlan1: associate with 00:14:6c:a2:0d:02 (try 2/3)
[   78.627897] wlan1: associate with 00:14:6c:a2:0d:02 (try 3/3)
[   78.731894] wlan1: association with 00:14:6c:a2:0d:02 timed out

```
and lspci -v:
```
03:00.0 Network controller: Qualcomm Atheros AR9287 Wireless Network Adapter (PCI-Express) (rev 01)
    Subsystem: Qualcomm Atheros Device 30a4
    Flags: bus master, fast devsel, latency 0, IRQ 19
    Memory at febe0000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: ath9k

```
I have it setup using infrastructure mode and all the defaults including WPA & WPA2 Personal. I'm running Ubuntu 14.04 AMD64. Anything else? The module is loaded. In fact, a few of them are:
```
ath9k                 164164  0 
ath9k_common           13551  1 ath9k
ath9k_hw              453856  2 ath9k_common,ath9k
ath                    28698  3 ath9k_common,ath9k,ath9k_hw
mac80211              630653  1 ath9k

```

---

### Post by varunendra on 2014-08-04
Eh, I just replied at your previous thread before noticing this one :p

But now that you have two cards, it can actually help troubleshooting the problem. But assuming you'll have to swap the card to try it, let's start with the current one. If we can't fix the issue with this one, we may try the older one again.

Please post the same script report that I asked for in your previous thread.

---

### Post by PenguinLust on 2014-08-04
Ok, what does that tell you (other than the fact that I've got a really long Ethernet cable plugged into my on-board LAN port as a backup)?
```

    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

bootsie 3.13.0-32-generic x86_64,  Ubuntu 14.04.1 LTS, trusty

CPU    : AMD Phenom(tm) II X4 955 Processor
Memory : 3952 MB
Uptime : 17:36:03 up 7 min,  2 users,  load average: 0.25, 0.34, 0.21


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

03:00.0 Network controller [0280]: Qualcomm Atheros AR9287 Wireless Network Adapter (PCI-Express) [168c:002e] (rev 01)
    Subsystem: Qualcomm Atheros Device [168c:30a4]
    Kernel driver in use: ath9k
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
    Subsystem: ASUSTeK Computer Inc. P8P67 and other motherboards [1043:8432]
    Kernel driver in use: r8169


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 004: ID 045e:0039 Microsoft Corp. IntelliMouse Optical
Bus 004 Device 003: ID 413c:2010 Dell Computer Corp. Keyboard
Bus 004 Device 002: ID 413c:1003 Dell Computer Corp. Keyboard Hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan1     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface        Soft blocked  Hard blocked
0: phy0: Wireless LAN      no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

ath9k                 164164  0 
ath9k_common           13551  1 ath9k
ath9k_hw              453856  2 ath9k_common,ath9k
ath                    28698  3 ath9k_common,ath9k,ath9k_hw
mac80211              630653  1 ath9k
cfg80211              484040  3 ath,ath9k,mac80211
mxm_wmi                13021  1 nouveau
wmi                    19177  2 mxm_wmi,nouveau


module parameters ~~~~~~~~~~~~~~~~~~

ath9k         (5): blink=0 | bt_ant_diversity=0 | btcoex_enable=0 | nohwcrypt=0 | ps_enable=0
cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
============================o=============o========o==============o=========o===========o==============o===========
 Interface & ID             | Type        | Driver | State        | Default | Speed     | Support      | HW Addr   
============================o=============o========o==============o=========o===========o==============o===========
 eth1  [Wired connection 2] | Wired       | r8169  | connected    | yes     | 100 Mb/s  |              | <MAC eth1>

    Address:         10.0.0.5
    Prefix:          24 (255.255.255.0)
    Gateway:         10.0.0.1
    DNS:             10.0.0.1
----------------------------+-------------+--------+--------------+---------+-----------+--------------+-----------
 wlan1                      | 802.11 WiFi | ath9k  | disconnected | no      |           | WEP/WPA/WPA2 | <MAC wlan1>

    heater-needing:  Infra, <MAC C-01 heater-needing>, Freq 2427 MHz, Rate 54 Mb/s, Strength 54 WPA2
    Bell_Network2:   Infra, <MAC C-02 Bell_Network2>, Freq 2437 MHz, Rate 54 Mb/s, Strength 52 WPA
----------------------------+-------------+--------+--------------+---------+-----------+--------------+-----------


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

heater-needing       : ssid=heater-needing | mac-address=<MAC wlan1> | ipv4=auto | ipv6=auto 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 127.0.1.1


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.0.0.1        0.0.0.0         UG    0      0        0 eth1
10.0.0.0        0.0.0.0         255.255.255.0   U     1      0        0 eth1

--- 10.0.0.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1000ms
rtt min/avg/max/mdev = 0.731/0.759/0.788/0.039 ms

--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.037/0.041/0.046/0.007 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "en_CA.UTF-8")
country CN:
    (2402 - 2482 @ 40), (N/A, 20)
    (5735 - 5835 @ 40), (N/A, 30)
    (57240 - 59400 @ 2160), (N/A, 28)
    (59400 - 63720 @ 2160), (N/A, 44)
    (63720 - 65880 @ 2160), (N/A, 28)


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan1     13 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 13 (2.472 GHz)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan1     Scan completed :
          Cell 01 - Address: <MAC C-01 heater-needing>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"heater-needing"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000002839536569
                    Extra: Last beacon: 4ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
          Cell 02 - Address: <MAC C-02 Bell_Network2>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=45/70  Signal level=-65 dBm  
                    Encryption key:on
                    ESSID:"Bell_Network2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000c01e210f
                    Extra: Last beacon: 4ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK


blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[ath9k]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
srcversion:     7EAAD420ADF6B9354F0C8C1
depends:        ath9k_hw,mac80211,ath9k_common,cfg80211,ath
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)

[ath9k_common]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
srcversion:     696B00A6C59713EC0966997
depends:        ath,ath9k_hw

[ath9k_hw]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
srcversion:     4809F3842A0542CD6B556D3
depends:        ath

[ath]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/ath/ath.ko
srcversion:     88A67C5359B02C5A710AFCF
depends:        cfg80211

[mac80211]
filename:       /lib/modules/3.13.0-32-generic/kernel/net/mac80211/mac80211.ko
srcversion:     8ADA881D348148A3358334C
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-32-generic/kernel/net/wireless/cfg80211.ko
srcversion:     E786D076B61F97809B04B64
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[mxm_wmi]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/platform/x86/mxm-wmi.ko
srcversion:     62CBD37DE87DF0C4CD7FBA3
depends:        wmi

[wmi]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/platform/x86/wmi.ko
srcversion:     CED5410F008DC70DF5F064B
depends:        
parm:           debug_event:Log WMI Events [0/1] (bool)
parm:           debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x10ec:0x8169 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x1814:0x0401 (rt61pci)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

# PCI device 0x168c:0x002e (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan1>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"

# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth1>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"


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

BOOT_IMAGE=/boot/vmlinuz-3.13.0-32-generic root=UUID=f7c1939e-6939-417e-af42-7f9980294b87 ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    1.767502] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    1.767731] audit: initializing netlink socket (disabled)
[    2.156831] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[   11.577405] wmi: Mapper loaded
[   11.685647] systemd-udevd[326]: renamed network interface eth0 to eth1
[   12.326291] ath: EEPROM regdomain: 0x809c
[   12.326294] ath: EEPROM indicates we should expect a country code
[   12.326296] ath: doing EEPROM country->regdmn map search
[   12.326297] ath: country maps to regdmn code: 0x52
[   12.326298] ath: Country alpha2 being used: CN
[   12.326299] ath: Regpair used: 0x52
[   12.441044] systemd-udevd[335]: renamed network interface wlan0 to wlan1
[   16.065414] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   17.151364] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   17.155302] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   17.326904] r8169 0000:04:00.0 eth1: link down
[   17.326950] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[   17.327209] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[   17.345697] r8169 0000:04:00.0 eth1: link down
[   18.977407] r8169 0000:04:00.0 eth1: link up
[   18.977416] IPv6: ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready

    ======== Done ========
```

---

### Post by varunendra on 2014-08-04
> **PenguinLust said:**
> Ok, what does that tell you (other than the fact that I've got a really long Ethernet cable plugged into my on-board LAN port as a backup)?
....

Nothing, other than the fact that the system never even tried to connect to the wireless since booting, obviously because it already got a wired connection.

I suggest deleting the current udev rules file to bring logical names to default wlan0, eth0. Usually not necessary but keeping things at defaults would be a good idea -
```
sudo rm /etc/udev/rules.d/70-persistent-net.rules
```

Additional changes -

[INDENT]**1)** Try setting the channel from 4 (or 'auto') to 1 or 11 in the router.

**2)** If the bandwidth in the router is set to 20/40 MHz auto mode, try fixing it to 20 MHz just for a test. If it works, you may enable 20/40 MHz again to see if it keeps working (in case it worked due to other settings suggested here).

**3)** Set "IPv6" to "Ignore" in Network Manager settings for the connection (when it is generated again).

**4)** Set a driver parameter quite often needed with ath9k driver -
```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
```[/INDENT]

..then disconnect the cable > reboot > try to connect via wireless > run the script again to generate a fresh report > post it back here.

And are you in China? Your language settings are for Canada, but the RegDomain code is set for China. Although the frequency/bandwidth settings for both Canada and China look same for channels 1-14, I suggest keeping it same as per the country setting in your router.

For example, if the country setting in your router is "Canada", you should try explicitly defining "CA" for regdomain settings. To do this permanently -
```
sudo sed -i 's/^REG.*=$/&CA/' /etc/default/crda
```
Of course change "CA" to the code of the country which you are in (and which should be set in the Router). A list of country codes : [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2#Decoding_table](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2#Decoding_table)

This will take effect after a reboot. To enforce the new settings immediately without rebooting -
```
sudo iw reg set CA
```


**PS:**
By the way, since both old and newer cards are having similar problems, have you tried to factory-reset the router/modem and configure it again? You can 'Export' its firmware & settings to a file if you want to save its current settings in case you need to revert to current state.

---

### Post by PenguinLust on 2014-08-06
Here's the new one, after disabling the wirefull Ethernet.
China, eh? No, I'm thoroughly foreign devil. I made the change back to Canada, as you instructed, although it was after I ran the diagnostic.
No, I haven't tried resetting the router. Is that next?
```

    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

bootsie 3.13.0-32-generic x86_64,  Ubuntu 14.04.1 LTS, trusty

CPU    : AMD Phenom(tm) II X4 955 Processor
Memory : 3952 MB
Uptime : 23:46:28 up 2 min,  2 users,  load average: 0.45, 0.25, 0.10


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

03:00.0 Network controller [0280]: Qualcomm Atheros AR9287 Wireless Network Adapter (PCI-Express) [168c:002e] (rev 01)
    Subsystem: Qualcomm Atheros Device [168c:30a4]
    Kernel driver in use: ath9k


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 004: ID 045e:0039 Microsoft Corp. IntelliMouse Optical
Bus 004 Device 003: ID 413c:2010 Dell Computer Corp. Keyboard
Bus 004 Device 002: ID 413c:1003 Dell Computer Corp. Keyboard Hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface        Soft blocked  Hard blocked
0: phy0: Wireless LAN      no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

ath9k                 164164  0 
ath9k_common           13551  1 ath9k
ath9k_hw              453856  2 ath9k_common,ath9k
ath                    28698  3 ath9k_common,ath9k,ath9k_hw
mac80211              630653  1 ath9k
mxm_wmi                13021  1 nouveau
cfg80211              484040  3 ath,ath9k,mac80211
wmi                    19177  2 mxm_wmi,nouveau


module parameters ~~~~~~~~~~~~~~~~~~

ath9k         (5): blink=0 | bt_ant_diversity=0 | btcoex_enable=0 | nohwcrypt=1 | ps_enable=0
cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: disconnected
================o=============o========o==============o=========o===========o==============o===========
 Interface & ID | Type        | Driver | State        | Default | Speed     | Support      | HW Addr   
================o=============o========o==============o=========o===========o==============o===========
 wlan0          | 802.11 WiFi | ath9k  | disconnected | no      |           | WEP/WPA/WPA2 | <MAC wlan0>

    Bell_Network2:   Infra, <MAC C-01 Bell_Network2>, Freq 2437 MHz, Rate 54 Mb/s, Strength 62 WPA
    heater-needing:  Infra, <MAC C-02 heater-needing>, Freq 2427 MHz, Rate 54 Mb/s, Strength 45 WPA2
----------------+-------------+--------+--------------+---------+-----------+--------------+-----------


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

no-auto-default=<MAC ID removed>,

[ifupdown]
managed=false


NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~

heater-needing       : ssid=heater-needing | mac-address=<MAC wlan0> | ipv4=auto | ipv6=ignore 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~



Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "en_CA.UTF-8")
country CN:
    (2402 - 2482 @ 40), (N/A, 20)
    (5735 - 5835 @ 40), (N/A, 30)
    (57240 - 59400 @ 2160), (N/A, 28)
    (59400 - 63720 @ 2160), (N/A, 44)
    (63720 - 65880 @ 2160), (N/A, 28)


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     13 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 13 (2.472 GHz)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 Bell_Network2>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=51/70  Signal level=-59 dBm  
                    Encryption key:on
                    ESSID:"Bell_Network2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000163cb5188
                    Extra: Last beacon: 4ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC C-02 heater-needing>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:on
                    ESSID:"heater-needing"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000055a1a20e1d
                    Extra: Last beacon: 4ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported


blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[ath9k]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
srcversion:     7EAAD420ADF6B9354F0C8C1
depends:        ath9k_hw,mac80211,ath9k_common,cfg80211,ath
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)

[ath9k_common]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
srcversion:     696B00A6C59713EC0966997
depends:        ath,ath9k_hw

[ath9k_hw]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
srcversion:     4809F3842A0542CD6B556D3
depends:        ath

[ath]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/ath/ath.ko
srcversion:     88A67C5359B02C5A710AFCF
depends:        cfg80211

[mac80211]
filename:       /lib/modules/3.13.0-32-generic/kernel/net/mac80211/mac80211.ko
srcversion:     8ADA881D348148A3358334C
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[mxm_wmi]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/platform/x86/mxm-wmi.ko
srcversion:     62CBD37DE87DF0C4CD7FBA3
depends:        wmi

[cfg80211]
filename:       /lib/modules/3.13.0-32-generic/kernel/net/wireless/cfg80211.ko
srcversion:     E786D076B61F97809B04B64
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[wmi]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/platform/x86/wmi.ko
srcversion:     CED5410F008DC70DF5F064B
depends:        
parm:           debug_event:Log WMI Events [0/1] (bool)
parm:           debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x168c:0x002e (ath9k)
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


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/boot/vmlinuz-3.13.0-32-generic root=UUID=f7c1939e-6939-417e-af42-7f9980294b87 ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    1.771012] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    1.771289] audit: initializing netlink socket (disabled)
[   10.812797] wmi: Mapper loaded
[   10.981660] ath: EEPROM regdomain: 0x809c
[   10.981663] ath: EEPROM indicates we should expect a country code
[   10.981664] ath: doing EEPROM country->regdmn map search
[   10.981665] ath: country maps to regdmn code: 0x52
[   10.981667] ath: Country alpha2 being used: CN
[   10.981667] ath: Regpair used: 0x52
[   15.845963] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   16.934595] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   16.937617] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   24.860724] wlan0: authenticate with <MAC C-02 heater-needing>
[   24.887584] wlan0: send auth to <MAC C-02 heater-needing> (try 1/3)
[   24.889531] wlan0: authenticated
[   24.889643] ath9k 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   24.889646] ath9k 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   24.892370] wlan0: associate with <MAC C-02 heater-needing> (try 1/3)
[   24.996357] wlan0: associate with <MAC C-02 heater-needing> (try 2/3)
[   25.100358] wlan0: associate with <MAC C-02 heater-needing> (try 3/3)
[   25.204358] wlan0: association with <MAC C-02 heater-needing> timed out
[   26.064655] wlan0: authenticate with <MAC C-02 heater-needing>
[   26.083387] wlan0: send auth to <MAC C-02 heater-needing> (try 1/3)
[   26.085296] wlan0: authenticated
[   26.085407] ath9k 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   26.085411] ath9k 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   26.088358] wlan0: associate with <MAC C-02 heater-needing> (try 1/3)
[   26.192343] wlan0: associate with <MAC C-02 heater-needing> (try 2/3)
[   26.296345] wlan0: associate with <MAC C-02 heater-needing> (try 3/3)
[   26.404341] wlan0: association with <MAC C-02 heater-needing> timed out
[   27.660639] wlan0: authenticate with <MAC C-02 heater-needing>
[   27.679424] wlan0: send auth to <MAC C-02 heater-needing> (try 1/3)
[   27.681271] wlan0: authenticated
[   27.681364] ath9k 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   27.681367] ath9k 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   27.684336] wlan0: associate with <MAC C-02 heater-needing> (try 1/3)
[   27.792334] wlan0: associate with <MAC C-02 heater-needing> (try 2/3)
[   27.896329] wlan0: associate with <MAC C-02 heater-needing> (try 3/3)
[   28.000329] wlan0: association with <MAC C-02 heater-needing> timed out
[   29.760616] wlan0: authenticate with <MAC C-02 heater-needing>
[   29.779357] wlan0: send auth to <MAC C-02 heater-needing> (try 1/3)
[   29.781197] wlan0: authenticated
[   29.781306] ath9k 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   29.781309] ath9k 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   29.784316] wlan0: associate with <MAC C-02 heater-needing> (try 1/3)
[   29.892317] wlan0: associate with <MAC C-02 heater-needing> (try 2/3)
[   29.996304] wlan0: associate with <MAC C-02 heater-needing> (try 3/3)
[   30.100298] wlan0: association with <MAC C-02 heater-needing> timed out
[   41.612550] wlan0: authenticate with <MAC C-02 heater-needing>
[   41.631307] wlan0: send auth to <MAC C-02 heater-needing> (try 1/3)
[   41.633147] wlan0: authenticated
[   41.633253] ath9k 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   41.633257] ath9k 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   41.636191] wlan0: associate with <MAC C-02 heater-needing> (try 1/3)
[   41.740183] wlan0: associate with <MAC C-02 heater-needing> (try 2/3)
[   41.844182] wlan0: associate with <MAC C-02 heater-needing> (try 3/3)
[   41.948183] wlan0: association with <MAC C-02 heater-needing> timed out
[   62.388343] wlan0: authenticate with <MAC C-02 heater-needing>
[   62.407028] wlan0: send auth to <MAC C-02 heater-needing> (try 1/3)
[   62.408861] wlan0: authenticated
[   62.408962] ath9k 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   62.408965] ath9k 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   62.411982] wlan0: associate with <MAC C-02 heater-needing> (try 1/3)
[   62.515979] wlan0: associate with <MAC C-02 heater-needing> (try 2/3)
[   62.619968] wlan0: associate with <MAC C-02 heater-needing> (try 3/3)
[   62.723969] wlan0: association with <MAC C-02 heater-needing> timed out
[   73.488214] wlan0: authenticate with <MAC C-02 heater-needing>
[   73.506956] wlan0: send auth to <MAC C-02 heater-needing> (try 1/3)
[   73.508797] wlan0: authenticated
[   73.508893] ath9k 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   73.508896] ath9k 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   73.511868] wlan0: associate with <MAC C-02 heater-needing> (try 1/3)
[   73.615855] wlan0: associate with <MAC C-02 heater-needing> (try 2/3)
[   73.719853] wlan0: associate with <MAC C-02 heater-needing> (try 3/3)
[   73.827865] wlan0: association with <MAC C-02 heater-needing> timed out
[   91.901385] wlan0: authenticate with <MAC C-02 heater-needing>
[   91.919117] wlan0: send auth to <MAC C-02 heater-needing> (try 1/3)
[   91.921024] wlan0: authenticated
[   91.921167] ath9k 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   91.921171] ath9k 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   91.923733] wlan0: associate with <MAC C-02 heater-needing> (try 1/3)
[   92.027709] wlan0: associate with <MAC C-02 heater-needing> (try 2/3)
[   92.131731] wlan0: associate with <MAC C-02 heater-needing> (try 3/3)
[   92.235713] wlan0: association with <MAC C-02 heater-needing> timed out
[  103.000529] wlan0: authenticate with <MAC C-02 heater-needing>
[  103.018789] wlan0: send auth to <MAC C-02 heater-needing> (try 1/3)
[  103.020779] wlan0: authenticated
[  103.020903] ath9k 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  103.020907] ath9k 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  103.023594] wlan0: associate with <MAC C-02 heater-needing> (try 1/3)
[  103.127584] wlan0: associate with <MAC C-02 heater-needing> (try 2/3)
[  103.231613] wlan0: associate with <MAC C-02 heater-needing> (try 3/3)
[  103.335597] wlan0: association with <MAC C-02 heater-needing> timed out

    ======== Done ========
```

---

### Post by praseodym on 2014-08-07
Now you need nameservers in your /etc/resolv.conf:
```

echo -e "nameserver 8.8.8.8\nnameserver 8.8.4.4" | sudo tee /etc/resolv.conf
sudo service network-manager restart
```
Additionally, "ignore" IPv6 in your network profile

---

### Post by PenguinLust on 2014-08-07
I thought the idea of DHCP was that it took care of /etc/resolve.conf.
What's "8.8.8.8" and "8.8.4.4"?
I thought I had set IPv6 to ignore, but I could check it again.
I'd be a bit surprised if this worked, because nameservers is a layer 3 issue and the wi-fi is below that and is what fails.

---

### Post by varunendra on 2014-08-08
Can you post the details of your router settings including country setting (for Regulatory Domain settings)?

Everything with the settings in Ubuntu looks fine to me (yes, including the resolv.conf file, which is dynamically updated if the Network Manager is using "dnsmasq" method, which it is as per your "NetworkManager.conf" file).

Still, assuming the failure may be due to a failed DHCP negotiation, please try manually setting a suitable IP configuration in Network Manager.

And yes, resetting the router to factory defaults is one of the possible solutions if you know how to do the '_Basic_' settings again (no advanced settings like firewall rules, port forwarding or MAC filtering please, at least while we are troubleshooting the wifi).

**PS:**
8.8.8.8 and 8.8.4.4 are popular DNS servers offered by Google.

---

### Post by PenguinLust on 2014-08-09
You'll have to be more specific about what router details you want, because I don't seem to be able to export them to text. The region is set to "United States" (and that combo box is greyed out for some reason). Despite what an earlier post might have suggested, I live in Canada. I can also tell you that the "mode" used to be "b and g" but I just tried changing it to "Auto 108Mps" and now it insists on using channel 6 and it still doesn't work.
I tried changing the interface settings to use a static IP instead of a dynamic one and it still failed.
Now I'm going to try resetting the router, but if I don't post back, assume it didn't work. It wouldn't be right if it did, because of the half dozen wi-fi devices I've used around here, I haven't had a problem w/any of them.

---

### Post by varunendra on 2014-08-12
> **PenguinLust said:**
> The region is set to "United States" (and that combo box is greyed out for some reason). Despite what an earlier post might have suggested, I live in Canada.
As per the last wireless_script report you posted, your RegDomain setting in Ubuntu is still set to 'CN' (China). So either you didn't try the "sed..." command I suggested for changing it, or there may have been some error while running it, most probably a typo. If you didn't try that, please do so now. If you tried, please show us the output of -
```
cat /etc/default/crda
```
After a few comment lines, it should show -
```
REGDOMAIN=CA
```
If it doesn't show 'CA', the command didn't execute correctly, please try it again.

> I can also tell you that the "mode" used to be "b and g" but I just tried changing it to "Auto 108Mps" and now it insists on using channel 6 and it still doesn't work.
"Auto 108Mps" sounds like an auto b/g/n mode, or maybe the auto part is just for the channel selection (the router will choose the channel it *thinks* is best depending on neighbouring signals). In any case, anything above 54 Mbps means N-channel and 108 means it is probably not very well supported by the router. As such, can you please try fixing it to g-only mode? It shouldn't be a big deal, but depending upon the quality of router's firmware, the N-channel implementation may be problematic sometimes.

> Now I'm going to try resetting the router, but if I don't post back, assume it didn't work. It wouldn't be right if it did, because of the half dozen wi-fi devices I've used around here, I haven't had a problem w/any of them.
If the settings are all okay, the ath9k driver should have worked. It has been reported to have some issues lately, but works. I don't know of any way to confirm whether the problem lies in the router or not (except trying a different router), but "Other devices work" - is never a proof of everything being alright in the router.

All drivers and firmware are programmed to ignore/tolerate some level of inconsistency/unusual behaviour on the "Other" side. It means even if one side (the driver or the router firmware) is buggy, the other side is supposed to somehow deal with it and continue the connection. Now due to rapidly changing kernel code since version 3.8, many drivers, including ath9k have been facing some regression. So while the problem may be in Ubuntu/kernel/driver, it is also quite possible that your router may have some kind of issue in its firmware that the newer versions of ath9k driver can't tolerate.

You may try an older version of Ubuntu (say, 12.04 or 12.04.1 or anything that uses kernel version older than 3.8) to see if the older ath9k driver in it works well with the same settings. But this kind of test is probably pointless, since the old driver will almost certainly fail to compile on the latest kernels, and I don't think using such an old kernel just for wifi is such a good idea, unless the wifi is really the most critical requirement for you.

**PS:**
If you can give us link to your router's user manual, it may help us a lot to see if there are any funny settings that need to be crosschecked/modified.

---

### Post by PenguinLust on 2014-08-12
Like I mentioned earlier, I fixed the region problem in software after running the script. Here it is again w/no mention of China:
```

    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

bootsie 3.13.0-32-generic x86_64,  Ubuntu 14.04.1 LTS, trusty

CPU    : AMD Phenom(tm) II X4 955 Processor
Memory : 3952 MB
Uptime : 20:08:43 up 1 min,  2 users,  load average: 0.75, 0.37, 0.14


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

03:00.0 Network controller [0280]: Qualcomm Atheros AR9287 Wireless Network Adapter (PCI-Express) [168c:002e] (rev 01)
    Subsystem: Qualcomm Atheros Device [168c:30a4]
    Kernel driver in use: ath9k


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 004: ID 045e:0039 Microsoft Corp. IntelliMouse Optical
Bus 004 Device 003: ID 413c:2010 Dell Computer Corp. Keyboard
Bus 004 Device 002: ID 413c:1003 Dell Computer Corp. Keyboard Hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface        Soft blocked  Hard blocked
0: phy0: Wireless LAN      no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

ath9k                 164164  0 
ath9k_common           13551  1 ath9k
ath9k_hw              453856  2 ath9k_common,ath9k
ath                    28698  3 ath9k_common,ath9k,ath9k_hw
mac80211              630653  1 ath9k
cfg80211              484040  3 ath,ath9k,mac80211
mxm_wmi                13021  1 nouveau
wmi                    19177  2 mxm_wmi,nouveau


module parameters ~~~~~~~~~~~~~~~~~~

ath9k         (5): blink=0 | bt_ant_diversity=0 | btcoex_enable=0 | nohwcrypt=1 | ps_enable=0
cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: disconnected
================o=============o========o==============o=========o===========o==============o===========
 Interface & ID | Type        | Driver | State        | Default | Speed     | Support      | HW Addr   
================o=============o========o==============o=========o===========o==============o===========
 wlan0          | 802.11 WiFi | ath9k  | disconnected | no      |           | WEP/WPA/WPA2 | <MAC wlan0>

    Bell_Network2:   Infra, <MAC C-01 Bell_Network2>, Freq 2462 MHz, Rate 54 Mb/s, Strength 54 WPA
    heater-needing:  Infra, <MAC C-02 heater-needing>, Freq 2412 MHz, Rate 54 Mb/s, Strength 64 WPA2
----------------+-------------+--------+--------------+---------+-----------+--------------+-----------


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

no-auto-default=<MAC ID removed>,<MAC eth0>,

[ifupdown]
managed=false


NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~

heater-needing       : ssid=heater-needing | mac-address=<MAC wlan0> | ipv4=manual | ipv6=ignore 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~



Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "en_CA.UTF-8")
country CA:
    (2402 - 2472 @ 40), (3, 27)
    (5170 - 5250 @ 40), (3, 17)
    (5250 - 5330 @ 40), (3, 20), DFS
    (5490 - 5710 @ 40), (3, 20), DFS
    (5735 - 5835 @ 40), (3, 30)


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     11 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 11 (2.462 GHz)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 Bell_Network2>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=47/70  Signal level=-63 dBm  
                    Encryption key:on
                    ESSID:"Bell_Network2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000003a6b282a9c
                    Extra: Last beacon: 20ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC C-02 heater-needing>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=50/70  Signal level=-60 dBm  
                    Encryption key:on
                    ESSID:"heater-needing"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000107013d2
                    Extra: Last beacon: 20ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported


blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[ath9k]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
srcversion:     7EAAD420ADF6B9354F0C8C1
depends:        ath9k_hw,mac80211,ath9k_common,cfg80211,ath
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)

[ath9k_common]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
srcversion:     696B00A6C59713EC0966997
depends:        ath,ath9k_hw

[ath9k_hw]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
srcversion:     4809F3842A0542CD6B556D3
depends:        ath

[ath]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/ath/ath.ko
srcversion:     88A67C5359B02C5A710AFCF
depends:        cfg80211

[mac80211]
filename:       /lib/modules/3.13.0-32-generic/kernel/net/mac80211/mac80211.ko
srcversion:     8ADA881D348148A3358334C
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-32-generic/kernel/net/wireless/cfg80211.ko
srcversion:     E786D076B61F97809B04B64
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[mxm_wmi]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/platform/x86/mxm-wmi.ko
srcversion:     62CBD37DE87DF0C4CD7FBA3
depends:        wmi

[wmi]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/platform/x86/wmi.ko
srcversion:     CED5410F008DC70DF5F064B
depends:        
parm:           debug_event:Log WMI Events [0/1] (bool)
parm:           debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x168c:0x002e (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

# PCI device 0x10ec:0x8168 (r8169)
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

BOOT_IMAGE=/boot/vmlinuz-3.13.0-32-generic root=UUID=f7c1939e-6939-417e-af42-7f9980294b87 ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    1.757831] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    1.758058] audit: initializing netlink socket (disabled)
[   10.188792] wmi: Mapper loaded
[   10.326897] ath: EEPROM regdomain: 0x809c
[   10.326900] ath: EEPROM indicates we should expect a country code
[   10.326901] ath: doing EEPROM country->regdmn map search
[   10.326902] ath: country maps to regdmn code: 0x52
[   10.326903] ath: Country alpha2 being used: CN
[   10.326904] ath: Regpair used: 0x52
[   15.367430] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   15.990506] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   15.993508] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   24.489137] wlan0: authenticate with <MAC C-02 heater-needing>
[   24.507960] wlan0: send auth to <MAC C-02 heater-needing> (try 1/3)
[   24.509836] wlan0: authenticated
[   24.509941] ath9k 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   24.509944] ath9k 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   24.512784] wlan0: associate with <MAC C-02 heater-needing> (try 1/3)
[   24.616775] wlan0: associate with <MAC C-02 heater-needing> (try 2/3)
[   24.720775] wlan0: associate with <MAC C-02 heater-needing> (try 3/3)
[   24.828775] wlan0: association with <MAC C-02 heater-needing> timed out
[   25.585106] wlan0: authenticate with <MAC C-02 heater-needing>
[   25.603897] wlan0: send auth to <MAC C-02 heater-needing> (try 1/3)
[   25.605775] wlan0: authenticated
[   25.605877] ath9k 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   25.605881] ath9k 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   25.608787] wlan0: associate with <MAC C-02 heater-needing> (try 1/3)
[   25.716756] wlan0: associate with <MAC C-02 heater-needing> (try 2/3)
[   25.820768] wlan0: associate with <MAC C-02 heater-needing> (try 3/3)
[   25.924761] wlan0: association with <MAC C-02 heater-needing> timed out
[   27.073071] wlan0: authenticate with <MAC C-02 heater-needing>
[   27.091851] wlan0: send auth to <MAC C-02 heater-needing> (try 1/3)
[   27.093694] wlan0: authenticated
[   27.093802] ath9k 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   27.093805] ath9k 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   27.096768] wlan0: associate with <MAC C-02 heater-needing> (try 1/3)
[   27.200755] wlan0: associate with <MAC C-02 heater-needing> (try 2/3)
[   27.304758] wlan0: associate with <MAC C-02 heater-needing> (try 3/3)
[   27.408751] wlan0: association with <MAC C-02 heater-needing> timed out
[   29.053031] wlan0: authenticate with <MAC C-02 heater-needing>
[   29.071825] wlan0: send auth to <MAC C-02 heater-needing> (try 1/3)
[   29.075043] wlan0: authenticated
[   29.075150] ath9k 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   29.075153] ath9k 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   29.076746] wlan0: associate with <MAC C-02 heater-needing> (try 1/3)
[   29.184738] wlan0: associate with <MAC C-02 heater-needing> (try 2/3)
[   29.288727] wlan0: associate with <MAC C-02 heater-needing> (try 3/3)
[   29.392728] wlan0: association with <MAC C-02 heater-needing> timed out
[   40.677042] wlan0: authenticate with <MAC C-02 heater-needing>
[   40.695736] wlan0: send auth to <MAC C-02 heater-needing> (try 1/3)
[   40.697622] wlan0: authenticated
[   40.697730] ath9k 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   40.697733] ath9k 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   40.700623] wlan0: associate with <MAC C-02 heater-needing> (try 1/3)
[   40.804607] wlan0: associate with <MAC C-02 heater-needing> (try 2/3)
[   40.908613] wlan0: associate with <MAC C-02 heater-needing> (try 3/3)
[   41.012608] wlan0: association with <MAC C-02 heater-needing> timed out
[   66.908691] wlan0: authenticate with <MAC C-02 heater-needing>
[   66.927494] wlan0: send auth to <MAC C-02 heater-needing> (try 1/3)
[   66.929372] wlan0: authenticated
[   66.929477] ath9k 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   66.929480] ath9k 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   66.932348] wlan0: associate with <MAC C-02 heater-needing> (try 1/3)
[   67.036338] wlan0: associate with <MAC C-02 heater-needing> (try 2/3)
[   67.140357] wlan0: associate with <MAC C-02 heater-needing> (try 3/3)
[   67.244336] wlan0: association with <MAC C-02 heater-needing> timed out
[   77.889255] wlan0: authenticate with <MAC C-02 heater-needing>
[   77.907481] wlan0: send auth to <MAC C-02 heater-needing> (try 1/3)
[   77.911166] wlan0: authenticated
[   77.911306] ath9k 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   77.911310] ath9k 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   77.916230] wlan0: associate with <MAC C-02 heater-needing> (try 1/3)
[   78.020245] wlan0: associate with <MAC C-02 heater-needing> (try 2/3)
[   78.132258] wlan0: associate with <MAC C-02 heater-needing> (try 3/3)
[   78.236270] wlan0: association with <MAC C-02 heater-needing> timed out

    ======== Done ========
```
I also took your advice about the switching to g mode only before running the script. It didn't make a difference. Well, I could try a different router. I have one here and... what wuddya know..? it works w/the other router. It's hard to say why. This router lets me set the region to "Canada" (which should be identical to the US anyway) and there are more flexible security options, but the security shouldn't matter, since it would fail w/the old router even if I set no security.
So clearly there's something about the old router that all other wi-fi devices I've used were able to workaround, but the software I'm using now isn't robust enough for that. That's what "Other devices work" proves.

Thanks for your help.

---

### Post by varunendra on 2014-08-12
> **PenguinLust said:**
> Like I mentioned earlier, I fixed the region problem in software after running the script..

Ugh! Ignorant me!! :redface:

I had that in mind two days ago, but two days later, completely overlooked that while writing that post (written at the end of an exhausting day, while travelling in an overcrowded bus). But anyway, a confirmation is always good.

I would still be interested in looking at the router's manual (for my own knowledge/record-keeping) even if you don't want to waste anymore time on it. Also the firmware version in it, if you can find it in the settings.

And yes, many current drivers are no more "robust enough" - perhaps the most polite way it can be put in. The "Fun" ways of Open Source software development can be really irritating sometimes. Sigh! I still love it! :p

---

### Post by PenguinLust on 2014-08-14
The router I'm no longer using is a Netgear WGT624v3. I'm pretty sure I've got the latest firmware upgrade. You can download the manual here: [http://www.downloads.netgear.com/files/GDC/WGT624V3/wgt624v3_ref_manual_25Apr05.pdf](http://www.downloads.netgear.com/files/GDC/WGT624V3/wgt624v3_ref_manual_25Apr05.pdf)

---

### Post by varunendra on 2014-08-15
Thanks! At least now I know that 108 Mbps is possible with 'g' mode, even though it is a non-standard proprietary extension to the g-mode standards.

The manual clearly states that if you choose the 108 speed, it'll use channel 6 only, and I think I understand why (given how they reach 108 Mbps speed). But that part doesn't seem to be the problem.

For now, the inability to change the reason makes me suspicious about the firmware, but even if it is buggy/restricted in some ways, the fact that other devices worked is still there, so I guess we don't have much clues to make a substantial conclusion.

Thanks for the link again, at least I learned something new. :)

---

