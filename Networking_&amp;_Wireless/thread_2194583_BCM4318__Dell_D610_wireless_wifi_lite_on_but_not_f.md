---
title: "BCM4318 / Dell D610 wireless wifi lite on but not finding network"
date: 2013-12-19
forum: Networking &amp; Wireless
---

### Post by wa3scm on 2013-12-19
12.04 lts installed Dell D610 with BCM4318 [AIR FORCE ONE 54G] wireless lan controller

wireless  worked well under Windows XP.  Hard drive failed so installed 12.04 on  new drive.  Could never get the wifi light to come on with FN +F2 with  initial installation or after installing several different drivers.  

I found a thread (can not refind it) on this forum which gave terminal code & removed drivers and dkms then installed new drivers and after reboot I had the wifi light lit.  I was able to configure wireless  WAN0 with infrastructure, ssid, wep2, password but the wireless card  does not connect automatically like the LAN cable does.

Is there something more I need to do to force wifi to look for networks? There are plenty in the neighborhood plus my linksys wireless router which I am trying to connect.

Thanks!

---

### Post by wa3scm on 2013-12-19
After reading how to post on this thread:

Dell Latitude D610 with new hard drive and Ubuntu 12.04 lts

```
ds@WA3SCM-LINUX:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express (rev 01)
03:01.0 CardBus bridge: Texas Instruments PCI6515 Cardbus Controller
03:01.5 Communication controller: Texas Instruments PCI6515 SmartCard Controller
03:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
```
```
ds@WA3SCM-LINUX:~$ lsusb
Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 003: ID 1058:0701 Western Digital Technologies, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 046d:c51b Logitech, Inc. V220 Cordless Optical Mouse for Notebooks
```


```
ds@WA3SCM-LINUX:~$ lspci -nn | grep 'Broadcom'
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express [14e4:1677] (rev 01)
03:03.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
```


```
ds@WA3SCM-LINUX:~$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:15:c5:24:6a:7d  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::215:c5ff:fe24:6a7d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:49176 errors:0 dropped:0 overruns:0 frame:0
          TX packets:47005 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:43381673 (43.3 MB)  TX bytes:7933744 (7.9 MB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:3601 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3601 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:269816 (269.8 KB)  TX bytes:269816 (269.8 KB)

wlan0     Link encap:Ethernet  HWaddr 00:16:ce:6b:3b:a4  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```


```
ds@WA3SCM-LINUX:~$ iwconfig
wlan0     IEEE 802.11bg  ESSID(smiley was here)ff/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr(smiley was here)ff   Fragment thr(smiley was here)ff
          Power Management(smiley was here)ff
          
lo        no wireless extensions.

eth1      no wireless extensions.
```


```
ds@WA3SCM-LINUX:~$ iwconfig wlan0
wlan0     IEEE 802.11bg  ESSID(smiley was here)ff/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr(smiley was here)ff   Fragment thr(smiley was here)ff
          Power Management(smiley was here)ff
```


```
ds@WA3SCM-LINUX:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12617  1 
bnep                   17919  2 
rfcomm                 38400  0 
bluetooth             211586  10 bnep,rfcomm
arc4                   12509  2 
snd_intel8x0           33458  2 
snd_ac97_codec        110254  1 snd_intel8x0
b43                   364688  0 
joydev                 17329  0 
ac97_bus               12670  1 snd_ac97_codec
snd_pcm                85934  2 snd_intel8x0,snd_ac97_codec
hid_generic            12484  0 
snd_seq_midi           13132  0 
i915                  554735  3 
snd_rawmidi            25157  1 snd_seq_midi
mac80211              546065  1 b43
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51593  2 snd_seq_midi,snd_seq_midi_event
usbhid                 46125  0 
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14137  3 snd_seq_midi,snd_rawmidi,snd_seq
hid                    87362  2 hid_generic,usbhid
cfg80211              454468  2 b43,mac80211
pcmcia                 39854  0 
drm_kms_helper         47749  1 i915
drm                   233935  4 i915,drm_kms_helper
dell_laptop            17209  0 
gpio_ich               13278  0 
yenta_socket           27427  0 
psmouse                82769  0 
snd                    57014  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
microcode              18433  0 
pcmcia_rsrc            18367  1 yenta_socket
soundcore              12600  1 snd
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
i2c_algo_bit           13316  1 i915
lpc_ich                17048  0 
dcdbas                 14065  1 dell_laptop
serio_raw              13031  0 
snd_page_alloc         18398  2 snd_intel8x0,snd_pcm
mac_hid                13077  0 
bcma                   39810  1 b43
ppdev                  12849  0 
video                  19116  1 i915
parport_pc             27612  1 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
usb_storage            48053  1 
ssb                    51554  1 b43
tg3                   150967  0 
ptp                    18232  1 tg3
pps_core               13736  1 ptp
```



