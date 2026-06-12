---
title: "How do I improve the stability of a Broadcom wireless device?"
date: 2018-07-09
forum: Networking &amp; Wireless
---

### Post by peridian on 2018-07-09
Hi,

Info from the ubuntu (16.04) wireless info script at the bottom...

Basically the same (annoying) problem as it appears quite a lot of people are having with Broadcom devices (I just couldn't find a post specifically covering this particular model) where the signal keeps dropping to zero and then disconnecting at random intervals, sometimes requiring a full reboot before it will reconnect.

It's an Asus Transformer T-100 (on which Ubuntu is not officially supported, but it does work), with a Broadcom BCM43241.

It's using the out of the box 'brcmfmac' driver (with the *sdio.txt file already in place for the *b4* bin file, as per [this post]("https://askubuntu.com/questions/386371/no-network-devices-available-for-bcm43241sdio-after-fresh-install-of-13-10")).  Is there a more up to date one than 6.10.197.71?

Is there a better alternative choice?  I notice from [this page]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx") there are several choices, but they don't list this particular model against them, is the official driver any better?

Regards,
Rob.

(had to substitute square brackets or the forum thought I was playing silly billy)

```

########## wireless info START ##########
Report from: 08 Jul 2018 21:45 BST +0100
Booted last: 08 Jul 2018 00:00 BST +0100
Script from: 10 Jan 2018 20:04 UTC +0000
##### release ###########################
Distributor ID: Ubuntu
Description: Ubuntu 16.04.4 LTS
Release: 16.04
Codename: xenial
##### kernel ############################
Linux 4.13.0-45-generic #50~16.04.1-Ubuntu SMP Wed May 30 11:18:27 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux
Parameters: ro, intel_idle.max_cstate=0, quiet, splash, vt.handoff=7
##### desktop ###########################
sed: can't read /home/{username}/.dmrc: No such file or directory
Could not be determined.
##### lspci #############################
##### lsusb #############################
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 145f:01da Trust 
Bus 001 Device 003: ID 0b05:17e0 ASUSTek Computer, Inc. 
Bus 001 Device 002: ID 0b05:17e4 ASUSTek Computer, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
##### PCMCIA card info ##################
##### rfkill ############################
0: phy0: Wireless LAN
Soft blocked: no
Hard blocked: no
##### lsmod #############################
snd_soc_sst_bytcr_rt5640 24576 1
brcmfmac 319488 0
brcmutil 16384 1 brcmfmac
asus_nb_wmi 28672 0
asus_wmi 28672 1 asus_nb_wmi
cfg80211 614400 1 brcmfmac
sparse_keymap 16384 1 asus_wmi
snd_soc_rt5670 131072 0
snd_soc_rt5645 147456 0
snd_soc_rt5640 118784 2 snd_soc_sst_bytcr_rt5640
snd_soc_sst_match 16384 2 snd_soc_sst_bytcr_rt5640,snd_intel_sst_acpi
snd_soc_rl6231 16384 3 snd_soc_rt5670,snd_soc_rt5640,snd_soc_rt5645
snd_soc_core 229376 5 snd_soc_sst_bytcr_rt5640,snd_soc_rt5670,snd_soc_rt5640,snd_soc_sst_atom_hifi2_platform,snd_soc_rt5645
snd_pcm 98304 8 snd_soc_sst_bytcr_rt5640,snd_soc_rt5670,snd_hdmi_lpe_audio,snd_pcm_dmaengine,snd_soc_rt5640,snd_soc_sst_atom_hifi2_platform,snd_soc_rt5645,snd_soc_core
wmi 24576 1 asus_wmi
video 40960 3 asus_wmi,int3406_thermal,i915
##### interfaces ########################
(/etc/network/interfaces)
auto lo
iface lo inet loopback
##### ifconfig ##########################
lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:65536 Metric:1
RX packets:759 errors:0 dropped:0 overruns:0 frame:0
TX packets:759 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:54783 (54.7 KB) TX bytes:54783 (54.7 KB)


wlan0 Link encap:Ethernet HWaddr <MAC 'wlan0' (IF1)> 
inet addr:{ipaddress} Bcast:{ipprefix}255 Mask:255.255.255.0
inet6 addr: fe80::<IP6 'wlan0' (IF1)>/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:8007 errors:0 dropped:0 overruns:0 frame:0
TX packets:4598 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:11301581 (11.3 MB) TX bytes:431233 (431.2 KB)
##### iwconfig ##########################
lo no wireless extensions.


wlan0 IEEE 802.11 ESSID:"{wlan}" 
Mode:Managed Frequency:2.462 GHz Access Point: <MAC '{wlan}' (AC1)> 
Bit Rate=24 Mb/s Tx-Power=31 dBm 
Retry short limit:7 RTS thrff Fragment thrff
Encryption keyff
Power Managementn
Link Quality=56/70 Signal level=-54 dBm 
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0
##### route #############################
Kernel IP routing table
Destination Gateway Genmask Flags Metric Ref Use Iface
0.0.0.0 {ipprefix}1 0.0.0.0 UG 600 0 0 wlan0
{ipprefix}0 0.0.0.0 255.255.255.0 U 600 0 0 wlan0
169.254.0.0 0.0.0.0 255.255.0.0 U 1000 0 0 wlan0
##### resolv.conf #######################
nameserver 127.0.1.1
##### network managers ##################
Installed:
NetworkManager
Running:
root 1038 1 0 21:20 ? 00:00:03 /usr/sbin/NetworkManager --no-daemon
##### NetworkManager info ###############
GENERAL.DEVICE: wlan0
GENERAL.TYPE: wifi
GENERAL.NM-TYPE: NMDeviceWifi
GENERAL.VENDOR: Broadcom Corp.
GENERAL.PRODUCT: BCM43241 WLAN card
GENERAL.DRIVER: brcmfmac
GENERAL.DRIVER-VERSION: 6.10.197.71
GENERAL.FIRMWARE-VERSION: 01-882d2634
GENERAL.HWADDR: <MAC 'wlan0' (IF1)>
GENERAL.MTU: 0
GENERAL.STATE: 100 (connected)
GENERAL.REASON: 0 (No reason given)
GENERAL.UDI: /sys/devices/platform/INT33BB:00/mmc_host/mmc1/mmc1:0001/mmc1:0001:1/net/wlan0
GENERAL.IP-IFACE: wlan0
GENERAL.IS-SOFTWARE: no
GENERAL.NM-MANAGED: yes
GENERAL.AUTOCONNECT: yes
GENERAL.FIRMWARE-MISSING: no
GENERAL.NM-PLUGIN-MISSING: no
GENERAL.PHYS-PORT-ID: --
GENERAL.CONNECTION: {wlan}
GENERAL.CON-UUID: c683bb37-e467-461a-8f69-e863cb8d8b25
GENERAL.CON-PATH: /org/freedesktop/NetworkManager/ActiveConnection/6
GENERAL.METERED: no (guessed)
CAPABILITIES.CARRIER-DETECT: no
CAPABILITIES.SPEED: 24 Mb/s
CAPABILITIES.IS-SOFTWARE: no
WIFI-PROPERTIES.WEP: yes
WIFI-PROPERTIES.WPA: yes
WIFI-PROPERTIES.WPA2: yes
WIFI-PROPERTIES.TKIP: yes
WIFI-PROPERTIES.CCMP: yes
WIFI-PROPERTIES.AP: yes
WIFI-PROPERTIES.ADHOC: yes
WIFI-PROPERTIES.2GHZ: yes
WIFI-PROPERTIES.5GHZ: yes
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0,2}
CONNECTIONS.AVAILABLE-CONNECTIONS(1): b9e96cf8-4260-4c94-92fb-8081c55b16ff | libra2
CONNECTIONS.AVAILABLE-CONNECTIONS(2): c683bb37-e467-461a-8f69-e863cb8d8b25 | {wlan}
IP4.ADDRESS(1): {ipaddress}/24
IP4.GATEWAY: {ipprefix}1
IP4.ROUTE(1): dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS(1): {ipprefix}1
IP6.ADDRESS(1): fe80::<IP6 'wlan0' (IF1)>/64
IP6.GATEWAY: 
SSID BSSID MODE CHAN FREQ RATE SIGNAL BARS SECURITY ACTIVE * 
{wlan} <MAC '{wlan}' (AC1)> Infra 11 2462 MHz 54 Mbit/s 75 â–‚â–„â–†_ WPA2 yes * 
{wlan} <MAC '{wlan}' (AC1)> Infra 11 2462 MHz 54 Mbit/s 66 â–‚â–„â–†_ WPA2 yes * 
##### NetworkManager.state ##############
(main)
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
##### NetworkManager.conf ###############
(main)
plugins=ifupdown,keyfile,ofono
dns=dnsmasq
(ifupdown)
managed=false
##### NetworkManager profiles ###########
((/etc/NetworkManager/system-connections/{wlan})) (600 root)
(connection) id={wlan} | type=wifi | permissions=
(wifi) mac-address=<MAC 'wlan0' (IF1)> | mac-address-blacklist= | ssid={wlan}
(ipv4) method=manual
(ipv6) method=ignore
##### Netplan config ####################
##### iw reg get ########################
Region: Europe/London (based on set time zone)
country GB: DFS-ETSI
(2402 - 2482 @ 40), (N/A, 20), (N/A)
(5170 - 5250 @ 80), (N/A, 20), (N/A)
(5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS
(5490 - 5710 @ 160), (N/A, 27), (0 ms), DFS
(57000 - 66000 @ 2160), (N/A, 40), (N/A)
##### iwlist channels ###################
lo no frequency information.


wlan0 32 channels in total; available frequencies :
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
Channel 38 : 5.19 GHz
Channel 40 : 5.2 GHz
Channel 42 : 5.21 GHz
Channel 44 : 5.22 GHz
Channel 46 : 5.23 GHz
Channel 48 : 5.24 GHz
Channel 52 : 5.26 GHz
Channel 56 : 5.28 GHz
Channel 60 : 5.3 GHz
Channel 64 : 5.32 GHz
Channel 100 : 5.5 GHz
Channel 104 : 5.52 GHz
Channel 108 : 5.54 GHz
Channel 112 : 5.56 GHz
Channel 116 : 5.58 GHz
Channel 120 : 5.6 GHz
Channel 124 : 5.62 GHz
Channel 128 : 5.64 GHz
Current Frequency:2.462 GHz (Channel 11)
##### iwlist scan #######################
lo Interface doesn't support scanning.


Channel occupancy:
2 APs on Frequency:2.412 GHz (Channel 1)
5 APs on Frequency:2.437 GHz (Channel 6)
3 APs on Frequency:2.462 GHz (Channel 11)
1 APs on Frequency:5.18 GHz (Channel 36)
1 APs on Frequency:5.24 GHz (Channel 48)


wlan0 Scan completed :
Cell 01 - Address: <MAC '{wlan}' (AC1)>
Channel:11
Frequency:2.462 GHz (Channel 11)
Quality=37/70 Signal level=-73 dBm 
Encryption keyn
ESSID:"{wlan}"
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
9 Mb/s; 12 Mb/s; 18 Mb/s
Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
Mode:Master
Extra:tsf=0000000000000000
Extra: Last beacon: 467172ms ago
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : CCMP
Pairwise Ciphers (1) : CCMP
Authentication Suites (1) : PSK
Preauthentication Supported
Cell 07 - Address: <MAC '{wlan}' (AC1)>
Channel:11
Frequency:2.462 GHz (Channel 11)
Quality=54/70 Signal level=-56 dBm 
Encryption keyn
ESSID:""
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
9 Mb/s; 12 Mb/s; 18 Mb/s
Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
Mode:Master
Extra:tsf=0000000000000000
Extra: Last beacon: 72ms ago
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : CCMP
Pairwise Ciphers (1) : CCMP
Authentication Suites (1) : PSK
Preauthentication Supported
Cell 12 - Address: <MAC '' (AC12)>
Channel:11
Frequency:2.462 GHz (Channel 11)
Quality=51/70 Signal level=-59 dBm 
Encryption keyn
ESSID:""
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
9 Mb/s; 12 Mb/s; 18 Mb/s
Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
Mode:Master
Extra:tsf=0000000000000000
Extra: Last beacon: 72ms ago
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : CCMP
Pairwise Ciphers (1) : CCMP
Authentication Suites (1) : PSK
Preauthentication Supported
##### module infos ######################
(brcmfmac)
filename: /lib/modules/4.13.0-45-generic/kernel/drivers/net/wireless/broadcom/brcm80211/brcmfmac/brcmfmac.ko
license: Dual BSD/GPL
description: Broadcom 802.11 wireless LAN fullmac driver.
author: Broadcom Corporation
firmware: brcm/brcmfmac4356-sdio.bin
firmware: brcm/brcmfmac4354-sdio.bin
firmware: brcm/brcmfmac43455-sdio.bin
firmware: brcm/brcmfmac43430-sdio.bin
firmware: brcm/brcmfmac43430a0-sdio.bin
firmware: brcm/brcmfmac4339-sdio.bin
firmware: brcm/brcmfmac43362-sdio.bin
firmware: brcm/brcmfmac4335-sdio.bin
firmware: brcm/brcmfmac43340-sdio.bin
firmware: brcm/brcmfmac4334-sdio.bin
firmware: brcm/brcmfmac4330-sdio.bin
firmware: brcm/brcmfmac4329-sdio.bin
firmware: brcm/brcmfmac43241b5-sdio.bin
firmware: brcm/brcmfmac43241b4-sdio.bin
firmware: brcm/brcmfmac43241b0-sdio.bin
firmware: brcm/brcmfmac43143-sdio.bin
firmware: brcm/brcmfmac43569.bin
firmware: brcm/brcmfmac43242a.bin
firmware: brcm/brcmfmac43236b.bin
firmware: brcm/brcmfmac43143.bin
firmware: brcm/brcmfmac4371-pcie.bin
firmware: brcm/brcmfmac4366c-pcie.bin
firmware: brcm/brcmfmac4366b-pcie.bin
firmware: brcm/brcmfmac4365c-pcie.bin
firmware: brcm/brcmfmac4365b-pcie.bin
firmware: brcm/brcmfmac4359-pcie.bin
firmware: brcm/brcmfmac4358-pcie.bin
firmware: brcm/brcmfmac43570-pcie.bin
firmware: brcm/brcmfmac4356-pcie.bin
firmware: brcm/brcmfmac4350c2-pcie.bin
firmware: brcm/brcmfmac4350-pcie.bin
firmware: brcm/brcmfmac43602-pcie.bin
srcversion: 8C19980354E6F4AFAF01379
depends: brcmutil,cfg80211
intree: Y
name: brcmfmac
vermagic: 4.13.0-45-generic SMP mod_unload 
parm: txglomsz:Maximum tx packet chain size (SDIO) (int)
parm: debug:Level of debug output (int)
parm: p2pon:Enable legacy p2p management functionality (int)
parm: feature_disableisable features (int)
parm: alternative_fw_path:Alternative firmware path (string)
parm: fcmode:Mode of firmware signalled flow control (int)
parm: roamoffo not use internal roaming engine (int)


(brcmutil)
filename: /lib/modules/4.13.0-45-generic/kernel/drivers/net/wireless/broadcom/brcm80211/brcmutil/brcmutil.ko
license: Dual BSD/GPL
description: Broadcom 802.11n wireless LAN driver utilities.
author: Broadcom Corporation
srcversion: 389318E018771B5453D0B02
depends: 
intree: Y
name: brcmutil
vermagic: 4.13.0-45-generic SMP mod_unload 


(cfg80211)
filename: /lib/modules/4.13.0-45-generic/kernel/net/wireless/cfg80211.ko
description: wireless configuration support
license: GPL
author: Johannes Berg
srcversion: A5EDD7467E172A70410EBCD
depends: 
intree: Y
name: cfg80211
vermagic: 4.13.0-45-generic SMP mod_unload 
parm: bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm: ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm: cfg80211_disable_40mhz_24ghzisable 40MHz support in the 2.4GHz band (bool)
##### module parameters #################
(brcmfmac)
debug: 0
roamoff: 0


(cfg80211)
bss_entries_limit: 1000
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00
##### /etc/modules ######################
##### modprobe options ##################
(/etc/modprobe.d/amd64-microcode-blacklist.conf)
blacklist microcode


(/etc/modprobe.d/blacklist-ath_pci.conf)
blacklist ath_pci


(/etc/modprobe.d/blacklist.conf)
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
blacklist uvcvideo


(/etc/modprobe.d/blacklist-rare-network.conf)
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off


(/etc/modprobe.d/intel-microcode-blacklist.conf)
blacklist microcode


(/etc/modprobe.d/iwlwifi.conf)
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211


(/etc/modprobe.d/mlx4.conf)
softdep mlx4_core post: mlx4_en


##### rc.local ##########################
exit 0
##### pm-utils ##########################
##### udev rules ########################
##### dmesg #############################
( 11.478795) brcmfmac: brcmf_c_preinit_dcmds: Firmware version = wl0: Jul 17 2013 07:36:07 version 6.10.197.71 (r412987) FWID 01-882d2634
( 11.678760) bytcr_rt5640 bytcr_rt5640: quirk IN1_MAP enabled
( 11.678765) bytcr_rt5640 bytcr_rt5640: quirk MCLK_EN enabled
( 11.707797) bytcr_rt5640 bytcr_rt5640: snd-soc-dummy-dai <-> media-cpu-dai mapping ok
( 11.707856) bytcr_rt5640 bytcr_rt5640: snd-soc-dummy-dai <-> deepbuffer-cpu-dai mapping ok
( 11.712284) bytcr_rt5640 bytcr_rt5640: rt5640-aif1 <-> ssp2-port mapping ok
( 13.792189) IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 3 times)
( 29.056977) IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
( 723.224540) IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 4 times)
( 812.692090) IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
( 823.398638) IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
( 830.753488) IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
( 841.186726) IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
( 1105.565798) IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
( 1299.660027) (UFW BLOCK) IN=wlan0 OUT= MAC=<MAC 'wlan0' (IF1)>:00:30:18:c2:86:f9:08:00 SRC={ipprefix}1 DST={ipaddress} LEN=132 TOS=0x00 PREC=0x00 TTL=64 ID=18142 PROTO=UDP SPT=53 DPT=38513 LEN=112 
( 1304.270022) (UFW BLOCK) IN=wlan0 OUT= MAC=<MAC 'wlan0' (IF1)>:00:30:18:c2:86:f9:08:00 SRC={ipprefix}1 DST={ipaddress} LEN=132 TOS=0x00 PREC=0x00 TTL=64 ID=63551 PROTO=UDP SPT=53 DPT=38513 LEN=112 
( 1309.390560) (UFW BLOCK) IN=wlan0 OUT= MAC=<MAC 'wlan0' (IF1)>:00:30:18:c2:86:f9:08:00 SRC={ipprefix}1 DST={ipaddress} LEN=132 TOS=0x00 PREC=0x00 TTL=64 ID=2355 PROTO=UDP SPT=53 DPT=31666 LEN=112 
( 1314.205628) (UFW BLOCK) IN=wlan0 OUT= MAC=<MAC 'wlan0' (IF1)>:00:30:18:c2:86:f9:08:00 SRC={ipprefix}1 DST={ipaddress} LEN=132 TOS=0x00 PREC=0x00 TTL=64 ID=45963 PROTO=UDP SPT=53 DPT=31666 LEN=112 
########## wireless info END ############

```

---

### Post by Frogs Hair on 2018-07-10
I find the proprietary driver from the additional drivers always performs better for me . I'm not using the same Broadcom device, but I would check software & updates/additional drivers first.

---

### Post by jeremy31 on 2018-07-10
I would do ```
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
```
That should disable wifi power management after a reboot.  See if disabling the firewall helps any as it is blocking some traffic that might be needed by the router

I don't think the proprietary driver in additional drivers covers the SDIO wifi cards like you have

---

### Post by peridian on 2018-07-10
> [COLOR=#000000]I would check software & updates/additional drivers first.[/COLOR]

I had looked in the proprietary repo, but couldn't seem to locate one for this device.

> [COLOR=#000000][FONT=&amp]sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*[/FONT][/COLOR]

That's new to me, I'll give that a try and see how it goes.

I've found [this article]("http://cachestocaches.com/2016/1/disabling-ubuntus-broken-wi-fi-driver/"), and [this post]("https://askubuntu.com/questions/529347/how-do-i-keep-my-wifi-from-dropping-out"), which I had tried previously and it cut out almost immediately so I rolled it back.  After posting here I thought I'd give it another go.  What I've found in the last few hours is that it doesn't stop the connection from dropping to zero, but it does seem to prevent the Network Manager from disconnecting most of the time, and even when it does disconnect, it reconnects almost immediately.  So still disruptive but not as frustrating.

Regards,
Rob.

---

### Post by jeremy31 on 2018-07-10
Disregard the article and post linked as those involve Intel wifi chipsets, but disabling IPv6 in Network Manager has helped some people with various wifi devices

---

