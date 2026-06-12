---
title: "WiFi dissapeared in Ubuntu 14.04"
date: 2018-03-02
forum: Networking &amp; Wireless
---

### Post by alexandrosfa on 2018-03-02
Hi! I rebooted my laptop and wifi dissapeared. Can you please help me?

I don't know if this information helps.

[COLOR=#3C3B37][FONT=&amp]00:00.0 Host bridge [0600]: Intel Corporation Atom Processor Z36xxx/Z37xxx Series SoC Transaction Register [8086:0f00] (rev 0e)[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=&amp]00:02.0 VGA compatible controller [0300]: Intel Corporation Atom Processor Z36xxx/Z37xxx Series Graphics & Display [8086:0f31] (rev 0e)[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=&amp]00:13.0 SATA controller [0106]: Intel Corporation Atom Processor E3800 Series SATA AHCI Controller [8086:0f23] (rev 0e)[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=&amp]00:14.0 USB controller [0c03]: Intel Corporation Atom Processor Z36xxx/Z37xxx Series USB xHCI [8086:0f35] (rev 0e)[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=&amp]00:1a.0 Encryption controller [1080]: Intel Corporation Atom Processor Z36xxx/Z37xxx Series Trusted Execution Engine [8086:0f18] (rev 0e)[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=&amp]00:1b.0 Audio device [0403]: Intel Corporation Atom Processor Z36xxx/Z37xxx Series High Definition Audio Controller [8086:0f04] (rev 0e)[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=&amp]00:1c.0 PCI bridge [0604]: Intel Corporation Atom Processor E3800 Series PCI Express Root Port 1 [8086:0f48] (rev 0e)[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=&amp]00:1c.1 PCI bridge [0604]: Intel Corporation Atom Processor E3800 Series PCI Express Root Port 2 [8086:0f4a] (rev 0e)[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=&amp]00:1f.0 ISA bridge [0601]: Intel Corporation Atom Processor Z36xxx/Z37xxx Series Power Control Unit [8086:0f1c] (rev 0e)[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=&amp]00:1f.3 SMBus [0c05]: Intel Corporation Atom Processor E3800 Series SMBus Controller [8086:0f12] (rev 0e)[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=&amp]01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 05)[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=&amp]02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)

[/FONT][/COLOR][COLOR=#3C3B37][FONT=&amp]lsusb
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 1908:2311 GEMBIRD 
Bus 001 Device 006: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 005: ID 13d3:3315 IMC Networks Bluetooth module
Bus 001 Device 003: ID 05e3:0608 Genesys Logic, Inc. Hub
Bus 001 Device 002: ID 1ea7:0064 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/FONT][/COLOR]


[COLOR=#3C3B37][FONT=&amp]rfkill list[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=&amp]0: hci0: Bluetooth[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=&amp]Soft blocked: no[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=&amp]Hard blocked: no[/FONT][/COLOR]

---

### Post by braghum on 2018-03-02
Does it stay like that if you reboot it again?

and...

[https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108)

---

### Post by alexandrosfa on 2018-03-02
> **braghum said:**
> Does it stay like that if you reboot it again?

Yes, it does
```

Report from: 02 Mar 2018 23:46 EET +0200

Booted last: 01 Jan 2014 14:01 EET +0200

Script from: 10 Jan 2018 20:04 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.5 LTS
Release:	14.04
Codename:	trusty

##### kernel ############################

Linux 4.4.0-116-generic #140~14.04.1-Ubuntu SMP Fri Feb 16 09:25:20 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

sed: can't read /root/.dmrc: No such file or directory

Could not be determined.

##### lspci #############################

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 05)
	Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:0123]
	Kernel driver in use: r8169

02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
	Subsystem: AzureWave Device [1a3b:2a47]

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 1908:2311 GEMBIRD 
Bus 001 Device 006: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 005: ID 13d3:3315 IMC Networks Bluetooth module
Bus 001 Device 003: ID 05e3:0608 Genesys Logic, Inc. Hub
Bus 001 Device 002: ID 1ea7:0064  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

##### lsmod #############################

cfg80211              561152  0 
snd_soc_rt5640        114688  0 
snd_soc_rl6231         16384  1 snd_soc_rt5640
snd_soc_core          212992  2 snd_soc_rt5640,snd_soc_sst_mfld_platform
snd_pcm               106496  8 snd_soc_rt5640,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_soc_sst_mfld_platform,snd_pcm_dmaengine,snd_hda_core
wmi                    20480  0 

##### interfaces ########################

[/etc/network/interfaces]
auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF1]>  
          inet addr:192.168.2.5  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'eth0' [IF1]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:554480 errors:0 dropped:0 overruns:0 frame:0
          TX packets:457606 errors:3 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:491449606 (491.4 MB)  TX bytes:141991032 (141.9 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:9089 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9089 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:847119 (847.1 KB)  TX bytes:847119 (847.1 KB)

##### iwconfig ##########################

lo        no wireless extensions.

eth0      no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 eth0
192.168.2.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

	NetworkManager

Running:

root      1064     1  0 11:52 ?        00:00:01 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: eth0  [&#917;&#957;&#963;&#973;&#961;&#956;&#945;&#964;&#951; &#963;&#973;&#957;&#948;&#949;&#963;&#951; 1] --------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF1]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.2.5
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.2.1

    DNS:             208.67.222.222
    DNS:             208.67.220.220

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

no-auto-default=<MAC 'eth0' [IF1]>,

[ifupdown]
managed=false

##### NetworkManager profiles ###########



[[/etc/NetworkManager/system-connections/VODAFONE WIFI]] (600 root)
[connection] id=VODAFONE WIFI | type=802-11-wireless
[802-11-wireless] ssid=VODAFONE WIFI | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto



##### Netplan config ####################

##### iw reg get ########################

Region: Europe/Athens (based on set time zone)

country 00:
	(2402 - 2472 @ 40), (3, 20)
	(2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
	(5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

lo        no frequency information.

eth0      no frequency information.

##### iwlist scan #######################

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

##### module infos ######################

[cfg80211]
filename:       /lib/modules/4.4.0-116-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     D2A8E57424453F0D1BE1DBE
depends:        
intree:         Y
vermagic:       4.4.0-116-generic SMP mod_unload modversions retpoline 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[cfg80211]
bss_entries_limit: 1000
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

lp
rtc

##### modprobe options ##################

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
# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF1]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x14e4:0x4727 (brcmsmac)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[41024.663088] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:cc:03:fa:a3:32:f8:08:00 SRC=192.168.2.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2  (repeated 98 times)

########## wireless info END ############

```[Download as text]("http://paste.ubuntu.com/p/FkTv3Fmfzt/plain/")

---

### Post by jeremy31 on 2018-03-02
I would ```
sudo apt-get purge bcmwl-kernel-source 
echo "blacklist b43" | sudo tee -a /etc/modprobe.d/blacklist.conf
echo "blacklist ssb" | sudo tee -a /etc/modprobe.d/blacklist.conf
```

Reboot

---

### Post by alexandrosfa on 2018-03-02
It works perfectly now! Thank you so much!!!

---

