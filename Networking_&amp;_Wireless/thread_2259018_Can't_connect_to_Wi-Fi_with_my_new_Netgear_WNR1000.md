---
title: "Can't connect to Wi-Fi with my new Netgear WNR1000 router"
date: 2015-01-01
forum: Networking &amp; Wireless
---

### Post by glenn10 on 2015-01-01
Hi,

I can see my new Netgear WNR1000 router, after i installed WiFi Radar but can't connect to it. Netbook EssPC with Lubuntu

```

    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

glenn-900HA 3.13.0-40-generic i686,  Ubuntu 14.04.1 LTS, trusty

CPU    : Intel(R) Atom(TM) CPU N270   @ 1.60GHz
Memory : 2005 MB
Uptime : 11:35:40 up 14 min,  4 users,  load average: 0.36, 0.42, 0.30


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

01:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8121/AR8113/AR8114 Gigabit or Fast Ethernet [1969:1026] (rev b0)
    Subsystem: ASUSTeK Computer Inc. Device [1043:8324]
    Kernel driver in use: ATL1E
02:00.0 Ethernet controller [0200]: Qualcomm Atheros AR242x / AR542x Wireless Network Adapter (PCI-Express) [168c:001c] (rev 01)
    Subsystem: AzureWave AW-GE780 802.11bg Wireless Mini PCIe Card [1a3b:1026]
    Kernel driver in use: ath5k


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 001 Device 002: ID 093a:2700 Pixart Imaging, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 15d9:0a4c Trust International B.V. USB+PS/2 Optical Mouse
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

      Interface              Soft blocked  Hard blocked
0: eeepc-wlan: Wireless LAN      no            no
1: phy0: Wireless LAN            no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

ath5k                 134977  0 
ath                    23922  1 ath5k
mac80211              546051  1 ath5k
cfg80211              409394  3 ath,ath5k,mac80211


module parameters ~~~~~~~~~~~~~~~~~~

ath5k         (3): fastchanswitch=N | nohwcrypt=N | no_hw_rfkill_switch=N
cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
============================o=============o========o==============o=========o===========o==============o===========
 Interface & ID             | Type        | Driver | State        | Default | Speed     | Support      | HW Addr   
============================o=============o========o==============o=========o===========o==============o===========
 eth0  [Wired connection 1] | Wired       | ATL1E  | connected    | yes     | 100 Mb/s  |              | <MAC eth0>

    Address:         192.168.1.6
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1
    DNS:             192.168.1.1
----------------------------+-------------+--------+--------------+---------+-----------+--------------+-----------
 wlan0                      | 802.11 WiFi | ath5k  | disconnected | no      |           | WEP/WPA/WPA2 | <MAC wlan0>
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

w-guest              : ssid=w-guest | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
Wi-Fi connection 1   : ssid=NETGEAR66 | mac-address=<MAC ID removed> | ipv4=auto | ipv6=auto 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 127.0.1.1


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

--- 192.168.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1000ms
rtt min/avg/max/mdev = 0.487/0.501/0.516/0.026 ms

--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.076/0.097/0.118/0.021 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "en_US.UTF-8")


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     14 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 14 (2.484 GHz)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~



blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/libpisock9.conf]
blacklist visor


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[ath5k]
filename:       /lib/modules/3.13.0-40-generic/kernel/drivers/net/wireless/ath/ath5k/ath5k.ko
srcversion:     F36818A2F0BCB2B0CC9BB8C
depends:        mac80211,cfg80211,ath
parm:           nohwcrypt:Disable hardware encryption. (bool)
parm:           fastchanswitch:Enable fast channel switching for AR2413/AR5413 radios. (bool)
parm:           no_hw_rfkill_switch:Ignore the GPIO RFKill switch state (bool)

[ath]
filename:       /lib/modules/3.13.0-40-generic/kernel/drivers/net/wireless/ath/ath.ko
srcversion:     88A67C5359B02C5A710AFCF
depends:        cfg80211

[mac80211]
filename:       /lib/modules/3.13.0-40-generic/kernel/net/mac80211/mac80211.ko
srcversion:     123C230E7AC85A31E4CA28B
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-40-generic/kernel/net/wireless/cfg80211.ko
srcversion:     C2478077E22138832B71659
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x1969:0x1026 (ATL1E)
SUBSYSTEM=="net",  ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>",  ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x168c:0x001c (ath5k)
SUBSYSTEM=="net",  ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>",  ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


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

BOOT_IMAGE=/boot/vmlinuz-3.13.0-40-generic root=UUID=42ddb5bb-5740-4c41-8f19-8d19bef43b64 ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    1.064366] microcode: Microcode Update Driver: v2.00 <[EMAIL="tigran@aivazian.fsnet.co.uk"]tigran@aivazian.fsnet.co.uk[/EMAIL]>, Peter Oruba
[    1.065163] audit: initializing netlink socket (disabled)
[    3.216839] psmouse serio1: elantech: assuming hardware version 1 (with firmware version 0x020022)
[   28.238939] ath5k 0000:02:00.0: can't disable ASPM; OS doesn't have ASPM control
[   28.239191] ath5k 0000:02:00.0: registered as 'phy0'
[   29.864850] ath: EEPROM regdomain: 0x60
[   29.864860] ath: EEPROM indicates we should expect a direct regpair map
[   29.864869] ath: Country alpha2 being used: 00
[   29.864875] ath: Regpair used: 0x60
[   29.969805] ath5k: phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[   32.264954] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   35.550177] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   35.554822] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  676.505538] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  684.593655] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  689.642348] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready

    ======== Done ========

```

