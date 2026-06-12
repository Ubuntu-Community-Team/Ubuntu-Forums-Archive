---
title: "Wifi not working - 14.04 LTS - Broadcom BCM4313"
date: 2014-07-05
forum: Networking &amp; Wireless
---

### Post by lars6 on 2014-07-05
Hi Forum

New to the forum as well as Ubuntu. Installed 14.04 on my Samsung SF310 laptop this morning. Everything went pretty smooth, but I can't get wi-fi to work.
Our home network can be seen by the computer, but it refuses to log on. Searched the forums but haven't been able to find anything that worked.
After install I upgraded the system (apt-get upgrade & apt get dist-upgrade)

I found the [Broadcom guide]("http://ubuntuforums.org/showthread.php?t=2214110") and then ran this:


```
lspci -nn -d 14e4:
```


which gave:
Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)

However this particular revision does not appear to be in the list.
Any hint on what to do?

Lastly the output from the script found in the [Before posting in Networking & Wireless]("http://ubuntuforums.org/showthread.php?t=370108") thread:


```
########## wireless info START ##########

##### release #####

Distributor ID: Ubuntu
Description: Ubuntu 14.04 LTS
Release: 14.04
Codename: trusty

##### kernel #####

Linux UbuntuLars 3.13.0-30-generic #54-Ubuntu SMP Mon Jun 9 22:45:01 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

##### lspci #####

02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
Subsystem: Askey Computer Corp. Device [144f:7179]
Kernel driver in use: wl
03:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. Yukon Optima 88E8059 [PCIe Gigabit Ethernet Controller with AVB] [11ab:4381] (rev 11)
Subsystem: Samsung Electronics Co Ltd Device [144d:c08b]
Kernel driver in use: sky2

##### lsusb #####

Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 2232:1001
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA Card Info #####

##### rfkill #####

1: samsung-wlan: Wireless LAN
Soft blocked: no
Hard blocked: no
2: samsung-bluetooth: Bluetooth
Soft blocked: yes
Hard blocked: no
3: phy0: Wireless LAN
Soft blocked: no
Hard blocked: no
4: brcmwl-0: Wireless LAN
Soft blocked: no
Hard blocked: no

##### lsmod #####

wl 4207846 0
lib80211 14381 2 wl,lib80211_crypt_tkip
cfg80211 484040 1 wl

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

wlan0 IEEE 802.11abg ESSIDff/any
Mode:Managed Access Point: Not-Associated
Retry long limit:7 RTS thrff Fragment thrff
Power Managementff


##### route #####

Kernel IP routing table
Destination Gateway Genmask Flags Metric Ref Use Iface
0.0.0.0 192.168.1.1 0.0.0.0 UG 0 0 0 eth0
192.168.1.0 0.0.0.0 255.255.255.0 U 1 0 0 eth0

##### resolv.conf #####

nameserver 127.0.1.1
search mydomain

##### nm-tool #####

NetworkManager Tool

State: connected (global)

- Device: eth0 [Wired connection 1] -------------------------------------------
Type: Wired
Driver: sky2
State: connected
Default: yes
HW Address: <MAC address removed>

Capabilities:
Carrier Detect: yes
Speed: 100 Mb/s

Wired Properties
Carrier: on

IPv4 Settings:
Address: 192.168.1.139
Prefix: 24 (255.255.255.0)
Gateway: 192.168.1.1

DNS: 192.168.1.1

- Device: wlan0 ----------------------------------------------------------------
Type: 802.11 WiFi
Driver: wl
State: disconnected
Default: no
HW Address: <MAC address removed>

Capabilities:

Wireless Properties
WEP Encryption: yes
WPA Encryption: yes
WPA2 Encryption: yes

Wireless Access Points
LDmac: Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 90 WPA WPA2
Gnet: Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 85 WPA2
Waoo2013: Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 82 WPA2
ogilvie: Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 52 WPA2
nsdc: Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 30 WPA2
Duly WiFI: Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 22 WPA2
familienet: Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 42 WPA2
Alkalifeldspatkrystaller: Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 25 WPA2
Smukke Esben: Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 14 WPA2

##### NetworkManager.state #####

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf #####

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### iwlist #####

wlan0 Scan completed :
Cell 01 - Address: <MAC address removed>
Channel:6
Frequency:2.437 GHz (Channel 6)
Quality=57/70 Signal level=-53 dBm
Encryption keyn
ESSID:"Waoo2013"
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
9 Mb/s; 12 Mb/s; 18 Mb/s
Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
Mode:Master
Extra:tsf=0000000000000000
Extra: Last beacon: 4ms ago
IE: Unknown: 000857616F6F32303133
IE: Unknown: 010882848B960C121824
IE: Unknown: 030106
IE: Unknown: 0706444B20010D14
IE: Unknown: 2A0104
IE: Unknown: 32043048606C
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : CCMP TKIP
Authentication Suites (1) : PSK
IE: Unknown: 2D1AAC001BFFFF000000000000000000000100000000000000000000
IE: Unknown: 3D1606000400000000000000000000000000000000000000
IE: Unknown: DD180050F2020101000003A4000027A4000042435D0062322E00
Cell 02 - Address: <MAC address removed>
Channel:6
Frequency:2.437 GHz (Channel 6)
Quality=70/70 Signal level=-35 dBm
Encryption keyn
ESSID:"Gnet"
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
9 Mb/s; 12 Mb/s; 18 Mb/s
Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
Mode:Master
Extra:tsf=0000000000000000
Extra: Last beacon: 4ms ago
IE: Unknown: 0004476E6574
IE: Unknown: 010882848B960C121824
IE: Unknown: 030106
IE: Unknown: 0706444B20010D14
IE: Unknown: 2A0104
IE: Unknown: 32043048606C
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : CCMP TKIP
Authentication Suites (1) : PSK
IE: Unknown: 2D1AAC001BFFFF000000000000000000000100000000000000000000
IE: Unknown: 3D1606000000000000000000000000000000000000000000
IE: Unknown: DD180050F2020101000003A4000027A4000042435D0062322E00
Cell 03 - Address: <MAC address removed>
Channel:6
Frequency:2.437 GHz (Channel 6)
Quality=35/70 Signal level=-75 dBm
Encryption keyn
ESSID:"ogilvie"
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
9 Mb/s; 12 Mb/s; 18 Mb/s
Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
Mode:Master
Extra:tsf=0000000000000000
Extra: Last beacon: 4ms ago
IE: Unknown: 00076F67696C766965
IE: Unknown: 010882848B960C121824
IE: Unknown: 030106
IE: Unknown: 0706444B20010D14
IE: Unknown: 2A0104
IE: Unknown: 32043048606C
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : CCMP TKIP
Authentication Suites (1) : PSK
IE: Unknown: 2D1AAC001BFFFF000000000000000000000100000000000000000000
IE: Unknown: 3D1606000400000000000000000000000000000000000000
IE: Unknown: DD180050F2020101000003A4000027A4000042435D0062322E00
Cell 04 - Address: <MAC address removed>
Channel:11
Frequency:2.462 GHz (Channel 11)
Quality=68/70 Signal level=-42 dBm
Encryption keyn
ESSID:"LDmac"
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
9 Mb/s; 12 Mb/s; 18 Mb/s
Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
Mode:Master
Extra:tsf=0000000000000000
Extra: Last beacon: 4ms ago
IE: Unknown: 00054C446D6163
IE: Unknown: 010882848B960C121824
IE: Unknown: 03010B
IE: Unknown: 0706444B20010D1E
IE: Unknown: 2A0100
IE: Unknown: 32043048606C
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : CCMP TKIP
Authentication Suites (1) : PSK
IE: Unknown: 2D1AAD511BFFFF000000000000000000000000000000000000000000
IE: Unknown: 3D160B080400000000000000000000000000000000000000
IE: Unknown: 46050200010000
IE: WPA Version 1
Group Cipher : TKIP
Pairwise Ciphers (1) : TKIP
Authentication Suites (1) : PSK
IE: Unknown: DD180050F2020101060003A4000027A4000042435E0062322F00
IE: Unknown: DD0700039301730B20
IE: Unknown: DD0E0017F207000101062837374880A6
IE: Unknown: DD0B0017F20100010100000007
Cell 05 - Address: <MAC address removed>
Channel:6
Frequency:2.437 GHz (Channel 6)
Quality=21/70 Signal level=-89 dBm
Encryption keyn
ESSID:"Qualen"
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
9 Mb/s; 12 Mb/s; 18 Mb/s
Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
Mode:Master
Extra:tsf=0000000000000000
Extra: Last beacon: 4ms ago
IE: Unknown: 00065175616C656E
IE: Unknown: 010882848B960C121824
IE: Unknown: 030106
IE: Unknown: 050401020000
IE: Unknown: 0706444B20010D14
IE: Unknown: 2A0104
IE: Unknown: 32043048606C
IE: Unknown: DD180050F2020101000003A4000027A4000042435D0062322E00
Cell 06 - Address: <MAC address removed>
Channel:6
Frequency:2.437 GHz (Channel 6)
Quality=27/70 Signal level=-83 dBm
Encryption keyn
ESSID:"familienet"
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
9 Mb/s; 12 Mb/s; 18 Mb/s
Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
Mode:Master
Extra:tsf=0000000000000000
Extra: Last beacon: 4ms ago
IE: Unknown: 000A66616D696C69656E6574
IE: Unknown: 010882848B960C121824
IE: Unknown: 030106
IE: Unknown: 050401020000
IE: Unknown: 0706444B20010D14
IE: Unknown: 2A0104
IE: Unknown: 32043048606C
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : CCMP TKIP
Authentication Suites (1) : PSK
IE: Unknown: 2D1AAC001BFFFF000000000000000000000100000000000000000000
IE: Unknown: 3D1606001700000000000000000000000000000000000000
IE: Unknown: DD180050F2020101000003A4000027A4000042435D0062322E00

##### iwlist channel #####

wlan0 26 channels in total; available frequencies :
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
Channel 14 : 2.484 GHz
Channel 36 : 5.18 GHz
Channel 38 : 5.19 GHz
Channel 40 : 5.2 GHz
Channel 42 : 5.21 GHz
Channel 44 : 5.22 GHz
Channel 46 : 5.23 GHz
Channel 48 : 5.24 GHz
Channel 149 : 5.745 GHz
Channel 153 : 5.765 GHz
Channel 157 : 5.785 GHz
Channel 161 : 5.805 GHz
Channel 165 : 5.825 GHz

##### modinfo #####

filename: /lib/modules/3.13.0-30-generic/updates/dkms/wl.ko
license: MIXED/Proprietary
srcversion: FF25FE784DC6BDFF69DAFCB
alias: pci:v*d*sv*sd*bc02sc80i*
depends: cfg80211,lib80211
vermagic: 3.13.0-30-generic SMP mod_unload modversions
parm: wl_txq_thresh:int
parm: oneonly:int
parm: piomode:int
parm: instance_base:int
parm: nompc:int
parm: intf_name:string

##### modules #####

lp
rtc

##### blacklist #####

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist-bcm43.conf]
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist brcm80211
blacklist brcmfmac
blacklist brcmsmac
blacklist bcma

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

# PCI device 0x11ab:0x4381 (sky2)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x14e4:0x4727 (brcmsmac)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #####

[ 1.995067] psmouse serio1: elantech: assuming hardware version 3 (with firmware version 0x851b00)
[ 10.623760] wl: module license 'MIXED/Proprietary' taints kernel.
[ 10.626112] wl: module verification failed: signature and/or required key missing - tainting kernel
[ 10.660273] INFO @wl_cfg80211_attach : Registered CFG80211 phy
[ 10.768137] wlan0: Broadcom BCM4727 802.11 Hybrid Wireless Controller 6.30.223.141 (r415941)
[ 3936.960915] ERROR @wl_dev_intvar_get : error (-1)
[ 3936.960920] ERROR @wl_cfg80211_get_tx_power : error (-1)

########## wireless info END ############
```


