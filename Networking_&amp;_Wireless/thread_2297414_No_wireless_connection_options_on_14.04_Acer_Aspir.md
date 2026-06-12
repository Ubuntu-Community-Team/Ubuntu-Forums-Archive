---
title: "No wireless connection options on 14.04 Acer Aspire V15"
date: 2015-10-03
forum: Networking &amp; Wireless
---

### Post by Matus_Pikuliak on 2015-10-03
Hey guys,

I have recently purchased acer aspire v15 nitro (VN7 591G) with Qualcomm Atheros QCA61xA network card. However after I installed Ubuntu, there are no wireless networking options in network menu. After running lshw I have found that one network controller is unclaimed. What should I do to fix it? Thanks for your help.

This is my wireless-info.txt

```

########## wireless info START ##########

Report from: 03 Oct 2015 16:59 CEST +0200

Booted last: 03 Oct 2015 16:54 CEST +0200

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.13.0-65-generic #105-Ubuntu SMP Mon Sep 21 18:50:58 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

07:00.0 Network controller [0280]: Qualcomm Atheros Device [168c:003e] (rev 20)
    Subsystem: Lite-On Communications Inc Device [11ad:0804]

08:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:0123]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 005: ID 04f2:b474 Chicony Electronics Co., Ltd 
Bus 003 Device 004: ID 06cb:2970 Synaptics, Inc. 
Bus 003 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 003 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 003 Device 006: ID 04ca:3011 Lite-On Technology Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

acer_wmi               32522  0 
sparse_keymap          13948  1 acer_wmi
mxm_wmi                13021  1 nouveau
wmi                    19177  3 acer_wmi,mxm_wmi,nouveau
video                  19476  3 i915,acer_wmi,nouveau

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.0.102  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'eth0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5516 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3976 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6026712 (6.0 MB)  TX bytes:552626 (552.6 KB)

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

root       764     1  0 16:54 ?        00:00:00 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.0.102
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1

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

Region: Europe/Bratislava (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (6, 20)
    (2457 - 2482 @ 40), (6, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (6, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 160), (6, 20), PASSIVE-SCAN, NO-IBSS
    (5250 - 5330 @ 160), (6, 20), DFS, PASSIVE-SCAN, NO-IBSS
    (5490 - 5730 @ 160), (6, 20), DFS, PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

##### module infos ######################

##### module parameters #################

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
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

##### dmesg #############################

[    4.049971] r8169 0000:08:00.0 eth0: link down
[    4.050151] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready (repeated 2 times)
[    4.051452] r8169 0000:08:00.0 eth0: link down
[    6.896352] r8169 0000:08:00.0 eth0: link up
[    6.896360] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  133.316178] r8169 0000:08:00.0 eth0: link down
[  137.356953] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[  147.557354] r8169 0000:08:00.0 eth0: link up
[  147.557371] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready

########## wireless info END ############


```

---

### Post by praseodym on 2015-10-03
Hi,

the device is too new, the driver needs to be installed:

```
sudo apt-get install --reinstall build-essential linux-headers-$(uname -r) linux-headers-generic dkms
wget kernel.ubuntu.com/~adamlee/lp1383184/ath10k-dkms_1.1_all.deb
sudo dpkg -i ath10k-dkms_1.1_all.deb 
```
No errors occurred? Then reboot.

---

### Post by Matus_Pikuliak on 2015-10-03
Thanks, but it didnt work, there is still no option for wireless networking. Here is current status

