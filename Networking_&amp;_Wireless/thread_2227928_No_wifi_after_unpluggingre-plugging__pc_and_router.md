---
title: "No wifi after unplugging/re-plugging  pc and router"
date: 2014-06-04
forum: Networking &amp; Wireless
---

### Post by Whiskurious on 2014-06-04
Hello,
I'm new to this forum.
Unfortunately my wireless connection seems to not be working under ubuntu (works fine on windows, same pc) after I unplugged the pc and the router (there was a really bad thunderstorm) and re-plugged everything back in.

I'm connected via cable, and tried to delete, rescan and reset wifi connection via the connection manager (hope I'm not getting the name wrong) but haven't solved much.

I'd really appreciate some help.

Thanks for taking the time to read through this.
Sorry for any nonsense I might have written, I'm no computer whiz. 8-[


EDIT:
Suggestions I followed from other threads. Hope this is useful.

```
 krys@Stitch:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: eth2  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        F4:6D:04:6E:85:C6

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.178
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8180
  State:             disconnected
  Default:           no
  HW Address:        00:23:F8:2F:CB:EB

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    FASTWEB-1-002196437A18: Infra, 00:21:96:43:7A:20, Freq 2437 MHz, Rate 54 Mb/s, Strength 20 WPA
    Alice-63658385:  Infra, 00:25:53:FB:29:8C, Freq 2412 MHz, Rate 54 Mb/s, Strength 93 WPA


krys@Stitch:~$ nm-tool

NetworkManager Tool

State: disconnected

- Device: eth2 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             disconnected
  Default:           no
  HW Address:        F4:6D:04:6E:85:C6

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8180
  State:             disconnected
  Default:           no
  HW Address:        00:23:F8:2F:CB:EB

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    FASTWEB-1-002196437A18: Infra, 00:21:96:43:7A:20, Freq 2437 MHz, Rate 54 Mb/s, Strength 20 WPA
    Alice-63658385:  Infra, 00:25:53:FB:29:8C, Freq 2412 MHz, Rate 54 Mb/s, Strength 93 WPA


krys@Stitch:~$ sudo lshw -C network
[sudo] password for krys: 
  *-network               
       description: Wireless interface
       product: RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wlan0
       version: 20
       serial: 00:23:f8:2f:cb:eb
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8180 driverversion=3.2.0-63-generic-pae firmware=N/A latency=32 link=no maxlatency=64 mingnt=32 multicast=yes wireless=IEEE 802.11bg
       resources: irq:16 ioport:d000(size=256) memory:fe501000-fe5011ff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth2
       version: 06
       serial: f4:6d:04:6e:85:c6
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8168e-2.fw ip=192.168.1.178 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:53 ioport:b000(size=256) memory:f0004000-f0004fff memory:f0000000-f0003fff

```