Thanks!
Lars

---

### Post by kc1di on 2014-07-05
That card uses the Boadcom b43 driver not the WL/Sta one.
you can try going to software center >edit>software sources>Additional drivers tab.
See if it offers you the b43 firmware , if so install it.  it sould blacklist wl for you.
If that doesn't work let me know we will have to do it the harder way :)

---

### Post by lars6 on 2014-07-05
Thanks for your reply, Dave.

Unfortunately, it doesn't look like there is any firmware available in the Additional drivers tab.
It lists the Broadcom driver though, but it seems like it is just showing the driver in use.


Cheers,
Lars

---

### Post by benhait on 2014-07-05
you can turn it off and on again
Regards
[www.fvtm.bu.edu.eg]("http://www.fvtm.bu.edu.eg")

---

### Post by kc1di on 2014-07-05
Ok got to additional drivers and uninstall the bcmwl-kernel-source

then go to a terminal and instlall b43 drivers with the following commands:
```
sudo apt-get install b43-fwcutter firmware-b43-installer
```

Reboot and see if it works.  let me know if it doesn't we will go from there.

---

### Post by lars6 on 2014-07-06
Sure enough, installing the b43 drivers worked!!!
Thanks for the help.

Cheers,
Lars

---

### Post by varunendra on 2014-07-06
I would love to see the current report, because the "b43" driver CAN NOT work with this card. It is supported by either the native "brcmsmac" (requires no additional firmware for this card) or proprietary "wl" driver (which you already had in the first report).