lsmod | grep "wlan_module_name" ==== not performed as do not know module name ===


dmesg gigantic... looked thru to find what I thought might be related to wifi

as follows:
```
[   17.451572] Bluetooth: Core ver 2.16
[   17.451603] NET: Registered protocol family 31
[   17.451606] Bluetooth: HCI device and connection manager initialized
[   17.452523] Bluetooth: HCI socket layer initialized
[   17.452528] Bluetooth: L2CAP socket layer initialized
[   17.452536] Bluetooth: SCO socket layer initialized
[   17.522769] type=1400 audit(1387470543.777:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=853 comm="apparmor_parser"
[   17.654138] Bluetooth: RFCOMM TTY layer initialized
[   17.654156] Bluetooth: RFCOMM socket layer initialized
[   17.654159] Bluetooth: RFCOMM ver 1.11
[   17.852981] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   17.852988] Bluetooth: BNEP filters: protocol multicast
[   17.853001] Bluetooth: BNEP socket layer initialized
[   21.142028] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[   21.142646] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[   21.304047] b43-phy0: Loading firmware version 508.1084 (2009-01-14 01:32:01)
[   21.368963] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   21.370714] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   22.489211] audit_printk_skb: 3 callbacks suppressed
[   22.489217] type=1400 audit(1387470548.741:13): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=925 comm="apparmor_parser"
[   22.489737] type=1400 audit(1387470548.741:14): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper//chromium_browser" pid=925 comm="apparmor_parser"
[   22.493730] type=1400 audit(1387470548.745:15): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=928 comm="apparmor_parser"
[   22.494366] type=1400 audit(1387470548.745:16): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=928 comm="apparmor_parser"
[   22.494727] type=1400 audit(1387470548.745:17): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=928 comm="apparmor_parser"
[   22.742363] tg3 0000:02:00.0 eth1: Link is up at 100 Mbps, full duplex
[   22.742370] tg3 0000:02:00.0 eth1: Flow control is on for TX and on for RX
[   22.742391] IPv6: ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[   22.864603] type=1400 audit(1387470549.117:18): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=929 comm="apparmor_parser"
[   22.873043] type=1400 audit(1387470549.125:19): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince//launchpad_integration" pid=929 comm="apparmor_parser"
[   22.875005] type=1400 audit(1387470549.125:20): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince//sanitized_helper" pid=929 comm="apparmor_parser"
[   22.876664] type=1400 audit(1387470549.129:21): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=929 comm="apparmor_parser"
[   22.881146] type=1400 audit(1387470549.133:22): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer//launchpad_integration" pid=929 comm="apparmor_parser"
[  356.612467] audit_printk_skb: 24 callbacks suppressed
[  356.612478] type=1400 audit(1387470882.865:31): apparmor="DENIED" operation="capable" parent=1 profile="/usr/sbin/cupsd" pid=880 comm="cupsd" pid=880 comm="cupsd" capability=36  capname="block_suspend"
[ 8089.902854] tg3 0000:02:00.0 eth1: Link is down
[ 8094.058249] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 8439.823022] tg3 0000:02:00.0 eth1: Link is up at 100 Mbps, full duplex
[ 8439.823035] tg3 0000:02:00.0 eth1: Flow control is on for TX and on for RX
[ 8439.823063] IPv6: ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
```



```
ds@WA3SCM-LINUX:~$ sudo lshw -C network
[sudo] password for ds: 
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5751 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 01
       serial: 00:15:c5:24:6a:7d
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.128 duplex=full firmware=5751-v3.29a ip=192.168.1.103 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:16 memory:dfdf0000-dfdfffff
  *-network
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:03:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:17 memory:dfcfe000-dfcfffff
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:16:ce:6b:3b:a4
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=3.8.0-35-generic firmware=508.1084 link=no multicast=yes wireless=IEEE 802.11bg
ds@WA3SCM-LINUX:~$ 
```

```
ds@WA3SCM-LINUX:~$ iwlist scan
wlan0     No scan results

lo        Interface doesn't support scanning.

eth1      Interface doesn't support scanning.
```