```

    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

Stitch 3.2.0-63-generic-pae i686,  Ubuntu 12.04.4 LTS, precise

CPU    : Intel(R) Core(TM) i5-2500K CPU @ 3.30GHz
Memory : 8060 MB
Uptime : 01:27:12 up 51 min,  4 users,  load average: 0.10, 0.17, 0.22


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

06:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller [10ec:8185] (rev 20)
    Subsystem: ZyXEL Communications Corporation Device [187e:8225]
    Kernel driver in use: rtl8180
--
08:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
    Subsystem: ASUSTeK Computer Inc. P8P67 and other motherboards [1043:8432]
    Kernel driver in use: r8169


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 001 Device 004: ID 046d:c51b Logitech, Inc. V220 Cordless Optical Mouse for Notebooks
Bus 001 Device 005: ID 058f:6465 Alcor Micro Corp. 


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

eeepc_wmi              12949  0 
asus_wmi               19624  1 eeepc_wmi
sparse_keymap          13658  1 asus_wmi
rtl8180                35880  0 
mac80211              436493  1 rtl8180
eeprom_93cx6           12687  1 rtl8180
cfg80211              178877  2 rtl8180,mac80211
wmi                    18744  1 asus_wmi


module parameters ~~~~~~~~~~~~~~~~~~

cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
eeepc_wmi     (1): hotplug_wireless=N
mac80211      (4): ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
============================o=============o=========o==============o=========o===========o==============o===========
 Interface & ID             | Type        | Driver  | State        | Default | Speed     | Support      | HW Addr   
============================o=============o=========o==============o=========o===========o==============o===========
 eth2  [Wired connection 1] | Wired       | r8169   | connected    | yes     | 100 Mb/s  |              | <MAC eth2>

    Address:         192.168.1.178
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1
    DNS:             192.168.1.1
----------------------------+-------------+---------+--------------+---------+-----------+--------------+-----------
 wlan0                      | 802.11 WiFi | rtl8180 | disconnected | no      |           | WEP/WPA/WPA2 | <MAC wlan0>

    FASTWEB-1-002196437A18: Infra, <MAC C-NA FASTWEB-1-002196437A18 1>, Freq 2437 MHz, Rate 54 Mb/s, Strength 20 WPA
    Alice-63658385:  Infra, <MAC C-01 Alice-63658385>, Freq 2412 MHz, Rate 54 Mb/s, Strength 93 WPA
----------------------------+-------------+---------+--------------+---------+-----------+--------------+-----------


NetworkManager.state ~~~~~~~~~~~~~~~

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


NetworkManager.conf ~~~~~~~~~~~~~~~~

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

no-auto-default=<MAC eth2>,

[ifupdown]
managed=false


NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~

Alice-63658385       : ssid=Alice-63658385 | permissions=user:krys:; | bssid=<MAC C-01 Alice-63658385> | ipv4=auto | ipv6=ignore 
Momisimisimi         : ssid=Momisimisimi | permissions=user:krys:; | bssid=<MAC ID removed> | ipv4=auto | ipv6=ignore 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

auto lo
iface lo inet loopback


resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 127.0.0.1
search homenet.telecomitalia.it


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth2
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth2
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth2

--- 192.168.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1000ms
rtt min/avg/max/mdev = 0.538/0.560/0.582/0.022 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "en_US.UTF-8")
country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 20), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     14 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 14 (2.484 GHz)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 Alice-63658385>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=87/100  Signal level=87/100  
                    Encryption key:on
                    ESSID:"Alice-63658385"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000017728a183
                    Extra: Last beacon: 1200ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK


blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[rtl8180]
filename:       /lib/modules/3.2.0-63-generic-pae/kernel/drivers/net/wireless/rtl818x/rtl8180/rtl8180.ko
srcversion:     930A3B495B2EAF96284A747
depends:        mac80211,eeprom_93cx6,cfg80211

[mac80211]
filename:       /lib/modules/3.2.0-63-generic-pae/kernel/net/mac80211/mac80211.ko
srcversion:     3CEA481F8EC50557EA4A241
depends:        cfg80211
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)

[eeprom_93cx6]
filename:       /lib/modules/3.2.0-63-generic-pae/kernel/drivers/misc/eeprom/eeprom_93cx6.ko
version:        1.0
srcversion:     B0E08119EEE31CFCE1C0A01
depends:        

[cfg80211]
filename:       /lib/modules/3.2.0-63-generic-pae/kernel/net/wireless/cfg80211.ko
srcversion:     A289A224DC04F871A44431D
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x11ab:/sys/devices/pci0000:00/0000:00:0a.0 (skge)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.1/0000:01:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth1>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.6/0000:08:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth2>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth2"

# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.4/0000:05:00.0/0000:06:00.0 (rtl8180)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


Custom files/entries ~~~~~~~~~~~~~~~

/etc/modules        : Default
/etc/rc.local       : Default
/etc/modprobe.d     : Default
/etc/pm/(cnf|pw|sl) : Default


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/boot/vmlinuz-3.2.0-63-generic-pae root=UUID=b6f2da02-53d4-41c1-9ac5-42818875d7fd ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    0.856151] audit: initializing netlink socket (disabled)
[    1.670869] wmi: Mapper loaded
[    1.681682] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[   20.377801] udevd[423]: renamed network interface eth0 to eth2
[   20.414901] rtl8180 0000:06:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   20.453893] asus_wmi: ASUS WMI generic driver loaded
[   20.454208] asus_wmi: Initialization: 0x0
[   20.454223] asus_wmi: BIOS WMI version: 0.9
[   20.454251] asus_wmi: SFUN value: 0x0
[   20.454417] input: Eee PC WMI hotkeys as /devices/platform/eeepc-wmi/input/input4
[   21.088057] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   24.529617] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   24.529842] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   24.684969] r8169 0000:08:00.0: eth2: link down
[   24.684974] r8169 0000:08:00.0: eth2: link down
[   24.685072] ADDRCONF(NETDEV_UP): eth2: link is not ready
[   24.685418] ADDRCONF(NETDEV_UP): eth2: link is not ready
[   26.444377] r8169 0000:08:00.0: eth2: link up
[   26.444499] ADDRCONF(NETDEV_CHANGE): eth2: link becomes ready
[   37.385367] eth2: no IPv6 routers present
[   51.860739] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[   52.060459] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[   52.260195] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[   52.459893] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[   58.583077] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[   58.782797] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[   58.982492] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[   59.182247] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[   65.305372] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[   65.505081] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[   65.704799] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[   65.904505] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[   72.027688] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[   72.227395] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[   72.427102] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[   72.626822] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[   78.753978] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[   78.953705] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[   79.153410] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[   79.353168] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[   85.476301] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[   85.675996] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[   85.875712] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[   86.075420] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[   92.198600] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[   92.398326] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[   92.598118] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[   92.797746] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[   98.916920] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[   99.116659] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[   99.316381] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[   99.516086] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[  158.902465] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[  159.102179] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[  159.301888] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[  159.501576] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[  165.620812] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[  165.820578] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[  166.020208] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[  166.219930] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[  172.339105] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[  172.538782] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[  172.738541] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[  172.938249] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[  179.057380] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[  179.257128] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[  179.456919] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[  179.656573] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[  185.775757] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[  185.975537] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[  186.175181] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[  186.374864] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[  192.494036] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[  192.693775] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[  192.893428] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[  193.093172] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[  199.216319] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[  199.416043] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[  199.615794] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[  199.815545] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[  205.934672] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[  206.134378] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[  206.334058] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[  206.533847] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[  212.652979] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[  212.852663] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[  213.056364] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[  213.256123] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[  220.086284] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[  220.286079] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[  220.485695] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[  220.685432] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[  226.804606] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[  227.004368] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[  227.204046] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[  227.403767] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[  233.522864] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[  233.722605] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[  233.922317] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[  234.122052] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[  240.245181] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[  240.444932] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[  240.644634] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[  240.844441] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[  246.963521] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[  247.163208] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[  247.362958] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[  247.562671] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[  253.681830] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[  253.881581] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[  254.081252] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[  254.280980] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[  258.886336] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[  259.086083] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[  259.285839] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[  259.485543] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[  265.604615] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[  265.804416] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[  266.004064] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[  266.203803] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[  272.326952] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[  272.526653] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[  272.726338] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[  272.926115] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[  277.791300] eth2: no IPv6 routers present
[  338.264894] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[  338.464704] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[  338.664491] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[  338.864329] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[  344.986565] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[  345.186378] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[  345.386189] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[  345.586001] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[  351.716199] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[  351.916001] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[  352.115825] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[  352.315637] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[  358.437908] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[  358.637688] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[  358.837511] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[  359.037314] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[  365.159599] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[  365.359359] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[  365.559167] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[  365.758993] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[  371.885353] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[  372.085031] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[  372.284867] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[  372.484679] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[  378.610944] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[  378.810730] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[  379.010545] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[  379.210321] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[  385.332564] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[  385.532403] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[  385.732200] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[  385.932055] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[  392.054237] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[  392.254042] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[  392.453848] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[  392.653661] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[  407.699556] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[  407.899370] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[  408.099163] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[  408.298973] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[  414.421239] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[  414.621025] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[  414.820820] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[  415.020673] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[  421.146855] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[  421.346694] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[  421.546536] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[  421.746318] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[  427.868557] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[  428.068380] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[  428.268183] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[  428.467997] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[  434.590238] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[  434.790067] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[  434.989840] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[  435.189665] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[  441.311904] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[  441.511717] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[  441.711526] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[  441.911338] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[  448.033602] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[  448.233389] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[  448.433216] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[  448.632978] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[  454.755260] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[  454.955062] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[  455.154873] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[  455.354684] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[  461.476921] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[  461.676738] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[  461.876574] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[  462.076337] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[  475.935317] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[  476.135133] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[  476.334924] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[  476.534749] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[  482.656965] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[  482.856775] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[  483.056673] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[  483.256393] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[  489.386639] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[  489.586447] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[  489.786289] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[  489.986119] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[  496.108354] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[  496.308108] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[  496.507954] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[  496.707763] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[  502.830028] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[  503.029833] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[  503.229625] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[  503.429437] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[  509.551642] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[  509.751463] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[  509.951279] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[  510.151085] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[  516.273344] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[  516.473137] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[  516.672945] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[  516.872786] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[  522.995047] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[  523.194917] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[  523.394647] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[  523.594470] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[  529.720718] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[  529.920504] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[  530.120323] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[  530.320150] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[  665.860567] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[  666.060379] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[  666.260189] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[  666.459999] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[  672.582232] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[  672.782042] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[  672.981854] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[  673.181664] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[  679.303881] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[  679.503718] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[  679.703530] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[  679.903341] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[  686.029573] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[  686.229400] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[  686.429214] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[  686.629010] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[  692.751249] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[  692.951027] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[  693.150846] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[  693.350700] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[  699.472922] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[  699.672734] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[  699.872543] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[  700.072381] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[  706.194613] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[  706.394387] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[  706.594203] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[  706.794052] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[  712.916237] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[  713.116079] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[  713.315893] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[  713.515673] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[  719.637944] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[  719.837751] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[  720.037569] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[  720.237376] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[ 1145.744912] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[ 1145.944702] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[ 1146.144511] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[ 1146.344287] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[ 1152.470560] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[ 1152.670357] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[ 1152.870182] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[ 1153.069991] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[ 1159.192233] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[ 1159.392014] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[ 1159.591857] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[ 1159.791627] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[ 1165.913908] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[ 1166.113720] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[ 1166.313522] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[ 1166.513312] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[ 1172.639600] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[ 1172.839389] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[ 1173.039198] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[ 1173.239033] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[ 1179.361245] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[ 1179.561063] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[ 1179.760845] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[ 1179.960667] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[ 1186.082917] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[ 1186.282735] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[ 1186.482517] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[ 1186.682382] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[ 1192.804621] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[ 1193.004406] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[ 1193.204223] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[ 1193.404013] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[ 1199.526287] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[ 1199.726075] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[ 1199.925863] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[ 1200.125699] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[ 1625.297532] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[ 1625.497346] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[ 1625.697182] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[ 1625.896967] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[ 1632.019199] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[ 1632.218985] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[ 1632.418827] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[ 1632.618668] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[ 1638.748841] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[ 1638.948654] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[ 1639.148485] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[ 1639.352269] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[ 1645.470568] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[ 1645.670416] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[ 1645.870168] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[ 1646.070040] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[ 1652.192175] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[ 1652.392028] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[ 1652.591819] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[ 1652.791721] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[ 1658.913889] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[ 1659.113705] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[ 1659.313485] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[ 1659.513303] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[ 1665.639538] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[ 1665.839380] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[ 1666.039183] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[ 1666.238998] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[ 1672.361258] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[ 1672.561026] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[ 1672.760883] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[ 1672.960670] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[ 1679.086905] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[ 1679.286779] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[ 1679.486556] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[ 1679.686318] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[ 2104.850176] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[ 2105.049987] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[ 2105.249822] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[ 2105.449608] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[ 2111.571850] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[ 2111.771676] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[ 2111.971472] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[ 2112.171281] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[ 2118.293524] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[ 2118.493418] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[ 2118.693146] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[ 2118.892964] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[ 2125.015219] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[ 2125.215004] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[ 2125.414923] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[ 2125.614630] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[ 2131.740861] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[ 2131.940674] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[ 2132.140474] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[ 2132.340322] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[ 2138.462546] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[ 2138.662338] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[ 2138.862158] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[ 2139.061972] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[ 2145.184235] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[ 2145.384023] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[ 2145.583833] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[ 2145.783675] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[ 2151.905846] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[ 2152.105694] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[ 2152.305509] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[ 2152.505339] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[ 2158.627557] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[ 2158.827366] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[ 2159.027180] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[ 2159.227016] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[ 2584.390828] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[ 2584.590638] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[ 2584.790452] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[ 2584.990286] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[ 2591.112523] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[ 2591.312326] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[ 2591.512139] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[ 2591.711957] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[ 2597.834139] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[ 2598.033981] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[ 2598.233799] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[ 2598.433601] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[ 2604.555874] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[ 2604.755660] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[ 2604.955562] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[ 2605.155281] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[ 2611.277523] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[ 2611.477336] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[ 2611.677143] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[ 2611.876961] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[ 2617.999172] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[ 2618.199020] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[ 2618.398815] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[ 2618.598632] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[ 2624.720892] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[ 2624.920732] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[ 2625.120487] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[ 2625.320302] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[ 2631.442565] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[ 2631.642351] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[ 2631.842177] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[ 2632.041979] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[ 2638.164218] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[ 2638.364027] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[ 2638.563837] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[ 2638.763648] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[ 2784.846156] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[ 2785.045938] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[ 2785.245770] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[ 2785.445617] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[ 2789.150080] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[ 2789.349878] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[ 2789.549728] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[ 2789.749541] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[ 2795.871802] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[ 2796.071615] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[ 2796.271400] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[ 2796.471280] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[ 2802.601447] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[ 2802.801265] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[ 2803.001069] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[ 2803.200882] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[ 2809.323083] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[ 2809.522906] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[ 2809.722720] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[ 2809.922524] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[ 2816.044797] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[ 2816.244605] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[ 2816.444417] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[ 2816.644209] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[ 2822.766468] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[ 2822.966277] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[ 2823.166089] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[ 2823.365888] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[ 2829.488143] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[ 2829.687952] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[ 2829.887774] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[ 2830.087597] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[ 2836.217830] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[ 2836.417615] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[ 2836.617451] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[ 2836.817240] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[ 2842.939481] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[ 2843.139292] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[ 2843.339074] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[ 2843.538915] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[ 2853.881180] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[ 2854.081018] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[ 2854.280804] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[ 2854.480618] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[ 2860.606858] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[ 2860.806642] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[ 2861.006451] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[ 2861.206252] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[ 2867.336491] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[ 2867.536339] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[ 2867.736140] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[ 2867.935918] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[ 2874.058216] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[ 2874.258005] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[ 2874.457818] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[ 2874.657624] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[ 2880.779886] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[ 2880.979675] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[ 2881.179502] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[ 2881.379320] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[ 2887.501538] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[ 2887.701315] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[ 2887.901158] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[ 2888.100971] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[ 2894.227206] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[ 2894.427007] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[ 2894.626830] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[ 2894.826642] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[ 2900.948903] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[ 2901.148691] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[ 2901.348514] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[ 2901.548314] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[ 2907.678570] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[ 2907.878360] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[ 2908.078194] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[ 2908.277981] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[ 2918.500385] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[ 2918.700158] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[ 2918.900008] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[ 2919.099797] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[ 2925.222021] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[ 2925.421844] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[ 2925.621679] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[ 2925.821468] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[ 2931.943732] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[ 2932.143487] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[ 2932.347321] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[ 2932.547125] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[ 2938.665382] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[ 2938.865213] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[ 2939.065004] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[ 2939.264815] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[ 2945.387058] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[ 2945.586864] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[ 2945.786683] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[ 2945.986595] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[ 2952.108731] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[ 2952.308564] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[ 2952.508352] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[ 2952.708161] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[ 2958.830371] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[ 2959.030215] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[ 2959.230026] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[ 2959.429813] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[ 2965.552048] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[ 2965.751849] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[ 2965.951724] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[ 2966.151513] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[ 2972.277711] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[ 2972.477619] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[ 2972.677328] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[ 2972.877160] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[ 2983.475230] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[ 2983.675016] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[ 2983.874832] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[ 2984.074645] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[ 2990.196853] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[ 2990.396691] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[ 2990.596476] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[ 2990.796283] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[ 2996.918549] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[ 2997.118479] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[ 2997.318178] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[ 2997.517988] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[ 3003.640225] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[ 3003.840041] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[ 3004.039850] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[ 3004.239682] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[ 3010.361899] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[ 3010.561711] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[ 3010.761549] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[ 3010.961360] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[ 3017.083599] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[ 3017.283383] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[ 3017.483333] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[ 3017.683006] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[ 3023.805245] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[ 3024.005061] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[ 3024.204857] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[ 3024.404682] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[ 3030.526919] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[ 3030.726736] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[ 3030.926545] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[ 3031.126381] wlan0: authentication with <MAC C-01 Alice-63658385> timed out
[ 3037.252564] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 1)
[ 3037.452389] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 2)
[ 3037.652217] wlan0: authenticate with <MAC C-01 Alice-63658385> (try 3)
[ 3037.852113] wlan0: authentication with <MAC C-01 Alice-63658385> timed out

    ======== Done ========
```