So my guess is that it is the "brcmsmac" that is automatically loading (obviously) after removing (purging) the "wl" driver, and installing the firmware has absolutely nothing to do with the fix.

---

### Post by kc1di on 2014-07-06
Glad it's working for you :)

---

### Post by kc1di on 2014-07-06
Varun - I'm not sure either why it works but this is the 3rd card that it has worked on. 

I really think and have not found one in my travels through the forums or the wikis that we need a clear and concise write up on the Broadcom Wireless cards and what works with what and how to install them.  Maybe someone has already done it , but I haven't seen it yet.  
I find a lot of out dated stuff , but nothing current , if I am in error and such a how to do exists please point me to it so I can point other to it also. 
I find there seems to be much confusion and many, many questions about this particular family of card in all the distros.  
Cheers - Dave

---

### Post by lars6 on 2014-07-06
Hi

Here is the current output of the script:

```


======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

UbuntuLars 3.13.0-30-generic x86_64, Ubuntu 14.04 LTS, trusty

CPU : Intel(R) Core(TM) i5 CPU M 480 @ 2.67GHz
Memory : 3741 MB
Uptime : 13:14:39 up 12 min, 2 users, load average: 0.13, 0.17, 0.17


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
Subsystem: Askey Computer Corp. Device [144f:7179]
Kernel driver in use: bcma-pci-bridge
03:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. Yukon Optima 88E8059 [PCIe Gigabit Ethernet Controller with AVB] [11ab:4381] (rev 11)
Subsystem: Samsung Electronics Co Ltd Device [144d:c08b]
Kernel driver in use: sky2


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 2232:1001
Bus 001 Device 004: ID 1532:0016 Razer USA, Ltd DeathAdder Mouse
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0 IEEE 802.11bgn ESSID:"LDmac"
Mode:Managed Frequency:2.462 GHz Access Point: <MAC C-01 LDmac>
Bit Rate=72.2 Mb/s Tx-Power=20 dBm
Retry long limit:7 RTS thrff Fragment thrff
Power Managementff
Link Quality=61/70 Signal level=-49 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:65 Missed beacon:0



rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Interface Soft blocked Hard blocked
1: samsung-wlan: Wireless LAN no no
2: samsung-bluetooth: Bluetooth yes no
3: phy0: Wireless LAN no no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

brcmsmac 563041 0
cordic 12574 1 brcmsmac
brcmutil 15618 1 brcmsmac
b43 387371 0
mac80211 626557 2 b43,brcmsmac
cfg80211 484040 3 b43,brcmsmac,mac80211
ssb 62379 1 b43
bcma 52096 3 b43,brcmsmac
mxm_wmi 13021 1 nouveau
wmi 19177 2 mxm_wmi,nouveau


module parameters ~~~~~~~~~~~~~~~~~~

b43 (10): allhwsupport=0 | bad_frames_preempt=0 | btcoex=1 | hwpctl=0 | hwtkip=0 | nohwcrypt=0 | pio=0 | qos=1 | verbose=2
cfg80211 (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211 (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
wmi (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
================o=============o==========o==============o=========o===========o==============o===========
Interface & ID | Type | Driver | State | Default | Speed | Support | HW Addr
================o=============o==========o==============o=========o===========o==============o===========
eth0 | Wired | sky2 | unavailable | no | | | <MAC eth0>
----------------+-------------+----------+--------------+---------+-----------+--------------+-----------
wlan0 [LDmac] | 802.11 WiFi | brcmsmac | connected | yes | 72 Mb/s | WEP/WPA/WPA2 | <MAC wlan0>

Waoo2013: Infra, <MAC C-08 Waoo2013>, Freq 2437 MHz, Rate 54 Mb/s, Strength 95 WPA2
Gnet: Infra, <MAC C-05 Gnet>, Freq 2437 MHz, Rate 54 Mb/s, Strength 57 WPA2
ogilvie: Infra, <MAC C-07 ogilvie>, Freq 2437 MHz, Rate 54 Mb/s, Strength 57 WPA2
mette: Infra, <MAC C-06 mette>, Freq 2437 MHz, Rate 54 Mb/s, Strength 22 WPA2
familienet: Infra, <MAC C-09 familienet>, Freq 2437 MHz, Rate 54 Mb/s, Strength 30 WPA2
GVP_Wifi: Infra, <MAC C-03 GVP_Wifi>, Freq 2417 MHz, Rate 54 Mb/s, Strength 29 WPA2
*LDmac: Infra, <MAC C-01 LDmac>, Freq 2462 MHz, Rate 54 Mb/s, Strength 69 WPA WPA2
nsdc: Infra, <MAC C-04 nsdc>, Freq 2462 MHz, Rate 54 Mb/s, Strength 32 WPA2
Smukke Esben: Infra, <MAC C-NA Smukke Esben 1>, Freq 2437 MHz, Rate 54 Mb/s, Strength 24 WPA2
Henrik: Infra, <MAC C-NA Henrik 1>, Freq 2427 MHz, Rate 54 Mb/s, Strength 20 WPA
Alkalifeldspatkrystaller: Infra, <MAC C-10 Alkalifeldspatkrystaller>, Freq 2437 MHz, Rate 54 Mb/s, Strength 42 WPA2
anitanet: Infra, <MAC C-02 anitanet>, Freq 2412 MHz, Rate 54 Mb/s, Strength 17 WEP

Address: 192.168.1.216
Prefix: 24 (255.255.255.0)
Gateway: 192.168.1.1
DNS: 192.168.1.1
----------------+-------------+----------+--------------+---------+-----------+--------------+-----------


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

LDmac : ssid=LDmac | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 127.0.1.1
search mydomain


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination Gateway Genmask Flags Metric Ref Use Iface
0.0.0.0 192.168.1.1 0.0.0.0 UG 0 0 0 wlan0
192.168.1.0 0.0.0.0 255.255.255.0 U 9 0 0 wlan0

--- 192.168.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1002ms
rtt min/avg/max/mdev = 1.027/1.970/2.914/0.944 ms

--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.033/0.034/0.036/0.006 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "en_US.UTF-8")
country DK:
(2402 - 2482 @ 40), (N/A, 20)
(5170 - 5250 @ 40), (N/A, 20)
(5250 - 5330 @ 40), (N/A, 20), DFS
(5490 - 5710 @ 40), (N/A, 27), DFS
(57240 - 65880 @ 2160), (N/A, 40), NO-OUTDOOR


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0 13 channels in total; available frequencies :
Channel 01 (2.412 GHz) - 13 (2.472 GHz)

Current Frequency:2.462 GHz (Channel 11)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0 Scan completed :
Cell 01 - Address: <MAC C-01 LDmac>
Channel:11
Frequency:2.462 GHz (Channel 11)
Quality=59/70 Signal level=-51 dBm
Encryption keyn
ESSID:"LDmac"
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
9 Mb/s; 12 Mb/s; 18 Mb/s
Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
Mode:Master
Extra:tsf=0000001f9cf1bcb9
Extra: Last beacon: 20ms ago
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : CCMP TKIP
Authentication Suites (1) : PSK
IE: WPA Version 1
Group Cipher : TKIP
Pairwise Ciphers (1) : TKIP
Authentication Suites (1) : PSK
Cell 02 - Address: <MAC C-02 anitanet>
Channel:1
Frequency:2.412 GHz (Channel 1)
Quality=23/70 Signal level=-87 dBm
Encryption keyn
ESSID:"anitanet"
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
24 Mb/s; 36 Mb/s; 54 Mb/s
Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
Mode:Master
Extra:tsf=00001ef81aa6259b
Extra: Last beacon: 20ms ago
Cell 03 - Address: <MAC C-03 GVP_Wifi>
Channel:2
Frequency:2.417 GHz (Channel 2)
Quality=26/70 Signal level=-84 dBm
Encryption keyn
ESSID:"GVP_Wifi"
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
9 Mb/s; 12 Mb/s; 18 Mb/s
Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
Mode:Master
Extra:tsf=00000095617e1380
Extra: Last beacon: 2204ms ago
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : CCMP TKIP
Authentication Suites (1) : PSK
Cell 04 - Address: <MAC C-04 nsdc>
Channel:11
Frequency:2.462 GHz (Channel 11)
Quality=27/70 Signal level=-83 dBm
Encryption keyn
ESSID:"nsdc"
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
9 Mb/s; 12 Mb/s; 18 Mb/s
Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
Mode:Master
Extra:tsf=0000001763463180
Extra: Last beacon: 104ms ago
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : CCMP TKIP
Authentication Suites (1) : PSK
Cell 05 - Address: <MAC C-05 Gnet>
Channel:6
Frequency:2.437 GHz (Channel 6)
Quality=61/70 Signal level=-49 dBm
Encryption keyn
ESSID:"Gnet"
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
9 Mb/s; 12 Mb/s; 18 Mb/s
Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
Mode:Master
Extra:tsf=000000037d77cc0f
Extra: Last beacon: 20ms ago
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : CCMP TKIP
Authentication Suites (1) : PSK
Cell 06 - Address: <MAC C-06 mette>
Channel:6
Frequency:2.437 GHz (Channel 6)
Quality=26/70 Signal level=-84 dBm
Encryption keyn
ESSID:"mette"
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
9 Mb/s; 12 Mb/s; 18 Mb/s
Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
Mode:Master
Extra:tsf=00000000147d5180
Extra: Last beacon: 1844ms ago
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : CCMP TKIP
Authentication Suites (1) : PSK
Cell 07 - Address: <MAC C-07 ogilvie>
Channel:6
Frequency:2.437 GHz (Channel 6)
Quality=48/70 Signal level=-62 dBm
Encryption keyn
ESSID:"ogilvie"
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
9 Mb/s; 12 Mb/s; 18 Mb/s
Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
Mode:Master
Extra:tsf=000000017c740ff4
Extra: Last beacon: 20ms ago
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : CCMP TKIP
Authentication Suites (1) : PSK
Cell 08 - Address: <MAC C-08 Waoo2013>
Channel:6
Frequency:2.437 GHz (Channel 6)
Quality=56/70 Signal level=-54 dBm
Encryption keyn
ESSID:"Waoo2013"
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
9 Mb/s; 12 Mb/s; 18 Mb/s
Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
Mode:Master
Extra:tsf=0000001065335fe0
Extra: Last beacon: 20ms ago
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : CCMP TKIP
Authentication Suites (1) : PSK
Cell 09 - Address: <MAC C-09 familienet>
Channel:6
Frequency:2.437 GHz (Channel 6)
Quality=35/70 Signal level=-75 dBm
Encryption keyn
ESSID:"familienet"
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
9 Mb/s; 12 Mb/s; 18 Mb/s
Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
Mode:Master
Extra:tsf=0000000006c7f1ab
Extra: Last beacon: 1300ms ago
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : CCMP TKIP
Authentication Suites (1) : PSK
Cell 10 - Address: <MAC C-10 Alkalifeldspatkrystaller>
Channel:6
Frequency:2.437 GHz (Channel 6)
Quality=37/70 Signal level=-73 dBm
Encryption keyn
ESSID:"Alkalifeldspatkrystaller"
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
9 Mb/s; 12 Mb/s; 18 Mb/s
Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
Mode:Master
Extra:tsf=000000010a360180
Extra: Last beacon: 1584ms ago
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : CCMP TKIP
Authentication Suites (1) : PSK


blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[brcmsmac]
filename: /lib/modules/3.13.0-30-generic/kernel/drivers/net/wireless/brcm80211/brcmsmac/brcmsmac.ko
firmware: brcm/bcm43xx_hdr-0.fw
firmware: brcm/bcm43xx-0.fw
srcversion: 43D6897F7EB716081DF69BE
depends: bcma,mac80211,brcmutil,cfg80211,cordic

[cordic]
filename: /lib/modules/3.13.0-30-generic/kernel/lib/cordic.ko
srcversion: 810E6E73D80DD7F75AC5B42
depends:

[brcmutil]
filename: /lib/modules/3.13.0-30-generic/kernel/drivers/net/wireless/brcm80211/brcmutil/brcmutil.ko
srcversion: E81EE4CBB6A7A689150D93D
depends:

[b43]
filename: /lib/modules/3.13.0-30-generic/kernel/drivers/net/wireless/b43/b43.ko
firmware: b43/ucode9.fw
firmware: b43/ucode5.fw
firmware: b43/ucode16_mimo.fw
firmware: b43/ucode15.fw
firmware: b43/ucode14.fw
firmware: b43/ucode13.fw
firmware: b43/ucode11.fw
srcversion: 42BAE2DB9BADE3E7ECA2CC0
depends: bcma,ssb,mac80211,cfg80211
parm: bad_frames_preempt:enable(1) / disable(0) Bad Frames Preemption (int)
parm: fwpostfixostfix for the .fw files to load. (string)
parm: hwpctl:Enable hardware-side power control (default off) (int)
parm: nohwcryptisable hardware encryption. (int)
parm: hwtkip:Enable hardware tkip. (int)
parm: qos:Enable QOS support (default on) (int)
parm: btcoex:Enable Bluetooth coexistence (default on) (int)
parm: verbose:Log message verbosity: 0=error, 1=warn, 2=info(default), 3=debug (int)
parm: pio:Use PIO accesses by default: 0=DMA, 1=PIO (int)
parm: allhwsupport:Enable support for all hardware (even it if overlaps with the brcmsmac driver) (int)

[mac80211]
filename: /lib/modules/3.13.0-30-generic/kernel/net/mac80211/mac80211.ko
srcversion: 6F23437712851B1B0563BCB
depends: cfg80211
parm: max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm: max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm: beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm: probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm: ieee80211_default_rc_algoefault rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename: /lib/modules/3.13.0-30-generic/kernel/net/wireless/cfg80211.ko
srcversion: 8B3D642D1F2E6406EF33F74
depends:
parm: ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm: cfg80211_disable_40mhz_24ghzisable 40MHz support in the 2.4GHz band (bool)

[ssb]
filename: /lib/modules/3.13.0-30-generic/kernel/drivers/ssb/ssb.ko
srcversion: 3DE188310F77C566C2E8CB3
depends:

[bcma]
filename: /lib/modules/3.13.0-30-generic/kernel/drivers/bcma/bcma.ko
srcversion: E41B811D88783DD5BC38565
depends:


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x11ab:0x4381 (sky2)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x14e4:0x4727 (brcmsmac)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


Custom files/entries ~~~~~~~~~~~~~~~

/etc/modules : Default
/etc/rc.local : Default
/etc/modprobe.d : Not Default
/etc/pm/(cnf|pw|sl) : Default

[/etc/modprobe.d]
iwlwifi.conf : remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211
mlx4.conf : softdep mlx4_core post: mlx4_en


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/boot/vmlinuz-3.13.0-30-generic root=UUID=89391658-6bbd-4848-99dc-65fc1143fc33 ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[ 0.648129] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[ 0.648462] audit: initializing netlink socket (disabled)
[ 1.987250] psmouse serio1: elantech: assuming hardware version 3 (with firmware version 0x851b00)
[ 10.420604] wmi: Mapper loaded
[ 11.117792] bcma: bus0: Found chip with id 0x4313, rev 0x01 and package 0x08
[ 11.117823] bcma: bus0: Core 0 found: ChipCommon (manuf 0x4BF, id 0x800, rev 0x24, class 0x0)
[ 11.117847] bcma: bus0: Core 1 found: IEEE 802.11 (manuf 0x4BF, id 0x812, rev 0x18, class 0x0)
[ 11.117893] bcma: bus0: Core 2 found: PCIe (manuf 0x4BF, id 0x820, rev 0x11, class 0x0)
[ 11.149315] bcma: bus0: Bus registered
[ 11.499076] Support for cores revisions 0x17 and 0x18 disabled by module param allhwsupport=0. Try b43.allhwsupport=1
[ 11.501359] b43: probe of bcma0:0 failed with error -524
[ 11.657834] brcmsmac bcma0:0: mfg 4bf core 812 rev 24 class 0 irq 16
[ 11.752250] ieee80211 phy0: registered radio enabled led device: brcmsmac-phy0:radio gpio: 243
[ 12.596041] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[ 14.629703] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 14.629710] brcmsmac bcma0:0: brcms_ops_config: change power-save mode: false (implement)
[ 14.629863] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 14.631586] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 15.326612] wlan0: authenticate with <MAC C-01 LDmac>
[ 15.328389] wlan0: send auth to <MAC C-01 LDmac> (try 1/3)
[ 15.329928] wlan0: authenticated
[ 15.333622] wlan0: associate with <MAC C-01 LDmac> (try 1/3)
[ 15.336842] wlan0: RX AssocResp from <MAC C-01 LDmac> (capab=0x1431 status=0 aid=4)
[ 15.337445] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 15.337482] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 15.337519] wlan0: associated
[ 15.337530] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 18.198783] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: 1 addresses (implement)

======== Done ========

```

