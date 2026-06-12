---
title: "First normal wifi speed then wifi slows down  (Ubuntu 14.04)"
date: 2014-12-04
forum: Networking &amp; Wireless
---

### Post by Brabanders_Olivier on 2014-12-04
Hi everyone

I dual boot ubuntu 14.04 with windows 8.1 and for a reason I can't explain, my wifi slows down after 15 minutes.
I've run the wireless script and here it is:
```

########## wireless info START ##########

Report from: 04 Dec 2014 12:20 CET +0100

Booted last: 04 Dec 2014 10:19 CET +0100

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.1 LTS
Release:	14.04
Codename:	trusty

##### kernel ############################

Linux 3.13.0-40-generic #69-Ubuntu SMP Thu Nov 13 17:53:56 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8192CE PCIe Wireless Network Adapter [10ec:8178] (rev 01)
	Subsystem: ASUSTeK Computer Inc. Device [1043:84b6]
	Kernel driver in use: rtl8192ce

04:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57781 Gigabit Ethernet PCIe [14e4:16b1] (rev 10)
	Subsystem: ASRock Incorporation Z77 Extreme4 motherboard [1849:96b1]
	Kernel driver in use: tg3

##### lsusb #############################

Bus 002 Device 004: ID 046d:c31c Logitech, Inc. Keyboard K120 for Business
Bus 002 Device 003: ID 1a44:0870 VASCO Data Security International 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 1532:0040 Razer USA, Ltd 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 058f:6387 Alcor Micro Corp. Flash Drive
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

##### lsmod #############################

mxm_wmi                13021  0 
rtl8192ce              53550  0 
rtl_pci                26690  1 rtl8192ce
rtlwifi                63475  2 rtl_pci,rtl8192ce
rtl8192c_common        53172  1 rtl8192ce
mac80211              626557  3 rtl_pci,rtlwifi,rtl8192ce
cfg80211              484040  2 mac80211,rtlwifi
wmi                    19177  1 mxm_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.0.178  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: 2a02:1810:9419:1000:12bf:48ff:fefb:8d84/64 Scope:Global
          inet6 addr: fe80::12bf:48ff:fefb:8d84/64 Scope:Link
          inet6 addr: 2a02:1810:9419:1000:d9a4:3ef3:9c76:b56a/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:99710 errors:0 dropped:0 overruns:0 frame:0
          TX packets:71604 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:113024746 (113.0 MB)  TX bytes:9298736 (9.2 MB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"telenet-7A4CB"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC 'telenet-7A4CB' [AC1]>   
          Bit Rate=144.4 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=62/70  Signal level=-48 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:364   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1
search home telenet.be

##### nm-tool ###########################

NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

- Device: wlan0  [telenet-7A4CB] -----------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192ce
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:
    Speed:           144 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    TELENETHOMESPOT: Infra, <MAC 'TELENETHOMESPOT' [AC2]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 26
    *telenet-7A4CB:  Infra, <MAC 'telenet-7A4CB' [AC1]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 68 WPA WPA2

  IPv4 Settings:
    Address:         192.168.0.178
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             195.130.131.131
    DNS:             195.130.130.3

  IPv6 Settings:
    Address:         2a02:1810:9419:1000:d9a4:3ef3:9c76:b56a
    Prefix:          64
    Gateway:         fe80::5e35:3bff:fe57:a4ce

    Address:         2a02:1810:9419:1000:12bf:48ff:fefb:8d84
    Prefix:          64
    Gateway:         fe80::5e35:3bff:fe57:a4ce

    Address:         fe80::12bf:48ff:fefb:8d84
    Prefix:          64
    Gateway:         fe80::5e35:3bff:fe57:a4ce

    DNS:             2a02:1800:100::43:2
    DNS:             2a02:1800:100::43:1

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

[[/etc/NetworkManager/system-connections/telenet-7A4CB]] (600 root)
[connection] id=telenet-7A4CB | type=802-11-wireless
[802-11-wireless] ssid=telenet-7A4CB | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/Brussels (based on set time zone)

country 00:
	(2402 - 2472 @ 40), (3, 20)
	(2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
	(5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

wlan0     13 channels in total; available frequencies :
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

##### iwlist scan #######################

Channel occupancy:

      2   APs on   Frequency:2.462 GHz (Channel 11)

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'telenet-7A4CB' [AC1]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=62/70  Signal level=-48 dBm  
                    Encryption key:on
                    ESSID:"telenet-7A4CB"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000bddf30d5d2
                    Extra: Last beacon: 4ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'TELENETHOMESPOT' [AC2]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=62/70  Signal level=-48 dBm  
                    Encryption key:off
                    ESSID:"TELENETHOMESPOT"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000bddf30e5cb
                    Extra: Last beacon: 4ms ago

##### module infos ######################

[rtl8192ce]
filename:       /lib/modules/3.13.0-40-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko
firmware:       rtlwifi/rtl8192cfwU_B.bin
firmware:       rtlwifi/rtl8192cfwU.bin
firmware:       rtlwifi/rtl8192cfw.bin
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger	<Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     EF063698748457BBEDB4633
depends:        rtlwifi,rtl_pci,rtl8192c-common,mac80211
intree:         Y
vermagic:       3.13.0-40-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        35:72:8C:DB:88:AA:70:FD:D3:AC:D1:53:A3:7B:51:31:92:A4:7F:D8
sig_hashalgo:   sha512
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)

[rtl_pci]
filename:       /lib/modules/3.13.0-40-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     D5E4890DC428FA5A1BF92DF
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       3.13.0-40-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        35:72:8C:DB:88:AA:70:FD:D3:AC:D1:53:A3:7B:51:31:92:A4:7F:D8
sig_hashalgo:   sha512

[rtlwifi]
filename:       /lib/modules/3.13.0-40-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     E1F4663325225EE8DBA54CA
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-40-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        35:72:8C:DB:88:AA:70:FD:D3:AC:D1:53:A3:7B:51:31:92:A4:7F:D8
sig_hashalgo:   sha512

[rtl8192c_common]
filename:       /lib/modules/3.13.0-40-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192c/rtl8192c-common.ko
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger	<Larry.Finger@lwfinger.net>
author:         Ziv Huang	<ziv_huang@realtek.com>
author:         Georgia		<georgia@realtek.com>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     32F826C623BC49F764F7974
depends:        
intree:         Y
vermagic:       3.13.0-40-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        35:72:8C:DB:88:AA:70:FD:D3:AC:D1:53:A3:7B:51:31:92:A4:7F:D8
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.13.0-40-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     123C230E7AC85A31E4CA28B
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-40-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        35:72:8C:DB:88:AA:70:FD:D3:AC:D1:53:A3:7B:51:31:92:A4:7F:D8
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-40-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     C2478077E22138832B71659
depends:        
intree:         Y
vermagic:       3.13.0-40-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        35:72:8C:DB:88:AA:70:FD:D3:AC:D1:53:A3:7B:51:31:92:A4:7F:D8
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rtl8192ce]
debug: 0
fwlps: Y
ips: Y
swenc: N
swlps: N

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
probe_wait_ms: 500

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

lp
rtc

##### modprobe options ##################

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

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x14e4:0x16b1 (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x10ec:0x8178 (rtl8192ce)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[    6.457849] wlan0: authenticate with <MAC 'telenet-7A4CB' [AC1]>
[    6.470035] wlan0: send auth to <MAC 'telenet-7A4CB' [AC1]> (try 1/3)
[    6.537440] wlan0: authenticated
[    6.541532] wlan0: associate with <MAC 'telenet-7A4CB' [AC1]> (try 1/3)
[    6.545062] wlan0: RX AssocResp from <MAC 'telenet-7A4CB' [AC1]> (capab=0x411 status=0 aid=4)
[    6.545216] wlan0: associated
[    6.545223] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

########## wireless info END ############

```