---

### Post by varunendra on 2014-06-05
Welcome to the forums Whiskurious!

Please delete the connection "Alice-63658385" from the saved connections in Network Manager, and try connecting again. Do this after a reboot, while keeping the Ethernet cable unplugged. If you are trying to connect to a different network than "Alice..." delete that one if it is saved. The new connection should be saved automatically as soon as you connect to it by supplying the security key. You shouldn't need to save any other info in the connection manually.

If this doesn't help, try a driver parameter by creating a conf file -
```
echo "options eeepc_wmi hotplug_wireless=Y" | sudo tee /etc/modprobe.d/eeepc_wmi.conf
```
..followed by a reboot. Then try connecting again. If it doesn't help either, post back a fresh report of wireless_script, with the above suggestions applied.

---

### Post by Whiskurious on 2014-06-05
HelloVarunendra[[COLOR=#DD4814]****[/COLOR]]("http://ubuntuforums.org/member.php?u=1043629"),
Thank you so much for taking the time to help me.
When I turned my pc on earlier today, I still had my cable attached from yesterday. 
However, I just noticed that the wireless connection is working, and has been since I logged in, and entered my KDE Wallet password.
I have no idea what happened, and that worries me a little, because I don't know how to "repeat" the process, should it happen again.
Do you, or anyone else have any ideas?
Should I post any future problems here (after working through your suggestions) or open a new thread?

Thanks again for your help.
Please let me know if I should mark this thread as solved.

---

### Post by varunendra on 2014-06-06
I've no idea what might have been the problem. Could be a stuck driver or firmware issue, but those are usually solved by a simple reboot. I think watch it for a day or two, then mark the thread as [SOLVED] if it keeps working without issues.

In case the problem returns, feel free to post here (removing the [Solved] prefix if you added it). If something critical changes in-between, e.g., the device or OS version, start a new thread.

---

