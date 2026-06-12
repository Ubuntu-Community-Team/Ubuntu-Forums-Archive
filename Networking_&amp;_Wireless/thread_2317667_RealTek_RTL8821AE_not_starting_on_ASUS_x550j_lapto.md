---
title: "RealTek RTL8821AE not starting on ASUS x550j laptop"
date: 2016-03-18
forum: Networking &amp; Wireless
---

### Post by kavanohk on 2016-03-18
Hi my wireless is not starting on my laptop, can you help me to take a look at the problem? Thanks a lot. 

```

    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

k-X550JX 4.2.0-34-generic x86_64,  Ubuntu 14.04.4 LTS, trusty

CPU    : Intel(R) Core(TM) i7-4720HQ CPU @ 2.60GHz
Memory : 7873 MB
Uptime : 00:03:00 up 5 min,  2 users,  load average: 0.42, 0.28, 0.13


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8821AE 802.11ac PCIe Wireless Network Adapter [10ec:8821]
    Subsystem: AzureWave Device [1a3b:2161]
04:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device [10ec:5287] (rev 01)
--
04:00.1 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 12)
    Subsystem: ASUSTeK Computer Inc. Device [1043:200f]
    Kernel driver in use: r8169


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 04f2:b48c Chicony Electronics Co., Ltd 
Bus 001 Device 003: ID 13d3:3414 IMC Networks 
Bus 001 Device 002: ID 046d:c077 Logitech, Inc. M105 Optical Mouse
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~



rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface               Soft blocked  Hard blocked
0: hci0: Bluetooth                no            no
1: asus-wlan: Wireless LAN        no            no
2: asus-bluetooth: Bluetooth      no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

asus_nb_wmi            24576  0 
asus_wmi               28672  1 asus_nb_wmi
mxm_wmi                16384  0 
sparse_keymap          16384  1 asus_wmi
video                  40960  2 i915,asus_wmi
wmi                    20480  2 mxm_wmi,asus_wmi


module parameters ~~~~~~~~~~~~~~~~~~

asus_nb_wmi   (1): wapf=1
video         (3): allow_duplicates=N | brightness_switch_enabled=Y | disable_backlight_sysfs_if=-1
wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
============================o=======o========o====  =======o=========o===========o==============o=====  ======
 Interface & ID             | Type  | Driver | State     | Default | Speed     | Support      | HW Addr   
============================o=======o========o====  =======o=========o===========o==============o=====  ======
 eth0  [Wired connection 1] | Wired | r8169  | connected | yes     | 100 Mb/s  |              | <MAC eth0>

    Address:         192.168.1.15
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254
    DNS:             192.168.1.254
----------------------------+-------+--------+-----------+---------+-----------+--------------+-----------


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

NTUSECURE            : ssid=NTUSECURE | mac-address=<MAC wlan0> | ipv4=auto 
NTUWL                : ssid=NTUWL | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
SINGTEL-E64B         : ssid=SINGTEL-E64B | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
what wifi            : ssid=what wifi | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 127.0.1.1


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

--- 192.168.1.254 ping statistics ---
3 packets transmitted, 2 received, 33% packet loss, time 2010ms
rtt min/avg/max/mdev = 15.907/46.328/76.750/30.422 ms

--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.012/0.017/0.022/0.005 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "en_SG.UTF-8")
country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

           - 


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~



blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[asus_nb_wmi]
filename:       /lib/modules/4.2.0-34-generic/kernel/drivers/platform/x86/asus-nb-wmi.ko
srcversion:     CE32C9C3CCE4BE7F4B5B168
depends:        asus-wmi
parm:           wapf:WAPF value (uint)

[asus_wmi]
filename:       /lib/modules/4.2.0-34-generic/kernel/drivers/platform/x86/asus-wmi.ko
srcversion:     D385C89D75055532B951C20
depends:        sparse-keymap,wmi,video

[mxm_wmi]
filename:       /lib/modules/4.2.0-34-generic/kernel/drivers/platform/x86/mxm-wmi.ko
srcversion:     D566C16ECB7E11FB9DF5C84
depends:        wmi

[video]
filename:       /lib/modules/4.2.0-34-generic/kernel/drivers/acpi/video.ko
srcversion:     F9D08BA7BA107EEB1492A78
depends:        
parm:           brightness_switch_enabled:bool
parm:           allow_duplicates:bool
parm:           disable_backlight_sysfs_if:int

[wmi]
filename:       /lib/modules/4.2.0-34-generic/kernel/drivers/platform/x86/wmi.ko
srcversion:     41F0EAB96A1B6E1B29D03E9
depends:        
parm:           debug_event:Log WMI Events [0/1] (bool)
parm:           debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x10ec:0x8821 (rtl8821ae)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


Custom files/entries ~~~~~~~~~~~~~~~

/etc/modules        : Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Default

[/etc/modprobe.d]
asus_nb_wmi.conf  : options asus_nb_wmi wapf=1
blacklist-native-rtl8192.conf: install rtl8192cu /bin/false
                    install rtl8192c_common /bin/false
                    install rtlwifi /bin/false
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
mlx4.conf         : softdep mlx4_core post: mlx4_en
rtl8821ae.conf    : options rtl8821ae swenc=1 ips=0 fwlps=0


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/boot/vmlinuz-4.2.0-34-generic.efi.signed root=UUID=9c564aa5-1c6d-461b-9c14-33cbf7b0adf0 ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    0.017314] Initializing cgroup subsys net_cls
[    0.017316] Initializing cgroup subsys net_prio
[    0.372508] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.372817] audit: initializing netlink subsys (disabled)
[    0.432787] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[   11.259364] wmi: Mapper loaded
[   11.301311] Bluetooth: hci0: rtl: examining hci_ver=06 hci_rev=000a lmp_ver=06 lmp_subver=8821
[   11.301314] Bluetooth: hci0: rtl: loading rtl_bt/rtl8821a_fw.bin
[   11.374009] asus_wmi: ASUS WMI generic driver loaded
[   11.375155] asus_wmi: Initialization: 0x1
[   11.375187] asus_wmi: BIOS WMI version: 7.9
[   11.375223] asus_wmi: SFUN value: 0x4a0877
[   11.376117] input: Asus WMI hotkeys as /devices/platform/asus-nb-wmi/input/input13
[   11.385760] asus_wmi: Number of fans: 1
[   11.672533] bluetooth hci0: Direct firmware load for rtl_bt/rtl8821a_fw.bin failed with error -2
[   11.672537] Bluetooth: hci0: Failed to load rtl_bt/rtl8821a_fw.bin
[   14.730166] Bluetooth: BNEP (Ethernet Emulation) ver 1.3

    ======== Done ========

```

