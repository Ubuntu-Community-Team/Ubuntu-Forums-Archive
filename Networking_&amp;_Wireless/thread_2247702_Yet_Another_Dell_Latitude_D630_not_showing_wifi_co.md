---
title: "Yet Another Dell Latitude D630 not showing wifi connection"
date: 2014-10-09
forum: Networking &amp; Wireless
---

### Post by scott-watkins on 2014-10-09
Hi there.

I've got the same problem as this thread:
ubuntuforums.org/showthread.php?t=2188955& 

I've installed linux-firmware-nonfree and that did not work. neither did copying over the iwlegacy drivers I found elswhere.

the wireless script output is as follows:


    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

BunOnBoard 3.13.0-37-generic i686,  Ubuntu 14.04.1 LTS, trusty

CPU    : Intel(R) Core(TM)2 Duo CPU     T7100  @ 1.80GHz
Memory : 2014 MB
Uptime : 16:49:32 up 18 min,  2 users,  load average: 0.52, 0.24, 0.29


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

09:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5755M Gigabit Ethernet PCI Express [14e4:1673] (rev 02)
    Subsystem: Dell Device [1028:01f9]
    Kernel driver in use: tg3
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
    Subsystem: Dell Wireless 1390 WLAN Mini-Card [1028:0007]
    Kernel driver in use: b43-pci-bridge


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 002 Device 004: ID 12d1:1506 Huawei Technologies Co., Ltd. E398 LTE/UMTS/GSM Modem/Networkcard
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 003: ID 0b97:7772 O2 Micro, Inc. OZ776 CCID Smartcard Reader
Bus 007 Device 002: ID 0b97:7761 O2 Micro, Inc. Oz776 1.1 Hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 413c:8140 Dell Computer Corp. Wireless 360 Bluetooth
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~

PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255


iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~



rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface               Soft blocked  Hard blocked
1: dell-wifi: Wireless LAN        no            no
2: dell-bluetooth: Bluetooth      no            no
3: hci0: Bluetooth                no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

b43                   356470  0 
dell_wmi               12665  0 
sparse_keymap          13708  1 dell_wmi
bcma                   42043  1 b43
mac80211              546051  1 b43
cfg80211              409394  2 b43,mac80211
wmi                    18673  1 dell_wmi
ssb_hcd                12749  0 
ssb                    51854  2 b43,ssb_hcd


module parameters ~~~~~~~~~~~~~~~~~~

b43          (10): allhwsupport=0 | bad_frames_preempt=0 | btcoex=1 | hwpctl=0 | hwtkip=0 | nohwcrypt=0 | pio=0 | qos=1 | verbose=2
cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
=============================================o========================o===================o=============o=========o===========o==============o===========
 Interface & ID                              | Type                   | Driver            | State       | Default | Speed     | Support      | HW Addr   
=============================================o========================o===================o=============o=========o===========o==============o===========
 cdc-wdm0  [WIND Mobile Laptop (data stick)] | Mobile Broadband (GSM) | option1, qmi_wwan | connected   | yes     |           |              |           

    Address:         10.148.22.36
    Prefix:          29 (255.255.255.248)
    Gateway:         10.148.22.33
    DNS:             199.7.156.169
    DNS:             199.7.156.168
---------------------------------------------+------------------------+-------------------+-------------+---------+-----------+--------------+-----------
 eth0                                        | Wired                  | tg3               | unavailable | no      |           |              | <MAC eth0>
---------------------------------------------+------------------------+-------------------+-------------+---------+-----------+--------------+-----------


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

nameserver 127.0.1.1


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.148.22.33    0.0.0.0         UG    0      0        0 wwan0
10.148.22.32    0.0.0.0         255.255.255.248 U     13     0        0 wwan0

--- 10.148.22.33 ping statistics ---
4 packets transmitted, 0 received, 100% packet loss, time 3024ms


--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.034/0.045/0.057/0.013 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "en_CA.UTF-8")
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

[b43]
filename:       /lib/modules/3.13.0-37-generic/kernel/drivers/net/wireless/b43/b43.ko
firmware:       b43/ucode9.fw
firmware:       b43/ucode5.fw
firmware:       b43/ucode16_mimo.fw
firmware:       b43/ucode15.fw
firmware:       b43/ucode14.fw
firmware:       b43/ucode13.fw
firmware:       b43/ucode11.fw
srcversion:     7ABBDDCA84C087640B27AE6
depends:        bcma,ssb,mac80211,cfg80211
parm:           bad_frames_preempt:enable(1) / disable(0) Bad Frames Preemption (int)
parm:           fwpostfix:Postfix for the .fw files to load. (string)
parm:           hwpctl:Enable hardware-side power control (default off) (int)
parm:           nohwcrypt:Disable hardware encryption. (int)
parm:           hwtkip:Enable hardware tkip. (int)
parm:           qos:Enable QOS support (default on) (int)
parm:           btcoex:Enable Bluetooth coexistence (default on) (int)
parm:           verbose:Log message verbosity: 0=error, 1=warn, 2=info(default), 3=debug (int)
parm:           pio:Use PIO accesses by default: 0=DMA, 1=PIO (int)
parm:           allhwsupport:Enable support for all hardware (even it if overlaps with the brcmsmac driver) (int)