```
ds@WA3SCM-LINUX:~$ sudo iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:16:B6:25:88:B2
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key(smiley was here)
Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000477e98aa4
                    Extra: Last beacon: 0ms ago
                    IE: Unknown: 000A4241434B535452454554
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180200F4000000
```



```
ds@WA3SCM-LINUX:~$ lsb_release -d
Description:    Ubuntu 12.04.3 LTS
```



```
ds@WA3SCM-LINUX:~$ uname -mr
3.8.0-35-generic i686
```



```
ds@WA3SCM-LINUX:~$ sudo service networking restart
stop: Unknown instance: 
networking stop/waiting
ds@WA3SCM-LINUX:~$ 
```

Note: smileys appeared in the text above preventing submission so were replaced with "(smiley was here)"

My issue is that the wireless does not connect.

I have messed with this issue for a long time.  Unspecifically as best as I can remember:

Lost hard drive
Made bootable ubuntu usb
Finally got ubuntu 12.04 to load onto hard drive
Got cable internet working with ease
Began learning Ubuntu
Worked at getting wireless working
  Read all kinds of advice
  Installed several different drivers
  None of them allowed the wifi light to come on
Put it on the shelf to cool off
Rejoined Ubuntu Forum
  Found a thread that gave terminal instructions to install B43
  Can not find that thread again
  After boot the D610 wifi light was lit up and I could configure WLAN0,
    but it does not connect.
  I dont know were to look to see if it is seeing any available networks.

Thanks for your help.

---

### Post by wa3scm on 2013-12-19
Found the thread and what I performed that turned the wifi light on follows:

```


Hi, please do:
 	Code:
 	sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source 
then:
 	Code:
 	sudo apt-get install b43-fwcutter firmware-b43-installer 
watch for errors, then unlug your wired connection and reboot.
Thanks 				

```

---