The images in the attachment are screenshots of my download and upload speed before and after my wifi slows down.
I hope someone can help me.

---

### Post by slickymaster on 2014-12-04
*Moved to the ***Networking & Wireless*** sub-forum*

---

### Post by wildmanne39 on 2014-12-04
The driver that your device uses is problematic but sometimes if we add some parameters to it and change some settings in the router we can get it to work if not we will have to compile an new driver.

First in your router change `802.11bgn` to `802.11bg`.

Second change the wep encryption to just wpa2 (CCMP)(AES) not (TKIP) if you have that option it will work best.

Third set your wireless channel in the router to 1 or 11 then save the router configuration and reboot it.

Fourth go into network manager at top right corner of the screen and click on edit connections>wireless tab and set IPV6 to ignore.  

Now open the terminal CTRL+ALT+_T then copy and paste the following code one line at a time for accuracy:

```
echo "options rtl8192ce swenc=1 ips=0" | sudo tee /etc/modprobe.d/rtl8192ce.conf
sudo modprobe -rfv rtl8192ce
sudo modprobe -v rtl8192ce
```
Thanks

---

### Post by carlwsnyder on 2014-12-04
You might also check with your ISP.  If it were your router settings, it will affect your internal network communications, as for example, a large file/folder backup from one machine on the network to another.

---

### Post by Brabanders_Olivier on 2014-12-16
Hi guys, sorry for the late reply, with exams it's been a busy week.
I did as you said Wild Man, unfortunaly, but now I have no connection with the internet anymore.
According to the menubar, I'm connected to my wireless network, but I can't get any connection what so ever.
I've tried executing the wireless script again, now the terminal tells me this:
```

wget: cannot redirect host-address '`dl.dropbox.com`'

```
any clue on what is going on?

---