Let me know if there is other things you would like me to test.

Cheers,
Lars

---

### Post by kc1di on 2014-07-06
As Varun said it seems the brcsmac is doing the work , there must be a conflict with the WL driver.  Perhaps wl would work also if you removed the brcsmac. However we got there removing the WL Driver seems to have worked.  ;)

---

### Post by varunendra on 2014-07-06
> **kc1di said:**
> Varun - I'm not sure either why it works but this is the 3rd card that it has worked on.

I have seen some posts recently where both b43 and brcmsmac load for this card (14e4:4727), and I personally consider it a bug because it was a conflict situation which was solved by blacklisting b43 so that only brcmsmac can load.

I'm not sure but I think it started happening in recent kernel versions (probably 3.13 onwards) due to making **bcma** a dependency of **brcmsmac** as well, whereas in previous versions, it was only a dependency of **b43**.

In OPs situation here, my guess is that it is probably either just **brcmsmac**, or both **b43** and **brcmsmac** loading for the card. The latter case would always have a risk of potential conflict problems causing intermittent or no connection issues from time to time. That's why I want to see the output I asked.

As for finding out which card is supported by which driver(s), it is quite easy in most cases. We figure it out with the help of Vendor/Product ID of the device in question. For example, the OPs card here is 14e4:4727, so the Vendor ID (VID) is 14e4 (Broadcom) and Product ID (PID) is 4727.