```

########## wireless info START ##########

Report from: 03 Oct 2015 18:46 CEST +0200

Booted last: 03 Oct 2015 18:45 CEST +0200

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.13.0-65-generic #105-Ubuntu SMP Mon Sep 21 18:50:58 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

07:00.0 Network controller [0280]: Qualcomm Atheros Device [168c:003e] (rev 20)
    Subsystem: Lite-On Communications Inc Device [11ad:0804]

08:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:0123]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 005: ID 04f2:b474 Chicony Electronics Co., Ltd 
Bus 003 Device 004: ID 06cb:2970 Synaptics, Inc. 
Bus 003 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 003 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 003 Device 006: ID 04ca:3011 Lite-On Technology Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

acer_wmi               32522  0 
sparse_keymap          13948  1 acer_wmi
mxm_wmi                13021  1 nouveau
wmi                    19177  3 acer_wmi,mxm_wmi,nouveau
video                  19476  3 i915,acer_wmi,nouveau

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.0.102  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'eth0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5401 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3394 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6742516 (6.7 MB)  TX bytes:392562 (392.5 KB)

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

root       753     1  0 18:45 ?        00:00:00 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: eth0  [Auto Ethernet] ------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.0.102
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1

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

nl80211 not found.

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

##### module infos ######################

##### module parameters #################

##### /etc/modules ######################

lp
rtc

##### modprobe options ##################

[/etc/modprobe.d/ath10k-dkms.conf]
options ath10k_core skip_otp=1

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
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

##### dmesg #############################

[    2.212296] r8169 0000:08:00.0 eth0: link down (repeated 2 times)
[    2.212346] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready (repeated 2 times)
[    5.035383] r8169 0000:08:00.0 eth0: link up
[    5.035389] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready

########## wireless info END ############



```

---

### Post by Matus_Pikuliak on 2015-10-03
I updated kernel to 3.19 and installed the driver mentioned in comment above. Finally I can see wireless networks. However, I cant connect to them.

EDIT: To be more precise, I cant connect 99% of time. Sometime it just connects and wifi works normally. It seems to be separate issue, so I will create new thread.

---

### Post by praseodym on 2015-10-04
Lets check now:```


modinfo ath10k_pci
dmesg | grep ath
iwconfig
ifconfig -a
lsmod
cat /etc/resolv.conf
route -n
iwlist chan
sudo iwlist scan
```

---

### Post by Matus_Pikuliak on 2015-10-04
Thanks for the reply, but somehow, maybe apt-get update, it fixes itself and wireless is now working. Only problem is that it takes quite a while to connect to wifi. At start of system it can take 50 seconds, normally 20-ish. I found [a thread]("http://askubuntu.com/questions/472138/ubuntu-14-04-wireless-slow-to-start") with similar problem, only more severe. However I don't know if the solution there is right for my situation.

