---
title: "No Wireless Or Ethernet connection"
date: 2015-02-14
forum: Networking &amp; Wireless
---

### Post by KuJiM on 2015-02-14
Hello 

I have just installed Ubuntu alongside Windows and for some reason it does not recognize my wireless network interface card. I did try to connect via Ethernet in my University but again it did not work. It found the network but kept trying to connect for ages without success.


then tried the following method from some posts found in this forum but no success.

1. 

sudo apt-get remove --purge firmware-b43-installer

then go here..
//[http://ubuntuforums.org/showthread.php?t=2098717](http://ubuntuforums.org/showthread.php?t=2098717)
post #7, copy the zip file first
then do..


sudo modprobe -rf b43
sudo modprobe b43
sudo apt-get update
sudo apt-get upgrade

2.cd Desktop
unzip b43.zip
sudo mkdir -p /lib/firmware/b43
sudo cp b43/* /lib/firmware/b43
Reboot, and check -




Code after the execution of the above commands:
--------------------------------------------------------------------------------------------------------------------------------------

kujim@kujim:/media/kujim/UUI$ uname -r
3.16.0-23-generic


kujim@kujim:/media/kujim/UUI$ cat /etc/issue
Ubuntu 14.10 \n \l


kujim@kujim:/media/kujim/UUI$ lspci -nn | egrep '0200|0280'
01:00.1 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 12)
02:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)


kujim@kujim:/media/kujim/UUI$ lsmod | egrep 'wl|b43'
b43                   400218  0 
mac80211              660592  1 b43
cfg80211              510218  2 b43,mac80211
ssb                    62366  1 b43
bcma                   52443  1 b43


kujim@kujim:/media/kujim/UUI$ rfkill list all
0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: acer-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no

------------------------------------------------------------------------------------------------------------------------------------------



########## wireless info START ##########


Report from: 14 Feb 2015 13:47 EST -0500


Booted last: 14 Feb 2015 13:33 EST -0500


Script from: 20 Sep 2014 23:04 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 14.10
Release:    14.10
Codename:    utopic


##### kernel ############################


Linux 3.16.0-23-generic #31-Ubuntu SMP Tue Oct 21 17:56:17 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


01:00.1 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 12)
    Subsystem: Acer Incorporated [ALI] Device [1025:0866]
    Kernel driver in use: r8169


02:00.0 Network controller 0280: Broadcom Corporation BCM43142 802.11b/g/n 14e4:4365 (rev 01)
    Subsystem: Lite-On Communications Inc Device [11ad:6645]
    Kernel driver in use: bcma-pci-bridge


##### lsusb #############################


Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 005: ID 04f2:b452 Chicony Electronics Co., Ltd 
Bus 002 Device 004: ID 04ca:2009 Lite-On Technology Corp. 
Bus 002 Device 003: ID 0781:5583 SanDisk Corp. 
Bus 002 Device 002: ID 040b:2013 Weltrend Semiconductor 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: acer-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no


##### lsmod #############################


b43                   400218  0 
mac80211              660592  1 b43
cfg80211              510218  2 b43,mac80211
ssb                    62366  1 b43
acer_wmi               32522  0 
sparse_keymap          13948  1 acer_wmi
bcma                   52443  1 b43
snd_soc_rt5640         93042  0 
snd_soc_rl6231         13037  1 snd_soc_rt5640
snd_soc_core          200108  1 snd_soc_rt5640
snd_pcm               104102  7 snd_soc_rt5640,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller,snd_pcm_dmaengine
wmi                    19193  1 acer_wmi
video                  20128  2 i915,acer_wmi


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


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface


##### resolv.conf #######################


##### nm-tool ###########################


NetworkManager Tool


State: disconnected


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth0' [IF]>


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off


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


no-auto-default=<MAC 'eth0' IF>,<MAC address>,


[ifupdown]
managed=false


##### NetworkManager profiles ###########


##### iw reg get ########################


Region: America/New_York (based on set time zone)


country 00: DFS-UNSET
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), NO-IR
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, NO-IR
    (5170 - 5250 @ 40), (3, 20), NO-IR
    (5735 - 5835 @ 40), (3, 20), NO-IR


##### iwlist channels ###################


eth0      no frequency information.


lo        no frequency information.


##### iwlist scan #######################


eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


##### module infos ######################


[b43]
filename:       /lib/modules/3.16.0-23-generic/kernel/drivers/net/wireless/b43/b43.ko
firmware:       b43/ucode9.fw
firmware:       b43/ucode5.fw
firmware:       b43/ucode16_mimo.fw
firmware:       b43/ucode15.fw
firmware:       b43/ucode14.fw
firmware:       b43/ucode13.fw
firmware:       b43/ucode11.fw
license:        GPL
author:         Rafa&#322; Mi&#322;ecki
author:         Gábor Stefanik
author:         Michael Buesch
author:         Stefano Brivio
author:         Martin Langer
description:    Broadcom B43 wireless driver
srcversion:     3CEE8C37D02010CA66D9311
depends:        bcma,ssb,mac80211,cfg80211
intree:         Y
vermagic:       3.16.0-23-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        D1:20:C4:7C:14:BE:B6:2E:AD:67:03:D4:17:12:CC:11:05:75:D2:97
sig_hashalgo:   sha512
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


[mac80211]
filename:       /lib/modules/3.16.0-23-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     0D5DBE66E4CC44B010DB516
depends:        cfg80211
intree:         Y
vermagic:       3.16.0-23-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        D1:20:C4:7C:14:BE:B6:2E:AD:67:03:D4:17:12:CC:11:05:75:D2:97
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/3.16.0-23-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     DEE8EAA48495E392CD51C2D
depends:        
intree:         Y
vermagic:       3.16.0-23-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        D1:20:C4:7C:14:BE:B6:2E:AD:67:03:D4:17:12:CC:11:05:75:D2:97
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


[ssb]
filename:       /lib/modules/3.16.0-23-generic/kernel/drivers/ssb/ssb.ko
license:        GPL
description:    Sonics Silicon Backplane driver
srcversion:     2055C3093DA2EE9DEB5572C
depends:        
intree:         Y
vermagic:       3.16.0-23-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        D1:20:C4:7C:14:BE:B6:2E:AD:67:03:D4:17:12:CC:11:05:75:D2:97
sig_hashalgo:   sha512


[bcma]
filename:       /lib/modules/3.16.0-23-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     D52E980A55E0AC3C372382C
depends:        
intree:         Y
vermagic:       3.16.0-23-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        D1:20:C4:7C:14:BE:B6:2E:AD:67:03:D4:17:12:CC:11:05:75:D2:97
sig_hashalgo:   sha512


##### module parameters #################


[b43]
allhwsupport: 0
bad_frames_preempt: 0
btcoex: 1
hwpctl: 0
hwtkip: 0
nohwcrypt: 0
pio: 0
qos: 1
verbose: 2


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


/etc/modprobe.d/iwlwifi.conf
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211


/etc/modprobe.d/mlx4.conf
softdep mlx4_core post: mlx4_en


/etc/modprobe.d/modesetting.conf
options cirrus modeset=1
options mgag200 modeset=1


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


##### dmesg #############################


[   13.063101] bcma: bus0: Found chip with id 0xA886, rev 0x01 and package 0x08
[   13.063127] bcma: bus0: Core 0 found: ChipCommon (manuf 0x4BF, id 0x800, rev 0x28, class 0x0)
[   13.063146] bcma: bus0: Core 1 found: IEEE 802.11 (manuf 0x4BF, id 0x812, rev 0x21, class 0x0)
[   13.063182] bcma: bus0: Core 2 found: PCIe (manuf 0x4BF, id 0x820, rev 0x16, class 0x0)
[   13.063226] bcma: bus0: Core 3 found: UNKNOWN (manuf 0x43B, id 0x368, rev 0x00, class 0x0)
[   13.077560] bcma: bus0: Bus registered


########## wireless info END ############





Can anyone spot what is wrong with it ?


I have no internet connection whatsoever in Ubuntu. I am posting this Thread in another OS. 


Thanks in advance


Kujim

---

### Post by chili555 on 2015-02-14
> Can anyone spot what is wrong with it ?Oh, yes and very easily. If you consult the stickie at the top of the forum: [http://ubuntuforums.org/showthread.php?t=2214110](http://ubuntuforums.org/showthread.php?t=2214110) Then you will see that b43 plus firmware is incorrect for your 14e4:4365 device. Instead, you need bcmwl-kernel-source. If you still have the install DVD or USB, you can install it easily: [http://askubuntu.com/questions/523458/unable-to-connect-to-any-wifi-in-ubuntu-14-04/523568#523568](http://askubuntu.com/questions/523458/unable-to-connect-to-any-wifi-in-ubuntu-14-04/523568#523568)

---

### Post by KuJiM on 2015-02-14
> **chili555 said:**
> Oh, yes and very easily. 

Thank you for time chili555, and after following ur instruction I very easily connected to the internet.

Once again, thank you

Kujim

---