Now to see which drivers in the system know and may support this card, run the command -
```
modprobe -c | grep -i 14e4.*4727
```
The result in my system (still on kernel 3.2 series) is -
```
alias pci:v0000**14E4**d0000**4727**sv*sd*bc*sc*i* **brcmsmac**
alias pci:v0000**14E4**d0000**4727**sv*sd*bc*sc*i* **[COLOR="#FF0000"]bcma[/COLOR]**
alias pci:v0000**14E4**d0000**4727**sv*sd*bc*sc*i* **wl**
```
As highlighted above, the 'bcma' module also has this id in its 'alias' list (means it is *supposed* to support it).

Now I know (by experience) that the bcma can not work alone and it always works as a supporting driver. So, to see which driver(s) it is a dependency of, I check the dependency tree of the system looking for the keyword 'bcma' with the command -
```
grep bcma /lib/modules/3.2.0-36-generic/**modules.dep**
```
The 'modules.dep' file is what contains all the dependency information. The result I get is -

```
**kernel/drivers/net/wireless/b43/b43.ko:** kernel/net/mac80211/mac80211.ko kernel/net/wireless/cfg80211.ko kernel/drivers/bcma/bcma.ko kernel/drivers/ssb/ssb.ko
kernel/drivers/bcma/bcma.ko:
```
..so it is ONLY the 'b43' module that depends on it (in current versions, 'brcmsmac' will also have it in its dependencies).