[dell_wmi]
filename:       /lib/modules/3.13.0-37-generic/kernel/drivers/platform/x86/dell-wmi.ko
srcversion:     0ED3A43A5709CF19B7DFD19
depends:        wmi,sparse-keymap

[bcma]
filename:       /lib/modules/3.13.0-37-generic/kernel/drivers/bcma/bcma.ko
srcversion:     E41B811D88783DD5BC38565
depends:        

[mac80211]
filename:       /lib/modules/3.13.0-37-generic/kernel/net/mac80211/mac80211.ko
srcversion:     B822641624778B987844F6F
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-37-generic/kernel/net/wireless/cfg80211.ko
srcversion:     C2478077E22138832B71659
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[wmi]
filename:       /lib/modules/3.13.0-37-generic/kernel/drivers/platform/x86/wmi.ko
srcversion:     CED5410F008DC70DF5F064B
depends:        
parm:           debug_event:Log WMI Events [0/1] (bool)
parm:           debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)

[ssb_hcd]
filename:       /lib/modules/3.13.0-37-generic/kernel/drivers/usb/host/ssb-hcd.ko
srcversion:     2A4C0EB5791EE9A11133FCB
depends:        ssb

[ssb]
filename:       /lib/modules/3.13.0-37-generic/kernel/drivers/ssb/ssb.ko
srcversion:     3DE188310F77C566C2E8CB3
depends:        


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x14e4:0x1673 (tg3)
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

BOOT_IMAGE=/boot/vmlinuz-3.13.0-37-generic root=UUID=d534e8af-439d-457e-8095-ca9ca88ea5bf ro quiet splash


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    0.844727] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.845114] audit: initializing netlink socket (disabled)
[    2.513942] ssb: Found chip with id 0x4311, rev 0x01 and package 0x00
[    2.513954] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x11, vendor 0x4243)
[    2.513963] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x0A, vendor 0x4243)
[    2.513973] ssb: Core 2 found: USB 1.1 Host (cc 0x817, rev 0x03, vendor 0x4243)
[    2.513982] ssb: Core 3 found: PCI-E (cc 0x820, rev 0x01, vendor 0x4243)
[    2.562217] tg3 0000:09:00.0 eth0: attached PHY is 5755 (10/100/1000Base-T Ethernet) (WireSpeed[1], EEE[0])
[    2.584132] ssb: Sonics Silicon Backplane found on PCI device 0000:0c:00.0
[   13.375905] wmi: Mapper loaded
[   14.935811] b43-phy0: Broadcom 4311 WLAN found (core revision 10)
[   14.980031] b43-phy0: Found PHY: Analog 4, Type 2 (G), Revision 8
[   15.204293] b43 ssb0:0: Direct firmware load failed with error -2
[   15.204299] b43 ssb0:0: Falling back to user helper
[   15.205127] b43 ssb0:0: Direct firmware load failed with error -2
[   15.205131] b43 ssb0:0: Falling back to user helper
[   15.206037] b43 ssb0:0: Direct firmware load failed with error -2
[   15.206040] b43 ssb0:0: Falling back to user helper
[   15.206962] b43 ssb0:0: Direct firmware load failed with error -2
[   15.206965] b43 ssb0:0: Falling back to user helper
[   15.208223] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   15.208294] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   15.208361] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[   22.670128] Bluetooth: BNEP (Ethernet Emulation) ver 1.3

    ======== Done ========

I'm stumped. Any ideas?

---

### Post by Hadaka on 2014-10-09
Hi, please open a terminal and while connected to the internet
via cable...ethernet...please do..
```
sudo apt-get remove --purge linux-firmware-nonfree
sudo apt-get remove --purge b43-fwcutter firmware-b43-installer
sudo apt-get install b43-fwcutter firmware-b43-installer
sudo modprobe -rf b43
sudo modprobe b43
```
Ignore any file not found messages, and speaking of ignore
please set your network manager IPv6 to ignore.
thanks.

---

