---
title: "Broadcom BCM4322 Wireless won't connect. Already ready previous threads"
date: 2015-09-02
forum: Networking &amp; Wireless
---

### Post by Bowei_Zhao on 2015-09-02
FIANL EDIT:

If you have a 2011 Macbook Pro with BCM4322 and are here reading this. You may be SoL.

Try out this thread first:
[http://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers](http://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers)

And if bcmwl-kernel-source and firmware-b43-installer both don't work. Then just stop.

You can read this thread and this one with another user in our predicament:
[http://ubuntuforums.org/showthread.php?t=2173985](http://ubuntuforums.org/showthread.php?t=2173985)

Just buy a wireless adapter that is supported by Linux like some TP Links or the Panda Wireless ones.

The only way my wireless works is if the computer first goes into sleep after booting into Ubuntu. But even then, it's only 75% of the time and there's problems where it drops connections, disconnects or dissapears sometimes after that.

It's honestly too much of a hassle for it to barely work so just get yourself an adapter. I bought a Panda Wireless Dual Band one. It sticks out but the mini adapters don't have very good signal range/quality so I opted for this. 

----------------------------------------------------
Original Post:


I am on a new install of Ubuntu 15.04 on a Macbook Pro with PCID 14e4:432b for Broadcom.


I have installed and tried both firmware-b43-installer, bcmwl-kernel-source, and fwcutter making sure to purge/remove the previous before trying the next.

I've read and tried:
[http://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers](http://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers)
[http://ubuntuforums.org/showthread.php?t=2214110](http://ubuntuforums.org/showthread.php?t=2214110)

and many others.


I have played around with modprobe both adding and # out the current bcm module with no success.


Do you have any suggestions for me at the moment? It shows that I am using b43-pci-bridge at the moment which doesn't sound like the firmware-b43 installer I got?

I am using Synaptic to manage my packages. I currently uninstalled firmware-b43-installer and fwcutter and going back in a circle to what I had originally, the bcmwl-kernel-source. Tried the modprobe -r wl and modprobe wl with sudo and what not but nothing is working.

rfkill shows everything is 'no' and my wlan does indeed show up in iwconfig and many other menus



I would appreciate any help. Thanks

---

### Post by chili555 on 2015-09-03
The prescribed driver package is bcmwl-kernel-source. Please install it, reboot and show me:```
iwconfig
rfkill list all
sudo iwlist wlan0 scan
```Thanks.

---

### Post by Bowei_Zhao on 2015-09-03
> **chili555 said:**
> The prescribed driver package is bcmwl-kernel-source. Please install it, reboot and show me:```
iwconfig
rfkill list all
sudo iwlist wlan0 scan
```Thanks.

Chili, I appreciate your help in this.

I have run those commands including a few others located below here:

```
**bo@bo-MacBookPro:~$ iwconfig**

eth0      no wireless extensions.


wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
lo        no wireless extensions.


[B]bo@bo-MacBookPro:~$ lspci -vvnn | grep -A 9 Network
[/B][COLOR=#ff0000]02:00.0 Network controller [0280]: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller [14e4:432b] (rev 01)
[/COLOR]    Subsystem: Apple Inc. AirPort Extreme [106b:008d]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort+ <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 256 bytes
    Interrupt: pin A routed to IRQ 21
    Region 0: Memory at d3200000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: wl


[B]bo@bo-MacBookPro:~$ lsmod
[/B]Module                  Size  Used by
bnep                   20480  2 
rfcomm                 69632  8 
nls_iso8859_1          16384  1 
[COLOR=#ff0000]wl                   6369280  0 
[/COLOR]nouveau              1368064  4 
snd_hda_codec_hdmi     53248  3 
mxm_wmi                16384  1 nouveau
snd_hda_codec_cirrus    20480  1 
snd_hda_codec_generic    69632  1 snd_hda_codec_cirrus
wmi                    20480  2 mxm_wmi,nouveau
ttm                    94208  1 nouveau
drm_kms_helper        126976  1 nouveau
drm                   344064  7 ttm,drm_kms_helper,nouveau
i2c_algo_bit           16384  1 nouveau
uvcvideo               90112  0 
snd_hda_intel          32768  3 
coretemp               16384  0 
snd_hda_controller     32768  1 snd_hda_intel
snd_hda_codec         143360  5 snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller,snd_hda_codec_cirrus
kvm_intel             151552  0 
kvm                   479232  1 kvm_intel
hid_apple              16384  0 
hid_appleir            16384  0 
hid_generic            16384  0 
videobuf2_vmalloc      16384  1 uvcvideo
joydev                 20480  0 
snd_hwdep              20480  1 snd_hda_codec
cfg80211              524288  1 wl
videobuf2_memops       16384  1 videobuf2_vmalloc
videobuf2_core         53248  1 uvcvideo
snd_pcm               106496  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller
applesmc               20480  0 
btusb                  40960  0 
snd_seq_midi           16384  0 
v4l2_common            16384  1 videobuf2_core
videodev              159744  3 uvcvideo,v4l2_common,videobuf2_core
bluetooth             491520  22 bnep,btusb,rfcomm
input_polldev          16384  1 applesmc
snd_seq_midi_event     16384  1 snd_seq_midi
media                  24576  2 uvcvideo,videodev
bcm5974                20480  0 
usbhid                 53248  0 
snd_rawmidi            32768  1 snd_seq_midi
snd_seq                65536  2 snd_seq_midi_event,snd_seq_midi
hid                   110592  4 hid_generic,usbhid,hid_appleir,hid_apple
shpchp                 40960  0 
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_pcm,snd_seq
snd                    86016  17 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_hda_codec_cirrus
soundcore              16384  2 snd,snd_hda_codec
sbs                    16384  0 
parport_pc             32768  0 
sbshc                  16384  1 sbs
ppdev                  20480  0 
apple_bl               16384  0 
video                  20480  1 nouveau
lp                     20480  0 
mac_hid                16384  0 
parport                45056  3 lp,ppdev,parport_pc
uas                    24576  0 
usb_storage            69632  1 uas
tg3                   167936  0 
firewire_ohci          40960  0 
firewire_core          69632  1 firewire_ohci
ptp                    20480  1 tg3
pps_core               20480  1 ptp
crc_itu_t              16384  1 firewire_core
ahci                   36864  3 
libahci                32768  1 ahci

[B]bo@bo-MacBookPro:~$ rfkill list all
[/B]0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


[B]bo@bo-MacBookPro:~$ sudo iwlist wlan0 scan
[/B]wlan0     No scan results

[B]bo@bo-MacBookPro:~$ sudo lshw -C network
[/B]  *-network               
       description: Wireless interface
[COLOR=#ff0000]       product: BCM4322 802.11a/b/g/n Wireless LAN Controller
[/COLOR]       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: d8:a2:5e:92:5f:36
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
  [COLOR=#ff0000]     configuration: broadcast=yes **driver=wl0** driverversion=6.30.223.248 (r487574) latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:21 memory:d3200000-d3203fff[/COLOR]
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5764M Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 10
       serial: c4:2c:03:1a:81:78
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.137 firmware=5764m-v3.38 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:27 memory:d3100000-d310ffff





```

I have bolded my main commands and other stuff to make it easier to read.

Thank you.


Since my original post. I have downgraded to a new install of 14.04 to see if that would fix it. It didn't. 

At one point or another, I was able to 'kinda' get my wireless to scan and see SSIDs but with no connect ability (won't actually connect). But only when I reset and set my modprobe with b43 or wl and not through natural means.


I have USB drives loaded with 14.04 and 15.04 so I can at a moment re-install or what not. I am currently out of the house. I will install synaptic later so I can manage my bcm packages later so I can follow your instructions.


I thank you again man. I'm on my wits end following all the instructions online trying to get it working including making sure to remove all installations of b43 or fwcutter after I test it to make sure it doesn't have compatiability issues

---

### Post by chili555 on 2015-09-03
We see nothing wrong and therefor fixable except that there are no scan results. Let's dig deeper:```
dmesg | grep -e wl -e 02:00
```I love and hate the old 'perfect except it doesn't work' problem.

---

### Post by Bowei_Zhao on 2015-09-03
> **chili555 said:**
> We see nothing wrong and therefor fixable except that there are no scan results. Let's dig deeper:```
dmesg | grep -e wl -e 02:00
```I love and hate the old 'perfect except it doesn't work' problem.


Thank you for taking the time to help me ):P

```
bo@bo-MacBookPro:~/hybrid_wl$ dmesg | grep -e wl -e 2:00
[    0.148409] pci 0000:02:00.0: [14e4:432b] type 00 class 0x028000
[    0.148431] pci 0000:02:00.0: reg 0x10: [mem 0xd3200000-0xd3203fff 64bit]
[    0.148549] pci 0000:02:00.0: supports D1 D2
[    0.148551] pci 0000:02:00.0: PME# supported from D0 D3hot D3cold
[    0.148581] pci 0000:02:00.0: System wakeup disabled by ACPI
[   16.402785] wl: module license 'MIXED/Proprietary' taints kernel.
[   16.409391] wl: module verification failed: signature and/or  required key missing - tainting kernel
[   16.645079] wlan0: Broadcom BCM432b 802.11 Hybrid Wireless Controller 6.30.223.248 (r487574)
[   63.015480] ERROR @wl_notify_scan_status : wlan0 Scan_results error (-22)
[   96.015432] ERROR @wl_notify_scan_status : wlan0 Scan_results error (-22)
[  139.024178] ERROR @wl_notify_scan_status : wlan0 Scan_results error (-22)
[  192.015899] ERROR @wl_notify_scan_status : wlan0 Scan_results error (-22)
[  255.015533] ERROR @wl_notify_scan_status : wlan0 Scan_results error (-22)
[  318.012041] ERROR @wl_notify_scan_status : wlan0 Scan_results error (-22)
[  381.015611] ERROR @wl_notify_scan_status : wlan0 Scan_results error (-22)
[  444.015490] ERROR @wl_notify_scan_status : wlan0 Scan_results error (-22)
[  507.019471] ERROR @wl_notify_scan_status : wlan0 Scan_results error (-22)
[  570.015559] ERROR @wl_notify_scan_status : wlan0 Scan_results error (-22)
[  633.024153] ERROR @wl_notify_scan_status : wlan0 Scan_results error (-22)
[  696.021483] ERROR @wl_notify_scan_status : wlan0 Scan_results error (-22)
[  759.020067] ERROR @wl_notify_scan_status : wlan0 Scan_results error (-22)
[  799.582118] ERROR @wl_dev_intvar_get : error (-1)
[  799.582123] ERROR @wl_cfg80211_get_tx_power : error (-1)
[  822.021564] ERROR @wl_notify_scan_status : wlan0 Scan_results error (-22)
[  861.205154] ERROR @wl_dev_intvar_get : error (-1)
[  861.205168] ERROR @wl_cfg80211_get_tx_power : error (-1)
[  885.025596] ERROR @wl_notify_scan_status : wlan0 Scan_results error (-22)
[  948.019475] ERROR @wl_notify_scan_status : wlan0 Scan_results error (-22)
[ 1011.015604] ERROR @wl_notify_scan_status : wlan0 Scan_results error (-22)
[ 1074.024238] ERROR @wl_notify_scan_status : wlan0 Scan_results error (-22)
[ 1137.028181] ERROR @wl_notify_scan_status : wlan0 Scan_results error (-22)
[ 1200.024119] ERROR @wl_notify_scan_status : wlan0 Scan_results error (-22)
[ 1263.028235] ERROR @wl_notify_scan_status : wlan0 Scan_results error (-22)
[ 1326.025703] ERROR @wl_notify_scan_status : wlan0 Scan_results error (-22)
[ 1389.028141] ERROR @wl_notify_scan_status : wlan0 Scan_results error (-22)
bo@bo-MacBookPro:~/hybrid_wl$ 

```

but yeah. I have been googing non-stop for hours and am baffled as to how it isn't working for me. Especially considering how many clean installs I have come from.

Could cfg80211 have anything to do with it?

---

### Post by Bowei_Zhao on 2015-09-03
I parsed more stuff and it is below from the other sticked post on this forum.

I bolded some parts I think may be important. I omitted my ip and other identifying info. 

```


Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.19.0-26-generic #28~14.04.1-Ubuntu SMP Wed Aug 12 14:09:17 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

[B]02:00.0 Network controller [0280]: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller [14e4:432b] (rev 01)
    Subsystem: Apple Inc. AirPort Extreme [106b:008d]
    Kernel driver in use: wl[/B]

03:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5764M Gigabit Ethernet PCIe [14e4:1684] (rev 10)
    Subsystem: Broadcom Corporation NetXtreme BCM5764M Gigabit Ethernet PCIe [14e4:1684]
    Kernel driver in use: tg3

##### lsusb #############################

Bus 002 Device 002: ID 05ac:8403 Apple, Inc. Internal Memory Card Reader
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 006: ID 05ac:8213 Apple, Inc. Bluetooth Host Controller
Bus 004 Device 005: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 004 Device 004: ID 05ac:8242 Apple, Inc. Built-in IR Receiver
Bus 004 Device 003: ID 17ef:601c Lenovo 
Bus 004 Device 002: ID 05ac:0236 Apple, Inc. Internal Keyboard/Trackpad (ANSI)
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 05ac:8507 Apple, Inc. Built-in iSight
Bus 001 Device 002: ID 05c6:676a Qualcomm, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
4: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

**wl                   6369280  0 **
**cfg80211              524288  1 wl**
mxm_wmi                16384  1 nouveau
wmi                    20480  2 mxm_wmi,nouveau

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
          Interrupt:20 

usb0      Link encap:Ethernet  HWaddr <MAC 'usb0' [IF]>  
               -omitted-
          inet6 addr: fe80::<IP6 'usb0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14877 errors:2 dropped:0 overruns:0 frame:2
          TX packets:13480 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11074399 (11.0 MB)  TX bytes:2367780 (2.3 MB)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet6 addr: fe80::<IP6 'wlan0' [IF]>/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:2637
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:21 

##### iwconfig ##########################

eth0      no wireless extensions.

usb0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### network managers ##################

Installed:

    NetworkManager

Running:

root       843     1  0 16:52 ?        00:00:00 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             disconnected
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 

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

- Device: usb0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            rndis_host
  State:             connected
  Default:           yes
  HW Address:        <MAC 'usb0' [IF]>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    -omitted-

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

[[/etc/NetworkManager/system-connections/The Promised LAN]] (600 root)
[connection] id=The Promised LAN | type=802-11-wireless
[802-11-wireless] ssid=The Promised LAN | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=ignore

##### iwlist channels ###################

eth0      no frequency information.

usb0      no frequency information.

lo        no frequency information.

wlan0     32 channels in total; available frequencies :
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
          Channel 32 : 5.16 GHz
          Channel 34 : 5.17 GHz
          Channel 36 : 5.18 GHz
          Channel 38 : 5.19 GHz
          Channel 40 : 5.2 GHz
          Channel 42 : 5.21 GHz
          Channel 44 : 5.22 GHz
          Channel 46 : 5.23 GHz
          Channel 48 : 5.24 GHz
          Channel 50 : 5.25 GHz
          Channel 52 : 5.26 GHz
          Channel 54 : 5.27 GHz
          Channel 56 : 5.28 GHz
          Channel 58 : 5.29 GHz
          Channel 60 : 5.3 GHz
          Channel 62 : 5.31 GHz
          Channel 64 : 5.32 GHz
          Channel 66 : 5.33 GHz

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

usb0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     No scan results

##### module infos ######################

[wl]
**filename:       /lib/modules/3.19.0-26-generic/updates/dkms/wl.ko**
license:        MIXED/Proprietary
srcversion:     9A49255BA90267D99664757
**depends:        cfg80211**
vermagic:       3.19.0-26-generic SMP mod_unload modversions 
parm:           passivemode:int
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string
[B]
[cfg80211]
filename:       /lib/modules/3.19.0-26-generic/kernel/net/wireless/cfg80211.ko[/B]
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     F28307769349A31F4B24FC2
depends:        
intree:         Y
vermagic:       3.19.0-26-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        ED:83:39:FD:1A:2F:8D:C0:EF:DC:5D:F7:12:9D:FB:17:0A:6F:6D:AB
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

**[cfg80211]**
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

lp
rtc
[COLOR=#ff0000]**wl**[/COLOR]

##### modprobe options ##################

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[B][/etc/modprobe.d/blacklist-bcm43.conf]
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist brcm80211
blacklist brcmfmac
blacklist brcmsmac
blacklist bcma[/B]

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

[B][/etc/modprobe.d/broadcom-sta-dkms.conf]
blacklist b43
blacklist b43legacy
blacklist b44
blacklist bcma
blacklist brcm80211
blacklist brcmsmac
blacklist ssb[/B]

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
# PCI device 0x14e4:0x1684 (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x14e4:0x432b (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[   14.478561] wl: module license 'MIXED/Proprietary' taints kernel.
**[   14.491595] wl: module verification failed: signature and/or  required key missing - tainting kernel**
[   14.552196] wlan0: Broadcom BCM432b 802.11 Hybrid Wireless Controller 6.30.223.248 (r487574)
[   63.022686] ERROR @wl_notify_scan_status : wlan0 Scan_results error (-22) (repeated 28 times)
**[ 1756.884828] wlan0: Broadcom BCM432b 802.11 Hybrid Wireless Controller 6.30.223.248 (r487574)**
[ 1757.875771] ERROR @wl_notify_scan_status : wlan0 Scan_results error (-22) (repeated 13 times)
[ 2380.500711] ERROR @wl_dev_intvar_get : error (-1)
[ 2381.677303] ERROR @wl_notify_scan_status : wlan0 Scan_results error (-22)

########## wireless info END ############
```

I appreciate it. Thank you

The stuff with the CFG80211, system kernal loading, modprobe, and module stuff installed are things I am unsure of.

I am currently using a tethered phone to access the internet with the computer which is why you will see an additional USB device in there giving internet. All ethernet plugs are taken up.

Thanks again

---

### Post by chili555 on 2015-09-03
> The stuff with the CFG80211, system kernal loading, modprobe, and module stuff installed are things I am unsure of.All pretty normal.

What is abnormal and, I suspect, a clue, is this stuff:> [ 1757.875771] ERROR @wl_notify_scan_status : wlan0 Scan_results error (-22) (repeated 13 times)
[ 2380.500711] ERROR @wl_dev_intvar_get : error (-1)
[ 2381.677303] ERROR @wl_notify_scan_status : wlan0 Scan_results error (-22)
I haven't found a fix yet. Googling...

---

### Post by Bowei_Zhao on 2015-09-03
> **chili555 said:**
> All pretty normal.

What is abnormal and, I suspect, a clue, is this stuff:I haven't found a fix yet. Googling...


Thank you.

I am at the moment also trying to get my Desktop ethernet working.

I just installed Linux Ubuntu 15.04 on my desktop. But unlike the laptop, it's ethernet isn't working... -_-

---

### Post by chili555 on 2015-09-03
What is the ethernet card?```
lspci -nn | grep 0200
```

---

### Post by Bowei_Zhao on 2015-09-03
> **chili555 said:**
> What is the ethernet card?```
lspci -nn | grep 0200
```


I have posted a new thread on my ethernet desktop problems. I think this will make it easier for people to also solve their problems. 

[http://ubuntuforums.org/showthread.php?t=2293272&p=13349719#post13349719](http://ubuntuforums.org/showthread.php?t=2293272&p=13349719#post13349719)

Did you find anything on your end with the Macbook's Broadcom issue? I've been trying other fixes to no avail.

EDIT:

I have solved my ethernet issue in the other thread. It was the drivers.

Now..it's still my Mac having issues with wifi on Ubuntu

EDIT 2:
I've read...honestly so many forums and tried so many things at this point
[http://ubuntuforums.org/showthread.php?t=2173985](http://ubuntuforums.org/showthread.php?t=2173985)

I've read through this and others. Here you said others had issues with the BCM4322.

I'll try more of course. But if push comes to shove, I'll get a wireless adapter i know is compatible with linux

---

### Post by Bowei_Zhao on 2015-09-04
Trying to use B43 drivers and no dice with that. I'm looking up threads on scanning issues but none of the fixes seem to be what i'm looking for.

---

### Post by chili555 on 2015-09-05
As far as I know, bcmwl-kernel-source is the only driver suite that works with your device.

I'm afraid I have but three suggestions remaining. First, is the version of bcmwl-kermel-source that you have the latest?```
sudo dpkg -s bcmwl-kernel-source
```We hope we see:```
Version: [COLOR="#FF0000"]6.30.223.248[/COLOR]+bdcom-0ubuntu[COLOR="#FF0000"]2[/COLOR]
```If not, let's work out how to upgrade.

Second, we might try a later kernel version from here: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.0.9-wily/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.0.9-wily/)

Finally, you might consider the solution at post #7  here: [https://bbs.archlinux.org/viewtopic.php?id=193779](https://bbs.archlinux.org/viewtopic.php?id=193779)

I regret I haven't any further ideas.

---

### Post by Bowei_Zhao on 2015-09-05
> **chili555 said:**
> As far as I know, bcmwl-kernel-source is the only driver suite that works with your device.

I'm afraid I have but three suggestions remaining. First, is the version of bcmwl-kermel-source that you have the latest?```
sudo dpkg -s bcmwl-kernel-source
```We hope we see:```
Version: [COLOR=#FF0000]6.30.223.248[/COLOR]+bdcom-0ubuntu[COLOR=#FF0000]2[/COLOR]
```If not, let's work out how to upgrade.

Second, we might try a later kernel version from here: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.0.9-wily/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.0.9-wily/)

Finally, you might consider the solution at post #7  here: [https://bbs.archlinux.org/viewtopic.php?id=193779](https://bbs.archlinux.org/viewtopic.php?id=193779)

I regret I haven't any further ideas.


```

[COLOR=#333333][FONT=sans-serif]I've spent over 80 hours trying to get my PCE AC 68 to work on Windows 7, Ubuntu, and Mint, with no success.[/FONT][/COLOR]
[COLOR=#333333][FONT=sans-serif]I have flawless wireless now. Here is my solution (I used an ethernet cord to install Mint, to update Mint via Update Manager [I have learned to stay away from apt-get update], and when plugging in the wireless adapter. I didn't try it any other way, but after all this, I do not need an ethernet cord):[/FONT][/COLOR]

[LIST=1]
[*]Throw away the PCE AC 68.

[*]Buy [TP-LINK TL-WN821N Wireless N300 USB Adapter]("http://amzn.com/B002T4D3M2").

[*]Wait for it to arrive

[*]Plug it in.
[/LIST]

```

Lol.

I did that last night. Bought a Panda Wireless adapter that is compatible with Linux.

I''ll update my original posts for any other poor souls with my predicament to not waste their time.

Thanks again Chili.

---