It means the 'b43' module is also *supposed* to support this card - **_something that I am deliberately refusing to believe here_** (and I may be wrong, maybe it has recently become really capable of handling it, I'd be curious to see that happening). The reason is, partly, this piece of information in the 'b43' module info (in current versions, not in my version here) -
```
~$ modinfo b43
filename: /lib/modules/3.11.0-18-generic/kernel/drivers/net/wireless/b43/b43.ko
....
....
parm: **allhwsupport:Enable support for all hardware (even it if overlaps with the brcmsmac driver)** (int)
```
The default value of this parameter is, I believe 0 - means "off" - so that it doesn't conflict with brcmsmac. In detail, I believe, it means "don't load the driver even if it is supposed to support a card IF the card is also supported by brcmsmac". In recent versions, either that value has been changed to "1" (on, intentionally by the developers to test the driver on such cards) or it simply fails to tell the system NOT to load it. In either case, a conflict situation is never good, and so is definitely a bug that needs to be fixed (if not already by now).

So that's what I know about this b43/brcmsmac confusion so far and I'm always open for new information and/or corrections. :)

---

### Post by varunendra on 2014-07-06
Thanks for the interest Lars!

As I suspected, we have a clear conflict situation here -> **lars6 said:**
> ```

lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

brcmsmac 563041 0
cordic 12574 1 brcmsmac
brcmutil 15618 1 brcmsmac
b43 387371 0
mac80211 626557 2 **[COLOR="#FF0000"]b43,brcmsmac[/COLOR]**
cfg80211 484040 3 **[COLOR="#FF0000"]b43,brcmsmac[/COLOR]**,mac80211
ssb 62379 1 b43
bcma 52096 3 **[COLOR="#FF0000"]b43,brcmsmac[/COLOR]**
mxm_wmi 13021 1 nouveau
wmi 19177 2 mxm_wmi,nouveau


module parameters ~~~~~~~~~~~~~~~~~~

b43 (10): **[COLOR="#FF0000"]allhwsupport=0[/COLOR]** | bad_frames_preempt=0 | btcoex=1 | hwpctl=0 | hwtkip=0 | nohwcrypt=0 | pio=0 | qos=1 | verbose=2
cfg80211 (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211 (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
wmi (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
================o=============o==========o==============o=========o===========o==============o===========
Interface & ID | Type | Driver | State | Default | Speed | Support | HW Addr
================o=============o==========o==============o=========o===========o==============o===========
eth0 | Wired | sky2 | unavailable | no | | | <MAC eth0>
----------------+-------------+----------+--------------+---------+-----------+--------------+-----------
wlan0 [LDmac] | 802.11 WiFi | **[COLOR="#0000CD"]brcmsmac[/COLOR]** | connected | yes | 72 Mb/s | WEP/WPA/WPA2 | <MAC wlan0>
```
..with a clear indication from "nm-tool" part that it is currently the 'brcmsmac' that is pulling the chords.