---

### Post by jeremy31 on 2016-03-18
First ```
sudo rm /etc/modprobe.d/blacklist-native-rtl8192.conf
```

Reboot run ```
rm wireless-info.txt && ./wireless-info
```

And post the new wireless-info.txt

---

### Post by kavanohk on 2016-03-19
Thanks my wireless is working again. :D
```

########## wireless info START ##########

Report from: 19 Mar 2016 15:01 SGT +0800

Booted last: 19 Mar 2016 14:52 SGT +0800

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.4 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 4.2.0-34-generic #39~14.04.1-Ubuntu SMP Fri Mar 11 11:38:02 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

GNOME

##### lspci #############################

03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8821AE 802.11ac PCIe Wireless Network Adapter [10ec:8821]
    Subsystem: AzureWave Device [1a3b:2161]
    Kernel driver in use: rtl8821ae

04:00.1 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 12)
    Subsystem: ASUSTeK Computer Inc. Device [1043:200f]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 04f2:b48c Chicony Electronics Co., Ltd 
Bus 001 Device 003: ID 13d3:3414 IMC Networks 
Bus 001 Device 002: ID 046d:c077 Logitech, Inc. M105 Optical Mouse
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: asus-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

rtl8821ae             319488  0 
btcoexist             180224  1 rtl8821ae
rtl_pci                40960  1 rtl8821ae
rtlwifi               102400  3 btcoexist,rtl_pci,rtl8821ae
asus_nb_wmi            24576  0 
asus_wmi               28672  1 asus_nb_wmi
mxm_wmi                16384  0 
sparse_keymap          16384  1 asus_wmi
mac80211              729088  3 rtl_pci,rtlwifi,rtl8821ae
cfg80211              540672  2 mac80211,rtlwifi
wmi                    20480  2 mxm_wmi,asus_wmi
video                  40960  2 i915,asus_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet6 addr: fe80::<IP6 'eth0' [IF]>/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:165 errors:0 dropped:0 overruns:0 frame:0
          TX packets:92 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:22865 (22.8 KB)  TX bytes:11842 (11.8 KB)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlan0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1363 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1172 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:538212 (538.2 KB)  TX bytes:167932 (167.9 KB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"what wifi"  
          Mode:Managed  Frequency:2.417 GHz  Access Point: <MAC 'what wifi' [AC1]>   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-15 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:5   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       879     1  0 14:52 ?        00:00:00 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         off

- Device: wlan0  [what wifi] ---------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8821ae
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:
    Speed:           72 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    SINGTEL-E64B:    Infra, <MAC 'SINGTEL-E64B' [AC9]>, Freq 5200 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    SINGTEL-E64B:    Infra, <MAC 'SINGTEL-E64B' [AC2]>, Freq 2417 MHz, Rate 54 Mb/s, Strength 67 WPA WPA2
    Singtel7002-3BA7:Infra, <MAC 'Singtel7002-3BA7' [AC6]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 57 WPA WPA2
    DVG-N5402SP-8af0a0: Infra, <MAC 'DVG-N5402SP-8af0a0' [AC5]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 50 WPA WPA2
    SINGTEL-957A:    Infra, <MAC 'SINGTEL-957A' [AN5]>, Freq 2447 MHz, Rate 54 Mb/s, Strength 44 WPA2
    House2:          Infra, <MAC 'House2' [AN6]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 47 WPA WPA2
    nasikandar:      Infra, <MAC 'nasikandar' [AC8]>, Freq 2427 MHz, Rate 54 Mb/s, Strength 47 WPA WPA2
    dlink-0920:      Infra, <MAC 'dlink-0920' [AC3]>, Freq 2432 MHz, Rate 54 Mb/s, Strength 40 WPA WPA2
    Suresh:          Infra, <MAC 'Suresh' [AN9]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 40 WPA WPA2
    *what wifi:      Infra, <MAC 'what wifi' [AC1]>, Freq 2417 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    SINGTEL-A887:    Infra, <MAC 'SINGTEL-A887' [AC4]>, Freq 2432 MHz, Rate 54 Mb/s, Strength 54 WPA WPA2
    dlink-4B04:      Infra, <MAC 'dlink-4B04' [AN12]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2
    Kanjonoko18:     Infra, <MAC 'Kanjonoko18' [AN13]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 37 WPA WPA2
    SINGTEL-45EC:    Infra, <MAC 'SINGTEL-45EC' [AN14]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 40 WPA WPA2
    SINGTEL-C7EF:    Infra, <MAC 'SINGTEL-C7EF' [AN15]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 37 WPA WPA2
    heavensberry:    Infra, <MAC 'heavensberry' [AN16]>, Freq 2422 MHz, Rate 54 Mb/s, Strength 44 WPA2
    dlink-E0A0:      Infra, <MAC 'dlink-E0A0' [AN17]>, Freq 2427 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2
    SINGTEL-9521:    Infra, <MAC 'SINGTEL-9521' [AN18]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    Singtel7002-6723:Infra, <MAC 'Singtel7002-6723:Infra, <MAC address>, Freq 2462 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2' [AN19]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    SIBYL SYSTEM:    Infra, <MAC 'SIBYL SYSTEM' [AN20]>, Freq 2457 MHz, Rate 54 Mb/s, Strength 37 WEP
    SINGTEL-9D9E:    Infra, <MAC 'SINGTEL-9D9E' [AN21]>, Freq 2432 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    SINGTEL-1051:    Infra, <MAC 'SINGTEL-1051' [AN22]>, Freq 2422 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2
    SINGTEL-62B2:    Infra, <MAC 'SINGTEL-62B2' [AN23]>, Freq 2422 MHz, Rate 54 Mb/s, Strength 40 WPA2
    Rai:             Infra, <MAC 'Rai' [AC7]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 37 WPA2
    ASUS:            Infra, <MAC 'ASUS' [AN25]>, Freq 2467 MHz, Rate 54 Mb/s, Strength 34 WPA2

  IPv4 Settings:
    Address:         192.168.1.5
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254

    DNS:             192.168.1.254

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/SINGTEL-E64B]] (600 root)
[connection] id=SINGTEL-E64B | type=802-11-wireless
[802-11-wireless] ssid=SINGTEL-E64B | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/NTUWL]] (600 root)
[connection] id=NTUWL | type=802-11-wireless
[802-11-wireless] ssid=NTUWL | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/NTUSECURE]] (600 root)
[ipv6] method=auto
[connection] id=NTUSECURE | type=802-11-wireless
[802-11-wireless] ssid=NTUSECURE | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/what wifi]] (600 root)
[connection] id=what wifi | type=802-11-wireless
[802-11-wireless] ssid=what wifi | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Asia/Singapore (based on set time zone)

country SG:
    (2402 - 2482 @ 40), (N/A, 20)
    (5170 - 5250 @ 40), (N/A, 20)
    (5250 - 5330 @ 40), (N/A, 20), DFS
    (5735 - 5835 @ 40), (N/A, 20)

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

wlan0     26 channels in total; available frequencies :
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
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 149 : 5.745 GHz
          Channel 153 : 5.765 GHz
          Channel 157 : 5.785 GHz
          Channel 161 : 5.805 GHz
          Channel 165 : 5.825 GHz
          Current Frequency:2.417 GHz (Channel 2)

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      2   APs on   Frequency:2.417 GHz (Channel 2)
      2   APs on   Frequency:2.432 GHz (Channel 5)
      3   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.447 GHz (Channel 8)
      1   APs on   Frequency:5.2 GHz (Channel 40)

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'what wifi' [AC1]>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=70/70  Signal level=-15 dBm  
                    Encryption key:on
                    ESSID:"what wifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000203ae5ac64
                    Extra: Last beacon: 48ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'SINGTEL-E64B' [AC2]>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=50/70  Signal level=-60 dBm  
                    Encryption key:on
                    ESSID:"SINGTEL-E64B"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000203b4549af
                    Extra: Last beacon: 48ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'dlink-0920' [AC3]>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"dlink-0920"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001bd515c7185
                    Extra: Last beacon: 6932ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'SINGTEL-A887' [AC4]>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"SINGTEL-A887"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000e3b28ed183
                    Extra: Last beacon: 6932ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'DVG-N5402SP-8af0a0' [AC5]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"DVG-N5402SP-8af0a0"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    ESSID:""
                    ESSID:""
                    ESSID:""
                    ESSID:""
                    ESSID:""
                    Mode:Master
                    Extra:tsf=00000003e3757eb5
                    Extra: Last beacon: 6620ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'Singtel7002-3BA7' [AC6]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"Singtel7002-3BA7"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000068029bb0
                    Extra: Last beacon: 6620ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'Rai' [AC7]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"Rai"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000002e46311aa
                    Extra: Last beacon: 6592ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC 'nasikandar' [AC8]>
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"nasikandar"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000011dc4dc4183
                    Extra: Last beacon: 5972ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC 'SINGTEL-E64B' [AC9]>
                    Channel:40
                    Frequency:5.2 GHz (Channel 40)
                    Quality=70/70  Signal level=-22 dBm  
                    Encryption key:on
                    ESSID:"SINGTEL-E64B"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001a7a1349a89
                    Extra: Last beacon: 48ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[rtl8821ae]
filename:       /lib/modules/4.2.0-34-generic/kernel/drivers/net/wireless/rtlwifi/rtl8821ae/rtl8821ae.ko
firmware:       rtlwifi/rtl8821aefw.bin
description:    Realtek 8821ae 802.11ac PCI wireless
license:        GPL
author:         Realtek WlanFAE    <wlanfae@realtek.com>
srcversion:     B44D8007FC715E99771FA11
depends:        rtlwifi,rtl_pci,btcoexist,mac80211
vermagic:       4.2.0-34-generic SMP mod_unload modversions 
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           msi:Set to 1 to use MSI interrupts mode (default 1)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)
parm:           disable_watchdog:Set to 1 to disable the watchdog (default 0)
 (bool)
parm:           int_clear:Set to 0 to disable interrupt clear before set (default 1)
 (bool)

[rtl_pci]
filename:       /lib/modules/4.2.0-34-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     8552A7BAFD0FCC2C41CF075
depends:        mac80211,rtlwifi
vermagic:       4.2.0-34-generic SMP mod_unload modversions 

[rtlwifi]
filename:       /lib/modules/4.2.0-34-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     990116D31097F1C4C1F7006
depends:        mac80211,cfg80211
vermagic:       4.2.0-34-generic SMP mod_unload modversions 

[mac80211]
filename:       /lib/modules/4.2.0-34-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     292BCC26A10EA884DF6B5FF
depends:        cfg80211
intree:         Y
vermagic:       4.2.0-34-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        D4:AC:CB:BD:31:2B:A9:DF:31:75:37:B8:F5:87:03:49:6C:E2:E7:C8
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.2.0-34-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     7982686FBE8064A87E02753
depends:        
intree:         Y
vermagic:       4.2.0-34-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        D4:AC:CB:BD:31:2B:A9:DF:31:75:37:B8:F5:87:03:49:6C:E2:E7:C8
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rtl8821ae]
debug: 1
disable_watchdog: N
fwlps: N
int_clear: Y
ips: N
msi: Y
swenc: Y
swlps: N

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
probe_wait_ms: 500

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

lp
rtc

##### modprobe options ##################

[/etc/modprobe.d/asus_nb_wmi.conf]
options asus_nb_wmi wapf=1

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

[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

[/etc/modprobe.d/rtl8821ae.conf]
options rtl8821ae swenc=1 ips=0 fwlps=0

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x10ec:0x8821 (rtl8821ae)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[   11.426270] rtlwifi: module verification failed: signature and/or required key missing - tainting kernel
[   11.470534] Using firmware rtlwifi/rtl8821aefw.bin
[   11.470694] rtlwifi: channel plan 0x7f
[   11.470695] rtlwifi: country code 13
[   11.473151] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   11.473330] rtlwifi: wireless switch is on
[   15.733874] rtl8821ae:_rtl8821ae_fw_free_to_go():<0-0> Checksum report OK ! REG_MCUFWDL:0x00070304 .
[   15.867515] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   15.917482] r8169 0000:04:00.1 eth0: link down (repeated 2 times)
[   15.917531] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   18.619108] r8169 0000:04:00.1 eth0: link up
[   18.619117] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   18.822605] wlan0: authenticate with <MAC 'what wifi' [AC1]>
[   18.822977] wlan0: send auth to <MAC 'what wifi' [AC1]> (try 1/3)
[   18.826994] wlan0: authenticated
[   18.829061] wlan0: associate with <MAC 'what wifi' [AC1]> (try 1/3)
[   18.833441] wlan0: RX AssocResp from <MAC 'what wifi' [AC1]> (capab=0x411 status=0 aid=2)
[   18.833648] wlan0: associated
[   18.833657] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  112.055205] r8169 0000:04:00.1 eth0: link down

########## wireless info END ############


```

---

### Post by jeremy31 on 2016-03-19
Please use thread tools menu to mark as solved

---