This is what comes from your commands:
```

piko@piko-Aspire-VN7-591G:~$ modinfo ath10k_pci
filename:       /lib/modules/3.19.0-30-generic/updates/dkms/ath10k_pci.ko
firmware:       ath10k/QCA6174/hw3.0/board.bin
firmware:       ath10k/QCA6174/hw3.0/firmware-5.bin
firmware:       ath10k/QCA6174/hw3.0/firmware-4.bin
firmware:       ath10k/QCA6174/hw2.1/board.bin
firmware:       ath10k/QCA6174/hw2.1/firmware-5.bin
firmware:       ath10k/QCA6174/hw2.1/firmware-4.bin
firmware:       ath10k/QCA988X/hw2.0/board.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-5.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-4.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-3.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-2.bin
firmware:       ath10k/QCA988X/hw2.0/firmware.bin
license:        Dual BSD/GPL
description:    Driver support for Atheros QCA988X PCIe devices
author:         Qualcomm Atheros
version:        backported from  () using backports 
srcversion:     51D77BB171261CA0793236B
alias:          pci:v0000168Cd0000003Esv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000003Csv*sd*bc*sc*i*
depends:        ath10k_core,compat
vermagic:       3.19.0-30-generic SMP mod_unload modversions 
parm:           irq_mode:0: auto, 1: legacy, 2: msi (default: 0) (uint)
parm:           reset_mode:0: auto, 1: warm only (default: 0) (uint)
piko@piko-Aspire-VN7-591G:~$ dmesg | grep ath
[    1.530116] Loaded X.509 cert 'Magrathea: Glacier signing key: 48a35745535d8d6f341b30c63c3aa38578743d0d'
[    2.872313] ath10k_pci 0000:07:00.0: pci irq msi-x interrupts 8 irq_mode 0 reset_mode 0
[    3.078349] ath10k_pci 0000:07:00.0: Direct firmware load for ath10k/cal-pci-0000:07:00.0.bin failed with error -2
[    3.078638] ath10k_pci 0000:07:00.0: Direct firmware load for ath10k/QCA6174/hw2.1/board-pci-168c:003e:11ad:0804.bin failed with error -2
[    3.078640] ath10k_pci 0000:07:00.0: failed to load spec board file, falling back to generic: -2
[    3.078855] ath10k_pci 0000:07:00.0: Direct firmware load for ath10k/QCA6174/hw2.1/firmware-5.bin failed with error -2
[    3.078857] ath10k_pci 0000:07:00.0: could not fetch firmware file 'ath10k/QCA6174/hw2.1/firmware-5.bin': -2
[    3.078862] ath10k_pci 0000:07:00.0: Direct firmware load for ath10k/QCA6174/hw2.1/firmware-4.bin failed with error -2
[    3.078864] ath10k_pci 0000:07:00.0: could not fetch firmware file 'ath10k/QCA6174/hw2.1/firmware-4.bin': -2
[    3.078868] ath10k_pci 0000:07:00.0: Direct firmware load for ath10k/QCA6174/hw2.1/firmware-3.bin failed with error -2
[    3.078870] ath10k_pci 0000:07:00.0: could not fetch firmware file 'ath10k/QCA6174/hw2.1/firmware-3.bin': -2
[    4.302523] ath10k_pci 0000:07:00.0: qca6174 hw2.1 (0x05010000, 0x003405ff, 168c:003e:11ad:0804 fallback) fw rome-hw2.1-v211-michalk api 2 htt 3.0 wmi 4 cal otp max_sta 32
[    4.302526] ath10k_pci 0000:07:00.0: debug 1 debugfs 1 tracing 0 dfs 0 testmode 0
[    4.378155] ath: EEPROM regdomain: 0x6c
[    4.378158] ath: EEPROM indicates we should expect a direct regpair map
[    4.378160] ath: Country alpha2 being used: 00
[    4.378161] ath: Regpair used: 0x6c
[   10.533056] ath: EEPROM regdomain: 0x8348
[   10.533058] ath: EEPROM indicates we should expect a country code
[   10.533059] ath: doing EEPROM country->regdmn map search
[   10.533060] ath: country maps to regdmn code: 0x3a
[   10.533061] ath: Country alpha2 being used: US
[   10.533061] ath: Regpair used: 0x3a
[   10.533062] ath: regdomain 0x8348 dynamically updated by country IE
piko@piko-Aspire-VN7-591G:~$ iwconfig
eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"optic_piko"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 64:70:02:FD:0F:FC   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=56/70  Signal level=-54 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:8   Missed beacon:0

lo        no wireless extensions.

piko@piko-Aspire-VN7-591G:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 30:65:ec:69:05:dc  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1077 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1077 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:131786 (131.7 KB)  TX bytes:131786 (131.7 KB)

wlan0     Link encap:Ethernet  HWaddr 5c:93:a2:9a:bb:21  
          inet addr:192.168.0.103  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::5e93:a2ff:fe9a:bb21/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3063 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2592 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2132759 (2.1 MB)  TX bytes:437264 (437.2 KB)

piko@piko-Aspire-VN7-591G:~$ lsmod
Module                  Size  Used by
ctr                    16384  1 
ccm                    20480  1 
arc4                   16384  2 
snd_hda_codec_hdmi     53248  1 
joydev                 20480  0 
btusb                  40960  0 
acer_wmi               20480  0 
sparse_keymap          16384  1 acer_wmi
snd_hda_codec_realtek    81920  1 
snd_hda_codec_generic    69632  1 snd_hda_codec_realtek
uvcvideo               90112  0 
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
intel_rapl             20480  0 
iosf_mbi               16384  1 intel_rapl
x86_pkg_temp_thermal    16384  0 
videobuf2_core         53248  1 uvcvideo
intel_powerclamp       20480  0 
coretemp               16384  0 
v4l2_common            16384  1 videobuf2_core
rfcomm                 69632  8 
videodev              159744  3 uvcvideo,v4l2_common,videobuf2_core
hid_multitouch         20480  0 
rtsx_usb_ms            20480  0 
bnep                   20480  2 
kvm_intel             151552  0 
memstick               20480  1 rtsx_usb_ms
bluetooth             491520  22 bnep,btusb,rfcomm
kvm                   479232  1 kvm_intel
crct10dif_pclmul       16384  0 
media                  24576  2 uvcvideo,videodev
snd_hda_intel          36864  6 snd_hda_codec_hdmi
crc32_pclmul           16384  0 
snd_hda_controller     32768  1 snd_hda_intel
ghash_clmulni_intel    16384  0 
snd_hda_codec         143360  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
snd_hwdep              20480  1 snd_hda_codec
aesni_intel           172032  3 
aes_x86_64             20480  1 aesni_intel
snd_pcm               106496  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller
lrw                    16384  1 aesni_intel
gf128mul               16384  1 lrw
glue_helper            16384  1 aesni_intel
ablk_helper            16384  1 aesni_intel
snd_seq_midi           16384  0 
cryptd                 20480  3 ghash_clmulni_intel,aesni_intel,ablk_helper
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
nouveau              1368064  0 
serio_raw              16384  0 
snd_seq                65536  2 snd_seq_midi_event,snd_seq_midi
ath10k_pci             45056  0 
ath10k_core           270336  1 ath10k_pci
ath                    32768  1 ath10k_core
mac80211              643072  1 ath10k_core
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_pcm,snd_seq
lpc_ich                24576  0 
cfg80211              532480  3 ath,mac80211,ath10k_core
compat                 24576  3 cfg80211,mac80211,ath10k_pci
mei_me                 20480  0 
snd                    86016  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
mxm_wmi                16384  1 nouveau
mei                    90112  1 mei_me
i915                 1048576  4 
ttm                    94208  1 nouveau
soundcore              16384  2 snd,snd_hda_codec
drm_kms_helper        126976  2 i915,nouveau
drm                   344064  7 ttm,i915,drm_kms_helper,nouveau
shpchp                 40960  0 
i2c_algo_bit           16384  2 i915,nouveau
ie31200_edac           16384  0 
edac_core              53248  1 ie31200_edac
wmi                    20480  3 acer_wmi,mxm_wmi,nouveau
video                  20480  3 i915,acer_wmi,nouveau
mac_hid                16384  0 
nls_iso8859_1          16384  1 
soc_button_array       16384  0 
parport_pc             32768  0 
ppdev                  20480  0 
lp                     20480  0 
parport                45056  3 lp,ppdev,parport_pc
usbhid                 53248  0 
hid                   110592  2 hid_multitouch,usbhid
rtsx_usb_sdmmc         28672  0 
rtsx_usb               24576  2 rtsx_usb_sdmmc,rtsx_usb_ms
ahci                   36864  3 
r8169                  81920  0 
libahci                32768  1 ahci
mii                    16384  1 r8169
piko@piko-Aspire-VN7-591G:~$ cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1
piko@piko-Aspire-VN7-591G:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0
piko@piko-Aspire-VN7-591G:~$ iwlist chan
eth0      no frequency information.

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
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
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
          Channel 132 : 5.66 GHz
          Channel 136 : 5.68 GHz
          Channel 140 : 5.7 GHz
          Channel 149 : 5.745 GHz
          Channel 153 : 5.765 GHz
          Channel 157 : 5.785 GHz
          Channel 161 : 5.805 GHz
          Channel 165 : 5.825 GHz
          Current Frequency:2.462 GHz (Channel 11)

lo        no frequency information.

piko@piko-Aspire-VN7-591G:~$ sudo iwlist scan
[sudo] password for piko: 
eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 64:70:02:FD:0F:FC
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=53/70  Signal level=-57 dBm  
                    Encryption key:on
                    ESSID:"optic_piko"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000c01151a6ed4
                    Extra: Last beacon: 76ms ago
                    IE: Unknown: 000A6F707469635F70696B6F
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A6E181EFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B070000000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DDAB0050F204104A0001101044000101103B0001031047001063041253101920061228647002FD0FFC1021001D54502D4C494E4B20546563686E6F6C6F6769657320436F2E204C74642E1023000A544C2D5752313034324E1024000D45562D323031302D30392D32301042000F3132333435363738393031323334371054000800060050F20400011011001B576972656C65737320526F7574657220544C2D5752313034324E44100800020086
                    IE: Unknown: DD1E00904C336E181EFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B070000000000000000000000000000000000000000
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: DD0600E04C020160
          Cell 02 - Address: 00:1B:FC:22:40:8A
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:on
                    ESSID:"XXX"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000907c0503e
                    Extra: Last beacon: 76ms ago
                    IE: Unknown: 0003585858
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030105
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180201F0000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

lo        Interface doesn't support scanning.



```