Despite the fact that it is currently working, we have a potential problem here, whenever the 'b43' module succeeds to claim a resource before brcmsmac can, there will be a connection problem.

If, Lars, you are simply interested in a clean, working system, simply blacklist the 'b43' module with the following command -
```
echo -e "blacklist b43\nblacklist ssb" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
From next boot, b43 won't load, leaving brcmsmac to work without possible conflicts.

But if you are willing to have some fun with us in testing, try blacklisting 'brcmsmac' instead, and see if the 'b43' module can actually handle the card. If you wish to try this DON't run the above code, instead try this -
```
echo "blacklist brcmsmac" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Reboot and check which ones are loaded -
```
lsmod | egrep 'b43|brcm
```
You should see ONLY b43 and supporting drivers, not brcmsmac. If so, does the wifi work? I believe it won't, in which case remove the 'brcmsmac' entry from the blacklist file with this command -
```
sudo sed -i '/blacklist brcmsmac/ d' /etc/modprobe.d/blacklist.conf
```
..followed by the command to blacklist "b43" and "ssb" I suggested first. The change would take effect since next boot.

---

### Post by kc1di on 2014-07-06
Thanks Varun, 
Appreciate your explanations.

---

### Post by lars6 on 2014-07-06
Hi Varun

Sure, let's see what we can find out.