### Post by wa3scm on 2013-12-19
```




*************** info trace ***************

***** uname -a *****

Linux WA3SCM-LINUX 3.8.0-35-generic #50~precise1-Ubuntu SMP Wed Dec 4 17:28:45 UTC 2013 i686 i686 i386 GNU/Linux

***** lsb_release *****

Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.3 LTS
Release:    12.04
Codename:    precise

***** lspci *****

02:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express [14e4:1677] (rev 01)
    Subsystem: Dell Latitude D610 [1028:0182]
    Kernel driver in use: tg3
--
03:03.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
    Subsystem: Dell Wireless 1370 WLAN Mini-PCI Card [1028:0005]
    Kernel driver in use: b43-pci-bridge

***** lsusb *****

Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 003: ID 1058:0701 Western Digital Technologies, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 046d:c51b Logitech, Inc. V220 Cordless Optical Mouse for Notebooks

***** PCMCIA Card Info *****

PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255

***** iwconfig *****

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

***** rfkill *****

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

***** lsmod *****

b43                   364688  0 
mac80211              546065  1 b43
cfg80211              454468  2 b43,mac80211
bcma                   39810  1 b43
ssb                    51554  1 b43

***** nm-tool *****

NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            b43
  State:             disconnected
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


- Device: eth1  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.103
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             75.75.76.76
    DNS:             75.75.75.75



***** NetworkManager.state *****

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

***** NetworkManager.conf *****

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false

***** interfaces *****

auto lo
iface lo inet loopback


***** iwlist *****

wlan0     No scan results


***** resolv.conf *****

nameserver 127.0.0.1
search hsd1.pa.comcast.net

***** blacklist *****

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

***** modinfo *****

filename:       /lib/modules/3.8.0-35-generic/kernel/drivers/net/wireless/b43/b43.ko
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
srcversion:     F6F97440A9DA6418F4C2856
alias:          bcma:m04BFid0812rev1Dcl*
alias:          bcma:m04BFid0812rev11cl*
alias:          ssb:v4243id0812rev10*
alias:          ssb:v4243id0812rev0F*
alias:          ssb:v4243id0812rev0D*
alias:          ssb:v4243id0812rev0C*
alias:          ssb:v4243id0812rev0B*
alias:          ssb:v4243id0812rev0A*
alias:          ssb:v4243id0812rev09*
alias:          ssb:v4243id0812rev07*
alias:          ssb:v4243id0812rev06*
alias:          ssb:v4243id0812rev05*
depends:        ssb,mac80211,bcma,cfg80211
intree:         Y
vermagic:       3.8.0-35-generic SMP mod_unload modversions 686 
parm:           bad_frames_preempt:enable(1) / disable(0) Bad Frames Preemption (int)
parm:           fwpostfix:Postfix for the .fw files to load. (string)
parm:           hwpctl:Enable hardware-side power control (default off) (int)
parm:           nohwcrypt:Disable hardware encryption. (int)
parm:           hwtkip:Enable hardware tkip. (int)
parm:           qos:Enable QOS support (default on) (int)
parm:           btcoex:Enable Bluetooth coexistence (default on) (int)
parm:           verbose:Log message verbosity: 0=error, 1=warn, 2=info(default), 3=debug (int)
parm:           pio:Use PIO accesses by default: 0=DMA, 1=PIO (int)

filename:       /lib/modules/3.8.0-35-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     F7A1658A8CB1D58E3D347C1
alias:          pci:v000014E4d00004727sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004359sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004358sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004357sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004353sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004331sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000A8D8sv*sd*bc*sc*i*
alias:          pci:v000014E4d00000576sv*sd*bc*sc*i*
depends:        
intree:         Y
vermagic:       3.8.0-35-generic SMP mod_unload modversions 686 

filename:       /lib/modules/3.8.0-35-generic/kernel/drivers/ssb/ssb.ko
license:        GPL
description:    Sonics Silicon Backplane driver
srcversion:     14621F6EC014F731244437C
alias:          pci:v000014E4d00004350sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000432Csv*sd*bc*sc*i*
alias:          pci:v000014E4d0000432Bsv*sd*bc*sc*i*
alias:          pci:v000014E4d00004329sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004328sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004325sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004324sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000A8D6sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004322sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004321sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004320sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004319sv*sd*bc*sc*i*
alias:          pci:v000014A4d00004318sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004318sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004315sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004312sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004311sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004307sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004306sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004301sv*sd*bc*sc*i*
depends:        
intree:         Y
vermagic:       3.8.0-35-generic SMP mod_unload modversions 686 


***** udev rules *****

# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0 (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0 (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1e.0/0000:03:03.0/ssb0:0 (b43-pci-bridge)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

***** dmesg *****

[    1.664097] ssb: Found chip with id 0x4318, rev 0x02 and package 0x02
[    1.664110] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x0D, vendor 0x4243)
[    1.664118] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x09, vendor 0x4243)
[    1.664125] ssb: Core 2 found: PCI (cc 0x804, rev 0x0C, vendor 0x4243)
[    1.664133] ssb: Core 3 found: PCMCIA (cc 0x80D, rev 0x07, vendor 0x4243)
[    1.704125] ssb: Sonics Silicon Backplane found on PCI device 0000:03:03.0
[   11.386715] b43-phy0: Broadcom 4318 WLAN found (core revision 9)
[   11.428043] b43-phy0: Found PHY: Analog 3, Type 2 (G), Revision 7
[   21.142028] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[   21.142646] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[   21.304047] b43-phy0: Loading firmware version 508.1084 (2009-01-14 01:32:01)
[   21.368963] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   21.370714] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   22.742363] tg3 0000:02:00.0 eth1: Link is up at 100 Mbps, full duplex
[   22.742370] tg3 0000:02:00.0 eth1: Flow control is on for TX and on for RX
[   22.742391] IPv6: ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[ 8089.902854] tg3 0000:02:00.0 eth1: Link is down
[ 8094.058249] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 8439.823022] tg3 0000:02:00.0 eth1: Link is up at 100 Mbps, full duplex
[ 8439.823035] tg3 0000:02:00.0 eth1: Flow control is on for TX and on for RX
[ 8439.823063] IPv6: ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready

****************** done ******************



```

---

### Post by wa3scm on 2013-12-22
Dell D610
Ubuntu 12.04 lts
Wireless Broadcom B43 Air Force One, BCM4318, 14e4:4318

These 3 did not work:
Broadcom STA Drivers
Firmware-b43-installer/b43-fwcutter
ndiswrapper

google search sent me to linuxquestions*org
I registered and was required to post a self introduction which included
 that I was trying to get bcm4318 working...

Soon a simple reply "Try sudo apt-get install linux-firmware-nonfree"

google search on linux-firmware-nonfree took me to sites with instructions hints and kinks
One was [www.ubuntuupdates.org/package/core/precise/multiverse/updates/linux-firmware-nonfree]("http://www.ubuntuupdates.org/package/core/precise/multiverse/updates/linux-firmware-nonfree").

Simply stated:
download base1.11 as .deb extensions
right click base
choose open with Ubuntu Software Center
choose Install
Reboot
Right click wireless router icon which now appears on top menu bar
Mess about connecting and setting up network in some reasonable fashion.
It is that easy (in Ubuntu terms)

---