---

### Post by praseodym on 2015-10-04
Change the encryption mode of your router to pure WPA2-AES (CCMP).

---

### Post by Matus_Pikuliak on 2015-10-05
I am currently on different router and the problem is gone, so I guess you are right about that. Thank you

---

### Post by Matus_Pikuliak on 2016-05-06
Hi, I am having the same problem. The link with driver does not work anymore. Is it accessible somewhere else?

```
wget kernel.ubuntu.com/~adamlee/lp1383184/ath10k-dkms_1.1_all.deb
```

---

### Post by jeremy31 on 2016-05-06
Please run the wireless script and post results

---

### Post by Matus_Pikuliak on 2016-05-06
Hi, I solved my problems with that driver back in October. My disk failed and I am currently reinstalling my system so that is why I need it. I am posting the wireless script nevertheless:

```


########## wireless info START ##########

Report from: 06 May 2016 18:06 CEST +0200

Booted last: 06 May 2016 15:56 CEST +0200

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.4 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 4.1.6-040106-generic #201508170230 SMP Mon Aug 17 06:32:14 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

07:00.0 Network controller [0280]: Qualcomm Atheros QCA6174 802.11ac Wireless Network Adapter [168c:003e] (rev 20)
    Subsystem: Lite-On Communications Inc Device [11ad:0804]
    Kernel driver in use: ath10k_pci

08:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:0123]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 004 Device 002: ID 8087:8000 Intel Corp. 
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 8087:8008 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 04f2:b474 Chicony Electronics Co., Ltd 
Bus 001 Device 004: ID 06cb:2970 Synaptics, Inc. touchpad
Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 006: ID 04ca:3011 Lite-On Technology Corp. 
Bus 001 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

acer_wmi               20480  0 
sparse_keymap          16384  1 acer_wmi
ath10k_pci             40960  0 
ath10k_core           258048  1 ath10k_pci
ath                    32768  1 ath10k_core
mac80211              745472  1 ath10k_core
mxm_wmi                16384  1 nouveau
cfg80211              552960  3 ath,mac80211,ath10k_core
wmi                    20480  3 acer_wmi,mxm_wmi,nouveau
video                  20480  3 i915,acer_wmi,nouveau

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'eth0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:453743 errors:0 dropped:0 overruns:0 frame:0
          TX packets:257809 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:631766642 (631.7 MB)  TX bytes:23107115 (23.1 MB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       825     1  0 15:56 ?        00:00:00 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
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
    Address:         192.168.1.103
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1

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

Region: Europe/Bratislava (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

##### module infos ######################

[ath10k_pci]
filename:       /lib/modules/4.1.6-040106-generic/kernel/drivers/net/wireless/ath/ath10k/ath10k_pci.ko
firmware:       ath10k/QCA988X/hw2.0/board.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-3.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-2.bin
firmware:       ath10k/QCA988X/hw2.0/firmware.bin
license:        Dual BSD/GPL
description:    Driver support for Atheros QCA988X PCIe devices
author:         Qualcomm Atheros
srcversion:     1A070BF5DF113EE3CEA4239
depends:        ath10k_core
intree:         Y
vermagic:       4.1.6-040106-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        35:54:79:EA:57:2B:A7:36:1F:E0:C7:5A:06:C6:1F:90:AE:79:79:1E
sig_hashalgo:   sha512
parm:           irq_mode:0: auto, 1: legacy, 2: msi (default: 0) (uint)
parm:           reset_mode:0: auto, 1: warm only (default: 0) (uint)

[ath10k_core]
filename:       /lib/modules/4.1.6-040106-generic/kernel/drivers/net/wireless/ath/ath10k/ath10k_core.ko
license:        Dual BSD/GPL
description:    Core module for QCA988X PCIe devices.
author:         Qualcomm Atheros
srcversion:     1925B7D4BC68962DD81F759
depends:        mac80211,cfg80211,ath
intree:         Y
vermagic:       4.1.6-040106-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        35:54:79:EA:57:2B:A7:36:1F:E0:C7:5A:06:C6:1F:90:AE:79:79:1E
sig_hashalgo:   sha512
parm:           debug_mask:Debugging mask (uint)
parm:           uart_print:Uart target debugging (bool)
parm:           skip_otp:Skip otp failure for calibration in testmode (bool)

[ath]
filename:       /lib/modules/4.1.6-040106-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     3704DB6ADA7793B03A1128D
depends:        cfg80211
intree:         Y
vermagic:       4.1.6-040106-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        35:54:79:EA:57:2B:A7:36:1F:E0:C7:5A:06:C6:1F:90:AE:79:79:1E
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/4.1.6-040106-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     74E30AABABDE7CAEA5C2EFE
depends:        cfg80211
intree:         Y
vermagic:       4.1.6-040106-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        35:54:79:EA:57:2B:A7:36:1F:E0:C7:5A:06:C6:1F:90:AE:79:79:1E
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.1.6-040106-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     7A34537645016AD6A2B4091
depends:        
intree:         Y
vermagic:       4.1.6-040106-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        35:54:79:EA:57:2B:A7:36:1F:E0:C7:5A:06:C6:1F:90:AE:79:79:1E
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[ath10k_pci]
irq_mode: 0
reset_mode: 0

[ath10k_core]
debug_mask: 0
skip_otp: N
uart_print: N

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
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
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

##### dmesg #############################

########## wireless info END ############

```