Running this: 
```
echo "blacklist brcmsmac" | sudo tee -a /etc/modprobe.d/blacklist.conf
```

Caused the wifi not to work any longer (after the reboot).

Running the next line:

```
lsmod | egrep 'b43|brcm
```

Does not appear to do anything at all. I guess it was supposed to print some stuff, right?

---

### Post by varunendra on 2014-07-06
First of all, thanks for testing with us Lars!
> **lars6 said:**
> Running this: 
```
echo "blacklist brcmsmac" | sudo tee -a /etc/modprobe.d/blacklist.conf
```

Caused the wifi not to work any longer (after the reboot).

Running the next line:

```
lsmod | egrep 'b43|brcm
```

Does not appear to do anything at all. I guess it was supposed to print some stuff, right?

Yup, it was supposed to print at least "b43" and supporting driver as per my previous assumption - which has now slightly changed due to above result.

Now it seems making 'bcma' a dependency of 'brcmsmac' is causing the trouble of b43/brcmsmac conflict (wherever the 'trouble' actually occurs). This is my theory now - the brcmsmac driver, when NOT blacklisted, loads normally as it should. But now since 'bcma' is a dependency of it, it also loads bcma which in turn also loads the 'b43' module. Problem occurs when b43 starts claiming other helping drivers like mac80211 and cfg80211 which may be needed exclusively by brcmsmac.

Since we blacklisted brcmsmac above, neither it, nor bcma loaded, and hence b43 also didn't load.

If you wish to test if manually loading 'b43' can do any magic and surprise me, try it with -
```
sudo modprobe -v b43
```
This will manually load b43 and its dependencies - ssb, bcma, mac80211 and cfg80211 modules. The surprise would be if the card really starts working with it. If it does, make sure it is actually 'b43', not brcmsmac loaded inadvertently by 'bcma' -
```
lsmod | egrep 'b43|brcm'
```

Assuming we'll have no surprise, and the card will not work with b43, remove brcmsmac from blacklist as I suggested in my previous post, and blacklist b43 and ssb instead. Reboot and enjoy your wireless. :)

---

### Post by kc1di on 2014-07-06
I'll be very interested also -- Dave

---

### Post by lars6 on 2014-07-06
> **varunendra said:**
> First of all, thanks for testing with us Lars!

That's the least I can do - you guys helped me getting it to run in the first place.

> **varunendra said:**
> 
If you wish to test if manually loading 'b43' can do any magic and surprise me, try it with -
```
sudo modprobe -v b43
```
This will manually load b43 and its dependencies - ssb, bcma, mac80211 and cfg80211 modules. The surprise would be if the card really starts working with it. If it does, make sure it is actually 'b43', not brcmsmac loaded inadvertently by 'bcma' -
```
lsmod | egrep 'b43|brcm'
```

Assuming we'll have no surprise, and the card will not work with b43, remove brcmsmac from blacklist as I suggested in my previous post, and blacklist b43 and ssb instead. Reboot and enjoy your wireless. :)

Yup, no surprises. It didn't work, but neither did this:

```
sudo sed '/blacklist brcmsmac/ d' /etc/modprobe.d/blacklist.conf
```
 followed by:
```
echo -e "blacklist b43\nblacklist ssb" | sudo tee -a /etc/modprobe.d/blacklist.conf
```

Wifi seems completely dead...

-Lars

---

### Post by varunendra on 2014-07-06
> **lars6 said:**
> Yup, no surprises. It didn't work, but neither did this:

```
sudo **[COLOR="#FF0000"]sed[/COLOR]** '/blacklist brcmsmac/ d' /etc/modprobe.d/blacklist.conf
```
 followed by:
```
echo -e "blacklist b43\nblacklist ssb" | sudo tee -a /etc/modprobe.d/blacklist.conf
```

Wifi seems completely dead...

-Lars

Oops! My mistake.... I forgot the '-i' option in the sed command, without which, it only prints the result on the screen, doesn't actually modify the file. Please run the corrected command -
```
sudo **[COLOR="#FF0000"]sed -i[/COLOR]** '/blacklist brcmsmac/ d' /etc/modprobe.d/blacklist.conf
```
This will delete the line "blacklist brcmsmac" from the file **/etc/modprobe.d/blacklist.conf**, which is blocking the brcmsmac driver from loading at startup.

To confirm that, check the contents of the file after running the command, then reboot and let me know I didn't forget anything this time. :)

---

### Post by lars6 on 2014-07-07
Yes, that worked. Now I'm back on wifi :-)

Thanks!
Lars

---

### Post by Sahil_Arora on 2014-10-19
> **kc1di said:**
> That card uses the Boadcom b43 driver not the WL/Sta one.
you can try going to software center >edit>software sources>Additional drivers tab.
See if it offers you the b43 firmware , if so install it.  it sould blacklist wl for you.
If that doesn't work let me know we will have to do it the harder way :)


Have a broadcom WIFI controller model :  Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)

The wifi is not working. I tried using that additional drivers option in software updates, but it didn't work. I need to fix it. Help. This is my  wirelessinfo.txt file attatched.[ATTACH]257359[/ATTACH]
Thanks :)

---

### Post by Hadaka on 2014-10-19
Hi, you posted on a solved thread that has a complete
different card and issue, PLEASE start a NEW thread
with your issue, your card is.....
Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
you may want to ask a mod to help you.
thanks.

---

