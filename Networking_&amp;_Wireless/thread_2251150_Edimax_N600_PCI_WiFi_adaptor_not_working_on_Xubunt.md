---
title: "Edimax N600 PCI WiFi adaptor not working on Xubuntu 14.10"
date: 2014-11-02
forum: Networking &amp; Wireless
---

### Post by billsmugs on 2014-11-02
I've installed Xubuntu 14.10 (64 bit) on a PC with an [Edimax N600 PCI WiFi adaptor]("http://www.edimax.com/edimax/merchandise/merchandise_detail/data/edimax/global/wireless_adapters_n600_dual-band/ew-7722pnd/") and I can't get it to work. I've tried using the ndiswrapper, but the supplied drivers are only available as an Installshield exe that I can't extract (on Xubuntu or on Windows with 7zip). I found a Windows XP virtual machine to get the .inf file etc, but that only got me the 32bit driver, which won't work. 

I also tried following this guide: [http://ubuntuforums.org/showthread.php?t=1476007](http://ubuntuforums.org/showthread.php?t=1476007) but I can't compile the drivers on my machine.

I'm currently using ethernet via a separate (Windows 8) laptop shared connection and I can boot into Windows 8 on this machine, where I'm using the same wireless card (though I'm using whatever generic drivers Windows installs, since the install CD crashed when I tried to install the official drivers) if that's useful for fixing this. I also have access to a 32bit XP VM and a 64bit Win 7 VM running on the WIn8 partition.

lspci lists the card as RT5592, but the XP drivers are called rt2860, if that makes a difference.

Here's the result of the wireless script in the stickied post:
```

########## wireless info START ##########

Report from: 02 Nov 2014 15:47 GMT +0000

Booted last: 02 Nov 2014 14:37 GMT +0000

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.10
Release:    14.10
Codename:    utopic

##### kernel ############################

Linux 3.16.0-24-generic #32-Ubuntu SMP Tue Oct 28 13:07:32 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Xubuntu

##### lspci #############################

00:19.0 Ethernet controller [0200]: Intel Corporation Ethernet Connection I217-V [8086:153b]
    Subsystem: Gigabyte Technology Co., Ltd Device [1458:e000]
    Kernel driver in use: e1000e

05:00.0 Network controller [0280]: Ralink corp. RT5592 PCIe Wireless Network Adapter [1814:5592]
    Subsystem: Device [7392:d722]

##### lsusb #############################

Bus 002 Device 002: ID 8087:8001 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8009 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 004: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 003 Device 003: ID 046d:c31c Logitech, Inc. Keyboard K120 for Business
Bus 003 Device 002: ID 04f3:0214 Elan Microelectronics Corp. Lynx M9 Optical Mouse
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

ndiswrapper           288024  0 
snd_soc_rt5640         93042  0 
snd_soc_rl6231         13037  1 snd_soc_rt5640
snd_soc_core          200108  1 snd_soc_rt5640
snd_pcm               104102  7 snd_soc_rt5640,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller,snd_pcm_dmaengine
mxm_wmi                13021  1 nouveau
wmi                    19193  2 mxm_wmi,nouveau

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.137.15  Bcast:192.168.137.255  Mask:255.255.255.0
          inet6 addr: fe80::76d4:35ff:fee7:ed33/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:112672 errors:0 dropped:0 overruns:0 frame:0
          TX packets:73940 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:127940577 (127.9 MB)  TX bytes:8985476 (8.9 MB)
          Interrupt:20 Memory:f7900000-f7920000 

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.137.1   0.0.0.0         UG    0      0        0 eth0
192.168.137.0   0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1
search mshome.net

##### nm-tool ###########################

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.137.15
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.137.1

    DNS:             192.168.137.1

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

##### iw reg get ########################

Region: Europe/London (based on set time zone)

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
filename:       /lib/modules/3.16.0-24-generic/updates/dkms/ndiswrapper.ko
license:        GPL
version:        1.59
description:    NDIS wrapper driver
author:         ndiswrapper team <ndiswrapper-general@lists.sourceforge.net>
srcversion:     DC1EFD919FDF2DB80D424C6
depends:        
vermagic:       3.16.0-24-generic SMP mod_unload modversions 
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
alias pci:v00001814d00000601sv00000015sd0000182Dbc*sc*i* ndiswrapper
alias pci:v00001814d00000601sv00000016sd0000182Dbc*sc*i* ndiswrapper
alias pci:v00001814d00000601sv00000022sd000017F9bc*sc*i* ndiswrapper
alias pci:v00001814d00000601sv00000023sd000017F9bc*sc*i* ndiswrapper
alias pci:v00001814d00000601sv0000002Asd00006409bc*sc*i* ndiswrapper
alias pci:v00001814d00000601sv00000061sd000017CFbc*sc*i* ndiswrapper
alias pci:v00001814d00000601sv00000063sd000017CFbc*sc*i* ndiswrapper
alias pci:v00001814d00000601sv00000300sd00005A57bc*sc*i* ndiswrapper
alias pci:v00001814d00000601sv00000361sd00005A57bc*sc*i* ndiswrapper
alias pci:v00001814d00000601sv00000500sd000018EBbc*sc*i* ndiswrapper
alias pci:v00001814d00000601sv0000130Esd00001043bc*sc*i* ndiswrapper
alias pci:v00001814d00000601sv0000130Fsd00001043bc*sc*i* ndiswrapper
alias pci:v00001814d00000601sv00002860sd00001814bc*sc*i* ndiswrapper
alias pci:v00001814d00000601sv00002860sd00008516bc*sc*i* ndiswrapper
alias pci:v00001814d00000601sv00003C0Asd00001186bc*sc*i* ndiswrapper
alias pci:v00001814d00000601sv00003C43sd00001186bc*sc*i* ndiswrapper
alias pci:v00001814d00000601sv00003C85sd00001948bc*sc*i* ndiswrapper
alias pci:v00001814d00000601sv00003C86sd00001948bc*sc*i* ndiswrapper
alias pci:v00001814d00000601sv00003C87sd00001948bc*sc*i* ndiswrapper
alias pci:v00001814d00000601sv00003C88sd00001948bc*sc*i* ndiswrapper
alias pci:v00001814d00000601sv00003C89sd00001948bc*sc*i* ndiswrapper
alias pci:v00001814d00000601sv00003C8Asd00001948bc*sc*i* ndiswrapper
alias pci:v00001814d00000601sv00003C8Bsd00001948bc*sc*i* ndiswrapper
alias pci:v00001814d00000601sv00007322sd00001113bc*sc*i* ndiswrapper
alias pci:v00001814d00000601sv00007708sd00001432bc*sc*i* ndiswrapper
alias pci:v00001814d00000601sv00007728sd00001432bc*sc*i* ndiswrapper
alias pci:v00001814d00000601sv00007758sd00001432bc*sc*i* ndiswrapper
alias pci:v00001814d00000601sv00008322sd00001113bc*sc*i* ndiswrapper
alias pci:v00001814d00000601sv00009161sd000016EFbc*sc*i* ndiswrapper
alias pci:v00001814d00000601sv00009261sd000016EFbc*sc*i* ndiswrapper
alias pci:v00001814d00000601sv00009262sd000016EFbc*sc*i* ndiswrapper
alias pci:v00001814d00000601sv0000C124sd00001259bc*sc*i* ndiswrapper
alias pci:v00001814d00000601sv0000C129sd00001259bc*sc*i* ndiswrapper
alias pci:v00001814d00000601sv0000C12Asd00001259bc*sc*i* ndiswrapper
alias pci:v00001814d00000601sv0000D057sd000010FCbc*sc*i* ndiswrapper
alias pci:v00001814d00000601sv0000E937sd00001458bc*sc*i* ndiswrapper
alias pci:v00001814d00000601sv0000ED07sd000014EAbc*sc*i* ndiswrapper
alias pci:v00001814d00000601sv0000ED09sd000014EAbc*sc*i* ndiswrapper
alias pci:v00001814d00000601sv*sd*bc*sc*i* ndiswrapper
alias pci:v00001814d00000681sv0000002Bsd00006409bc*sc*i* ndiswrapper
alias pci:v00001814d00000681sv00000300sd00001A32bc*sc*i* ndiswrapper
alias pci:v00001814d00000681sv00000503sd00001A32bc*sc*i* ndiswrapper
alias pci:v00001814d00000681sv00002890sd00008516bc*sc*i* ndiswrapper
alias pci:v00001814d00000681sv00003C85sd00001948bc*sc*i* ndiswrapper
alias pci:v00001814d00000681sv00003C86sd00001948bc*sc*i* ndiswrapper
alias pci:v00001814d00000681sv00006247sd000018E8bc*sc*i* ndiswrapper
alias pci:v00001814d00000681sv00007722sd00001113bc*sc*i* ndiswrapper
alias pci:v00001814d00000681sv00007738sd00001432bc*sc*i* ndiswrapper
alias pci:v00001814d00000681sv00007748sd00001432bc*sc*i* ndiswrapper
alias pci:v00001814d00000681sv00007768sd00001432bc*sc*i* ndiswrapper
alias pci:v00001814d00000681sv00008722sd00001113bc*sc*i* ndiswrapper
alias pci:v00001814d00000681sv0000E938sd00001458bc*sc*i* ndiswrapper
alias pci:v00001814d00000681sv0000E939sd00001458bc*sc*i* ndiswrapper
alias pci:v00001814d00000681sv0000E93Asd00001458bc*sc*i* ndiswrapper
alias pci:v00001814d00000681sv0000ED08sd000014EAbc*sc*i* ndiswrapper
alias pci:v00001814d00000681sv*sd*bc*sc*i* ndiswrapper
alias pci:v00001814d00000701sv00000037sd0000182Dbc*sc*i* ndiswrapper
alias pci:v00001814d00000701sv00000043sd0000182Dbc*sc*i* ndiswrapper
alias pci:v00001814d00000701sv00000301sd00005A57bc*sc*i* ndiswrapper
alias pci:v00001814d00000701sv00000302sd00005A57bc*sc*i* ndiswrapper
alias pci:v00001814d00000701sv00001205sd00001259bc*sc*i* ndiswrapper
alias pci:v00001814d00000701sv00001206sd00001259bc*sc*i* ndiswrapper
alias pci:v00001814d00000701sv00002760sd00008516bc*sc*i* ndiswrapper
alias pci:v00001814d00000701sv00003C8Csd00001948bc*sc*i* ndiswrapper
alias pci:v00001814d00000701sv00003C8Dsd00001948bc*sc*i* ndiswrapper
alias pci:v00001814d00000701sv00003C90sd00001948bc*sc*i* ndiswrapper
alias pci:v00001814d00000701sv00003C91sd00001948bc*sc*i* ndiswrapper
alias pci:v00001814d00000701sv00003C92sd00001948bc*sc*i* ndiswrapper
alias pci:v00001814d00000701sv00003C93sd00001948bc*sc*i* ndiswrapper
alias pci:v00001814d00000701sv00007312sd00001113bc*sc*i* ndiswrapper
alias pci:v00001814d00000701sv00007727sd00001432bc*sc*i* ndiswrapper
alias pci:v00001814d00000701sv00009151sd000016EFbc*sc*i* ndiswrapper
alias pci:v00001814d00000701sv00009251sd000016EFbc*sc*i* ndiswrapper
alias pci:v00001814d00000701sv00009252sd000016EFbc*sc*i* ndiswrapper
alias pci:v00001814d00000701sv0000C12Bsd00001259bc*sc*i* ndiswrapper
alias pci:v00001814d00000701sv0000C12Csd00001259bc*sc*i* ndiswrapper
alias pci:v00001814d00000701sv*sd*bc*sc*i* ndiswrapper
alias pci:v00001814d00000781sv00000036sd00001B0Abc*sc*i* ndiswrapper
alias pci:v00001814d00000781sv00000297sd00001028bc*sc*i* ndiswrapper
alias pci:v00001814d00000781sv00000298sd00001028bc*sc*i* ndiswrapper
alias pci:v00001814d00000781sv00000299sd00001028bc*sc*i* ndiswrapper
alias pci:v00001814d00000781sv0000029Asd00001028bc*sc*i* ndiswrapper
alias pci:v00001814d00000781sv00000302sd00001A32bc*sc*i* ndiswrapper
alias pci:v00001814d00000781sv00001059sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v00001814d00000781sv0000130Fsd00001043bc*sc*i* ndiswrapper
alias pci:v00001814d00000781sv00002790sd00001814bc*sc*i* ndiswrapper
alias pci:v00001814d00000781sv00002790sd00008516bc*sc*i* ndiswrapper
alias pci:v00001814d00000781sv00006263sd000018E8bc*sc*i* ndiswrapper
alias pci:v00001814d00000781sv00006600sd000011ADbc*sc*i* ndiswrapper
alias pci:v00001814d00000781sv00006601sd000011ADbc*sc*i* ndiswrapper
alias pci:v00001814d00000781sv00006890sd00001462bc*sc*i* ndiswrapper
alias pci:v00001814d00000781sv00007600sd000011ADbc*sc*i* ndiswrapper
alias pci:v00001814d00000781sv00007712sd00001113bc*sc*i* ndiswrapper
alias pci:v00001814d00000781sv00008320sd00001043bc*sc*i* ndiswrapper
alias pci:v00001814d00000781sv0000832Esd00001043bc*sc*i* ndiswrapper
alias pci:v00001814d00000781sv0000890Asd00001462bc*sc*i* ndiswrapper
alias pci:v00001814d00000781sv0000E002sd0000105Bbc*sc*i* ndiswrapper
alias pci:v00001814d00000781sv0000E93Bsd00001458bc*sc*i* ndiswrapper
alias pci:v00001814d00000781sv*sd*bc*sc*i* ndiswrapper
alias pci:v00001814d00003060sv00003060sd00001B75bc*sc*i* ndiswrapper
alias pci:v00001814d00003060sv00003C04sd00001186bc*sc*i* ndiswrapper
alias pci:v00001814d00003060sv00003C44sd00001186bc*sc*i* ndiswrapper
alias pci:v00001814d00003060sv00003C95sd00001948bc*sc*i* ndiswrapper
alias pci:v00001814d00003060sv00007711sd00001432bc*sc*i* ndiswrapper
alias pci:v00001814d00003060sv000084E2sd00001043bc*sc*i* ndiswrapper
alias pci:v00001814d00003060sv*sd*bc*sc*i* ndiswrapper
alias pci:v00001814d00003062sv00000038sd0000182Dbc*sc*i* ndiswrapper
alias pci:v00001814d00003062sv0000005Esd0000182Dbc*sc*i* ndiswrapper
alias pci:v00001814d00003062sv00003062sd00001B75bc*sc*i* ndiswrapper
alias pci:v00001814d00003062sv00003062sd00008516bc*sc*i* ndiswrapper
alias pci:v00001814d00003062sv00007722sd00001432bc*sc*i* ndiswrapper
alias pci:v00001814d00003062sv*sd*bc*sc*i* ndiswrapper
alias pci:v00001814d00003090sv00000307sd00001A32bc*sc*i* ndiswrapper
alias pci:v00001814d00003090sv00000E40sd0000105Bbc*sc*i* ndiswrapper
alias pci:v00001814d00003090sv00000E41sd0000105Bbc*sc*i* ndiswrapper
alias pci:v00001814d00003090sv00000E42sd0000105Bbc*sc*i* ndiswrapper
alias pci:v00001814d00003090sv00000E43sd0000105Bbc*sc*i* ndiswrapper
alias pci:v00001814d00003090sv00000E44sd0000105Bbc*sc*i* ndiswrapper
alias pci:v00001814d00003090sv00001057sd000013BDbc*sc*i* ndiswrapper
alias pci:v00001814d00003090sv00001087sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v00001814d00003090sv00001453sd0000103Cbc*sc*i* ndiswrapper
alias pci:v00001814d00003090sv00001A87sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v00001814d00003090sv00002041sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v00001814d00003090sv00002A41sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v00001814d00003090sv00003000sd00001854bc*sc*i* ndiswrapper
alias pci:v00001814d00003090sv00003001sd00001854bc*sc*i* ndiswrapper
alias pci:v00001814d00003090sv00003090sd00001814bc*sc*i* ndiswrapper
alias pci:v00001814d00003090sv00003090sd00008516bc*sc*i* ndiswrapper
alias pci:v00001814d00003090sv00003872sd00001462bc*sc*i* ndiswrapper
alias pci:v00001814d00003090sv00006602sd000011ADbc*sc*i* ndiswrapper
alias pci:v00001814d00003090sv00006622sd000011ADbc*sc*i* ndiswrapper
alias pci:v00001814d00003090sv00006632sd000011ADbc*sc*i* ndiswrapper
alias pci:v00001814d00003090sv00006891sd00001462bc*sc*i* ndiswrapper
alias pci:v00001814d00003090sv00006894sd00001462bc*sc*i* ndiswrapper
alias pci:v00001814d00003090sv00007186sd0000144Fbc*sc*i* ndiswrapper
alias pci:v00001814d00003090sv00007602sd000011ADbc*sc*i* ndiswrapper
alias pci:v00001814d00003090sv0000872Asd00001462bc*sc*i* ndiswrapper
alias pci:v00001814d00003090sv0000872Bsd00001462bc*sc*i* ndiswrapper
alias pci:v00001814d00003090sv0000891Asd00001462bc*sc*i* ndiswrapper
alias pci:v00001814d00003090sv0000891Bsd00001462bc*sc*i* ndiswrapper
alias pci:v00001814d00003090sv0000E93Csd00001458bc*sc*i* ndiswrapper
alias pci:v00001814d00003090sv0000E93Dsd00001458bc*sc*i* ndiswrapper
alias pci:v00001814d00003090sv0000F101sd000017AAbc*sc*i* ndiswrapper
alias pci:v00001814d00003090sv*sd*bc*sc*i* ndiswrapper
alias pci:v00001814d00003091sv00001088sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v00001814d00003091sv00001A87sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v00001814d00003091sv00003091sd00008516bc*sc*i* ndiswrapper
alias pci:v00001814d00003091sv00006892sd00001462bc*sc*i* ndiswrapper
alias pci:v00001814d00003091sv0000E93Esd00001458bc*sc*i* ndiswrapper
alias pci:v00001814d00003091sv*sd*bc*sc*i* ndiswrapper
alias pci:v00001814d00003092sv00000015sd000015A9bc*sc*i* ndiswrapper
alias pci:v00001814d00003092sv00003092sd00008516bc*sc*i* ndiswrapper
alias pci:v00001814d00003092sv*sd*bc*sc*i* ndiswrapper
alias pci:v00001814d00003290sv00001771sd000010CFbc*sc*i* ndiswrapper
alias pci:v00001814d00003290sv00002101sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v00001814d00003290sv00002A87sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v00001814d00003290sv00002B87sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v00001814d00003290sv00002C87sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v00001814d00003290sv00002E87sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v00001814d00003290sv00006009sd000011ADbc*sc*i* ndiswrapper
alias pci:v00001814d00003290sv00006019sd000011ADbc*sc*i* ndiswrapper
alias pci:v00001814d00003290sv00007196sd0000144Fbc*sc*i* ndiswrapper
alias pci:v00001814d00003290sv0000E055sd0000105Bbc*sc*i* ndiswrapper
alias pci:v00001814d00003290sv0000F0B0sd00001814bc*sc*i* ndiswrapper
alias pci:v00001814d00003290sv*sd*bc*sc*i* ndiswrapper
alias pci:v00001814d00003562sv00003562sd00008516bc*sc*i* ndiswrapper
alias pci:v00001814d00003562sv0000D05Esd000010FCbc*sc*i* ndiswrapper
alias pci:v00001814d00003562sv*sd*bc*sc*i* ndiswrapper
alias pci:v00001814d00003592sv00001638sd0000103Cbc*sc*i* ndiswrapper
alias pci:v00001814d00003592sv00003592sd00008516bc*sc*i* ndiswrapper
alias pci:v00001814d00003592sv00006007sd000011ADbc*sc*i* ndiswrapper
alias pci:v00001814d00003592sv0000F003sd00001814bc*sc*i* ndiswrapper
alias pci:v00001814d00003592sv*sd*bc*sc*i* ndiswrapper
alias pci:v00001814d00003593sv0000F102sd000017AAbc*sc*i* ndiswrapper
alias pci:v00001814d00003593sv*sd*bc*sc*i* ndiswrapper
alias pci:v00001814d0000359Fsv00003390sd0000103Cbc*sc*i* ndiswrapper
alias pci:v00001814d0000359Fsv*sd*bc*sc*i* ndiswrapper
alias pci:v00001814d00005360sv*sd*bc*sc*i* ndiswrapper
alias pci:v00001814d00005362sv*sd*bc*sc*i* ndiswrapper
alias pci:v00001814d00005390sv00001155sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v00001814d00005390sv00001636sd0000103Cbc*sc*i* ndiswrapper
alias pci:v00001814d00005390sv00001A55sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v00001814d00005390sv00006008sd000011ADbc*sc*i* ndiswrapper
alias pci:v00001814d00005390sv00006605sd000011ADbc*sc*i* ndiswrapper
alias pci:v00001814d00005390sv0000E054sd0000105Bbc*sc*i* ndiswrapper
alias pci:v00001814d00005390sv0000F001sd00001814bc*sc*i* ndiswrapper
alias pci:v00001814d00005390sv0000F051sd00001814bc*sc*i* ndiswrapper
alias pci:v00001814d00005390sv0000F052sd00001814bc*sc*i* ndiswrapper
alias pci:v00001814d00005390sv*sd*bc*sc*i* ndiswrapper
alias pci:v00001814d00005392sv00003C06sd00001186bc*sc*i* ndiswrapper
alias pci:v00001814d00005392sv00006606sd000011ADbc*sc*i* ndiswrapper
alias pci:v00001814d00005392sv0000F053sd00001814bc*sc*i* ndiswrapper
alias pci:v00001814d00005392sv0000F054sd00001814bc*sc*i* ndiswrapper
alias pci:v00001814d00005392sv*sd*bc*sc*i* ndiswrapper
alias pci:v00001814d0000539Asv00001839sd0000103Cbc*sc*i* ndiswrapper
alias pci:v00001814d0000539Asv000018ECsd0000103Cbc*sc*i* ndiswrapper
alias pci:v00001814d0000539Asv*sd*bc*sc*i* ndiswrapper
alias pci:v00001814d0000539Bsv000018EDsd0000103Cbc*sc*i* ndiswrapper
alias pci:v00001814d0000539Bsv*sd*bc*sc*i* ndiswrapper
alias pci:v00001814d0000539Fsv00001637sd0000103Cbc*sc*i* ndiswrapper
alias pci:v00001814d0000539Fsv00001774sd0000103Cbc*sc*i* ndiswrapper
alias pci:v00001814d0000539Fsv0000F002sd00001814bc*sc*i* ndiswrapper
alias pci:v00001814d0000539Fsv*sd*bc*sc*i* ndiswrapper
alias pci:v00001814d00005592sv0000851Asd00001043bc*sc*i* ndiswrapper
alias pci:v00001814d00005592sv0000D722sd00007392bc*sc*i* ndiswrapper
alias pci:v00001814d00005592sv*sd*bc*sc*i* ndiswrapper

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x8086:0x153b (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

##### dmesg #############################

[  919.684157] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
[  919.687466] ndiswrapper (check_nt_hdr:141): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B
[  919.687468] ndiswrapper (load_sys_files:200): couldn't prepare driver 'rt2860'
[  919.687735] ndiswrapper (load_wrap_driver:103): couldn't load driver rt2860; check system log for messages from 'loadndisdriver'

########## wireless info END ############


```

---

### Post by chili555 on 2014-11-02
Please see: [http://ubuntuforums.org/showthread.php?t=2217996&page=4](http://ubuntuforums.org/showthread.php?t=2217996&page=4) Especially, my post #37:> At this moment, I know of no reliable way to get the [COLOR="#FF0000"]1814:5592[/COLOR] device going in later kernels such as 3.13.0-xx used in Ubuntu 14.04. I have googled some information that it was to be included in rt2800pci, but, as of 3.16.1, it isn't there yet.

I wish I had better news.I suggest you read the later posts, including:> Thank you. This version of the driver seems to have fixed my issue with the Asus PCE-N53 after upgrading to the 3.11.0-26-generic kernel. A computer with no network connection is not much use these days!

Edit: Erk! I spoke too soon. The computer has just frozen a second or two after starting the Software Updater. I will investigate to see whether this keeps happening.

Edit again: I rebooted and it froze again. I have to suspect there's something wrong with the driver.

---

### Post by billsmugs on 2014-11-02
Thanks for the link, I followed the steps in post #39 and I can now connect via WiFi! I haven't seen any problems yet (touch wood), but I did have to run  "sudo modprobe rt5592sta" after rebooting to connect again. If I set this command to run at startup (would I do this by adding it (minus "sudo") to /etc/rc.local?) will that potentially cause any issues? Will I have to recompile/reinstall after Xubuntu updates?

---

### Post by chili555 on 2014-11-02
> **billsmugs said:**
> Thanks for the link, I followed the steps in post #39 and I can now connect via WiFi! I haven't seen any problems yet (touch wood), but I did have to run  "sudo modprobe rt5592sta" after rebooting to connect again. If I set this command to run at startup (would I do this by adding it (minus "sudo") to /etc/rc.local?) will that potentially cause any issues? Will I have to recompile/reinstall after Xubuntu updates?Yes, you will have to recompile after a later kernel, also known as linux-image is installed. After the requested reboot:```
cd Directory/where/you/extracted
make clean
make
sudo make install
sudo modprobe rt5592sta
```To get it to load on boot:```
sudo -i
echo rt5592sta  >>  /etc/modules
exit
```Glad it's working.

---

### Post by billsmugs on 2014-11-02
Could I potentially use DKMS to automatically recompile after kernal updates? If i added the following dkms.conf file to the source directory (and registered it with DKMS), would that be correct:
```
MAKE="make -C  KERNELDIR=/lib/modules/${kernelver}/build"
CLEAN="make -C clean"
BUILT_MODULE_NAME=RT2860STA
BUILT_MODULE_LOCATION=./
PACKAGE_NAME=rt5592sta
PACKAGE_VERSION=1.0
REMAKE_INITRD=yes
```

(Based on the example here: [https://help.ubuntu.com/community/DKMS](https://help.ubuntu.com/community/DKMS) ) and would I still have to add "rt5592sta" to /etc/modules manually?

---

### Post by chili555 on 2014-11-02
Frankly, I don't know. I am not experienced with DKMS; I can barely spell it! I suggest you Private Message praseodym. He seems to know more DKMS than I.

---

### Post by billsmugs on 2014-11-02
Thanks for all your help, I'll have a look into the DKMS stuff myself a bit more and contact praseodym if I'm still stuck.

---

### Post by jbdough on 2014-11-30
I am really happy to report the patch referenced at [pcvonz]("http://ubuntuforums.org/member.php?u=1735700")['s post #39]("http://ubuntuforums.org/showthread.php?t=2217996&p=13106385#post13106385")
works with a [Rosewill N600PCE]("http://www.rosewill.com/products/2322/ProductDetail_Specifications.htm")

02:00.0 Network controller: Ralink corp. RT5592 PCIe Wireless Network Adapter


Ubuntu 14.04.1 LTS
3.13.0-40-generic #69-Ubuntu SMP Thu Nov 13 17:53:56 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by jms-ubuntu-en on 2014-12-31
> **billsmugs said:**
> Thanks for all your help, I'll have a look into the DKMS stuff myself a bit more and contact praseodym if I'm still stuck.

Did you get this driver to autocompile with DKMS?

---

### Post by billsmugs on 2014-12-31
> **jms-ubuntu-en said:**
> Did you get this driver to autocompile with DKMS?

I'm afraid I didn't really get round to looking at it in detail. Since kernel updates doesn't happen too often I've just been re-running the compilation/installation commands manually each time (with a view to creating a script once I'm sure of which ones need to be repeated each time). I was looking at doing something like this: [http://ubuntuforums.org/showthread.php?t=835573](http://ubuntuforums.org/showthread.php?t=835573) to avoid having to learn all the DKMS stuff but I haven't got round to it yet.

---