---

### Post by praseodym on 2015-01-01
Deactivate the hardware encryption of the driver
```

echo "options ath5k nohwcrypt=1" | sudo tee -a /etc/modprobe.d/ath5k.conf
sudo modprobe -rfv ath5k
sudo modprobe -v ath5k
```
and "Ignore" IPv6 in the network settings

---

### Post by chili555 on 2015-01-01
Also, make sure your new router isn't set to only use N speeds as your older Atheros doesn't do N:> Subsystem: AzureWave AW-GE780 802.11[COLOR="#FF0000"]bg[/COLOR] Wireless Mini PCIeI'd also suggest a fixed channel, 1, 6 or 11, rather than auto channel selection. Several card/driver combinations in Linux have difficulty hitting a constantly moving target.

---

### Post by glenn10 on 2015-01-01
Thanks but still no good. 

When I setup the WiFI in Network Manger, the same don't automatically appear in the found connection in WiFi radart. When I click "connect" it says starting WPA supplicant and then gets stuck in "Acquiring IP Address (DHCP). I've re-booted

Thanks,
Glenn

---

### Post by praseodym on 2015-01-01
14 channels are the region setting for Japan. You are in the US?
```

sudo apt-get install iw
iw reg get
sudo iw reg set [COLOR="#FF0000"]US[/COLOR]
iw reg get
iwlist chan
sudo iwlist scan
```
Change the red US for your country code.

---

### Post by glenn10 on 2015-01-01
Yes, I'm in the US and I set the channel to 11

---

### Post by glenn10 on 2015-01-01
Revise that, when I tried:

sudo iw reg set 11

got not a valid ISO/IEC 3166-1 alph2
Special non-alpha2 usable entries
00 World Regulatory domain

01, 06 same rejection

---

### Post by praseodym on 2015-01-01
It is
```

sudo iw reg set US
```

---

### Post by glenn10 on 2015-01-01
thanks did that and still working on it

---

### Post by glenn10 on 2015-01-01
Okay problem resolved!

I was working in a different GUI interface and found one for a netbook within my Lubuntu boot. In the taskbar, I was able to select my router, insert the password and good to go!

It looks like the other interface was for a desktop perhaps! Don't know why the same credentials and setup would not work. I am not new to Linux, started with Redhat 4.0 over 20 years ago and was fervent then, now just an occasion user.

Appreciate all the responses I got today and will be spending more time here.

Thanks!
Glenn

---

