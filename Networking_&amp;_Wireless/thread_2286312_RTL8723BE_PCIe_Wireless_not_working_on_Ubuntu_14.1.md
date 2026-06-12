---
title: "RTL8723BE PCIe Wireless not working on Ubuntu 14.10 x64"
date: 2015-07-11
forum: Networking &amp; Wireless
---

### Post by byhoratiss on 2015-07-11
Hi everyone,

I'm new in Ubuntu and a have a few problems with my notebook (Positivo BGH 970), my wireless never worked as expected (stops working after a while) and my bluetooth never worked (but in Windows did, but I remove it (because I love Ubuntu).
I tried several times to make my wireless work: I installed the rtlwifi_new drivers, but I think I did it wrong. After that didn't solved my problems, I installed the "ndiswrapper" driver, using the drivers downloaded from the manufacturer (for Win8.1), but after rebooting, of course, not working again.

So, can any of you show me the light?
Of course, sorry about my english.

This is the output of the wireless-info script:
```

########## wireless info START ##########


Report from: 11 Jul 2015 09:43 ART -0300


Booted last: 11 Jul 2015 09:36 ART -0300


Script from: 21 May 2015 09:10 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 14.10
Release:    14.10
Codename:    utopic


##### kernel ############################


Linux 3.16.0-43-generic #58-Ubuntu SMP Fri Jun 19 11:04:02 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


GNOME


##### lspci #############################


02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:b729]


03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device [10ec:5287] (rev 01)


03:00.1 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 12)
    Subsystem: CLEVO/KAPOK Computer Device [1558:5494]
    Kernel driver in use: r8169


##### lsusb #############################


Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 004: ID 0458:003a KYE Systems Corp. (Mouse Systems) NetScroll+ Mini Traveler / Genius NetScroll 120
Bus 002 Device 003: ID 04f2:b43b Chicony Electronics Co., Ltd 
Bus 002 Device 002: ID 0bda:b002 Realtek Semiconductor Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no


##### lsmod #############################


wmi                    19193  0 
ndiswrapper           288024  0 
snd_soc_rt5640         93042  0 
snd_soc_rl6231         13037  1 snd_soc_rt5640
snd_soc_core          200204  1 snd_soc_rt5640
snd_pcm               104102  7 snd_soc_rt5640,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller,snd_pcm_dmaengine


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.0.17  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::82fa:5bff:fe0d:af60/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:80012 errors:0 dropped:0 overruns:0 frame:0
          TX packets:49441 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:109193537 (109.1 MB)  TX bytes:5292307 (5.2 MB)


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0


##### resolv.conf #######################


nameserver 127.0.1.1


##### network managers ##################


Installed:


    NetworkManager


Running:


root       960     1  0 09:36 ?        00:00:00 NetworkManager


##### NetworkManager info ###############


NetworkManager Tool


State: connected (global)


- Device: eth0  [Cableada automática] -----------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>


  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         192.168.0.17
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1


    DNS:             200.42.4.204
    DNS:             200.49.130.41


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


[[/etc/NetworkManager/system-connections/Tissera]] (600 root)
[connection] id=Tissera | type=802-11-wireless
[802-11-wireless] ssid=Tissera | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/AndroidAP]] (600 root)
[connection] id=AndroidAP | type=802-11-wireless
[802-11-wireless] ssid=AndroidAP | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/WiFi-Arnet-Hesiel]] (600 root)
[connection] id=WiFi-Arnet-Hesiel | type=802-11-wireless
[802-11-wireless] ssid=WiFi-Arnet-Hesiel | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/PyP]] (600 root)
[connection] id=PyP | type=802-11-wireless
[802-11-wireless] ssid=PyP | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/patricia]] (600 root)
[connection] id=patricia | type=802-11-wireless
[802-11-wireless] ssid=patricia | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: America/Argentina/Buenos_Aires (based on set time zone)


country 00: DFS-UNSET
    (2402 - 2472 @ 40), (6, 20)
    (2457 - 2482 @ 40), (6, 20), PASSIVE-SCAN
    (2474 - 2494 @ 20), (6, 20), NO-OFDM, PASSIVE-SCAN
    (5170 - 5250 @ 160), (6, 20), PASSIVE-SCAN
    (5250 - 5330 @ 160), (6, 20), DFS, PASSIVE-SCAN
    (5490 - 5730 @ 160), (6, 20), DFS, PASSIVE-SCAN


##### iwlist channels ###################


eth0      no frequency information.


lo        no frequency information.


##### iwlist scan #######################


eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


##### module infos ######################


[ndiswrapper]
filename:       /lib/modules/3.16.0-43-generic/updates/dkms/ndiswrapper.ko
license:        GPL
version:        1.59
description:    NDIS wrapper driver
author:         ndiswrapper team <ndiswrapper-general@lists.sourceforge.net>
srcversion:     DC1EFD919FDF2DB80D424C6
depends:        
vermagic:       3.16.0-43-generic SMP mod_unload modversions 
parm:           if_name:Network interface name or template (default: wlan%d) (charp)
parm:           proc_uid:The uid of the files created in /proc (default: 0). (int)
parm:           proc_gid:The gid of the files created in /proc (default: 0). (int)
parm:           debug:debug level (int)
parm:           hangcheck_interval:The interval, in seconds, for checking if driver is hung. (default: 0) (int)
parm:           utils_version:Compatible version of utils (read only: 1.9) (charp)


##### module parameters #################


grep: /sys/module/ndiswrapper/parameters/debug: Permission denied
grep: /sys/module/ndiswrapper/parameters/hangcheck_interval: Permission denied
grep: /sys/module/ndiswrapper/parameters/if_name: Permission denied
grep: /sys/module/ndiswrapper/parameters/proc_gid: Permission denied
grep: /sys/module/ndiswrapper/parameters/proc_uid: Permission denied
grep: /sys/module/ndiswrapper/parameters/utils_version: Permission denied
[ndiswrapper]


##### /etc/modules ######################


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


[/etc/modprobe.d/modesetting.conf]
options cirrus modeset=1
options mgag200 modeset=1


[/etc/modprobe.d/ndiswrapper.conf]
alias pci:v000010ECd00008172sv0000E020sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008172sv*sd*bc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00000315sd00001A32bc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00001139sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00001629sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv0000169Fsd0000103Cbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv000016B3sd000010CFbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00001786sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00001A39sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00002057sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00002078sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00002315sd00001A32bc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00002481sd00001B9Abc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00002A57sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00003824sd00001462bc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00003874sd00001462bc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00006150sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00006176sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00006177sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00006178sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00006179sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00006180sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00006181sd00001025bc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00006182sd00001025bc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00006191sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00006192sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00006193sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00006194sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00006195sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00007150sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00007176sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00007177sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00007178sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00007179sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00007180sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00007181sd00001025bc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00007182sd00001025bc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00007185sd0000144Fbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00007191sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00007192sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00007193sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00007194sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00007195sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00007611sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008130sd00001025bc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008131sd00001025bc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008150sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008175sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008176sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008176sd0000185Fbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008181sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008182sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008184sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008185sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008186sd00001025bc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008187sd00001025bc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv0000818Asd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008191sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008192sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008193sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008194sd00001028bc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008195sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008197sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008198sd00001028bc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008199sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008200sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008201sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008202sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008203sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008204sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008205sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008206sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008207sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008208sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008209sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008210sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008211sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008212sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008213sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008214sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008215sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008216sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008217sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008218sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008219sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008220sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008221sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008222sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008230sd00001025bc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008231sd00001025bc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv0000824Asd00001462bc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008297sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv000084B5sd00001043bc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv000085E5sd00001043bc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv0000874Asd00001462bc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00009150sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00009174sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00009175sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00009176sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00009177sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00009181sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00009182sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00009184sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00009185sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00009186sd00001025bc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00009187sd00001025bc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00009191sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00009192sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00009193sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00009194sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00009195sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00009196sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00009197sd00001028bc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00009198sd00001028bc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00009199sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00009200sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00009201sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00009202sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00009203sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00009204sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00009205sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv*sd*bc*sc*i* ndiswrapper
alias pci:v000010ECd00008177sv*sd*bc*sc*i* ndiswrapper
alias pci:v000010ECd00008178sv00001178sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v000010ECd00008178sv00001400sd00001B9Abc*sc*i* ndiswrapper
alias pci:v000010ECd00008178sv00001401sd00001B9Abc*sc*i* ndiswrapper
alias pci:v000010ECd00008178sv00001402sd00001B9Abc*sc*i* ndiswrapper
alias pci:v000010ECd00008178sv00006178sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008178sv00006179sd00001025bc*sc*i* ndiswrapper
alias pci:v000010ECd00008178sv00006180sd00001025bc*sc*i* ndiswrapper
alias pci:v000010ECd00008178sv00007178sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008178sv00007179sd00001025bc*sc*i* ndiswrapper
alias pci:v000010ECd00008178sv00007180sd00001025bc*sc*i* ndiswrapper
alias pci:v000010ECd00008178sv00007622sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008178sv00007622sd00007392bc*sc*i* ndiswrapper
alias pci:v000010ECd00008178sv00008178sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008178sv00008179sd00001025bc*sc*i* ndiswrapper
alias pci:v000010ECd00008178sv00008180sd00001025bc*sc*i* ndiswrapper
alias pci:v000010ECd00008178sv00008183sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008178sv00008186sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008178sv00008189sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008178sv00008190sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008178sv00008191sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008178sv000084B6sd00001043bc*sc*i* ndiswrapper
alias pci:v000010ECd00008178sv000085E3sd00001043bc*sc*i* ndiswrapper
alias pci:v000010ECd00008178sv00009178sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008178sv00009179sd00001025bc*sc*i* ndiswrapper
alias pci:v000010ECd00008178sv00009180sd00001025bc*sc*i* ndiswrapper
alias pci:v000010ECd00008178sv*sd*bc*sc*i* ndiswrapper
alias pci:v000010ECd00008179sv00000179sd000017AAbc*sc*i* ndiswrapper
alias pci:v000010ECd00008179sv00000180sd00001025bc*sc*i* ndiswrapper
alias pci:v000010ECd00008179sv00000181sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008179sv00000182sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008179sv00000183sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008179sv00000184sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008179sv00000185sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008179sv00000187sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008179sv00000188sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008179sv00000189sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008179sv00000190sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008179sv00000191sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008179sv00000192sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008179sv00000193sd000017AAbc*sc*i* ndiswrapper
alias pci:v000010ECd00008179sv00000194sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008179sv00000195sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008179sv00001238sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v000010ECd00008179sv000012A8sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v000010ECd00008179sv000012B8sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v000010ECd00008179sv000012C8sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v000010ECd00008179sv000012D8sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v000010ECd00008179sv0000197Dsd0000103Cbc*sc*i* ndiswrapper
alias pci:v000010ECd00008179sv00001D38sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v000010ECd00008179sv00001F38sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v000010ECd00008179sv00008179sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008179sv00008180sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008179sv0000E08Asd0000105Bbc*sc*i* ndiswrapper
alias pci:v000010ECd00008179sv*sd*bc*sc*i* ndiswrapper
alias pci:v000010ECd0000818Bsv0000001Bsd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd0000818Bsv0000002Bsd000017AAbc*sc*i* ndiswrapper
alias pci:v000010ECd0000818Bsv0000818Bsd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd0000818Bsv0000819Bsd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd0000818Bsv*sd*bc*sc*i* ndiswrapper
alias pci:v000010ECd00008191sv*sd*bc*sc*i* ndiswrapper
alias pci:v000010ECd00008193sv00000186sd00001025bc*sc*i* ndiswrapper
alias pci:v000010ECd00008193sv00008193sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008193sv00008194sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008193sv00008195sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008193sv00008293sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008193sv00009293sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008193sv*sd*bc*sc*i* ndiswrapper
alias pci:v000010ECd00008723sv00000723sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008723sv00000724sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008723sv00000725sd00001025bc*sc*i* ndiswrapper
alias pci:v000010ECd00008723sv00000726sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008723sv00000727sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008723sv00000728sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008723sv00000729sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008723sv00000730sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008723sv00000731sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008723sv00000732sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008723sv00000733sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008723sv00000734sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008723sv00002114sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v000010ECd00008723sv00008723sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008723sv*sd*bc*sc*i* ndiswrapper
alias pci:v000010ECd00008724sv00008724sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008724sv*sd*bc*sc*i* ndiswrapper
alias pci:v000010ECd0000872Asv0000872Asd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd0000872Asv*sd*bc*sc*i* ndiswrapper
alias pci:v000010ECd0000872Bsv0000872Bsd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd0000872Bsv*sd*bc*sc*i* ndiswrapper
alias pci:v000010ECd00008753sv00008753sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008753sv*sd*bc*sc*i* ndiswrapper
alias pci:v000010ECd00008812sv000020EFsd0000148Fbc*sc*i* ndiswrapper
alias pci:v000010ECd00008812sv00008812sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008812sv0000A811sd000017AAbc*sc*i* ndiswrapper
alias pci:v000010ECd00008812sv0000A812sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008812sv0000A813sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008812sv*sd*bc*sc*i* ndiswrapper
alias pci:v000010ECd00008821sv00002161sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v000010ECd00008821sv0000216Asd00001A3Bbc*sc*i* ndiswrapper
alias pci:v000010ECd00008821sv0000216Bsd00001A3Bbc*sc*i* ndiswrapper
alias pci:v000010ECd00008821sv0000216Csd00001A3Bbc*sc*i* ndiswrapper
alias pci:v000010ECd00008821sv000085B4sd00001043bc*sc*i* ndiswrapper
alias pci:v000010ECd00008821sv00008821sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008821sv0000A801sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008821sv0000A802sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008821sv0000A803sd000017AAbc*sc*i* ndiswrapper
alias pci:v000010ECd00008821sv0000A804sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008821sv0000A821sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008821sv*sd*bc*sc*i* ndiswrapper
alias pci:v000010ECd0000B723sv00002159sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v000010ECd0000B723sv0000215Asd00001A3Bbc*sc*i* ndiswrapper
alias pci:v000010ECd0000B723sv00002165sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v000010ECd0000B723sv000021FDsd0000103Cbc*sc*i* ndiswrapper
alias pci:v000010ECd0000B723sv00002231sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000010ECd0000B723sv0000B001sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000010ECd0000B723sv0000B723sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd0000B723sv0000B724sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd0000B723sv0000B725sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd0000B723sv0000B726sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd0000B723sv0000B727sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd0000B723sv0000B728sd000017AAbc*sc*i* ndiswrapper
alias pci:v000010ECd0000B723sv0000B729sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd0000B723sv0000B730sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd0000B723sv0000B731sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd0000B723sv0000B732sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd0000B723sv0000B733sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd0000B723sv0000B734sd00001025bc*sc*i* ndiswrapper
alias pci:v000010ECd0000B723sv0000B735sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd0000B723sv0000B736sd000017AAbc*sc*i* ndiswrapper
alias pci:v000010ECd0000B723sv0000B737sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd0000B723sv0000B738sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd0000B723sv0000E089sd0000105Bbc*sc*i* ndiswrapper
alias pci:v000010ECd0000B723sv0000E08Dsd0000105Bbc*sc*i* ndiswrapper
alias pci:v000010ECd0000B723sv*sd*bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv000030A1sd000017AAbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv*sd*bc*sc*i* ndiswrapper


[/etc/modprobe.d/rtl8723be.conf]
options rtl8723be fwlps=0 ips=N


##### rc.local ##########################


/etc/init.d/bluetooth stop


exit 0


##### pm-utils ##########################


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0xb723 (rtl8723be)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# USB device 0x:0x (rt2800usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"


##### dmesg #############################


[   17.270348] ndiswrapper: module verification failed: signature and/or  required key missing - tainting kernel
[   17.271206] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
[   18.473605] uvcvideo: Found UVC 1.00 device Chicony USB 2.0 Camera (04f2:b43b)


########## wireless info END ############

```

---

### Post by praseodym on 2015-07-11
Hi,

Ndiswrapper and the Windows driver are not needed here:

```
sudo modprobe -rfv ndiswrapper
sudo apt-get remove --purge ndisgtk ndiswrapper*
echo "options rtl8723be swenc=1 fwlps=0 ips=0" | sudo tee /etc/modprobe.d/rtl8723be.conf
sudo modprobe -v rtl8723be
```

---

### Post by byhoratiss on 2015-07-11
I used your commands, but still after a reboot, the Wifi connections doesn't show up.
Could it be a matter related to network-manager?

Any clue about what's wrong with my system? (besides the user :D)

---

### Post by byhoratiss on 2015-07-11
Thank you so much! It works!

---