---

### Post by jeremy31 on 2016-05-06
It should work after adding the firmware with the kernel you have.  If I remember correctly Adam Lee's DKMS installed backported kernel modules and some firmware
```
wget https://mirrors.kernel.org/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.157_all.deb
sudo dpkg -i linux-firmware_1.157_all.deb
```

Reboot

---

### Post by Matus_Pikuliak on 2016-05-06
Nope, this doesn't seem to work - no wifi options in connections. If I remember correctly last time the only thing I did was installing the driver.

```


########## wireless info START ##########

Report from: 07 May 2016 00:20 CEST +0200

Booted last: 07 May 2016 00:17 CEST +0200

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.4 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 4.1.6-040106-generic #201508170230 SMP Mon Aug 17 06:32:14 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

07:00.0 Network controller [0280]: Qualcomm Atheros QCA6174 802.11ac Wireless Network Adapter [168c:003e] (rev 20)
    Subsystem: Lite-On Communications Inc Device [11ad:0804]
    Kernel driver in use: ath10k_pci

08:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:0123]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 004 Device 002: ID 8087:8000 Intel Corp. 
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 8087:8008 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 04f2:b474 Chicony Electronics Co., Ltd 
Bus 001 Device 004: ID 06cb:2970 Synaptics, Inc. touchpad
Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 006: ID 04ca:3011 Lite-On Technology Corp. 
Bus 001 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

acer_wmi               20480  0 
sparse_keymap          16384  1 acer_wmi
ath10k_pci             40960  0 
ath10k_core           258048  1 ath10k_pci
ath                    32768  1 ath10k_core
mac80211              745472  1 ath10k_core
cfg80211              552960  3 ath,mac80211,ath10k_core
mxm_wmi                16384  1 nouveau
wmi                    20480  3 acer_wmi,mxm_wmi,nouveau
video                  20480  3 i915,acer_wmi,nouveau

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'eth0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:611 errors:0 dropped:0 overruns:0 frame:0
          TX packets:688 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:367139 (367.1 KB)  TX bytes:97794 (97.7 KB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       779     1  0 00:17 ?        00:00:00 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
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
    Address:         192.168.1.103
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1

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

Region: Europe/Bratislava (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

##### module infos ######################

[ath10k_pci]
filename:       /lib/modules/4.1.6-040106-generic/kernel/drivers/net/wireless/ath/ath10k/ath10k_pci.ko
firmware:       ath10k/QCA988X/hw2.0/board.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-3.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-2.bin
firmware:       ath10k/QCA988X/hw2.0/firmware.bin
license:        Dual BSD/GPL
description:    Driver support for Atheros QCA988X PCIe devices
author:         Qualcomm Atheros
srcversion:     1A070BF5DF113EE3CEA4239
depends:        ath10k_core
intree:         Y
vermagic:       4.1.6-040106-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        35:54:79:EA:57:2B:A7:36:1F:E0:C7:5A:06:C6:1F:90:AE:79:79:1E
sig_hashalgo:   sha512
parm:           irq_mode:0: auto, 1: legacy, 2: msi (default: 0) (uint)
parm:           reset_mode:0: auto, 1: warm only (default: 0) (uint)

[ath10k_core]
filename:       /lib/modules/4.1.6-040106-generic/kernel/drivers/net/wireless/ath/ath10k/ath10k_core.ko
license:        Dual BSD/GPL
description:    Core module for QCA988X PCIe devices.
author:         Qualcomm Atheros
srcversion:     1925B7D4BC68962DD81F759
depends:        mac80211,cfg80211,ath
intree:         Y
vermagic:       4.1.6-040106-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        35:54:79:EA:57:2B:A7:36:1F:E0:C7:5A:06:C6:1F:90:AE:79:79:1E
sig_hashalgo:   sha512
parm:           debug_mask:Debugging mask (uint)
parm:           uart_print:Uart target debugging (bool)
parm:           skip_otp:Skip otp failure for calibration in testmode (bool)

[ath]
filename:       /lib/modules/4.1.6-040106-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     3704DB6ADA7793B03A1128D
depends:        cfg80211
intree:         Y
vermagic:       4.1.6-040106-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        35:54:79:EA:57:2B:A7:36:1F:E0:C7:5A:06:C6:1F:90:AE:79:79:1E
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/4.1.6-040106-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     74E30AABABDE7CAEA5C2EFE
depends:        cfg80211
intree:         Y
vermagic:       4.1.6-040106-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        35:54:79:EA:57:2B:A7:36:1F:E0:C7:5A:06:C6:1F:90:AE:79:79:1E
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.1.6-040106-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     7A34537645016AD6A2B4091
depends:        
intree:         Y
vermagic:       4.1.6-040106-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        35:54:79:EA:57:2B:A7:36:1F:E0:C7:5A:06:C6:1F:90:AE:79:79:1E
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[ath10k_pci]
irq_mode: 0
reset_mode: 0

[ath10k_core]
debug_mask: 0
skip_otp: N
uart_print: N

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
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
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

##### dmesg #############################

[   93.863924] r8169 0000:08:00.0 eth0: link up
[   93.863933] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  150.666337] r8169 0000:08:00.0 eth0: link down (repeated 2 times)
[  165.227295] r8169 0000:08:00.0 eth0: link up

########## wireless info END ############


```

---

### Post by jeremy31 on 2016-05-06
This is very strange, please post ```
dkms status; dmesg | grep ath10k
```

Are you manually loading ath10k_pci?  If you are then backports should fix this
```
sudo apt-get install build-essential git linux-headers-generic
wget https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v4.4.2/backports-4.4.2-1.tar.gz
tar -zxvf backports-4.4.2-1.tar.gz
cd backports-4.4.2-1
make defconfig-wifi
make
sudo make install
```

Reboot and I hope good news arrives

---

### Post by Matus_Pikuliak on 2016-05-06
Thank you a lot, wi-fi works now after I installed backports :)

---

### Post by jeremy31 on 2016-05-06
As a downside, if you update the kernel you will need to reinstall the backports if the newer kernel doesn't support your wifi by
```
cd backports-4.4.2-1
make clean
make defconfig-wifi
make
sudo make install
```

I think this issue was fixed in Ubuntu 15.10, so when you decide to update to 16.04 it should just work

---

