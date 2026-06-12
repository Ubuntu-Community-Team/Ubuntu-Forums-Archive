---
title: "lubuntu acer netbook wireless network not detected after getting new router"
date: 2014-09-07
forum: Networking &amp; Wireless
---

### Post by nbloomis on 2014-09-07
I got a new router recently, and I think I may have deleted the connection in lubuntu's network preferences.  I am not sure if my wireless card is even responding right now (acer netbook with lubuntu on external hd).  I know it isn't the router because I have other computers connecting to it.  I'm thinking maybe I can 'Add' new connection, maybe fill in some info on the bottom of the router?  I wish I could just detect the network and connect...
Any help is much appreciated!
Nate

---

### Post by varunendra on 2014-09-11
Please follow the instructions in this post to download and run 'wireless_script' (experimental version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

### Post by nbloomis on 2014-09-16
```


    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

nathan-AOA110 3.11.0-20-generic i686,  Ubuntu 13.10, saucy

CPU    : Intel(R) Atom(TM) CPU N270   @ 1.60GHz
Memory : 1495 MB
Uptime : 11:12:48 up 8 min,  2 users,  load average: 0.02, 0.26, 0.24


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
    Subsystem: Acer Incorporated [ALI] Device [1025:015b]
    Kernel driver in use: r8169
03:00.0 Ethernet controller [0200]: Qualcomm Atheros AR242x / AR542x Wireless Network Adapter (PCI-Express) [168c:001c] (rev 01)
    Subsystem: Foxconn International, Inc. Device [105b:e008]
    Kernel driver in use: ath5k


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 001 Device 003: ID 0c45:62c0 Microdia Sonix USB 2.0 Camera
Bus 001 Device 002: ID 0bc2:2100 Seagate RSS LLC 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface        Soft blocked  Hard blocked
0: phy0: Wireless LAN      no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

ath5k                 135055  0 
ath                    19187  1 ath5k
mac80211              517444  1 ath5k
cfg80211              401762  3 ath,ath5k,mac80211
wmi                    18590  0 


module parameters ~~~~~~~~~~~~~~~~~~

ath5k         (3): fastchanswitch=N | nohwcrypt=N | no_hw_rfkill_switch=N
cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
============================o=============o========o==============o=========o===========o==============o===========
 Interface & ID             | Type        | Driver | State        | Default | Speed     | Support      | HW Addr   
============================o=============o========o==============o=========o===========o==============o===========
 wlan0                      | 802.11 WiFi | ath5k  | disconnected | no      |           | WEP/WPA/WPA2 | <MAC wlan0>
----------------------------+-------------+--------+--------------+---------+-----------+--------------+-----------
 eth0  [Wired connection 1] | Wired       | r8169  | connected    | yes     | 100 Mb/s  |              | <MAC eth0>

    Address:         192.168.0.3
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1
    DNS:             209.18.47.61
    DNS:             209.18.47.62
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

[ifupdown]
managed=false


NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~

belkin.789           : ssid=belkin.789 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Brewbakers           : ssid=Brewbakers | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Brewbakers_Guest     : ssid=Brewbakers_Guest | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
Fairpoint6E6F        : ssid=Fairpoint6E6F | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Fairpoint6E6F 1      : ssid=Fairpoint6E6F | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 127.0.1.1


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

--- 192.168.0.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 0.596/0.926/1.256/0.330 ms

--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.070/0.075/0.081/0.010 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "en_US.UTF-8")


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     13 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 13 (2.472 GHz)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     No scan results


blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/libpisock9.conf]
blacklist visor


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[ath5k]
filename:       /lib/modules/3.11.0-20-generic/kernel/drivers/net/wireless/ath/ath5k/ath5k.ko
srcversion:     68167C5D7C0F1F5FF5D8D62
depends:        mac80211,cfg80211,ath
parm:           nohwcrypt:Disable hardware encryption. (bool)
parm:           fastchanswitch:Enable fast channel switching for AR2413/AR5413 radios. (bool)
parm:           no_hw_rfkill_switch:Ignore the GPIO RFKill switch state (bool)

[ath]
filename:       /lib/modules/3.11.0-20-generic/kernel/drivers/net/wireless/ath/ath.ko
srcversion:     A890CDBC88E6EF28CD751DD
depends:        cfg80211

[mac80211]
filename:       /lib/modules/3.11.0-20-generic/kernel/net/mac80211/mac80211.ko
srcversion:     34FD9A3AD4E345E1F271195
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.11.0-20-generic/kernel/net/wireless/cfg80211.ko
srcversion:     A9AE06A9BEF1DAB62A8C8ED
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[wmi]
filename:       /lib/modules/3.11.0-20-generic/kernel/drivers/platform/x86/wmi.ko
srcversion:     2DABFFAB67882C8B2FC580C
depends:        
parm:           debug_event:Log WMI Events [0/1] (bool)
parm:           debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x168c:/sys/devices/pci0000:00/0000:00:1c.2/0000:03:00.0 (ath5k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


Custom files/entries ~~~~~~~~~~~~~~~

/etc/modules        : Not Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Default

[/etc/modules]
loop

[/etc/modprobe.d]
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
mlx4.conf         : softdep mlx4_core post: mlx4_en


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/boot/vmlinuz-3.11.0-20-generic root=UUID=eb4c8660-a3e2-4f47-8e73-9124219efbe7 ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    1.084550] audit: initializing netlink socket (disabled)
[    1.712553] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[   23.940924] wmi: Mapper loaded
[   24.753289] ath5k 0000:03:00.0: can't disable ASPM; OS doesn't have ASPM control
[   24.753601] ath5k 0000:03:00.0: registered as 'phy0'
[   25.841266] ath: EEPROM regdomain: 0x65
[   25.841276] ath: EEPROM indicates we should expect a direct regpair map
[   25.841285] ath: Country alpha2 being used: 00
[   25.841291] ath: Regpair used: 0x65
[   25.880163] ath5k: phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[   26.658783] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   27.021958] acer_wmi: Acer Laptop ACPI-WMI Extras
[   27.021971] acer_wmi: Blacklisted hardware detected - not loading
[   27.843263] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[   31.904710] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   31.905624] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready

    ======== Done ========


```

thank you for your help, Varun.
- Nate

---

### Post by varunendra on 2014-09-16
> **nbloomis said:**
> ```
nathan-AOA110 3.11.0-20-generic i686,  **[COLOR="#FF0000"]Ubuntu 13.10, saucy[/COLOR]**
....
[   27.021971] acer_wmi: **[COLOR="#FF0000"]Blacklisted hardware detected[/COLOR]** - not loading
```

First, 13.10 has reached its EOL (End Of Life), means it is no more supported and you won't get any updates for it.

Secondly, is the same card working earlier? I'm concerned about the wmi error highlighted above, although it doesn't say which hardware it is complaining about, but all it handles is hotkeys and radio devices, their switches etc.

It is highly recommended you try a Live DVD/USB of either 12.04.4 or 14.04.1, and if it works, do a clean install of it. If it is not the hardware, but the software or driver, it would make much more sense to troubleshoot it on a supported version.

---

### Post by QIII on 2014-09-16
Please do as Varun asks and install a currently supported version of Ubuntu or your flavor of choice.

I understand that your problem is not solved, but the Staff does not want members to spend time helping out with unsupported releases.

Please see this for [this]("http://ubuntuforums.org/showthread.php?t=2229730") Staff's position.

When you have installed a supported version, please feel free to start a new thread if you encounter problems.

Thread closed.

---

